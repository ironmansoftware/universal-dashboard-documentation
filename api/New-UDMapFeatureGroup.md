---
external help file: UniversalDashboard-help.xml
Module Name: UniversalDashboard
online version: 
schema: 2.0.0
---

# New-UDMapFeatureGroup

## SYNOPSIS
A feature group is a collection of map features that can be toggled together.

## SYNTAX

```
New-UDMapFeatureGroup [[-Id] <String>] [[-Popup] <Hashtable>] [-Content] <ScriptBlock> [<CommonParameters>]
```

## DESCRIPTION
A feature group is a collection of map features that can be toggled together. You can use New-UDMapOverlay to toggle feature groups. You can also add and remove features from feature groups using Add-UDElement and Remove-UDElement.

## EXAMPLES

### Feature Group
```
New-UDMapFeatureGroup -Id 'Feature-Group' -Content {
    New-UDMapMarker -Id 'marker' -Latitude 51.505 -Longitude -0.09
    New-UDMapMarker -Id 'marker' -Latitude 51.515 -Longitude -0.19
    New-UDMapMarker -Id 'marker' -Latitude 51.555 -Longitude -0.11
}
```

Creates a feature group with three markers that are part of the group. 

## PARAMETERS

### -Content
A script block containing the features of this feature group.

```yaml
Type: ScriptBlock
Parameter Sets: (All)
Aliases: 

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id
The ID of this feature group.

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

### -Popup
A popup to display when this feature group is selected. Use New-UDMapPopup to create a popup.

```yaml
Type: Hashtable
Parameter Sets: (All)
Aliases: 

Required: False
Position: 1
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

