# Grid Layout

{% hint style="info" %}
Universal Dashboard is now a part of PowerShell Universal. This documentation is for reference to the v2 version of Universal Dashboard and is no longer maintained. PowerShell Universal Documentation can be found [here](https://docs.ironmansoftware.com).
{% endhint %}

## Grid Layout

The `New-UDGridLayout` provides the ability to layout controls on your UD page using JSON instead of deeply nesting controls in `New-UDRow` and `New-UDColumn` controls. It also provides the ability to drag and drop the layout of the page. This eliminates the need to write as much code and provides a much cleaner looking dashboard.

### Getting Started with New-UDGridLayout

To use `New-UDGridLayout`, simply put components you'd like to layout in the `-Content` script block. It is required that all components you wish to layout have an ID set.

```text
New-UDGridLayout -Content {
    New-UDCard -Title "Card 1" -Id 'Card1' 
    New-UDCard -Title "Card 2" -Id 'Card2'
    New-UDCard -Title "Card 3" -Id 'Card3'
}
```

When no layout is provided, the cards will just be stacked on the page.

![](../.gitbook/assets/image%20%2842%29.png)

You can move the cards using the handles in the top right corner of each card. This allows you to resize and move each card.

![](../.gitbook/assets/image%20%2823%29.png)

You can use the `-Persist` cmdlet to store the layout in the browser's local storage.

### Saving Layouts

{% hint style="info" %}
AdminMode mode is only available in the Enterprise Version
{% endhint %}

The layout JSON format is documented on the [React Grid Layout GitHub](https://github.com/strml/react-grid-layout) repository. In order to avoid generating this JSON yourself, you can use the admin mode mode of Universal Dashboard. To do this, specify the `-AdminMode` parameter of `Start-UDDashboard`.

```text
$Dashboard = New-UDDashboard -Title "New-UDGridLayout" -Content {
    New-UDGridLayout -Content {
        New-UDCard -Title "Card 1" -Id 'Card1' 
        New-UDCard -Title "Card 2" -Id 'Card2'
        New-UDCard -Title "Card 3" -Id 'Card3'
    } 
} 
Start-UDDashboard -Dashboard $Dashboard -Port 10001 -AdminMode
```

Now, when you start your dashboard, a floating action button in the bottom right of the dashboard will be shown. Adjust your page as you see fit and then click the Copy Layout button. This will store the JSON in the clipboard which you can copy to your script.

![Copy Layout Button](../.gitbook/assets/image%20%2844%29%20%281%29.png)

To include the layout in your script, place the JSON string as a value to the `-Layout` property of `New-UDGridLayout`.

```text
$Dashboard = New-UDDashboard -Title "New-UDGridLayout" -Content {
    New-UDGridLayout -Layout '{"lg":[{"w":1,"h":1,"x":0,"y":0,"i":"grid-element-Card1","moved":false,"static":true},{"w":3,"h":3,"x":1,"y":4,"i":"grid-element-Card2","moved":false,"static":true},{"w":3,"h":4,"x":1,"y":0,"i":"grid-element-Card3","moved":false,"static":true}]}' -Content {
        New-UDCard -Title "Card 1" -Id 'Card1' 
        New-UDCard -Title "Card 2" -Id 'Card2'
        New-UDCard -Title "Card 3" -Id 'Card3'
    } 
} 
Start-UDDashboard -Dashboard $Dashboard -Port 10001 -AdminMode
```

Once you are satisfied with your layout, you can remove the AdminMe switch.The controls will be laid out as you have defined and the handles will no longer be visible.

![](../.gitbook/assets/image%20%2817%29.png)

