# Nivo

{% hint style="info" %}
Not available in Community Edition

Requires 2.2.0-beta2
{% endhint %}

## About Nivo

Nivo provides a rich set of dataviz components, built on top of the awesome D3 and React libraries.

* [Nivo](https://nivo.rocks/)
* [D3](https://d3js.org/)
* [React](https://github.com/facebook/react)

The Universal Dashboard Nivo implementation exposes numerous different types of data visualizations. You can view your data in standard bar and line charts or calendar or treemap views that look at data in different ways. The charts are interactive and can be updated automatically. 

You can play with all the different charts over on the [Nivo website](https://nivo.rocks/components).

## Creating a Nivo chart

Nivo charts are created with the `New-UDNivoChart` cmdlet. You can provide data and customize the chart in tons of different ways. Let's create a simple line chart. 

```text
 $Data = @(
    @{
        id = 'stock price'
        data = 1..50 | ForEach-Object {
            @{
                x = (Get-Date).AddDays($_ * -1)
                y = (Get-Random -Minimum 0 -Maximum 100)
            }
        }
    }
)
New-UDNivoChart -Line -Data $Data -Height 400 -Width 900
```

The above code produces the following chart. 

![Nivo Line Chart](../../../.gitbook/assets/image%20%2810%29.png)

As you can see the data needs to be a  particular format for each type of chart. The documentation for each chart will provide the data structure you should use. For Example: the "Calendar" requires an object containing HashTables whereas some charts may accept JSON or PowerShell objects.

## Colors

Nivo comes with numerous color palettes out of the box. You can select [one of the color palettes](https://nivo.rocks/guides/colors) by name using the `-Colors` property. 

```text
 $Data = @(
    @{
        country = 'USA'
        burgers = (Get-Random -Minimum 10 -Maximum 100)
        fries = (Get-Random -Minimum 10 -Maximum 100)
        sandwich = (Get-Random -Minimum 10 -Maximum 100)
    }
    @{
        country = 'Germany'
        burgers = (Get-Random -Minimum 10 -Maximum 100)
        fries = (Get-Random -Minimum 10 -Maximum 100)
        sandwich = (Get-Random -Minimum 10 -Maximum 100)
    }
    @{
        country = 'Japan'
        burgers = (Get-Random -Minimum 10 -Maximum 100)
        fries = (Get-Random -Minimum 10 -Maximum 100)
        sandwich = (Get-Random -Minimum 10 -Maximum 100)
    }
)
New-UDNivoChart -Colors 'dark2' -Bar -Data $Data -Height 400 -Width 900 -Keys @('burgers', 'fries', 'sandwich')  -IndexBy 'country'    
```

The above script produces the following chart. 

![Bar chart with the dark2 color palette](../../../.gitbook/assets/image%20%2817%29.png)

## Patterns

You can also define patterns to use with your charts. You can use lines, dots or squares to provide extra emphasis to particular vectors of a series. 

The first step is to define a pattern using `New-UDNivoPattern` . The following pattern creates dots that are staggered and padded 1 pixel. The color of the dot is `#38bcb2` and the background color is the color inherited from the color palette defined for the chart.

```text
$Pattern = New-UDNivoPattern -Dots -Id 'dots' -Background "inherit" -Color "#38bcb2" -Size 4 -Padding 1 -Stagger
```

The next step is to assign the pattern to one or more elements in the series. You can use `New-UDNivoFill` to specify element ID's and pattern ID's.

```text
$Fill = New-UDNivoFill -ElementId "fries" -PatternId 'dots'
```

Now, the fries element will be assigned the pattern. You'll have to pass the pattern and fill to the `New-UDNivoChart` cmdlet. 

The full chart script looks like this.

```text
$Data = @(
    @{
        country = 'USA'
        burgers = (Get-Random -Minimum 10 -Maximum 100)
        fries = (Get-Random -Minimum 10 -Maximum 100)
        sandwich = (Get-Random -Minimum 10 -Maximum 100)
    }
    @{
        country = 'Germany'
        burgers = (Get-Random -Minimum 10 -Maximum 100)
        fries = (Get-Random -Minimum 10 -Maximum 100)
        sandwich = (Get-Random -Minimum 10 -Maximum 100)
    }
    @{
        country = 'Japan'
        burgers = (Get-Random -Minimum 10 -Maximum 100)
        fries = (Get-Random -Minimum 10 -Maximum 100)
        sandwich = (Get-Random -Minimum 10 -Maximum 100)
    }
)

$Pattern = New-UDNivoPattern -Dots -Id 'dots' -Background "inherit" -Color "#38bcb2" -Size 4 -Padding 1 -Stagger
$Fill = New-UDNivoFill -ElementId "fries" -PatternId 'dots'

New-UDNivoChart -Definitions $Pattern -Fill $Fill -Bar -Data $Data -Height 400 -Width 900 -Keys @('burgers', 'fries', 'sandwich')  -IndexBy 'country'
```

The above script results in the following chart. 

![Bar chart with a pattern](../../../.gitbook/assets/image%20%2816%29.png)

## Interactive Charts

Nivo charts support `OnClick` event handlers. You can provide a script block to the `-OnClick` parameter of `New-UDNivoChart` to create an event handler. When a user clicks the chart, your script block will be invoked and the `$EventData` property will be populated with the JSON from the Nivo chart. The event data contains the data point as well as positional information. 

```text
$Data = @(
    @{
        country = 'USA'
        burgers = (Get-Random -Minimum 10 -Maximum 100)
        fries = (Get-Random -Minimum 10 -Maximum 100)
        sandwich = (Get-Random -Minimum 10 -Maximum 100)
    }
    @{
        country = 'Germany'
        burgers = (Get-Random -Minimum 10 -Maximum 100)
        fries = (Get-Random -Minimum 10 -Maximum 100)
        sandwich = (Get-Random -Minimum 10 -Maximum 100)
    }
    @{
        country = 'Japan'
        burgers = (Get-Random -Minimum 10 -Maximum 100)
        fries = (Get-Random -Minimum 10 -Maximum 100)
        sandwich = (Get-Random -Minimum 10 -Maximum 100)
    }
)
New-UDNivoChart -Bar -Data $Data -Height 400 -Width 900 -Keys @('burgers', 'fries', 'sandwich')  -IndexBy 'country' -OnClick {
    Show-UDToast -Message $EventData -Position topLeft
}
```

The above script produces the following chart.

![Interactive Nivo Chart](../../../.gitbook/assets/interactive%20%281%29.gif)

## Auto-Reloading Charts

Rather than implementing an endpoint parameter directly, the Nivo charts rely on their parent to refresh. The easiest way to accomplish this is to place a Nivo chart in a UDColumn that auto refreshes. Make sure to specify the `-Id` parameter for the chart as React will not know to update the chart data unless there is a persistent Id specified. 

Here's an example of a chart that reloads every second.

```text
New-UDRow -Columns {
    New-UDColumn -SmallSize 6 -AutoRefresh -RefreshInterval 1 -Endpoint { 
        $Data = @(
            @{
                country = 'USA'
                burgers = (Get-Random -Minimum 10 -Maximum 100)
                fries = (Get-Random -Minimum 10 -Maximum 100)
                sandwich = (Get-Random -Minimum 10 -Maximum 100)
            }
            @{
                country = 'Germany'
                burgers = (Get-Random -Minimum 10 -Maximum 100)
                fries = (Get-Random -Minimum 10 -Maximum 100)
                sandwich = (Get-Random -Minimum 10 -Maximum 100)
            }
            @{
                country = 'Japan'
                burgers = (Get-Random -Minimum 10 -Maximum 100)
                fries = (Get-Random -Minimum 10 -Maximum 100)
                sandwich = (Get-Random -Minimum 10 -Maximum 100)
            }
        )
    
        New-UDNivoChart -Id 'barChart' -Bar -Data $Data -Height 400 -Width 900 -Keys @('burgers', 'fries', 'sandwich')  -IndexBy 'country'
    }
}
```

The resulting chart looks like this. 

![Autorefresh Nivo Chart](../../../.gitbook/assets/autorefresh%20%281%29.gif)

You can also control the animations by either disabling them with `-DisableAnimation` or change the damping and stiffness with `-MotionDamping` and `-MotionStiffness`.

