---
external help file: UniversalDashboard-help.xml
Module Name: UniversalDashboard
online version: 
schema: 2.0.0
---

# New-UDMapVectorLayer

## SYNOPSIS
Creates a vector layer to display polylines, polygons, circles or rectangles. 

## SYNTAX

### Circle
```
New-UDMapVectorLayer [-Id <String>] [-Color <DashboardColor>] [-FillColor <DashboardColor>]
 [-FillOpacity <Double>] [-Weight <Int32>] [-Opacity <Double>] [-Circle] -Latitude <Double> -Longitude <Double>
 -Radius <Int32> [-Popup <Object>] [<CommonParameters>]
```

### Polyline
```
New-UDMapVectorLayer [-Id <String>] [-Color <DashboardColor>] [-FillColor <DashboardColor>]
 [-FillOpacity <Double>] [-Weight <Int32>] [-Opacity <Double>] [-Polyline] -Positions <Object>
 [<CommonParameters>]
```

### Polygon
```
New-UDMapVectorLayer [-Id <String>] [-Color <DashboardColor>] [-FillColor <DashboardColor>]
 [-FillOpacity <Double>] [-Weight <Int32>] [-Opacity <Double>] [-Polygon] -Positions <Object>
 [<CommonParameters>]
```

### Rectangle
```
New-UDMapVectorLayer [-Id <String>] [-Color <DashboardColor>] [-FillColor <DashboardColor>]
 [-FillOpacity <Double>] [-Weight <Int32>] [-Opacity <Double>] [-Rectangle] -LatitudeTopLeft <Double>
 -LongitudeTopLeft <Double> -LatitudeBottomRight <Double> -LongitudeBottomRight <Double> [<CommonParameters>]
```

### GeoJSON
```
New-UDMapVectorLayer [-Id <String>] [-Color <DashboardColor>] [-FillColor <DashboardColor>]
 [-FillOpacity <Double>] [-Weight <Int32>] [-Opacity <Double>] -GeoJSON <String> [<CommonParameters>]
```

## DESCRIPTION
Creates a vector layer to display polylines, polygons, circles or rectangles. This cmdlet is used to draw routes or other shapes denoting regions of the map. You can customize colors and opacity.

## EXAMPLES

### Example 1
```
New-UDMapVectorLayer -Circle -Latitude 59.505 -Longitude -0.99 -Radius 10 -Color Blue -FillColor Blue
```

Creates a blue circle vector at 59.505/-0.99 with a radius of 10.

## PARAMETERS

### -Circle
Draws a circle.

```yaml
Type: SwitchParameter
Parameter Sets: Circle
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Color
The color used for the stroke of the shape.

```yaml
Type: DashboardColor
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FillColor
The color used for the fill of the shape.

```yaml
Type: DashboardColor
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FillOpacity
The opacity of the fill for this shape.

```yaml
Type: Double
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -GeoJSON
A GeoJSON string defining the vector. 

```yaml
Type: String
Parameter Sets: GeoJSON
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id
The ID of this vector layer.

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

### -Latitude
The latitude to the center of the circle.

```yaml
Type: Double
Parameter Sets: Circle
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LatitudeBottomRight
The latitude of the bottom right corner fo the rectangle.

```yaml
Type: Double
Parameter Sets: Rectangle
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LatitudeTopLeft
The latitude of the top left corner fo the rectangle.

```yaml
Type: Double
Parameter Sets: Rectangle
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Longitude
The longitude to the center of the circle.

```yaml
Type: Double
Parameter Sets: Circle
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LongitudeBottomRight
The longitude to the bottom right of the rectangle.

```yaml
Type: Double
Parameter Sets: Rectangle
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LongitudeTopLeft
The longitude to the top left of the rectangle.

```yaml
Type: Double
Parameter Sets: Rectangle
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Opacity
The opacity of the stroke for this vector.

```yaml
Type: Double
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Polygon
Draws a polygon

```yaml
Type: SwitchParameter
Parameter Sets: Polygon
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Polyline
Draws a polyline

```yaml
Type: SwitchParameter
Parameter Sets: Polyline
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Popup
A popup to show when this circle is clicked.

```yaml
Type: Object
Parameter Sets: Circle
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Positions
The positions that define the polyline or polygon. This should be an array of arrays. Each sub-array should be a pair of coordinates. 

```yaml
Type: Object
Parameter Sets: Polyline, Polygon
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Radius
The radius of the circle.

```yaml
Type: Int32
Parameter Sets: Circle
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Rectangle
Draws a rectangle.

```yaml
Type: SwitchParameter
Parameter Sets: Rectangle
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Weight
The weight of the stroke for this vector.

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

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None

## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

