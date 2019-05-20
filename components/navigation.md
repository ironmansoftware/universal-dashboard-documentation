# Navigation

{% hint style="info" %}
Requires Universal Dashboard 2.3 or later
{% endhint %}

By default, when new [Pages](pages.md) are added to a dashboard, a navigation menu will be created that provides access to all the static pages. Dynamic pages will not show up in the navigation menu. 

## Customizing Navigation

To customize navigation, you can use the `New-UDSideNav` and `New-UDSideNavItem` cmdlets for full control over the navigation pane. In the simplest form, you can add items to the side navigation and the provide the side nav to the dashboard. 

```text
$Page1 = New-UDPage -Name "Page Name" -Content { New-UDCard -Id 'page-1' }
$Page2 = New-UDPage -Name "Page Name 2" -Content { New-UDCard -Id 'page-2'}

$Navigation = New-UDSideNav -Content {
    New-UDSideNavItem -Text "My First Page" -PageName "Page Name" -Icon group
    New-UDSideNavItem -Text "My Second Page" -PageName "Page Name 2" -Icon User
    New-UDSideNavItem -Text "Google" -Url 'https://www.google.com' -Icon Users
}

$Dashboard = New-UDDashboard -Title "Navigation" -Pages @($Page1, $Page2) -Navigation $Navigation
```

## Hiding the Side Navigation and Hamburger Menu Button

You can hide the side navigation completely by using the `-None` parameter of `New-UDSideNav` . 

```text
$Page1 = New-UDPage -Name "Page Name" -Content { New-UDCard -Id 'page-1' }
$Page2 = New-UDPage -Name "Page Name 2" -Content { New-UDCard -Id 'page-2'}

$Navigation = New-UDSideNav -None

New-UDDashboard -Title "Navigation" -Pages @($Page1, $Page2) -Navigation $Navigation
```

## Creating Nested Menu Structures 

To create nested menu structures in the side navigation menu, use the `-Children` parameter of `New-UDSideNavItem` to provide the child nodes for the menu. 

```text
$Page1 = New-UDPage -Name "Page Name" -Content { New-UDCard -Id 'page-1' }
$Page2 = New-UDPage -Name "Page Name 2" -Content { New-UDCard -Id 'page-2'}

$Navigation = New-UDSideNav -Content {
    New-UDSideNavItem -Text "Section" -Children {
        New-UDSideNavItem -Text "My Second Page" -PageName "Page Name 2" -Icon User
        New-UDSideNavItem -Text "Google" -Url 'https://www.google.com' -Icon Users
    }
} -Fixed

New-UDDashboard -Title "Navigation" -Pages @($Page1, $Page2) -Navigation $Navigation
```

## Including Dividers and Subheaders

Menus can include dividers and subheaders. Both of these items can be created using the `New-UDSideNavItem` cmdlet. 

```text
$Page1 = New-UDPage -Name "Page Name" -Content { New-UDCard -Id 'page-1' }
$Page2 = New-UDPage -Name "Page Name 2" -Content { New-UDCard -Id 'page-2'}

$Navigation = New-UDSideNav -Content {
    New-UDSideNavItem -Text "My First Page" -PageName "Page Name" -Icon group
    New-UDSideNavItem -Subheader -Text "Subheader"
    New-UDSideNavItem -Text "My Second Page" -PageName "Page Name 2" -Icon User
    New-UDSideNavItem -Divider
    New-UDSideNavItem -Text "Google" -Url 'https://www.google.com' -Icon Users
} -Fixed

New-UDDashboard -Title "Navigation" -Pages @($Page1, $Page2) -Navigation $Navigation
```

## Dynamically Building Menus

Menus can be built dynamically by providing an endpoint script block to `New-UDSideNav` . This script block will be called the first time a user loads the dashboard and on page refreshes. 

```text
$Page1 = New-UDPage -Name "Page Name" -Content { New-UDCard -Id 'page-1' }
$Page2 = New-UDPage -Name "Page Name 2" -Content { New-UDCard -Id 'page-2'}

$Navigation = New-UDSideNav -Endpoint {
    New-UDSideNavItem -Text "My First Page" -OnClick { Show-UDModal -Content { New-UDCard -Id "ModalCard" } } -Icon group
} -Fixed

New-UDDashboard -Title "Navigation" -Pages @($Page1, $Page2) -Navigation $Navigation
```

