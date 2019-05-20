# REST API Authentication

Updated: 3/3/2018 Required Version: 1.5.0

{% hint style="info" %}
Not available in Community Edition. 
{% endhint %}

## JSON Web Tokens

REST API authentication takes advantage of JSON web tokens to provide a mechanism to authentication users and applications again a REST API. Tokens can be granted on the command line or through an endpoint and then provided as part of the Authorization header when making future requests.

Visit [JWT.IO](https://jwt.io/) to learn more about JSON web tokens

## Basic Authentication

To setup basic authentication, you can use `New-UDAuthenticationMethod` with `Start-UDRestApi`. Simply pass a new authentication method to the `-AuthenticationMethod` parameter of `Start-UDRestApi`.

```text
$Method = New-UDAuthenticationMethod
Start-UDRestApi -AuthenticationMethod $Method ...
```

The REST API is now protected from requests that do not contain a valid Bearer token. To generate a token for the API, you can use `Grant-UDJsonWebToken`.

```text
$Token = Grant-UDJsonWebToken -UserName 'Adam'
```

The token can then be used with `Invoke-RestMethod` or another HTTP tool as part of the headers.

```text
Invoke-RestMethod -Headers @{ Authorization = "Bearer $Token" }
```

## Configuration Authentication

`New-UDAuthenticationMethod` offers several configuration options that provide additional security when configuring the protection for a REST API. You will want to override the `-SigningKey` parameter. It defaults to `default_signing_key`. Changing this value ensures that the signing key is unique for your REST API.

```text
$Method = New-UDAuthenticationMethod -SigningKey "SuperSecretKey"
Start-UDRestApi -AuthenticationMethod $Method ...
```

When changing the signing key, audience or issuer, make sure to specify the same value when using `Grant-UDJsonWebToken`

```text
$Token = Grant-UDJsonWebToken -UserName 'Adam' -SigningKey "SuperSecretKey"
```

## Enabling Authentication through the REST API

To enable authentication through the REST API, you can specify an endpoint based authentication method with `New-UDAuthenticationMethod`.

```text
$AuthMethod = New-UDAuthenticationMethod -Endpoint {
    #Perform authentication here
    New-UDAuthenticationResult -Success -UserName $Credential.UserName
}

$Server = Start-UDRestApi -Port 10001 -Endpoint @(
    New-UDEndpoint -Url "user/me" -Method "GET" -Endpoint {
        @($User) | ConvertTo-Json
        }
)-AuthenticationMethod $AuthMethod
```

From there, users can authenticate again `/api/login` to retrieve a token and then use it on subsequent requests.

```text
$Token = Invoke-RestMethod -Uri http://localhost:10001/api/login -Method POST -Body @{ UserName = "Adam"; Password = "Test" } 

$users = Invoke-RestMethod -Uri http://localhost:10001/api/user/me -Headers @{ Authorization = "Bearer $($Token.Token)" }
```

## Configuring Tokens

`Grant-UDJsonWebToken` provides several configuration options for tokens. You can specify expiration as well as user names. Default expiration is 1 year. User names are available within UDEndpoints that by using the `$User` variable.

```text
$Token = Grant-UDJsonWebToken -UserName 'Adam' -Expiry (Get-Date).AddDays(10)
```

