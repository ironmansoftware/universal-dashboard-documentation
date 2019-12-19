# Endpoints

Endpoints define the functionality that is executed with in the Universal Dashboard server. They can call any PowerShell script to retrieve data and send it to the client's web browser. Components that support server-side functionality will define an `Endpoint` parameter.

## Getting Started with Endpoints

Endpoints are simple PowerShell script blocks but do have some unique properties. The endpoints are executed within the Universal Dashboard service in a runspace pool that does not share the same execution environment as the runspace that started the dashboard.

Modules, functions and variables imported into the default runspace will automatically be imported into the sub-runspaces created by UD. You can configure which entities are imported by using `New-UDEndpointInitialization`. See the section below on Working with Variables, Functions and Modules for more information. 

Endpoints should return data in the manner that the component they are defined on expects. Many cmdlets, like `New-UDMonitor`, have a matching output cmdlet you should use, like `Out-UDMonitorData`, to return data from you endpoint.

```text
New-UDMonitor -Title "Downloads per second" -Type Line -Endpoint {
     Get-Random -Minimum 0 -Maximum 10 | Out-UDMonitorData
}
```

In the above example, the `Endpoint` parameter's script block is called whenever a user visits the website or the UDMonitor refreshes its data. Keep this in mind when defining script block functionality because long running endpoints can cause slow responses within your web site.

## Working with Variables, Functions and Modules

Universal Dashboard will attempt to copy variables from one scope to another when endpoints are defined. This means that global variables _may_ end up in the endpoint's runspace and be available for use. Some global variables, such as PowerCLI default server variables, do not behave well when copied in this manner.

To better control which entities get imported into the sub-runspaces, `New-UDDashboard` exposes an `EndpointInitialization` parameter. You can use `New-UDEndpointInitialization` to create a new initial session state for the runspaces created within UD. This is a good place to define any modules, functions or variables you'd like defined globally. 

In the below example, I'm defining a variable and importing a module that I would like to use later in the script.

```text
$TargetDrive = "C:\"
$Dashboard = New-UDDashboard -Title "Variables, Modules and Functions" -Content {
    New-UDCounter -Title "Using PSCX and my Variable" -Endpoint {
        Get-DriveInfo | Where-Object Name -eq $TargetDrive | Select -Expand TotalSize
    }
} -EndpointInitialization (
    New-UDEndpointInitialization -Module 'Pcsx' -Variable 'TargetDrive'
)
Start-UDDashboard -Dashboard $Dashboard
```

Running the dashboard will yield the following result.

![](../.gitbook/assets/endpoint-initialization-script.png)

## Debugging Endpoints

Since Endpoints are just PowerShell scripts, there are bound to be issues. Terminating errors within endpoints will result in the dashboard displaying an error in the UI.

![](../.gitbook/assets/displaying-an-error.png)

Sometimes this is enough information to successfully correct your script and move on. If you are still experiencing issues, please review the section on [debugging](../debugging.md).

