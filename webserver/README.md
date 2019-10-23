The Universal Dashboard webserver is based on the ASP.NET Core Kestrel webserver. It's cross-platform and can be hosted in numerous different ways. See [Running Dashboards](./running-dashboards/README.md) to learn more how to start the webserver. 

## Web Server Options 

### HTTPS

Universal Dashboard supports HTTPS. In order to enable HTTPS, you can specify a certificate file and password or a X509Certificate2 returned from the Certificate provider in PowerShell.

To enable HTTPS, simply specify the `-CertificateFile` and `-CertificatePassword` or `-Certificate` parameter on `Start-UDDashboard`.

```text
$cert = ( Get-ChildItem -Path cert:\LocalMachine\My\2BB51C6FF080B51FCA6D52F0B8B4E5369732AE23 )

Start-UDDashboard -Content {
    New-UDDashboard -Title "Secure Dashboard" -Content {
        New-UDElement -Tag "h1" -Content { "Super Secure" }
    }
} -Port 10000 -Certificate $cert
```

The dashboard will now be available on HTTPS and no longer available on HTTP.

#### HTTP to HTTPS redirection 

You can enable HTTP to HTTPS redirection by specifying a port for HTTP (default 80) and a port for HTTPS (default 443). If the user visits the HTTP port, they will automatically be redirected to the HTTPS port. The redirection happens via a `308` permanent redirect status code from the web server. 

```
$Dashboard = Start-UDDashboard -Port 10001 -HttpsPort 10002 -Certificate $Cert

try 
{
    $Request = Invoke-WebRequest http://localhost:10001/dashboard
}
catch 
{
    $_.Exception.Response.StatusCode | should be 308
}

$Request = Invoke-WebRequest https://localhost:10002/dashboard
$Request.StatusCode | Should be 200
```

