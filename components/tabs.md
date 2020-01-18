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

![Tabs](../.gitbook/assets/image%20%2860%29.png)

## Creating a Tab Container that only Renders Tabs When Active

For performance reasons, you may not want a tab to render it's content unless it's displayed. This is helpful for auto-refreshing tables or grids that may be displayed in tabs but not visible by default. The default behavior of tabs is to render all the tabs but hide them when not show. 

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
} -RenderWhenActive
```

## Dynamic Tab Content 

To load content when the dashboard is loaded by the end user, is the `-Dynamic` switch. 

```text
New-UDTabContainer -Tabs {
    New-UDTab -Text "Tab 1" -Content {
        New-UDElement -Tag 'div' -Content { "The date is: $(Get-Date)"}
    } -Dynamic
    New-UDTab -Text "Tab 2" -Content {
        New-UDElement -Tag 'div' -Content { "Tab 2 Content"}
    }
    New-UDTab -Text "Tab 3" -Content {
        New-UDElement -Tag 'div' -Content { "Tab 3 Content"}
    }
}
```

