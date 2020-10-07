# Twitter

{% hint style="info" %}
Universal Dashboard is now a part of PowerShell Universal. This documentation is for reference to the v2 version of Universal Dashboard and is no longer maintained. PowerShell Universal Documentation can be found [here](https://docs.ironmansoftware.com).
{% endhint %}

## Twitter

{% hint style="info" %}
Not available in Community Edition.
{% endhint %}

To enable login with Twitter OAuth authentication, you can use the New-UDAuthenticationMethod cmdlet to allow users to enter their Twitter credentials to login to your dashboard.

First, you need to register your application with Twitter. You can follow the directions [here](https://docs.microsoft.com/en-us/aspnet/core/security/authentication/social/twitter-logins?tabs=aspnetcore2x).

When registering your application, the callback URL should be: `http(s)://<server:port>/signin-twitter`

Next, you need to call New-UDAuthenticationMethod and specify the AppId, AppSecret and Provider name.

```text
$Method = New-UDAuthenticationMethod -AppId 1234 -AppSecret Abc123 -Provider Twitter
$LoginPage = New-UDLoginPage -AuthenticationMethod $Method
```

