---
external help file: UniversalDashboard.dll-Help.xml
Module Name: UniversalDashboard
online version: https://go.microsoft.com/fwlink/?LinkID=217032
schema: 2.0.0
---

# New-UDNivoChart

## SYNOPSIS
Creates a Nivo chart.

## SYNTAX

### Bar
```
New-UDNivoChart [-Id <String>] -Data <Object> [-Definitions <Object>] [-Fill <Object>] [-BorderWidth <Int32>]
 [-BorderColor <String>] [-IndexBy <String>] [-MinValue <Int32>] [-MaxValue <Int32>] [-Padding <Single>]
 [-Responsive] [-Width <Int32>] [-Height <Int32>] [-Colors <Object>] [-ColorBy <Object>] [-UseDataColor]
 [-DisableInteractive] [-OnClick <Object>] [-MarginTop <Int32>] [-MarginBottom <Int32>] [-MarginLeft <Int32>]
 [-MarginRight <Int32>] [-LabelSkipWidth <Int32>] [-LabelSkipHeight <Int32>] [-EnableGridX]
 [-GridXValues <Object[]>] [-EnableGridY] [-GridYValues <Object[]>] [-DisableAnimations]
 [-MotionStiffness <Int32>] [-MotionDamping <Int32>] -Keys <String[]> [-Layers <String[]>] [-AxisTop <Object>]
 [-AxisBottom <Object>] [-AxisLeft <Object>] [-AxisRight <Object>] [-Bar] [-GroupMode <String>]
 [-Layout <String>] [-Reverse] [-InnerPadding <Single>] [-BorderRadius <Int32>] [-DisableLabel]
 [<CommonParameters>]
```

### Pie
```
New-UDNivoChart [-Id <String>] -Data <Object> [-Definitions <Object>] [-Fill <Object>] [-BorderWidth <Int32>]
 [-BorderColor <String>] [-Responsive] [-Width <Int32>] [-Height <Int32>] [-Colors <Object>]
 [-ColorBy <Object>] [-UseDataColor] [-DisableInteractive] [-OnClick <Object>] [-MarginTop <Int32>]
 [-MarginBottom <Int32>] [-MarginLeft <Int32>] [-MarginRight <Int32>] [-Pie] [-StartAngle <Int32>]
 [-EndAngle <Int32>] [-Fit <Boolean>] [-InnerRadius <Int32>] [-PadAngle <Int32>] [-CornerRadius <Int32>]
 [-SortByValue] [-DisableRadiusLabels] [-RadiusLabelSkipAngle <Int32>] [-RadiusLabelsLinkOffset <Int32>]
 [-RadialLabelsLinkDiagonalLength <Int32>] [-RadialLabelsLinkHorizontalLength <Int32>]
 [-RadialLabelsTextXOffset <Int32>] [-RadialLabelsLinkStrokeWidth <Int32>] [-DisableSliceLabels]
 [-SlicesLabelsSkipAngle <Int32>] [-SlicesLabelsTextColor <Int32>] [<CommonParameters>]
```

### Stream
```
New-UDNivoChart [-Id <String>] -Data <Object> [-Definitions <Object>] [-Fill <Object>] [-BorderWidth <Int32>]
 [-BorderColor <String>] [-Responsive] [-Width <Int32>] [-Height <Int32>] [-Colors <Object>]
 [-ColorBy <Object>] [-UseDataColor] [-DisableInteractive] [-OnClick <Object>] [-MarginTop <Int32>]
 [-MarginBottom <Int32>] [-MarginLeft <Int32>] [-MarginRight <Int32>] [-EnableGridX] [-GridXValues <Object[]>]
 [-EnableGridY] [-GridYValues <Object[]>] [-DisableAnimations] [-MotionStiffness <Int32>]
 [-MotionDamping <Int32>] [-Keys <String[]>] [-DotSize <Int32>] [-DotBorderWidth <Int32>]
 [-DisableStackTooltip] [-AxisTop <Object>] [-AxisBottom <Object>] [-AxisLeft <Object>] [-AxisRight <Object>]
 [-Stream] [-OffsetType <String>] [-Order <String>] [-Curve <String>] [-FillOpactiy <Single>]
 [-DotColor <String>] [<CommonParameters>]
```

