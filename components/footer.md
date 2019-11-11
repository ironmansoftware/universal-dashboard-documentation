# Footer

The footer can be customized to show different links, set copyright text or to customize the colors. 

## Removing "Created with PowerShell Universal Dashboard"

If you have a license for PowerShell Universal Dashboard Premium or Enterprise, you can remove the link as follows. 

```text
$Footer = New-UDFooter 
$Dashboard = New-UDDashboard -Content { } -Title "Footer" -Footer $Footer
```

## Adding Links to the Footer 

```text
$Footer = New-UDFooter -Links @(
    New-UDLink -Text "Ironman Software" -Url "https://ironmansoftware.com"
    New-UDLink -Text "Poshud.com" -Url "https://poshud.com"
)
$Dashboard = New-UDDashboard -Content { } -Title "Footer" -Footer $Footer
```

## Setting Copyright Text

```text
$Footer = New-UDFooter -Copyright "Ironman Software, 2019"
$Dashboard = New-UDDashboard -Content { } -Title "Footer" -Footer $Footer
```

