﻿{% hint style="info" %}
Universal Dashboard is now a part of PowerShell Universal. This documentation is for reference to the v2 version of Universal Dashboard and is no longer maintained. PowerShell Universal Documentation can be found [here](https://docs.ironmansoftware.com).
{% endhint %}


---
external help file: UniversalDashboard-help.xml
Module Name: UniversalDashboard
online version: 
schema: 2.0.0
---

# Set-UDContentType

## SYNOPSIS
Sets the content-type HTTP header for a HTTP response.

## SYNTAX

```
Set-UDContentType [-ContentType] <Object> [<CommonParameters>]
```

## DESCRIPTION
Sets the content-type HTTP header for a HTTP response. This should be in control's Endpoint script blocks.

## EXAMPLES

### Example 1
```
PS C:\> Set-UDContentType -ContentType "application/xml"
```

Sets the content type to XML if an endpoint wanted to return XML.

## PARAMETERS

### -ContentType
The content type to set.

```yaml
Type: Object
Parameter Sets: (All)
Aliases: 

Required: True
Position: 0
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



