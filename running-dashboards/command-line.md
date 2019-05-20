# Command Line

## Starting a Dashboard

Dashboards can be run from the command line by using the `Start-UDDashboard` cmdlet. This cmdlet accepts a port and dashboard to run. The port can be any valid port number not currently being used by the system. Multiple dashboards can be run in the same PowerShell session on different ports.

Running the following cmdlet would start a dashboard listening on port 1000.

```text
$MyDashboard = New-UDDashboard -Title "Hello, World" -Content {
    New-UDCard -Title "Hello, Universal Dashboard" 
}

Start-UDDashboard -Port 1000 -Dashboard $MyDashboard
```

You should be able to view your dashboard by visiting [http://localhost:1000](http://localhost:1000)

## Getting Running Dashboards

Using `Get-UDDashboard`, you can return all the dashboards running in the current PowerShell session. This does not list dashboards in different processes. It only lists dashboards running in the current process.

```text
PS> Get-UDDashboard

Name       Port Running
----       ---- -------
Dashboard0 1000    True
```

## Stopping Dashboards

Dashboards can be stopped with `Stop-UDDashboard`. This cmdlet will stop the ASP.NET web service and release the port that the dashboard is listening on. To stop all running dashboards for a process, you can pipe from `Get-UDDashboard`.

```text
Get-UDDashboard | Stop-UDDashboard
```

### Auto Reload

Auto-reloading a dashboard allows for faster dashboard development. When you have a script that contains `Start-UDDashboard` and specify the `-AutoReload` parameter, the dashboard will reload automatically when changes are made to the script. Simply save your script and the running dashboard will refresh. If you have a webpage open to your dashboard, it will reload automatically. It provides instant feedback with changes to your dashboard.

Currently, if there is an error within your script and the auto-reload fails, you will need to start the dashboard manually.

For example, assume you have a dashboard defined in `dashboard.ps1`.

```text
$MyDashboard = New-UDDashboard -Title "Hello, World" -Content {
    New-UDCard -Title "Hello, Universal Dashboard" 
}

Start-UDDashboard -Port 1000 -Dashboard $MyDashboard -AutoReload
```

You can now run `dashboard.ps1`.

```text
PS> .\dashboard.ps1
```

Since you are running a dashboard saved as a script, `-AutoReload` will restart the server as soon as there is a change to `dashboard.ps1`. If you made the following change and saved the file, the web page would reload and your dashboard would be updated.

```text
$MyDashboard = New-UDDashboard -Title "Hello, Galaxy" -Content {
    New-UDCard -Title "Hello, Universal Dashboard" 
}

Start-UDDashboard -Port 1000 -Dashboard $MyDashboard -AutoReload
```

In addition to `-AutoReload`, you can also manually reload your dashboard with `Get-UDDashboard`, `Stop-UDDashboard` and `Start-UDDashboard`.

```text
PS> Get-UDDashboard | Stop-UDDashboard
PS> $MyDashboard = New-UDDashboard -Title "Hello, World" -Content {
    New-UDCard -Title "Hello, Universal Dashboard" 
}

PS> Start-UDDashboard -Port 1000 -Dashboard $MyDashboard
```

### Wait

The Wait parameter is specified if you would like the current PowerShell execution to block while the dashboard is running. This parameter is required for running in Azure and IIS.

