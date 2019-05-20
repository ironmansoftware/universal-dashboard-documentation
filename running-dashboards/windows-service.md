# Windows Service

## Required Version: 1.6.0

## Date Modified: 5/8/2018

Universal Dashboard can be run as a Windows service. This is accomplished using `Publish-UDDashboard`.

## Creating a dashboard to run as a service

This sample dashboard is an example of a dashboard that can run as a service.

```text
$Dashboard = New-UDDashboard -Title "Dashboard as a Service" -Content {
}

Start-UDDashboard -Port 10000 -Dashboard $Dashboard
```

This dashboard should be saved as `dashboard.ps1`. Unlike when publishing for Azure or IIS, do not use the `-Wait` parameter.

## Publishing a dashboard service

To publish a `dashboard.ps1` file as a service, you can use `Publish-UDDashboard`.

```text
Publish-UDDashboard -DashboardFile ".\dashboard.ps1"
```

`Publish-UDDashboard` will copy the dashboard.ps1 file into the UniversalDashboard module folder and then register `UniversalDashboard.exe` as a service using `sc.exe`. The service is set to automatic by default but using the `-Manual` switch you can set it to Manual.

If you want to deploy the entire UD module to another folder, use the `-TargetPath` parameter to deploy the `dashboard.ps1` and Universal Dashboard module to a target folder. The service will be installed from there.

Running `Publish-UDDashboard` multiple times will result in the service being deleted using `sc.exe` and then reinstalled.

