# Web Server

{% hint style="info" %}
Universal Dashboard is now a part of PowerShell Universal. This documentation is for reference to the v2 version of Universal Dashboard and is no longer maintained. PowerShell Universal Documentation can be found [here](https://docs.ironmansoftware.com).
{% endhint %}

## Web Server

The Universal Dashboard webserver is based on the ASP.NET Core Kestrel webserver. It's cross-platform and can be hosted in numerous different ways. See [Running Dashboards](https://github.com/ironmansoftware/universal-dashboard-documentation/tree/17bb33e1a84341bfd1084e5d3d2ff535c7f2dbe7/webserver/running-dashboards/README.md) to learn more how to start the webserver.

### Web Server Options

#### HTTPS

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

**HTTP to HTTPS redirection**

You can enable HTTP to HTTPS redirection by specifying a port for HTTP \(default 80\) and a port for HTTPS \(default 443\). If the user visits the HTTP port, they will automatically be redirected to the HTTPS port. The redirection happens via a `308` permanent redirect status code from the web server.

```text
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

#### Listening Address

By default, the web server will listen on all available addresses. You can adjust the listen addresses by using the `-ListenAddress` parameter and passing in a valid IP Address. This is helpful when building desktop apps, like `UDForge`, that should not open a web server to listen beyond the local machine.

```text
Start-UDDashboard -Port 10000 -ListenAddress '127.0.0.1'
```

