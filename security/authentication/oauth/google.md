# Google

{% hint style="info" %}
Not available in Community Edition. 
{% endhint %}

To enable login with Google OAuth authentication, you can use the New-UDAuthenticationMethod cmdlet to allow users to enter their Google credentials to login to your dashboard.

First, you need to register your application with Google. You can follow the directions [here](https://docs.microsoft.com/en-us/aspnet/core/security/authentication/social/google-logins?tabs=aspnetcore2x).

When registering your application, the callback URL should be: `http(s)://<server:port>/signin-google`

Next, you need to call New-UDAuthenticationMethod and specify the AppId, AppSecret and Provider name.

```text
$Method = New-UDAuthenticationMethod -AppId 1234 -AppSecret Abc123 -Provider Google
$LoginPage = New-UDLoginPage -AuthenticationMethod $Method
```

