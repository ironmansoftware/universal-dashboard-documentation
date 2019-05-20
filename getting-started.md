# Getting Started

## 1. Install

Universal Dashboard is a PowerShell module that can be installed from the PowerShell Gallery.

```text
Install-Module UniversalDashboard -AcceptLicense
```

## 2. Create a Dashboard

Create a new dashboard and add a control to the page.

```text
$Dashboard = New-UDDashboard -Title "Hello, World!" -Content {
    New-UDHeading -Text "Hello, World!" -Size 1
}
```

## 3. Start the Dashboard 

Start the dashboard. Make sure to select an open port. 

```text
Start-UDDashboard -Dashboard $Dashboard -Port 10001
```

## Learn More

* [Concepts](concepts.md)
* [Layouts](components/formatting.md)
* [Components](components/)
* [Security](security/)

