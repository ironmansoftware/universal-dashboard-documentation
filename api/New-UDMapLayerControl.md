﻿{% hint style="info" %}
Universal Dashboard is now a part of PowerShell Universal. This documentation is for reference to the v2 version of Universal Dashboard and is no longer maintained. PowerShell Universal Documentation can be found [here](https://docs.ironmansoftware.com).
{% endhint %}


---
external help file: UniversalDashboard-help.xml
Module Name: UniversalDashboard
online version: 
schema: 2.0.0
---

# New-UDMapLayerControl

## SYNOPSIS
Configures a layer control in the map.

## SYNTAX

```
New-UDMapLayerControl [[-Id] <String>] [[-Position] <String>] [[-Content] <ScriptBlock>] [<CommonParameters>]
```

## DESCRIPTION
Configures a layer control in the map. When you use a layer control, you can toggle base layers as well as multiple overlays using the layer control.

## EXAMPLES

### Example 1
```
New-UDMapLayerControl -Id 'layercontrol' -Content {
    New-UDMapBaseLayer -Name "Black and White" -Content {
        New-UDMapRasterLayer -TileServer 'https://tiles.wmflabs.org/bw-mapnik/{z}/{x}/{y}.png' 
    } 

    New-UDMapBaseLayer -Name "Mapnik" -Content {
        New-UDMapRasterLayer -TileServer 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png' 
    } 

    New-UDMapBaseLayer -Name "Bing" -Content {
        New-UDMapRasterLayer -Bing -ApiKey 'asdf3rwf34afaw-sdfasdfa23feaw-23424dfsdfa' -Type Road
    } -Checked

    New-UDMapOverlay -Name "Markers" -Content {
        New-UDMapFeatureGroup -Id 'Feature-Group' -Content {
            New-UDMapMarker -Id 'marker' -Latitude 51.505 -Longitude -0.09
        } 
    } -Checked

    New-UDMapOverlay -Name "Cluster" -Content {
        New-UDMapMarkerClusterLayer -Id 'cluster-layer' -Markers @(
            1..100 | ForEach-Object {
                $Random = Get-Random -Minimum 0 -Maximum 100
                $RandomLat = $Random + 400
                New-UDMapMarker -Latitude "51.$RandomLat" -Longitude "-0.$Random"
            }
        )
    } -Checked

}
```

Creates a map with 3 base layers to select from as well as 2 overlay layers. 

## PARAMETERS

### -Content
The base layers and overlays that you will display in your map.

```yaml
Type: ScriptBlock
Parameter Sets: (All)
Aliases: 

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id
The ID of this layer control.

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

### -Position
The position of the layer selection control.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 
Accepted values: topright, topleft, bottomright, bottomleft

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



