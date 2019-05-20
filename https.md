# HTTPS

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

