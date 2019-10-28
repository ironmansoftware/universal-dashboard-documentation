---
external help file: UniversalDashboard-help.xml
Module Name: UniversalDashboard
online version: 
schema: 2.0.0
---

# New-UDMapBaseLayer

## SYNOPSIS
The base layer for the map. 

## SYNTAX

```
New-UDMapBaseLayer [[-Id] <String>] [-Name] <String> [-Content] <ScriptBlock> [-Checked] [<CommonParameters>]
```

## DESCRIPTION
The base layer for the map. You can have multiple base layers on a map. You can use the layer control to switch between base layers. Base layers are typically satelite or street raster layers. 

## EXAMPLES

### Base layer with a tile server raster layer
```
New-UDMapBaseLayer -Name 'Black and White' -Content {
    New-UDMapRasterLayer -TileServer 'https://tiles.wmflabs.org/bw-mapnik/{z}/{x}/{y}.png' 
} -Checked
```

Creates a base layer with a tile server raster layer defined. This layer is visible by default.

## PARAMETERS

### -Checked
Whether this base layer is selected.

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

### -Content
The contents of this base layer. Use the New-UDMapRasterLayer cmdlet to specify a tile layer.

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
The ID of this base layer.

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

### -Name
The name of the base layer. This will appear in the layer control.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: True
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

