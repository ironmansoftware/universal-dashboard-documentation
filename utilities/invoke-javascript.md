# Invoke JavaScript

## Invoke-UDJavaScript

You can use Invoke-UDJavaScript to execute arbitrary JavaScript from any UD Endpoint. 

```text
Invoke-UDJavaScript -javaScript "console.log('Hello!')"
```

## Invoke-UDEvent

You can use Invoke-UDEvent to invoke the event handler for any element using JavaScript. 

```text
Invoke-UDEvent -Id 'elementId' -Event 'onClick'
```

