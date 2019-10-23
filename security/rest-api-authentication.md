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

To enable authentication through the REST API, you can specify an endpoint based authentication method with `New-UDAuthenticationMethod`. When you specify the result of `New-UDAuthenticationResult` you can include a token that the user can then use for Bearer authentication for other REST API calls. The endpoint will receive a `PSCredential` object that you can then use to authenticate in whatever means is necessary.

```text
$AuthMethods = @()
$AuthMethods += New-UDAuthenticationMethod -Endpoint {
    param($Credential)

    #Perform authentication here
    $Token = Grant-UDJsonWebToken -Identity $Credential.UserName -Issuer "IMS"
    New-UDAuthenticationResult -Success -UserName $Credential.UserName -Token $Token
}

$AuthMethods += New-UDAuthenticationMethod -Issuer "IMS"

$Server = Start-UDRestApi -Port 10001 -Endpoint @(
    New-UDEndpoint -Url "user/me" -Method "GET" -Endpoint {
        @($User) | ConvertTo-Json
        }
)-AuthenticationMethod $AuthMethods
```

From there, users can authenticate again `/login` to retrieve a token and then use it on subsequent requests.

```text
$Token = Invoke-RestMethod -Uri http://localhost:10001/login -Method POST -Body @{ UserName = "Adam"; Password = "Test" } 
$users = Invoke-RestMethod -Uri http://localhost:10001/api/user/me -Headers @{ Authorization = "Bearer $($Token.Token)" }
```

## Configuring Tokens

`Grant-UDJsonWebToken` provides several configuration options for tokens. You can specify expiration as well as user names. Default expiration is 1 year. User names are available within UDEndpoints that by using the `$User` variable.

```text
$Token = Grant-UDJsonWebToken -UserName 'Adam' -Expiry (Get-Date).AddDays(10)
```

Web tokens can include any set of information that you want to include with the user's token by specifying a hashtable and providing it to the `-Payload` parameter. You can then use the `ConvertTo-UDJsonWebToken` to convert a string representation of a JSON web token to an object. 

```
PS F:\universal-dashboard-documentation> $Token = Grant-UDJsonWebToken -Identity 'Adam' -Payload @{Account = 'Billing'}
PS F:\universal-dashboard-documentation> ConvertTo-UDJsonWebToken -Token $Token

Actor                   : 
Audiences               : {UniversalDashboard}
Claims                  : {http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name: Adam, http://schemas.xmlsoap.org/ws/2005/05/identity/claims/hash:   
                          de19e3e8-2be5-4ad6-a14c-b0988979773c, sub: UniversalDashboard, nbf: 1571843025…}
EncodedHeader           : eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9
EncodedPayload          : eyJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy93cy8yMDA1LzA1L2lkZW50aXR5L2NsYWltcy9uYW1lIjoiQWRhbSIsImh0dHA6Ly9zY2hlbWFzLnhtbHNvYXAub3Jn
                          L3dzLzIwMDUvMDUvaWRlbnRpdHkvY2xhaW1zL2hhc2giOiJkZTE5ZTNlOC0yYmU1LTRhZDYtYTE0Yy1iMDk4ODk3OTc3M2MiLCJzdWIiOiJVbml2ZXJzYWxEYXNoYm9h 
                          cmQiLCJuYmYiOjE1NzE4NDMwMjUsImV4cCI6MTYwMzQ2NTQyNSwiaXNzIjoicG9zaHVkLmNvbSIsImF1ZCI6IlVuaXZlcnNhbERhc2hib2FyZCIsIkFjY291bnQiOiJC 
                          aWxsaW5nIn0
Header                  : {[alg, HS256], [typ, JWT]}
Id                      :
Issuer                  : poshud.com
Payload                 : {[http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name, Adam],
                          [http://schemas.xmlsoap.org/ws/2005/05/identity/claims/hash, de19e3e8-2be5-4ad6-a14c-b0988979773c], [sub, UniversalDashboard],   
                          [nbf, 1571843025]…}
InnerToken              :
RawAuthenticationTag    : 
RawCiphertext           : 
RawData                 : eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy93cy8yMDA1LzA1L2lkZW50aXR5L2NsYWltcy9uYW1lIjoiQWRhbSI 
                          sImh0dHA6Ly9zY2hlbWFzLnhtbHNvYXAub3JnL3dzLzIwMDUvMDUvaWRlbnRpdHkvY2xhaW1zL2hhc2giOiJkZTE5ZTNlOC0yYmU1LTRhZDYtYTE0Yy1iMDk4ODk3OTc 
                          3M2MiLCJzdWIiOiJVbml2ZXJzYWxEYXNoYm9hcmQiLCJuYmYiOjE1NzE4NDMwMjUsImV4cCI6MTYwMzQ2NTQyNSwiaXNzIjoicG9zaHVkLmNvbSIsImF1ZCI6IlVuaXZ 
                          lcnNhbERhc2hib2FyZCIsIkFjY291bnQiOiJCaWxsaW5nIn0.Hfl8YPzLmYAxXpy2_mqiRMvjyHwSAr2ZZy6EspdEvg0
RawEncryptedKey         :
RawInitializationVector :
RawHeader               : eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9
RawPayload              : eyJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy93cy8yMDA1LzA1L2lkZW50aXR5L2NsYWltcy9uYW1lIjoiQWRhbSIsImh0dHA6Ly9zY2hlbWFzLnhtbHNvYXAub3Jn 
                          L3dzLzIwMDUvMDUvaWRlbnRpdHkvY2xhaW1zL2hhc2giOiJkZTE5ZTNlOC0yYmU1LTRhZDYtYTE0Yy1iMDk4ODk3OTc3M2MiLCJzdWIiOiJVbml2ZXJzYWxEYXNoYm9h 
                          cmQiLCJuYmYiOjE1NzE4NDMwMjUsImV4cCI6MTYwMzQ2NTQyNSwiaXNzIjoicG9zaHVkLmNvbSIsImF1ZCI6IlVuaXZlcnNhbERhc2hib2FyZCIsIkFjY291bnQiOiJC
                          aWxsaW5nIn0
RawSignature            : Hfl8YPzLmYAxXpy2_mqiRMvjyHwSAr2ZZy6EspdEvg0
SecurityKey             :
SignatureAlgorithm      : HS256
SigningCredentials      :
EncryptingCredentials   :
SigningKey              :
Subject                 : UniversalDashboard
ValidFrom               : 10/23/2019 3:03:45 PM
ValidTo                 : 10/23/2020 3:03:45 PM

PS F:\universal-dashboard-documentation> $Object = ConvertTo-UDJsonWebToken -Token $Token
PS F:\universal-dashboard-documentation> $Object.Payload

Key                                                        Value
---                                                        -----
http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name Adam
http://schemas.xmlsoap.org/ws/2005/05/identity/claims/hash de19e3e8-2be5-4ad6-a14c-b0988979773c
sub                                                        UniversalDashboard
nbf                                                        1571843025
exp                                                        1603465425
iss                                                        poshud.com
aud                                                        UniversalDashboard
Account                                                    Billing
```

