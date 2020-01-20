# IIS

To run a dashboard in IIS, you will need to configure an application pool and website just as you would with any other IIS web application. 

In addition to the standard IIS configuration, you will need the following.

* [ASP.NET Core Hosting Bundle](https://dotnet.microsoft.com/download/dotnet-core/thank-you/runtime-aspnetcore-2.2.8-windows-hosting-bundle-installer)
* [WebSocket Protocol](https://docs.microsoft.com/en-us/iis/get-started/whats-new-in-iis-8/iis-80-websocket-protocol-support)

#### OS limitations

It's important to note the difference between client OS and server OS:

* Client OS: have a max on concurrent connections, as it's limited to 10 max.
* Server OS: have no limitation. \(except standard defined by IIS\)

## Configuring a site for Universal Dashboard

To host a Universal Dashboard website, you'll want to install the UniversalDashboard module to a location that the ApplicationPool user has access to. The default application pool user will not be able to access anything outside of wwwroot. You will need to either install Universal Dashboard to that location or provide additional access to an alternate folder for that user. 

The recommended approach is provide a location on the `$Env:PSModulePath` that enables the user to load modules from. For example, you could have all your modules stored in `C:\PowerShellModules\` and then you would add that path to the `$Env:PSModulePath` environment variable. If you configure it in this manner, you'll be able to upgrade Universal Dashboard in a single place and all your websites will load the new module.

Once you have the UniversalDashboard module installed, you will need copy the `web.config` file included with UD as well as your script to the websites folder. You can click Explore to view this folder. 

![](../../.gitbook/assets/explore-iis.png)

The `web.config` file should start PowerShell.exe or Pwsh.exe. As an argument to the process, you'll want to include the dashboard script. Edit the `aspNetCore` node in the `web.config` file to include this information.

```text
<aspNetCore processPath="C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe" arguments=".\dashboard.ps1" />
```

Create a `.ps1` file and place it in the `wwwroot` folder. The dashboard should contain a dashboard definition and a call to `Start-UDDashboard` with the `-Wait` parameter specified.

```text
 Start-UDDashboard -Wait -Dashboard (
    New-UDDashboard -Title "Hello, IIS" -Content {
        New-UDCard -Title "Hello, IIS"
    }
)
```

Your website directory should now contain a `web.config` file and a PowerShell script that will execute when accessing the website. 

![](../../.gitbook/assets/image%20%2849%29.png)

Navigate to the IIS website in your browser and you should see Universal Dashboard running.

![](../../.gitbook/assets/iis-running.png)

## Creating Nested IIS Sites

{% hint style="info" %}
Requires Universal Dashboard 2.3 or later
{% endhint %}

To create a nested IIS site, follow the same steps as above but nest your UD site beneath another site. You will have to make one change to the UD installation in this type of configuration. Within the UD folder, find the `index.html` file in the `client` folder.

Within this file, change the `base` 's `href` attribute to match the relative URL of your UD installation. If you wanted to have the URL resolve to `http://myServer:8080/dashboards/dashboard`you would set the value of the `href` attribute to `/dashboards/dashboard/`.

For the URL of the two script files, you will need to remove the preceding `/` .

An example `index.html` looks like this.

```text
<!DOCTYPE html>
<html>
<head>
    <base href="/dashboards/dashboard/"/>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>PowerShell Universal Dashboard</title>
<link rel="shortcut icon" href="favicon.ico"></head>
<body>
    <div id="app" class="app"/>
    <script type="text/javascript" src="main.9be8329c352d5b5e7801.bundle.js"></script><script type="text/javascript" src="vendor.9be8329c352d5b5e7801.bundle.js"></script></body>
</html>
```

## Licensing

The license should be named license.lic and placed in the `net472` or the `netstandard2.0` folder within the module installation directory. This will ensure that the license is persistent throughout restarts.

## Troubleshooting

Check the Application Log in the Event Viewer for .NET runtime errors. You can also run your script from the command line to view errors that may be present when starting the dashboard that may be preventing it from loading in IIS. 

Some other tips from the community:

1. Build Verbose Logging Into your solution
2. Build Verbose Error Logging **AND** handling into your solution
3. Ensure that your final syntax is correct. There are some nuances that yield different results when running as a script vs interactively.

### Logging

You can enable logging by specifying a path in the `web.config` file. You can change the `stdoutLogFile` path to a location that IIS has the permissions to write to. You can then add `Enable-UDLogging` to the top of your `dashboard.ps1` file to turn on console logging for Universal Dashboard. This is a complete `web.config` example

```text
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <!--
    Configure your application settings in appsettings.json. Learn more at http://go.microsoft.com/fwlink/?LinkId=786380
  -->
  <system.webServer>
    <security>
      <!-- <requestFiltering removeServerHeader ="true" /> -->
    </security>
    <handlers>
      <add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />
    </handlers>
    <aspNetCore processPath=".\net472\universaldashboard.server.exe" arguments="" stdoutLogEnabled="true" stdoutLogFile="C:\LogFiles\stdout" forwardWindowsAuthToken="false" />
    <httpProtocol>
      <customHeaders>
        <remove name="X-Powered-By" />
      </customHeaders>
    </httpProtocol>  
  </system.webServer>
</configuration>
```

Log files will then be written and timestamped to the directory and name you select.

