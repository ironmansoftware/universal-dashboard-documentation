---
external help file: UniversalDashboard-help.xml
Module Name: UniversalDashboard
online version: 
schema: 2.0.0
---

# New-UDMapPopup

## SYNOPSIS
Creates a popup that can be assigned to vectors, markers and feature groups.

## SYNTAX

```
New-UDMapPopup [[-Id] <String>] [[-Content] <ScriptBlock>] [[-Longitude] <Single>] [[-Latitude] <Single>]
 [[-MaxWidth] <Int32>] [[-MinWidth] <Int32>] [<CommonParameters>]
```

## DESCRIPTION
Creates a popup that can be assigned to vectors, markers and feature groups. A popup is shown when clicking on the assigned feature.

## EXAMPLES

### Example 1
```
New-UDMapPopup -Content {
    New-UDCard -Title "Marker Information" -Content {

    }
} -MaxWidth 600
```

Creates a popup that displays a UDCard and has a max width of 600 pixels.

## PARAMETERS

### -Content
The content of the popup. This can be any Universal Dashboard component.

```yaml
Type: ScriptBlock
Parameter Sets: (All)
Aliases: 

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id
The ID of this popup.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Latitude
The latitude of this popup. By default, the popup will appear near the clicked feature.

```yaml
Type: Single
Parameter Sets: (All)
Aliases: 

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Longitude
The longitude of this popup. By default, the popup will appear near the clicked feature.

```yaml
Type: Single
Parameter Sets: (All)
Aliases: 

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxWidth
The maximum width, in pixels.

```yaml
Type: Int32
Parameter Sets: (All)
Aliases: 

Required: False
Position: 4
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MinWidth
{{Fill MinWidth Description}}

```yaml
Type: Int32
Parameter Sets: (All)
Aliases: 

Required: False
Position: 5
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

