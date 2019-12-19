# WS-Federation

{% hint style="info" %}
This feature is not supported in Community Edition
{% endhint %}

WS-Federation supports both Active Directory Federation Services and Azure Active Directory.

You first need to configure ADFS or AzureAD to support Universal Dashboard.

## Configuring ADFS for Universal Dashboard

### Service Settings

These are the current Federation Service settings for our domain.

![](../../.gitbook/assets/image%20%2849%29.png)

### Relying Parties

You need to configure the following Relying Parties settings for Universal Dashboard. On the Identifiers tab, provide the URL to the Universal Dashboard website. HTTPS is required.

![](../../.gitbook/assets/image%20%2855%29.png)

On the Endpoints tab. You'll need to include a WS-Federation Passive Endpoint. Make sure to include the trailing slash.

![](../../.gitbook/assets/image%20%287%29.png)

Finally, you'll need to configure a Claim Issuance Policy for the Relying Party Trust. Create an Issuance Transform Rule that sends at least the Name and Name ID to Universal Dashboard.

![](../../.gitbook/assets/image%20%2863%29.png)

You can configure additional claims you'd like to use if you are using Claims-based Authorization in Universal Dashboard.

## Configuring For Azure Active Directory

Follow the documentation for the Azure Active Directory configuration found on this [Microsoft Document](https://docs.microsoft.com/en-us/aspnet/core/security/authentication/ws-federation?view=aspnetcore-2.2#azure-active-directory).

## Configuring Universal Dashboard

After configuring ADFS or AAD, you can now use the `New-UDAuthenticationMethod` cmdlet to connect to your WS-Fed instance. For our ADFS instance, this is the authentication method configuration we are using.

```text
$Authentication = New-UDAuthenticationMethod -MetadataAddress 'https://ironman.local:443/FederationMetadata/2007-06/FederationMetadata.xml' -Wtrealm https://ironman.local:12345
$LoginPage = New-UDLoginPage -AuthenticationMethod $Authentication
```

When running your dashboard, you should now be prompted for your credentials either via the Internet Explorer single-sign system or you will be forwarded to the WS-Fed login page.

![](../../.gitbook/assets/image%20%2839%29.png)

