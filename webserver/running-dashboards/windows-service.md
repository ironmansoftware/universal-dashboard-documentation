# Windows Service

{% hint style="info" %}
Universal Dashboard is now a part of PowerShell Universal. This documentation is for reference to the v2 version of Universal Dashboard and is no longer maintained. PowerShell Universal Documentation can be found [here](https://docs.ironmansoftware.com).
{% endhint %}

## Windows Service

Universal Dashboard can be run as a Windows service. This is accomplished using [NSSM](https://nssm.cc/). You will need to install the Universal Dashboard module in a location that the account running the service has access to.

```text
Install-Module UniversalDashboard -Scope AllUsers
```

The script that you are using should specify the -Port and -Wait parameters. You can use either `Start-UDDashboard` or `Start-UDRestApi`.

```text
Import-Module UniversalDashboard

Start-UDRestApi -Port 8080 -Endpoint @(
    New-UDEndpoint -url "user" -Method "GET" -Endpoint {
        @("test","test2","test3") | ConvertTo-Json
    }
) -Wait
```

To install a new service with NSSM, you can use the following command line.

```text
 .\nssm install "Universal Dashboard" powershell.exe C:\users\adamr\desktop\dashboard.ps1
```

