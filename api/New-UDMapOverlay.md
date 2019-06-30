---
external help file: UniversalDashboard-help.xml
Module Name: UniversalDashboard
online version: 
schema: 2.0.0
---

# New-UDMapOverlay

## SYNOPSIS
Creates an overlay layer in a layer control.

## SYNTAX

```
New-UDMapOverlay [[-Id] <String>] [-Name] <String> [-Content] <ScriptBlock> [-Checked]
```

## DESCRIPTION
Creates an overlay layer in a layer control. When an overlay is used in the layer control, you can toggle on and off that overlay using the layer control switch. You can specify as many layers as you would like. 

## EXAMPLES

### Example 1
```
New-UDMapOverlay -Name "Heatmap" -Content {
    New-UDMapHeatmapLayer -Id 'heatmap' -Points @() 
} -Checked 
```

Creates a heatmap overlay within the layer control. The name of the overlay will be Heatmap and can be toggled using the layer control. 

## PARAMETERS

### -Checked
Whether this overlay is shown by default.

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
The content of this overlay.

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
The ID of this overlay. 

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
The name of this overlay. This will appear in the layer switch control.

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

## INPUTS

### None


## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