### Treemap
```
New-UDNivoChart [-Id <String>] -Data <Object> [-Definitions <Object>] [-Fill <Object>] [-BorderWidth <Int32>]
 [-BorderColor <String>] [-Responsive] [-Width <Int32>] [-Height <Int32>] [-Colors <Object>]
 [-ColorBy <Object>] [-UseDataColor] [-DisableInteractive] [-OnClick <Object>] [-MarginTop <Int32>]
 [-MarginBottom <Int32>] [-MarginLeft <Int32>] [-MarginRight <Int32>] [-InnerPadding <Single>] [-DisableLabel]
 [-Treemap] [-Identity <String>] [-Value <String>] [-Tile <String>] [-LeavesOnly] [-OuterPadding <Int32>]
 [<CommonParameters>]
```

### Heatmap
```
New-UDNivoChart [-Id <String>] -Data <Object> [-Definitions <Object>] [-Fill <Object>] [-IndexBy <String>]
 [-MinValue <Int32>] [-MaxValue <Int32>] [-Padding <Single>] [-Responsive] [-Width <Int32>] [-Height <Int32>]
 [-Colors <Object>] [-ColorBy <Object>] [-UseDataColor] [-DisableInteractive] [-OnClick <Object>]
 [-MarginTop <Int32>] [-MarginBottom <Int32>] [-MarginLeft <Int32>] [-MarginRight <Int32>]
 [-LabelSkipWidth <Int32>] [-LabelSkipHeight <Int32>] [-EnableGridX] [-GridXValues <Object[]>] [-EnableGridY]
 [-GridYValues <Object[]>] [-DisableAnimations] [-MotionStiffness <Int32>] [-MotionDamping <Int32>]
 [-Keys <String[]>] [-CellOpacity <Single>] [-CellBorderWidth <Int32>] [-Heatmap] [-ForceSquare]
 [-SizeVariation <Int32>] [-DisableLabels] [<CommonParameters>]
```

### Line
```
New-UDNivoChart [-Id <String>] -Data <Object> [-Definitions <Object>] [-Fill <Object>] [-Responsive]
 [-Width <Int32>] [-Height <Int32>] [-Colors <Object>] [-ColorBy <Object>] [-UseDataColor]
 [-DisableInteractive] [-OnClick <Object>] [-MarginTop <Int32>] [-MarginBottom <Int32>] [-MarginLeft <Int32>]
 [-MarginRight <Int32>] [-EnableGridX] [-GridXValues <Object[]>] [-EnableGridY] [-GridYValues <Object[]>]
 [-Layers <String[]>] [-DotSize <Int32>] [-DotBorderWidth <Int32>] [-DisableStackTooltip] [-AxisTop <Object>]
 [-AxisBottom <Object>] [-AxisLeft <Object>] [-AxisRight <Object>] [-Line] [-LineWidth <Int32>] [-EnableArea]
 [-AreaBaselineValue <String>] [-AreaOpacity <Single>] [-AreaBlendMode <String>] [-DisableDots]
 [-EnableDotLabel] [-DotLabelYOffset <Int32>] [-YScaleStacked] [-YScaleMin <Int32>] [-YScaleMax <Int32>]
 [-Curve <String>] [<CommonParameters>]
```

### Calendar
```
New-UDNivoChart [-Id <String>] -Data <Object> [-Definitions <Object>] [-Fill <Object>] [-Responsive]
 [-Width <Int32>] [-Height <Int32>] [-Colors <Object>] [-ColorBy <Object>] [-UseDataColor]
 [-DisableInteractive] [-OnClick <Object>] [-MarginTop <Int32>] [-MarginBottom <Int32>] [-MarginLeft <Int32>]
 [-MarginRight <Int32>] [-Calendar] -From <DateTime> -To <DateTime> [-Domain <Object>] [-EmptyColor <Object>]
 [-YearSpacing <Int32>] [-YearLegendOffset <Int32>] [-MonthSpacing <Int32>] [-MonthLegendOffset <Int32>]
 [-DaySpacing <Int32>] [-DayLegendOffset <Int32>] [<CommonParameters>]
```

## DESCRIPTION
Creates a Nivo chart. 

## EXAMPLES

### Simple Bar Chart
```powershell
$Data = @(
    @{
        state = "idaho"
        population = 1720000
    }
    @{
        state = "wisconsin"
        population = 5800000
    }
    @{
        state = "montana"
        population = 1050000
    }
    @{
        state = "illinois"
        population = 12800000
    }
)

New-UDNivoChart -Bar -Data $Data -Keys 'population' -IndexBy 'state' -Height 500 -Width 1000 -MarginTop 50 -MarginRight 130 -MarginBottom 50 -MarginLeft 60 -Padding 0.3
```

