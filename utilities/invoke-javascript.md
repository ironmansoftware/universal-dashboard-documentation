# Invoke JavaScript

{% hint style="info" %}
Universal Dashboard is now a part of PowerShell Universal. This documentation is for reference to the v2 version of Universal Dashboard and is no longer maintained. PowerShell Universal Documentation can be found [here](https://docs.ironmansoftware.com).
{% endhint %}

## Invoke JavaScript

### Invoke-UDJavaScript

You can use Invoke-UDJavaScript to execute arbitrary JavaScript from any UD Endpoint.

```text
Invoke-UDJavaScript -javaScript "console.log('Hello!')"
```

### Invoke-UDEvent

You can use Invoke-UDEvent to invoke the event handler for any element using JavaScript.

```text
Invoke-UDEvent -Id 'elementId' -Event 'onClick'
```

