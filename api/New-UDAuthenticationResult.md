﻿{% hint style="info" %}
Universal Dashboard is now a part of PowerShell Universal. This documentation is for reference to the v2 version of Universal Dashboard and is no longer maintained. PowerShell Universal Documentation can be found [here](https://docs.ironmansoftware.com).
{% endhint %}


---
external help file: UniversalDashboard.dll-Help.xml
Module Name: UniversalDashboard
online version: 
schema: 2.0.0
---

# New-UDAuthenticationResult

## SYNOPSIS
Returns a result of authentication.

## SYNTAX

```
New-UDAuthenticationResult [-Success] [-UserName <String>] [-RedirectUrl <String>] [-ErrorMessage <String>]
 [-Role <String[]>] [-Token <String>] [<CommonParameters>]
```

## DESCRIPTION
Returns a result of authentication. This should be used in the Endpoint for a New-UDAuthenticationMethod.

## EXAMPLES

### Example 1
```
PS C:\> New-UDAuthenticationMethod -Endpoint {
                    param([PSCredential]$Credential)
        
                    if ($Credential.UserName -eq "Adam") {
                        New-UDAuthenticationResult -UserName "Adam" -Success
                    } else {
                        New-UDAuthenticationResult -ErrorMessage "You're not Adam!!"
                    }
                }
```

Validates that the user is Adam. If it isn't it returns an error.

## PARAMETERS

### -ErrorMessage
An error message to return for an unsuccessful authentication.

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

### -RedirectUrl
Redirects to a URL after login.

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

### -Role
The role or roles for the user being authenticated. 

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

### -Success
Whether this authentication was a success.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Token
The JSON web token to provide the user. 

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

### -UserName
The username for the authenticated user. 

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



