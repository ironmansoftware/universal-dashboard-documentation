---
external help file: UniversalDashboard.dll-Help.xml
Module Name: UniversalDashboard
online version: https://go.microsoft.com/fwlink/?LinkID=217032
schema: 2.0.0
---

# ConvertTo-UDJsonWebToken

## SYNOPSIS
Converts a JSON web token into an object.

## SYNTAX

```
ConvertTo-UDJsonWebToken [-Token] <String> [<CommonParameters>]
```

## DESCRIPTION
Converts a JSON web token into an object.

## EXAMPLES

### Example 1
```
PS C:\> ConvertTo-UDJsonWebToken -Token 'asdfas3asdfas='
```

Converts a web token into a object.

## PARAMETERS

### -Token
The token to convert to an object.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### System.String

## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

