# Windows

{% hint style="info" %}
Not available in Community Edition.
{% endhint %}

To use Windows Authentication, you will need to [host Universal Dashboard in IIS](https://github.com/adamdriscoll/universal-dashboard-documentation/tree/15ca122d89e54271ad0661a8e75dd3cf33c0520c/security/running-dashboards/iis.md).

After configuring UD to run in IIS, you will need to [enable Windows Authentication on your site](https://docs.microsoft.com/en-us/aspnet/core/security/authentication/windowsauth?view=aspnetcore-2.2#iis-configuration).

Next, you need to ensure that your `web.config` file has `forwardWindowsAuthToken` set to true.

```text
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <!--
    Configure your application settings in appsettings.json. Learn more at http://go.microsoft.com/fwlink/?LinkId=786380
  -->
  <system.webServer>
    <handlers>
      <add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />
    </handlers>
    <aspNetCore processPath=".\net472\universaldashboard.server.exe" arguments="" stdoutLogEnabled="true" stdoutLogFile="\\?\%home%\LogFiles\stdout" forwardWindowsAuthToken="true"  />
  </system.webServer>
</configuration>
```

The last step is to configure your dashboard to use Windows authentication. Specify a new authentication method with the `-Windows` switch parameter and pass it to `New-UDLoginPage`. Include the `-PassThru` parameter to avoid having the login page shown. You should now be able to login to your UD site as the current user.

```text
Start-UDDashboard -Content {
    $Auth = New-UDAuthenticationMethod -Windows
    $LoginPage = New-UDLoginPage -AuthenticationMethod @($Auth) -PassThru

    New-UDDashboard -Title "Line" -Content { 
        New-UDRow -Columns {
            New-UDColumn -Size 12 -Endpoint  {
                New-UDHeading -Text "Logged in as $user"
            }
        }
    } -LoginPage $LoginPage 
} -Wait -AllowHttpForLogin
```

## Claims-Based Authorization with Windows Authentication 

You can use claims-based authorization with Windows Authentication by use the `$UserPrincipal.HasClaims()` method. There are several claims that will be provided by Windows to the Universal Dashboard authorization system. You can find a [list here](https://docs.microsoft.com/en-us/windows-server/identity/ad-fs/technical-reference/the-role-of-claims). 

Here is an example of a dashboard that uses claims-based authorization and Windows authentication to verify that a user has particular group membership before showing a page. 

```text

$AccountingPolicy = New-UDAuthorizationPolicy -Name "Accounting" -Endpoint {
    param($ClaimsPrincipal)
    $ClaimsPrincipal.HasClaim("http://schemas.microsoft.com/ws/2008/06/identity/claims/groupsid", "S-1-5-21-931991156-4110752182-3137855529-1012") 
}

$AdminPolicy = New-UDAuthorizationPolicy -Name "Admins" -Endpoint {
    param($ClaimsPrincipal)
    $ClaimsPrincipal.HasClaim("http://schemas.microsoft.com/ws/2008/06/identity/claims/groupsid", "S-1-5-21-931991156-4110752182-3137855529-1011")
}

$AuthMethod = New-UDAuthenticationMethod -Windows
$LoginPage = New-UDLoginPage -AuthenticationMethod $AuthMethod -PassThru -AuthorizationPolicy @($AccountingPolicy, $AdminPolicy)

$AdminPage = New-UDPage -Name "Admins" -AuthorizationPolicy "Admins" -Content {
    New-UDCard -Title "Admins" -Content {}
}

$AccountingPage = New-UDPage -Name "Accounting" -AuthorizationPolicy "Accounting" -Content {
    New-UDCard -Title "Accounting" -Content {}
}

$Dashboard = New-UDDashboard -LoginPage $LoginPage -Title "Hi" -Pages @($AdminPage, $AccountingPage)

Start-UDDashboard -Wait -Dashboard $Dashboard -AllowHttpForLogin

```

