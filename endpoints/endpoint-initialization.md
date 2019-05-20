# Endpoint Initialization

{% hint style="info" %}
Required Version: 2.0 or later
{% endhint %}

Endpoints within Universal Dashboard are run using a shared runspace pool. Runspaces are created and retained to ensure that performance is as best as it can be. As requests come in, more runspaces will be created up to a certain limit and then runspaces will be reused. When the runspaces are created, they are initialized with the return value of the `New-UDEndpointInitialization` cmdlet. This value is passed to the `New-UDDashboard` cmdlet via the `-EndpointInitialization` cmdlet. 

## Passing Variables to Endpoints

Much like `global:` scope variables, variables that you pass to endpoints are available in all endpoints. To pas a variable, simply provide the name of the variable to the initialization cmdlet. 

```text
$MyVariable = "Hi, there!"
New-UDEndpointInitialization -Variable MyVariable
```

You'll now be able to use `$MyVariable` in all your endpoints. 

You can also pass arrays of variable names. 

```text
$MyVariable = "Hi, there!"
$YourVariable = "Good bye!"
New-UDEndpointInitialization -Variable @("MyVariable", "YourVariable")
```

## Passing Functions to Endpoints

Functions are passed just like variables but using the `-Function` parameter. 

```text
function Get-MeABeer () { }
New-UDEndpointInitialization -Function "Get-MeABeer"  
```

They also support arrays. 

```text
function Get-MeABeer () { }
function Get-YourSelfABeer() { }
New-UDEndpointInitialization -Function @("Get-MeABeer", "Get-YourSelfABeer")
```

## Loading Modules in Endpoints

The name or path of the module should be provided to the `-Module` parameter. You can specify arrays of modules or paths. Relative paths are relative to the current file. 

```text
New-UDEndpointInitialization -Module @("ActiveDirectory", ".\HelpFunctions.psm1")
```

## Other Endpoint Initialization Properties

The `New-UDEndpointInitiailization` cmdlet returns a [InitialSessionState object](https://docs.microsoft.com/en-us/dotnet/api/system.management.automation.runspaces.initialsessionstate?view=powershellsdk-1.1.0). This object is part of the PowerShell SDK and provides more customization than does the cmdlet. You can store the result in a variable and set additional properties. 

```text
$Init = New-UDEndpointInitialization 
$Init.LanguageMode = 'ConstrainedLanguage'
```



