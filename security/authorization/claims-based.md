# Claims-Based

{% hint style="info" %}
Universal Dashboard is now a part of PowerShell Universal. This documentation is for reference to the v2 version of Universal Dashboard and is no longer maintained. PowerShell Universal Documentation can be found [here](https://docs.ironmansoftware.com).
{% endhint %}

## Claims-Based

{% hint style="info" %}
Not available in Community Edition.
{% endhint %}

Claims-based authorization allows for even more control of which users have access to which results. You can create a new claim policy with the `New-UDAuthorizationPolicy` cmdlet.

Policies are provided to the `New-UDLoginPage` cmdlet and can be assigned to resources by name.

For example, you could create a policy to check to see if the user is part of a group. The user is a [ClaimsPrinciple](https://msdn.microsoft.com/en-us/library/system.security.claims.claimsprincipal%28v=vs.110%29.aspx) object.

```text
$AuthorizationPolicy = New-UDAuthorizationPolicy -Name "Policy" -Endpoint {
    param($User)

    $User.HasClaim("group", "administrator")
}
```

You could then assign the policy to a page. The policy would be evaluated when the user was loading the page.

```text
 New-UDPage -Name "Settings" -Content {
    New-UDHeading -Text "Settings"
} -AuthorizationPolicy "Policy"
```

This works well with authentication methods that provide claims, like Azure Active Directory. You can then manage your users claims, like group membership, from within Azure rather than changing the code of your dashboard.

### Hiding Controls based on Policies

You can use the `Get-UDAuthorizationPolicy` cmdlet to return the list of policies that a user has been granted.

```text
New-UDCard -Title "Authorized Card" -Endpoint {
    $Policies = Get-UDAuthorizationPolicy 
    if ($Policies -contains "Admin")
    {
        New-UDHeading -Text "You are an Admin" 
    }
}
```

