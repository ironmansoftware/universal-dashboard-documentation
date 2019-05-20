# Bar

## Simple Bar Chart

This is a simple Nivo bar chart. The data must be in a key value format such as the one defined below. This particular chart is indexed by state and the y-axis is the population. 

```text
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

![Simple bar chart](../../../.gitbook/assets/image%20%286%29.png)

## Multiple Data Keys

This bar chart provides multiple data points per indexed bar. 

```text
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

![Bar chart with multiple data keys](../../../.gitbook/assets/image%20%2821%29.png)

## Grouped Layout

This bar chart is grouped rather than stacked. 

```text
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

![Grouped bar chart](../../../.gitbook/assets/image%20%289%29.png)

## Horizontal Layout

```text
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

![Horizontal Layout](../../../.gitbook/assets/image%20%282%29.png)



