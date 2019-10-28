---
external help file: UniversalDashboard-help.xml
Module Name: UniversalDashboard
online version: 
schema: 2.0.0
---

# New-UDSparklines

## SYNOPSIS
Mini charts that are good for tables and grids. 

## SYNTAX

```
New-UDSparklines [[-Id] <String>] [-Data] <Single[]> [[-Type] <String>] [[-Width] <Int32>] [[-Height] <Int32>]
 [[-Margin] <Int32>] [[-Minimum] <Single>] [[-Maximum] <Single>] [[-Color] <DashboardColor>]
 [[-Style] <Hashtable>] [<CommonParameters>]
```

## DESCRIPTION
Mini charts that are good for tables and grids. 

## EXAMPLES

### Line
```
New-UDSparklines -Data @(13,45,12,34,12,64) -Color blue -Type lines -Height 100 -Width 500 -Margin 10
```

Creates a blue line sparkline 

### Bar
```
New-UDSparklines -Data @(13,45,12,34,12,64) -Color blue -Type bars -Height 100 -Width 500 -Margin 10
```

Creates a blue bar sparkline 

## PARAMETERS

### -Color
Color of the sparkline.

```yaml
Type: DashboardColor
Parameter Sets: (All)
Aliases: 

Required: False
Position: 8
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Data
Data to show in the spark line. This should be an array of numbers.

```yaml
Type: Single[]
Parameter Sets: (All)
Aliases: 

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Height
The height of the sparkline in pixels.

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

### -Id
The ID of this sparkline.

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

### -Margin
The marin in pixels around the sparkline. 

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

### -Maximum
The maximum value to display in the sparkline. 

```yaml
Type: Single
Parameter Sets: (All)
Aliases: 

Required: False
Position: 7
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Minimum
The minimum value to display in the sparkline. 

```yaml
Type: Single
Parameter Sets: (All)
Aliases: 

Required: False
Position: 6
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Style
A CSS style to apply to the sparkline. 

```yaml
Type: Hashtable
Parameter Sets: (All)
Aliases: 

Required: False
Position: 9
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Type
The type of sparkline. 

```yaml
Type: String
Parameter Sets: (All)
Aliases: 
Accepted values: lines, bars, both

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Width
The width, in pixels, of the sparkline. 

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

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None

## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

