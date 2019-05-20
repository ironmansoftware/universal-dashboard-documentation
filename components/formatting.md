# Formatting

## Formatting with Layouts

Layouts provide a simple way to format dashboards into columns and rows. The New-UDLayout cmdlet has a Columns parameter to specify the number of columns in the layout. Based on the content of the layout, rows will be added whenever there are more items than columns.

For example, a layout with three cards and three columns would be formatted like this.

```text
New-UDLayout -Columns 3 -Content {  
    New-UDCard  
    New-UDCard  
    New-UDCard  
}
```

|  |  |  |
| :--- | :--- | :--- |


If you were to specify more than three items in the content, another row would be added.

```text
New-UDLayout -Columns 3 -Content {    
    New-UDCard    
    New-UDCard    
    New-UDCard    
     New-UDCard     
     New-UDCard    
     New-UDCard    
}
```

|  |  |  |
| :--- | :--- | :--- |
|  |  |  |

## Formatting with Rows and Columns

For more control over the format of your dashboard, you can use the New-UDRow and New-UDColumn cmdlets. The row and column system is a PowerShell implementation of the Grid system found in [Materialize](http://materializecss.com/grid.html). Each row is broken down into 12 equally size areas. Each column can be 1-12 in size.

For example, the definition below would create a row with a single column that stretched the width of the page.

```text
New-UDRow -Columns {            
    New-UDColumn -Size 12 {
}            
}
```

|  |
| :--- |


To create two equally sized columns, you could make them both 6 in size.

```text
New-UDRow -Columns {              
    New-UDColumn -Size 6 {
}              
    New-UDColumn -Size 6 {
}              
}
```

|  |  |
| :--- | :--- |


You can also nest rows with in columns.

```text
New-UDRow -Columns {                
    New-UDColumn -Size 6 {
        New-UDRow -Columns {
New-UDColumn -Size 12 {                
               }
 }                
       }
}                
    New-UDColumn -Size 6 {
}                
}
```

