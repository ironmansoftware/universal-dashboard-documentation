---
external help file: UniversalDashboard-help.xml
Module Name: UniversalDashboard
online version: 
schema: 2.0.0
---

# New-UDMapMarker

## SYNOPSIS
Creates a marker on the map.

## SYNTAX

### LatLng
```
New-UDMapMarker [-Id <String>] -Longitude <Single> -Latitude <Single> [-Attribution <String>]
 [-Opacity <Int32>] [-ZIndex <Int32>] [-Popup <Hashtable>] [-Icon <Hashtable>]
```

### GeoJSON
```
New-UDMapMarker [-Id <String>] [-Attribution <String>] [-Opacity <Int32>] [-ZIndex <Int32>]
 [-Popup <Hashtable>] [-Icon <Hashtable>] -GeoJSON <String>
```

## DESCRIPTION
Creates a marker on the map. 

## EXAMPLES

### Example 1
```
New-UDMapMarker -Id 'marker' -Latitude 51.505 -Longitude -0.09
```

Creates a map marker with a default icon at 51.505/-0.09.

## PARAMETERS

### -Attribution
Attribution to show along with the marker.

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

### -GeoJSON
A GeoJSON string that defines the location of this marker.

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

### -Icon
A custom icon to show as this marker. You can create a custom icon with New-UDMapIcon.

```yaml
Type: Hashtable
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id
The ID of this marker.

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
The latitude of the marker location.

```yaml
Type: Single
Parameter Sets: LatLng
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Longitude
The longitude of the marker location.

```yaml
Type: Single
Parameter Sets: LatLng
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Opacity
The opacity of this marker.

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

### -Popup
A popup to show when the marker is clicked. Use New-UDMapPopup to create a popup.

```yaml
Type: Hashtable
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ZIndex
The z-index of this marker.

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

