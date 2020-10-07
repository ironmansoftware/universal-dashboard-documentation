# OpenID Connect

{% hint style="info" %}
Universal Dashboard is now a part of PowerShell Universal. This documentation is for reference to the v2 version of Universal Dashboard and is no longer maintained. PowerShell Universal Documentation can be found [here](https://docs.ironmansoftware.com).
{% endhint %}

## OpenID Connect

You can configure Universal Dashboard to use any compatible OpenID Connect service. This includes services like AzureAD. OpenID Connect also allows the generation of tokens that can be used with other PowerShell modules like the Azure module.

### Configuring OpenID Connect

To configure authentication using OpenID Connect, use the `OpenID` parameter set for `New-UDAuthenticationMethod`. There are various parameters you will need to specify. You can get the values to these parameters from your OpenID Connect provider. Here is an example of connecting to Azure Active Directory with Universal Dashboard.

This configuration returns an access token that can then be used with other Azure services. It's required to specify the resource you'd like to access as that user.

```text
$AuthenticationMethod = New-UDAuthenticationMethod -ResponseType 'id_token token' -ClientSecret 'xxxxxx' -ClientId 'e241925f-8972-415c-b0e2-86b45568737a' -Authority 'https://login.microsoftonline.com/680ef960-6d96-4e60-afb1-9bb9d54784d6' -Resource 'https://management.azure.com/' -PassThru
```

### Access Tokens

OpenID Connect can provide on-behalf-of access tokens. Users that login to OpenID Connect enabled service can then use their credentials to access other services. One example of this is the ability to use the Azure PowerShell module with the access token returned by the UD OpenID Connect feature.

The access and id token are available as properties of the `$Session` variable.

```text
Connect-AzAccount -AccessToken $Session.AccessToken -AccoundId $User
```

Access tokens will only be returned if you specify the `ResponseType` of `token` when using `New-UDAuthenticationMethod`.

