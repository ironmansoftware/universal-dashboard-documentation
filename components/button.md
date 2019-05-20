# Button

Buttons are used for basic interactions from users. You can add event handlers to buttons to perform actions when they are clicked.

## Raised

![](../.gitbook/assets/raised-button.png)

```text
New-UDButton -Text "Button" 
New-UDButton -Text "Button" -Icon cloud -IconAlignment left
New-UDButton -Text "Button" -Icon cloud -IconAlignment right
```

## Floating

![](../.gitbook/assets/floating-button.png)

```text
New-UDButton -Floating -Icon plus
```

## OnClick Event Handler

{% hint style="info" %}
See [Event Handler Endpoints ](https://docs.universaldashboard.io/endpoints/event-handler-endpoints)for more information about how event handlers work.
{% endhint %}

A ScriptBlock that is invoked when the button is clicked.

```text
New-UDButton -Text "Click me!" -OnClick {
    Show-UDToast -Message "Clicked!"
}
```

## Passing Variables to a Button OnClick Handler

```text
$MyVariable = "Some Text"
New-UDButton -Text "Click me!" -OnClick (
    New-UDEndpoint -Endpoint {
        Show-UDToast -Message $ArgumentList[0]
    } -ArgumentList @($MyVariable)
)
```

