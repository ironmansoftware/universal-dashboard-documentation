# Forms

{% hint style="info" %}
Not available in Community Edition. 
{% endhint %}

Forms authentication is accomplished using the New-UDAuthenticationMethod cmdlet paired with the AuthenticationMethod parameter of the New-UDLoginPage cmdlet. Use the Endpoint parameter of New-UDAuthenticationMethod to specify an endpoint to be executed when a user attempts to login to the dashboard. The param block of the Endpoint script block show contain a $Credential parameter to accept the credentials of the user.

You can then authenticate the user however you want. This could be using something like Active Directory or another method via PowerShell.

To return an authentication result to the user, use New-UDAuthenticationResult. The Success switch parameter specifies that the authentication was a success. If you want to use a custom error message, you can use the ErrorMessage parameter. You should pass the user's user name to the UserName parameter during a successful authentication.

```text
$FormLogin = New-UDAuthenticationMethod -Endpoint {
    param([PSCredential]$Credentials)

    if ($Credentials.UserName -eq "Adam" -and $Credentials.GetNetworkCredential().Password -eq "SuperSecretPassword") {
        New-UDAuthenticationResult -Success -UserName "Adam"
    }

    New-UDAuthenticationResult -ErrorMessage "You aren't Adam!!!"
}
```

