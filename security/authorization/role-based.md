# Role-Based

{% hint style="info" %}
Universal Dashboard is now a part of PowerShell Universal. This documentation is for reference to the v2 version of Universal Dashboard and is no longer maintained. PowerShell Universal Documentation can be found [here](https://docs.ironmansoftware.com).
{% endhint %}

## Role-Based

{% hint style="info" %}
Not available in Community Edition.
{% endhint %}

You can setup roll-based authorization by specifying the role a user is granted during login with `New-UDAuthenticationResult`.

```text
$FormLogin = New-UDAuthenticationMethod -Endpoint {
    param([PSCredential]$Credentials)

    if ($Credentials.UserName -eq "Adam" -and $Credentials.GetNetworkCredential().Password -eq "SuperSecretPassword") {
        New-UDAuthenticationResult -Success -UserName "Adam" -Role "Administrator"
    }

    New-UDAuthenticationResult -ErrorMessage "You aren't Adam!!!"
}
```

You can then permit access to pages and REST API endpoints by assigning roles to them.

```text
New-UDPage -Title 'Settings Page' -AuthorizedRole "Administrator" -Content {
    "Only available to admins"
}
```

You can also specify multiple roles per page or endpoint.

```text
New-UDPage -Title 'Home Page' -AuthorizedRole @("Administrator", "User") -Content {
    "Available to everyone"
}
```

