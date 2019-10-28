---
external help file: UniversalDashboard-help.xml
Module Name: UniversalDashboard
online version: 
schema: 2.0.0
---

# New-UDMapIcon

## SYNOPSIS
Creates a map icon for a marker.

## SYNTAX

```
New-UDMapIcon [-Url] <String> [[-Height] <Int32>] [[-Width] <Int32>] [[-AnchorX] <Int32>] [[-AnchorY] <Int32>]
 [[-PopupAnchorX] <Int32>] [[-PopupAnchorY] <Int32>] [<CommonParameters>]
```

## DESCRIPTION
Creates a map icon for a marker. This is used to specify custom icons for markers.

## EXAMPLES

### Example 1
```
New-UDMapIcon -Url http://domain.com/icon.png -Height 16 -Width 16
```

Creates a map icon based on the icon.png file. The icon will be 16x16 pixels in size. 

## PARAMETERS

### -AnchorX
The offset of where to anchor the icon to the map.

```yaml
Type: Int32
Parameter Sets: (All)
Aliases: 

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AnchorY
The offset of where to anchor the icon to the map.

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

### -Height
The height of the icon in pixels.

```yaml
Type: Int32
Parameter Sets: (All)
Aliases: 

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PopupAnchorX
The offset of where to anchor a popup coming from the top of this icon.

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

### -PopupAnchorY
The offset of where to anchor a popup coming from the top of this icon.

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

### -Url
The URL to the icon file.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Width
The width of the icon in pixels.

```yaml
Type: Int32
Parameter Sets: (All)
Aliases: 

Required: False
Position: 2
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