This is a simple Nivo bar chart. The data must be in a key value format such as the one defined below. This particular chart is indexed by state and the y-axis is the population. 

### Multiple Data Keys
```powershell
$Data = @(
    @{
        state = "idaho"
        programmers = 45021
        farmers = 532453
    }
    @{
        state = "wisconsin"
        programmers = 234242
        farmers = 2345234
    }
    @{
        state = "montana"
        programmers = 97233
        farmers = 654434
    }
    @{
        state = "illinois"
        programmers = 123121
        farmers = 4535353
    }
)

New-UDNivoChart -Bar -Data $Data -Keys @('programmers', 'farmers') -IndexBy 'state' -Height 500 -Width 1000 -MarginTop 50 -MarginRight 130 -MarginBottom 50 -MarginLeft 60 -Padding 0.3
```

This bar chart provides multiple data points per indexed bar. 

### Grouped Layout
```powershell
$Data = @(
    @{
        state = "idaho"
        programmers = 45021
        farmers = 532453
    }
    @{
        state = "wisconsin"
        programmers = 234242
        farmers = 2345234
    }
    @{
        state = "montana"
        programmers = 97233
        farmers = 654434
    }
    @{
        state = "illinois"
        programmers = 123121
        farmers = 4535353
    }
)

New-UDNivoChart -Bar -Data $Data -Keys @('programmers', 'farmers') -IndexBy 'state' -Height 500 -Width 1000 -MarginTop 50 -MarginRight 130 -MarginBottom 50 -MarginLeft 60 -Padding 0.3 -GroupMode grouped
```

### Horizontal Layout
```powershell
$Data = @(
    @{
        state = "idaho"
        programmers = 45021
        farmers = 532453
    }
    @{
        state = "wisconsin"
        programmers = 234242
        farmers = 2345234
    }
    @{
        state = "montana"
        programmers = 97233
        farmers = 654434
    }
    @{
        state = "illinois"
        programmers = 123121
        farmers = 4535353
    }
)

New-UDNivoChart -Bar -Data $Data -Keys @('programmers', 'farmers') -IndexBy 'state' -Height 500 -Width 1000 -MarginTop 50 -MarginRight 130 -MarginBottom 50 -MarginLeft 60 -Padding 0.3 -Layout horizontal
```

### Simple Calendar 
```powershell
$Data = @()
for($i = 365; $i -gt 0; $i--) {
    $Data += @{
        day = (Get-Date).AddDays($i * -1).ToString("yyyy-MM-dd")
        value = Get-Random
    }
}

$From = (Get-Date).AddDays(-365)
$To = Get-Date

New-UDNivoChart -Calendar -Data $Data -From $From -To $To -Height 500 -Width 1000 -MarginTop 50 -MarginRight 130 -MarginBottom 50 -MarginLeft 60
```

The data needs to be an array of day and value hashtables. The day should be formatted in year, month, day format. For example: 2019-04-07 . You will need to set the start date and end date using the -To and -From values. 

### Heatmap 
```powershell
$Data = @(
    @{
        state = "idaho"
        cats = 72307
        dogs = 23429
        moose = 23423
        bears = 784
    }
    @{
        state = "wisconsin"
        cats = 2343342
        dogs = 3453623
        moose = 1
        bears = 23423
    }
    @{
        state = "montana"
        cats = 9234
        dogs = 3973457
        moose = 23472
        bears = 347303
    }
    @{
        state = "colorado"
        cats = 345973789
        dogs = 0237234
        moose = 2302
        bears = 2349772
    }
)
New-UDNivoChart -Heatmap -Data $Data -IndexBy 'state' -keys @('cats', 'dogs', 'moose', 'bears')  -Height 500 -Width 1000 -MarginTop 50 -MarginRight 130 -MarginBottom 50 -MarginLeft 60
```

A heat map shows a set of data in a grid in line with other vectors of data. You will need to define an array of hashtables. One axis will be the property to index by while the other vector will be a set of keys as defined by other properties of the hash table. 

## PARAMETERS

### -AreaBaselineValue
Define the value to be used for area baseline. Please note that this value isn't the position of the baseline but the value used to compute it.

