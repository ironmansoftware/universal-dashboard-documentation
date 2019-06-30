---
external help file: UniversalDashboard-help.xml
Module Name: UniversalDashboard
online version: https://go.microsoft.com/fwlink/?LinkID=217032
schema: 2.0.0
---

# New-UDMapMarkerClusterLayer

## SYNOPSIS
Creates a layer that clusters markers together.

## SYNTAX

```
New-UDMapMarkerClusterLayer [[-Id] <String>] [[-Markers] <Hashtable[]>] [[-MinimumClusterSize] <Int32>]
 [[-GridSize] <Int32>]
```

## DESCRIPTION
Creates a layer that clusters markers together. As the user zooms out from the map, markers that are close to each other will be clustered into groups. 

## EXAMPLES

### Example 1
```
PS C:\> {{ Add example code here }}
```

{{ Add example description here }}

## PARAMETERS

### -GridSize
The number of pixels away a marker must be from another marker before it is clustered. The default is 60.

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

### -Id
The ID of this component.

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

### -Markers
The markers to include in this cluster layer. You can use New-UDMapMarker to create these markers. 

```yaml
Type: Hashtable[]
Parameter Sets: (All)
Aliases: 

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MinimumClusterSize
The minimum number of markers required to create a cluster. The default is 2.

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

## INPUTS

### None


## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

