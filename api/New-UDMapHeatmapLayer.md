---
external help file: UniversalDashboard-help.xml
Module Name: UniversalDashboard
online version: 
schema: 2.0.0
---

# New-UDMapHeatmapLayer

## SYNOPSIS
Creates a heatmap layer.

## SYNTAX

```
New-UDMapHeatmapLayer [-Points] <Object> [[-Id] <String>] [[-MaxIntensity] <Double>] [[-Radius] <Double>]
 [[-MaxZoom] <Int32>] [[-MinOpacity] <Double>] [[-Blur] <Int32>] [[-Gradient] <Hashtable>] [<CommonParameters>]
```

## DESCRIPTION
Creates a heatmap layer. Heatmaps accept various positions with an optional intesity value.

## EXAMPLES

### Example 1
```
New-UDMapHeatmapLayer -Id 'heatmap' -Points @(
    @(51.505, -0.09, "625"),
    @(51.505234, -0.0945654, "625"),
    @(51.50645, -0.098768, "625"),
    @(51.5056575, -0.0945654, "625"),
    @(51.505955, -0.095675, "625"),
    @(51.505575, -0.09657, "625"),
    @(51.505345, -0.099876, "625"),
    @(51.505768, -0.0923432, "625"),
    @(51.505567, -0.02349, "625"),
    @(51.50545654, -0.092342, "625"),
    @(51.5045645, -0.09342, "625")
)
```

Creates a heatmap based on ten points with varying latitude, longitude and intensity.

## PARAMETERS

### -Blur
The amount of blur to apply to points.

```yaml
Type: Int32
Parameter Sets: (All)
Aliases: 

Required: False
Position: 6
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Gradient
The gradient values for this map. This value should be a hashtable with different stops in the gradient. The keys in the hashtable are the intensity values while the values are the colors. @{ '0.4' = 'red'; '0.6' = 'blue'; '0.8' = 'green' }

```yaml
Type: Hashtable
Parameter Sets: (All)
Aliases: 

Required: False
Position: 7
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id
The ID of this heatmap layer.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxIntensity
The maximum intensity value. 

```yaml
Type: Double
Parameter Sets: (All)
Aliases: 

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxZoom
The maximum zoom level of this heatmap.

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

### -MinOpacity
The minimum opacity of the points.

```yaml
Type: Double
Parameter Sets: (All)
Aliases: 

Required: False
Position: 5
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Points
The points for this heat map. This should consist of an array of arrays. Each point is an array that specifies the latitude, longitude and intensity. @( @(75, 123, 1), @(75, 123, 1), @(75, 123, 1), @(75, 123, 1) )

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

### -Radius
The radius of the points.

```yaml
Type: Double
Parameter Sets: (All)
Aliases: 

Required: False
Position: 3
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

