# Windows Service

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

