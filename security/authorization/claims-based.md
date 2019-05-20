# Claims-Based

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

