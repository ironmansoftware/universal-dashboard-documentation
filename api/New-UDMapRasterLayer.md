---
external help file: UniversalDashboard-help.xml
Module Name: UniversalDashboard
online version: 
schema: 2.0.0
---

# New-UDMapRasterLayer

## SYNOPSIS
Creates a raster layer that is typically used as a base layer. 

## SYNTAX

### Generic
```
New-UDMapRasterLayer [-Id <String>] [-TileServer <String>] [-Attribution <String>] [-Opacity <Int32>]
 [-ZIndex <Int32>] [-Name <String>]
```

### Bing
```
New-UDMapRasterLayer [-Id <String>] -ApiKey <String> [-Type <String>] [-Bing] [-Attribution <String>]
 [-Opacity <Int32>] [-ZIndex <Int32>] [-Name <String>]
```

## DESCRIPTION
Creates a raster layer that is typically used as a base layer. Base layers are usually tile servers that provide a tile like a satelite or road view. 

## EXAMPLES

### Open Tile Server
```
New-UDMapRasterLayer -TileServer 'https://tiles.wmflabs.org/bw-mapnik/{z}/{x}/{y}.png' 
```

Creates a raster layer using the wmflabs tile server.

### Bing Tile Server
```
New-UDMapRasterLayer -Bing -ApiKey 'asdf3rwf34afaw-sdfasdfa23feaw-23424dfsdfa' -Type Road
```

Creates a raster layer using the Bing Map API and selecting the road tiles. 

## PARAMETERS

### -ApiKey
Bing Maps API key.

```yaml
Type: String
Parameter Sets: Bing
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Attribution
Map attribution.

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

### -Bing
Enable Bing Maps API support.

```yaml
Type: SwitchParameter
Parameter Sets: Bing
Aliases: 

Required: True
Position: Named
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
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name
The name of this raster layer. This will appear in the layer control.

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

### -Opacity
The opacity of the raster layer.

```yaml
Type: Int32
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TileServer
The URL of the tile server to use.

```yaml
Type: String
Parameter Sets: Generic
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Type
The type of Bing tile to use. This defaults to Aerial.

```yaml
Type: String
Parameter Sets: Bing
Aliases: 
Accepted values: Aerial, AerialWithLabels, AerialWithLabelsOnDemand, CanvasDark, CanvasLight, CanvasGray, Road

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ZIndex
The z-index of this raster layer.

```yaml
Type: Int32
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

## INPUTS

### None


## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

