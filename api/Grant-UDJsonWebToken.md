---
external help file: UniversalDashboard.dll-Help.xml
Module Name: UniversalDashboard
online version: 
schema: 2.0.0
---

# Grant-UDJsonWebToken

## SYNOPSIS
Grants a JSON web token for the specified user or application.

## SYNTAX

```
Grant-UDJsonWebToken [-Audience <String>] [-Issuer <String>] [-SigningKey <String>] -Identity <String>
 [-Subject <String>] [-Expiry <DateTime>] [-Role <String[]>] [-Payload <Hashtable>] [<CommonParameters>]
```

## DESCRIPTION
Grants a JSON web token for the specified user. You can adjust the JSON web token parameters in addition to specifying the user.

## EXAMPLES

### Example 1
```
PS C:\> $Token = Grant-UDJsonWebToken -UserName "Adam"
PS C:\> Invoke-RestMethod http://localhost/api/resource -Headers @{ Authorization = "Bearer $Token"}
```

Creates a JSON web token for Adam and then uses that token to access a protected resource on the API.

## PARAMETERS

### -Audience
The aud (audience) claim identifies the recipients that the JWT is intended for.  

See: https://self-issued.info/docs/draft-ietf-oauth-json-web-token.html#rfc.section.4.1.3

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Expiry
The exp (expiration time) claim identifies the expiration time on or after which the JWT MUST NOT be accepted for processing. 

See: https://self-issued.info/docs/draft-ietf-oauth-json-web-token.html#rfc.section.4.1.4

```yaml
Type: DateTime
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Identity
The identity of the user or applicaiton. 

```yaml
Type: String
Parameter Sets: (All)
Aliases: UserName, Application

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Issuer
The iss (issuer) claim identifies the principal that issued the JWT. 

See: https://self-issued.info/docs/draft-ietf-oauth-json-web-token.html#rfc.section.4.1.1

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Payload
{{Fill Payload Description}}

```yaml
Type: Hashtable
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Role
The roles to provide the user of the JSON web token. 

```yaml
Type: String[]
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SigningKey
The secret key used to sign the web token. This should be treated as a password.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Subject
The sub (subject) claim identifies the principal that is the subject of the JWT. 

See: https://self-issued.info/docs/draft-ietf-oauth-json-web-token.html#rfc.section.4.1.2

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None

## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

