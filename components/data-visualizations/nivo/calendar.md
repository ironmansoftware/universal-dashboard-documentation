# Calendar

Much like the GitHub activity chart, the calendar chart shows a value per day and colors the day based on the value in comparison to the other values. 

## Simple Calendar 

The data needs to be an array of day and value hashtables. The day should be formatted in year, month, day format. For example: `2019-04-07` . You will need to set the start date and end date using the `-To` and `-From` values. 

```text
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

![Simple Calendar Chart](../../../.gitbook/assets/image%20%2813%29.png)