```yaml
Type: String
Parameter Sets: Line
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AreaBlendMode
Defines CSS mix-blend-mode property for areas.

```yaml
Type: String
Parameter Sets: Line
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AreaOpacity
Area opacity (0~1), depends on EnableArea.

```yaml
Type: Single
Parameter Sets: Line
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AxisBottom
Bottom axis configuration. Use New-UDNivoChartAxisOptions to create the object for this parameter.

```yaml
Type: Object
Parameter Sets: Bar, Stream, Line
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AxisLeft
Left axis configuration. Use New-UDNivoChartAxisOptions to create the object for this parameter.

```yaml
Type: Object
Parameter Sets: Bar, Stream, Line
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AxisRight
Right axis configuration. Use New-UDNivoChartAxisOptions to create the object for this parameter.

```yaml
Type: Object
Parameter Sets: Bar, Stream, Line
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AxisTop
Top axis configuration. Use New-UDNivoChartAxisOptions to create the object for this parameter.

```yaml
Type: Object
Parameter Sets: Bar, Stream, Line
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Bar
Creates a Bar chart.

```yaml
Type: SwitchParameter
Parameter Sets: Bar
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -BorderColor
Border color.

```yaml
Type: String
Parameter Sets: Bar, Pie, Stream, Treemap
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -BorderRadius
The rounding of the border in pixels.

```yaml
Type: Int32
Parameter Sets: Bar
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -BorderWidth
The width of the border in pixels.

```yaml
Type: Int32
Parameter Sets: Bar, Pie, Stream, Treemap
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Calendar
Creates a calendar chart.

```yaml
Type: SwitchParameter
Parameter Sets: Calendar
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CellBorderWidth
Cell border width (px).

```yaml
Type: Int32
Parameter Sets: Heatmap
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CellOpacity
Cell opacity (0~1).

```yaml
Type: Single
Parameter Sets: Heatmap
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ColorBy
Property to use to determine node color.

```yaml
Type: Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Colors
Defines color range.

```yaml
Type: Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CornerRadius
Rounded slices.

```yaml
Type: Int32
Parameter Sets: Pie
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Curve
Curve interpolation.

```yaml
Type: String
Parameter Sets: Stream, Line
Aliases:
Accepted values: basis, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Data
The data for the chart. Each chart has a different data shape requirement. Visit the documentation for full examples of the data shape.

```yaml
Type: Object
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DayLegendOffset
define offset from day edge to its label.

```yaml
Type: Int32
Parameter Sets: Calendar
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DaySpacing
define spacing between each day cell.

```yaml
Type: Int32
Parameter Sets: Calendar
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Definitions
Pattern or gradient definitions. Use New-UDNivoPattern to create a new pattern or gradient. 

```yaml
Type: Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisableAnimations
Disables chart animations.

```yaml
Type: SwitchParameter
Parameter Sets: Bar, Stream, Heatmap
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisableDots
Disables dots on the line chart.

```yaml
Type: SwitchParameter
Parameter Sets: Line
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisableInteractive
Disables interaction. OnClick handlers will not be fired.

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

### -DisableLabel
Disables labels.

```yaml
Type: SwitchParameter
Parameter Sets: Bar, Treemap
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisableLabels
Disables labels

```yaml
Type: SwitchParameter
Parameter Sets: Heatmap
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisableRadiusLabels
Disables labels on the radius of the pie chart.

```yaml
Type: SwitchParameter
Parameter Sets: Pie
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisableSliceLabels
Disables labels on the slices of the pie chart.

```yaml
Type: SwitchParameter
Parameter Sets: Pie
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisableStackTooltip
Disables the stacked tool tip.

```yaml
Type: SwitchParameter
Parameter Sets: Stream, Line
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Domain
define min/max value (eg. @(0, 300) to compute colors, if set to auto, it extract min/max value from data property.

```yaml
Type: Object
Parameter Sets: Calendar
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DotBorderWidth
Width of the dots border (px).

```yaml
Type: Int32
Parameter Sets: Stream, Line
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DotColor


```yaml
Type: String
Parameter Sets: Stream
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DotLabelYOffset
Label Y offset from dot shape (px).  

```yaml
Type: Int32
Parameter Sets: Line
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DotSize
Size of the dots (px).

```yaml
Type: Int32
Parameter Sets: Stream, Line
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EmptyColor
color to use to fill days without available value.

