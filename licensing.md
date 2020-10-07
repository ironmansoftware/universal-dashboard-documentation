# Licensing

{% hint style="info" %}
Universal Dashboard is now a part of PowerShell Universal. This documentation is for reference to the v2 version of Universal Dashboard and is no longer maintained. PowerShell Universal Documentation can be found [here](https://docs.ironmansoftware.com).
{% endhint %}

## Licensing

{% hint style="info" %}
This page does not apply to Universal Dashboard Community Edition
{% endhint %}

### Install via Set-UDLicense

`Set-UDLicense` is used to install a Universal Dashboard license. The `-License` parameter expects the contents of a license file. To install a license, you the following command line.

```text
Set-UDLicense -License (Get-Content .\license.txt -Raw)
```

### Install via Environment Variable

If you set the `%UDLICENSE%` environment variable, UD will load the license from it. This is good for cloud-based deployments.

```text
$Env:UDLICENSE = (Get-Content .\license.txt -Raw)
```

### Install via ApplicationData deployment

One of the places that UD will attempt to load a license is from the ApplicationData folder. This folder is different depending on the operating system you are running. You will have to create the following folder and file structure. The contents of `license.lic` should be the license contents you received after purchase.

```text
WIN: C:\Users\adam\AppData\Roaming\UniversalDashboard/license.lic
LIN: /home/adam/.config/UniversalDashboard/license.lic
OSX: /Users/adam/.config/UniversalDashboard/license.lic
```

### Install via bin deployment

Another place that UD looks for a license during startup is within the binary folder for UD. If you are running Windows PowerShell, this will be the `/UniveraslDashboard/net472` folder. If you are running PowerShell Core, this will be the `/UniversalDashboard/netstandard2.0` folder. The file should be named `license.lic` and include the contents of the license you received after purchase.

