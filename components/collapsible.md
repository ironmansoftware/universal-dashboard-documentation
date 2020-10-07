# Collapsible

{% hint style="info" %}
Universal Dashboard is now a part of PowerShell Universal. This documentation is for reference to the v2 version of Universal Dashboard and is no longer maintained. PowerShell Universal Documentation can be found [here](https://docs.ironmansoftware.com).
{% endhint %}

## Collapsible

Collapsibles are accordion elements that expand when clicked on. They allow you to hide content that is not immediately relevant to the user.

### Creating a Collapsible

`New-UDCollapsible` can be used to create a new group of collapsible items. `New-UDCollapsibleItem` defines a new collapsible item that can contain any other control. The icon and title are customizable.

```text
 New-UDCollapsible -Items {
    New-UDCollapsibleItem -Title "Item 1" -Icon arrow_circle_right -Content {
        "Some content"
    }
}
```

![Collapsible](../.gitbook/assets/collapsible%20%282%29.gif)