```yaml
Type: Object
Parameter Sets: Calendar
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnableArea
Enable/disable area below each line.

```yaml
Type: SwitchParameter
Parameter Sets: Line
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnableDotLabel
Enable/disable dots label.

```yaml
Type: SwitchParameter
Parameter Sets: Line
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnableGridX
Enable/disable x grid. 

```yaml
Type: SwitchParameter
Parameter Sets: Bar, Stream, Heatmap, Line
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnableGridY
Enable/disable y grid.

```yaml
Type: SwitchParameter
Parameter Sets: Bar, Stream, Heatmap, Line
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EndAngle
End angle (deg.) useful to make gauges for example.

```yaml
Type: Int32
Parameter Sets: Pie
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Fill
Assigns patterns and gardients to elements. Use New-UDNivoFill to create objects for this property.

```yaml
Type: Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FillOpactiy
Layers fill opacity.

```yaml
Type: Single
Parameter Sets: Stream
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Fit
If 'true', pie will be omptimized to occupy more space when using partial pie.

```yaml
Type: Boolean
Parameter Sets: Pie
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ForceSquare
Force square cells (width = height).

```yaml
Type: SwitchParameter
Parameter Sets: Heatmap
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -From
start date

```yaml
Type: DateTime
Parameter Sets: Calendar
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -GridXValues
Specify values to use for vertical grid lines.

```yaml
Type: Object[]
Parameter Sets: Bar, Stream, Heatmap, Line
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -GridYValues
Specify values to use for horizontal grid lines.

```yaml
Type: Object[]
Parameter Sets: Bar, Stream, Heatmap, Line
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -GroupMode

How to group bars, must be one of: 'grouped', 'stacked'.

```yaml
Type: String
Parameter Sets: Bar
Aliases:
Accepted values: grouped, stacked

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Heatmap
Creates a heatmap.

```yaml
Type: SwitchParameter
Parameter Sets: Heatmap
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Height
not required if using -Responsive
Also note that width exclude top/bottom axes, please add margin to make sure they're visible.

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

### -Id
Id for this chart.

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

### -Identity
The key used to get the node's identity.

```yaml
Type: String
Parameter Sets: Treemap
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IndexBy
Key to use to index the data, this key must exist in each data item.

```yaml
Type: String
Parameter Sets: Bar, Heatmap
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InnerPadding
Padding between elements in the chart.

```yaml
Type: Single
Parameter Sets: Bar, Treemap
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InnerRadius
Padding between slices.

```yaml
Type: Int32
Parameter Sets: Pie
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Keys
Keys to use to determine each serie.

```yaml
Type: String[]
Parameter Sets: Bar
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

```yaml
Type: String[]
Parameter Sets: Stream, Heatmap
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LabelSkipHeight
Skip label if bar height is lower than provided value, ignored if 0 (px).

```yaml
Type: Int32
Parameter Sets: Bar, Heatmap
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LabelSkipWidth
Skip label if bar width is lower than provided value, ignored if 0 (px).

```yaml
Type: Int32
Parameter Sets: Bar, Heatmap
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Layers
Defines the order of layers, available layers are:grid, axes, bars, markers, legends.

```yaml
Type: String[]
Parameter Sets: Bar, Line
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Layout
How to display bars, must be one of: 'horizontal', 'vertical'.

```yaml
Type: String
Parameter Sets: Bar
Aliases:
Accepted values: vertical, horizontal

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LeavesOnly

Only render leaf nodes (no parent).

```yaml
Type: SwitchParameter
Parameter Sets: Treemap
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Line
Creates a line chart.

```yaml
Type: SwitchParameter
Parameter Sets: Line
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LineWidth
Line width (px).

```yaml
Type: Int32
Parameter Sets: Line
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MarginBottom
Margin on the bottom of the chart.

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

### -MarginLeft
Margin on the left of the chart.

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

### -MarginRight
Margin on the right of the chart.

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

### -MarginTop
Margin on the top of the chart.

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

### -MaxValue
Maximum value, if 'auto', will use max value from the provided data.

```yaml
Type: Int32
Parameter Sets: Bar, Heatmap
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MinValue
Minimum value, if 'auto', will use min value from the provided data.

```yaml
Type: Int32
Parameter Sets: Bar, Heatmap
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MonthLegendOffset
define offset from month edge to its label.

