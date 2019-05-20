# Event Handler Endpoints

When ever you create an element that has an event handler, like UDButton's onClick handler, a new endpoint is generated on the server to run your PowerShell script. Because this script is a new endpoint, it will have different variable scoping depending on where it lives within the dashboard. 

## Automatic Variable Scoping

{% hint style="info" %}
Note that automatic variable scoping can be problematic. See manual variable scoping for better control of variable scopes within event handlers. 
{% endhint %}

You can use automatic variable scoping for event handlers. UD will attempt to copy variables used within their parent script block into the endpoint script block. The below example will use the `$Variable` as the contents for the message. 

```text
$Variable = "Test" 

New-UDButton -OnClick {
    Show-UDToast -Message $Variable
}
```

Although this technique usually works, in certain circumstances it can fail to automatically copy variables into the endpoint's scope. This usually happens when dealing with readonly variables or loop variables. 

This for example may not work. `$item` will be null when clicking `Show-UDToast`.

```text
foreach($item in $list) {
    New-UDButton -OnClick {
        Show-UDToast -Message $item
    }
}
```

To work around this limitation, you can use manual variable scoping. 

## Manual Variable Scoping 

Manual variable scoping takes advantage of the `-ArgumentList` parameter of components that provide event handlers. Instead of passing a script block to the event handler parameter, pass a new UDEndpoint to the parameter instead. 

```text
foreach($item in $list) {
    New-UDButton -OnClick (New-UDEndpoint -Endpoint {
        Show-UDToast -Message $ArgumentList[0]
    } -ArgumentList $item)
}
```

Pass any variables you'd like to see within the endpoint through the `-ArgumentList` parameter. Within the endpoint you can access this list of variables via the `$ArgumentList` variable.  

