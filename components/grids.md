# Grids

Grids output data similar to tables but allow for paging and sorting the data in the grid. Grids are produced using the [Griddle ](https://griddlegriddle.github.io/Griddle/docs/)library. Grids are created with the New-UDGrid cmdlet and data for the grid is output using the Out-UDGridData cmdlet.

## Simple Grid

To create a simple grid, pass data from a cmdlet to Out-UDGridData from within the New-UDGrid's Endpoint script block.

```text
New-UdGrid -Title "Processes" -Endpoint {
    Get-Process | Select Name,ID,WorkingSet,CPU | Out-UDGridData
}
```

## Custom Headers

To specify custom headers, use the -Headers parameter of New-UDGrid.

The below script selects the Name, Id, WorkingSet and CPU of ProcessInfo objects returned by Get-Process. The gird auto refreshes every minute.

```text
New-UdGrid -Title "Processes" -Headers @("Name", "ID", "Working Set", "CPU") -Properties @("Name", "Id", "WorkingSet", "CPU") -AutoRefresh -RefreshInterval 60 -Endpoint {
       Get-Process | Select Name,ID,WorkingSet,CPU | Out-UDGridData
}
```

The above script produces the following grid.

![](../.gitbook/assets/griddle.png)

## Formatting DateTimes on the client

If your data set includes a System.DateTime object as one of the properties, the UDGrid component will format the DateTime is the user's browsers local time zone settings. It uses [MomentJS](https://momentjs.com/docs/#/displaying/) to format the date time into a readable string. By default, it uses the `lll` format which yields a date time such as `Sep 4, 1986 8:30 PM`. You can customize the date time format by specifying the `-DateTimeFormat` on `New-UDGrid`.

```text
New-UdGrid -Title "Files" -Headers @("Name", "Last Write Time") -Properties @("Name", "LastWriteTime") -AutoRefresh -RefreshInterval 60 -Endpoint {
       Get-ChildItem C:\temp |  | Out-UDGridData
} -DateTimeFormat 'LLLL'
```

## Including links in columns

In addition to passing raw data down to a grid, you can also include links. Use the `New-UDLink` cmdlet to add links into columns.

```text
$Dashboard = New-UDDashboard -Title "Grids - Custom Columns" -Content {
    New-UDGrid -Title "Animals" -Headers @("Animal", "Order", "Wikipedia") -Properties @("Animal", "Order", "Article") -Endpoint {
    $Data = @(
    [PSCustomObject]@{Animal="Frog";Order="Anura";Article=(New-UDLink -Text "Wikipedia" -Url "https://en.wikipedia.org/wiki/Frog")}
    [PSCustomObject]@{Animal="Tiger";Order="Carnivora";Article=(New-UDLink -Text "Wikipedia" -Url "https://en.wikipedia.org/wiki/Tiger")}
    [PSCustomObject]@{Animal="Bat";Order="Chiroptera";Article=(New-UDLink -Text "Wikipedia" -Url "https://en.wikipedia.org/wiki/Bat")}
    [PSCustomObject]@{Animal="Fox";Order="Carnivora";Article=(New-UDLink -Text "Wikipedia" -Url "https://en.wikipedia.org/wiki/Fox")}
)
        $Data | Out-UDGridData
    }
}
Start-UDDashboard -Dashboard $Dashboard
```

## Server Side Processing

When the `-ServerSideProcessing` parameter is specified, it calls the `Endpoint` script block to perform the paging, filtering and sorting. To allow for this, there are several variables that are provided when the `Endpoint` script block is executed.

| Name | Description | Type |
| :--- | :--- | :--- |
| $Skip | The number of records to skip. | integer |
| $Take | The number of records to take. | integer |
| $SortColumn | The name of the property or column to sort on. | string |
| $SortAscending | Whether to sort ascending, otherwise descending. | string |
| $FilterText | The text to filter items or records by. | string |


```text
$Dashboard = New-UDDashboard -Title "Grids - Custom Columns" -Content {
    $Headers = @("Animal", "Order", "Wikipedia")
    $Properties = @("Animal", "Order", "Article")
    New-UDGrid -Title "Animals" -ServerSideProcessing -PageSize 5 -Headers $Headers -Properties $Properties -Endpoint {
    $Data = @(
    [PSCustomObject]@{Animal="Frog";Order="Anura";Article=(New-UDLink -Text "Wikipedia" -Url "https://en.wikipedia.org/wiki/Frog")}
    [PSCustomObject]@{Animal="Tiger";Order="Carnivora";Article=(New-UDLink -Text "Wikipedia" -Url "https://en.wikipedia.org/wiki/Tiger")}
    [PSCustomObject]@{Animal="Bat";Order="Chiroptera";Article=(New-UDLink -Text "Wikipedia" -Url "https://en.wikipedia.org/wiki/Bat")}
    [PSCustomObject]@{Animal="Fox";Order="Carnivora";Article=(New-UDLink -Text "Wikipedia" -Url "https://en.wikipedia.org/wiki/Fox")}
    [PSCustomObject]@{Animal="Lion";Order="Carnivora";Article=(New-UDLink -Text "Wikipedia" -Url "https://en.wikipedia.org/wiki/Lion")}
    [PSCustomObject]@{Animal="Leopard";Order="Carnivora";Article=(New-UDLink -Text "Wikipedia" -Url "https://en.wikipedia.org/wiki/Leopard")}
    [PSCustomObject]@{Animal="Cat";Order="Carnivora";Article=(New-UDLink -Text "Wikipedia" -Url "https://en.wikipedia.org/wiki/Cat")}
    [PSCustomObject]@{Animal="Goldfish";Order="Cypriniformes";Article=(New-UDLink -Text "Wikipedia" -Url "https://en.wikipedia.org/wiki/Goldfish")}
    [PSCustomObject]@{Animal="Eel";Order="Anguilliformes";Article=(New-UDLink -Text "Wikipedia" -Url "https://en.wikipedia.org/wiki/Eel")}
    [PSCustomObject]@{Animal="Parrot";Order="Anguilliformes";Article=(New-UDLink -Text "Wikipedia" -Url "https://en.wikipedia.org/wiki/Parrot")}
    [PSCustomObject]@{Animal="Crocodile";Order="Crocodilia";Article=(New-UDLink -Text "Wikipedia" -Url "https://en.wikipedia.org/wiki/Crocodile")}
)
        $FilteredAndSortedData = $Data | 
            Where-Object Animal -like "*$filtertext*" |
            Sort-Object $SortColumn -Descending:(!$SortAscending) 
        
        $FilteredAndSortedData | 
            Select-Object -Skip $Skip -First $take |
            Out-UDGridData -TotalItems $FilteredAndSortedData.Count
    }
}
Start-UDDashboard -Dashboard $Dashboard
```
Important points here:
- It's important to do the filter and sort before the paging with skip and first, as it will not behave as expected.
- Totalitems need to be specified, else UD dont know how many pages there are, and it will not display the page info