```yaml
Type: Int32
Parameter Sets: Calendar
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MonthSpacing

```yaml
Type: Int32
Parameter Sets: Calendar
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MotionDamping
Motion damping.

```yaml
Type: Int32
Parameter Sets: Bar, Stream, Heatmap
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MotionStiffness
Motion stiffness.

```yaml
Type: Int32
Parameter Sets: Bar, Stream, Heatmap
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OffsetType

```yaml
Type: String
Parameter Sets: Stream
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OnClick
And endpoint to receive onClick events from the chart. $EventData will be a JSON string containing informationa about the point in the
chart that was clicked. OnClick does not work when -DisableInteraction is specified. 

```yaml
Type: Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Order
Layers order.

```yaml
Type: String
Parameter Sets: Stream
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OuterPadding
Padding on the outside of blocks.

```yaml
Type: Int32
Parameter Sets: Treemap
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PadAngle
Padding (deg.) between each pie slice.

```yaml
Type: Int32
Parameter Sets: Pie
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Padding
Padding between each bar (ratio).

```yaml
Type: Single
Parameter Sets: Bar, Heatmap
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Pie
Creates a pie chart.

```yaml
Type: SwitchParameter
Parameter Sets: Pie
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RadialLabelsLinkDiagonalLength
Link diagonal length.

```yaml
Type: Int32
Parameter Sets: Pie
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RadialLabelsLinkHorizontalLength
Links horizontal length.

```yaml
Type: Int32
Parameter Sets: Pie
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RadialLabelsLinkStrokeWidth
Links stroke width.

```yaml
Type: Int32
Parameter Sets: Pie
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RadialLabelsTextXOffset
X offset from links' end.

```yaml
Type: Int32
Parameter Sets: Pie
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RadiusLabelSkipAngle
Skip label if corresponding slice's angle is lower than provided value.

```yaml
Type: Int32
Parameter Sets: Pie
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RadiusLabelsLinkOffset
Link offset from pie outer radius, useful to have links overlapping pie slices.

```yaml
Type: Int32
Parameter Sets: Pie
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Responsive
The height and width of the chart will automatically adjust to fit its parent.

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

### -Reverse
Reverses the data.

```yaml
Type: SwitchParameter
Parameter Sets: Bar
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SizeVariation
Size variation (0~1), if value is 0 size won't be affected. If you use for example the value 0.3, cell width/height will vary between 0.7~1 according to its corresponding value.

```yaml
Type: Int32
Parameter Sets: Heatmap
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SlicesLabelsSkipAngle
Skip label if corresponding slice's angle is lower than provided value.

```yaml
Type: Int32
Parameter Sets: Pie
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SlicesLabelsTextColor

```yaml
Type: Int32
Parameter Sets: Pie
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SortByValue
If 'true', arcs will be ordered according to their associated value.

```yaml
Type: SwitchParameter
Parameter Sets: Pie
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -StartAngle
Start angle (deg.) useful to make gauges for example.

```yaml
Type: Int32
Parameter Sets: Pie
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Stream
Creates a stream chart.

```yaml
Type: SwitchParameter
Parameter Sets: Stream
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Tile
valid values are: 'squarify', 'slice', 'dice', 'slice-dice',

```yaml
Type: String
Parameter Sets: Treemap
Aliases:
Accepted values: squarify, slice, dice, slice-dice

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -To
End date

```yaml
Type: DateTime
Parameter Sets: Calendar
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Treemap
Creates a treemap

```yaml
Type: SwitchParameter
Parameter Sets: Treemap
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseDataColor
Specifies whether to use the color defined in the data as the color that is used on the chart.

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

### -Value
The key to use to retrieve nodes value.

```yaml
Type: String
Parameter Sets: Treemap
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Width
The width of the chart in pixels.

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

### -YScaleMax
The max value for the y axis.

```yaml
Type: Int32
Parameter Sets: Line
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -YScaleMin
The min value for the y axis.

```yaml
Type: Int32
Parameter Sets: Line
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -YScaleStacked
Whether to stack the y scale.

```yaml
Type: SwitchParameter
Parameter Sets: Line
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -YearLegendOffset
Offset for the year legend.

```yaml
Type: Int32
Parameter Sets: Calendar
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -YearSpacing
Spacing around the years.

```yaml
Type: Int32
Parameter Sets: Calendar
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.
For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None

## OUTPUTS

### System.Object
## NOTES

## RELATED LINKS
