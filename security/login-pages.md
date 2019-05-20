# Login Pages

{% hint style="info" %}
Not available in Community Edition. 
{% endhint %}

Login pages allow you to create dashboards that require authentication to access. You can define your own authentication endpoint to perform the authentication yourself or use a third party OAuth provider to do so. To create your login page, you can use the New-UDLoginPage and LoginPage parameter of New-UDDashboard.

```text
$Dashboard = New-UDDashboard -LoginPage $LoginPage -Page @(
    $MyDashboardPage
)
```

![](https://github.com/adamdriscoll/universal-dashboard-documentation/tree/af4316e3e00472681e93b097c7d9de94f48e4d60/security/.gitbook/assets/login-page.png)

## Authentication Methods

You can use one or more authentication methods for a login page. UD currently supports the following authentication methods.

* [Forms](authentication/forms.md)
* OAuth
  * [Facebook](authentication/oauth/facebook.md)
  * [Google](authentication/oauth/google.md)
  * [Microsoft](authentication/oauth/microsoft.md)
  * [Twitter](authentication/oauth/twitter.md)

To specify an authentication method for a login page, use the `New-UDAuthenticationMethod` cmdlet.

```text
 $AuthenticationMethod = New-UDAuthenticationMethod -Endpoint {
    param([PSCredential]$Credentials)

    if ($Credentials.UserName -eq "Adam" -and $Credentials.GetNetworkCredential().Password -eq "SuperSecretPassword") {
        New-UDAuthenticationResult -Success -UserName "Adam"
    }

    New-UDAuthenticationResult -ErrorMessage "You aren't Adam!!!"
}

$LoginPage = New-UDLoginPage -AuthenticationMethod $AuthenticationMethod
```

To specify multiple authentication methods, just pass an array of authentication methods to the `New-UDLoginPage` cmdlet.

```text
$AuthenticationMethod = @()
$AuthenticationMethod += New-UDAuthenticationMethod -AppId 1234 -AppSecret Abc123 -Provider Facebook
$AuthenticationMethod += New-UDAuthenticationMethod -AppId 1234 -AppSecret Abc123 -Provider Twitter
$AuthenticationMethod += New-UDAuthenticationMethod -AppId 1234 -AppSecret Abc123 -Provider Google
$AuthenticationMethod += New-UDAuthenticationMethod -AppId 1234 -AppSecret Abc123 -Provider Microsoft
$AuthenticationMethod += New-UDAuthenticationMethod -Endpoint {

}

$LoginPage = New-UDLoginPage -AuthenticationMethod $AuthenticationMethod
```

## Customizing a Login Page

There are several aspects of the login page you can customize to meet your branding and color preferences.

* Logo - Use New-UDImage to specify the logo you wish to show above the login dialog. 
* PageBackgroundColor - The background color of the page. This can be any hex color. 
* LoginFormBackgroundColor - The background color of the login form. This can be any hex color. 
* LoginFormFontColor - The font color of the login form. This can be any hex color. 
* LoadingText - The loading text to show while authentication is in progress

## Accessing the User name in a Dashboard

In any Endpoint script block, you can access the user name. This means that Charts, Dynamic Pages, Tables and other controls can access the $User variable to get the current logged in user name.

See [Variables Defined in Endpoints](../endpoints/variables-defined-in-endpoints.md) for more information.

