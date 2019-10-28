---
external help file: UniversalDashboard.dll-Help.xml
Module Name: UniversalDashboard
online version: https://go.microsoft.com/fwlink/?LinkID=217032
schema: 2.0.0
---

# New-UDAuthorizationPolicy

## SYNOPSIS
Creates a new authorization policy for a page or endpoint.

## SYNTAX

```
New-UDAuthorizationPolicy [-Endpoint <Object>] [-Name <String>] [<CommonParameters>]
```

## DESCRIPTION
Creates a new authorization policy for a page or endpoint.

## EXAMPLES

### Example 1
```
PS C:\> $Policy = New-UDAuthorizationPolicy -Name "Policy" -Endpoint {
            param($User)

            if ($User.Identity.Name -eq 'Adam') {
                return $false
            }

            $true
        }
PS C:\> $LoginPage = New-UDLoginPage -AuthenticationMethod $AuthenticationMethod -AuthorizationPolicy @($Policy)
PS C:\> $Page = New-UDPage -Name "Home" -Content {
                New-UDHeading -Text "Home" -Id "Home"
            } -AuthorizationPolicy "Policy"
```

Creates a new authorization policy where only the user 'Adam' could view the home page. 

## PARAMETERS

### -Endpoint
The endpoint that is invoked when a page is loaded to evaluate whether the user can view the page. The endpoint should return true of false. 

```yaml
Type: Object
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name
The name of the policy. This is the name that should be provided to REST endpoints and pages. 

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

