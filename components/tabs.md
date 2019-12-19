# Tabs

A standard tab control that allows you to specify multiple tabs with a title and content. You can place any UD element within the content. 

## Creating a Tab Container and Tabs

You'll need to create an outer tab container and then include one or more tabs within the container. Each tab needs a Text for the title and a Content script block. 

```text
New-UDTabContainer -Tabs {
    New-UDTab -Text "Tab 1" -Content {
        New-UDElement -Tag 'div' -Content { "Tab 1 Content"}
    }
    New-UDTab -Text "Tab 2" -Content {
        New-UDElement -Tag 'div' -Content { "Tab 2 Content"}
    }
    New-UDTab -Text "Tab 3" -Content {
        New-UDElement -Tag 'div' -Content { "Tab 3 Content"}
    }
}
```

![Tabs](../.gitbook/assets/image%20%2854%29.png)

