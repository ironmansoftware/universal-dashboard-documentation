# Toasts

{% hint style="info" %}
Universal Dashboard is now a part of PowerShell Universal. This documentation is for reference to the v2 version of Universal Dashboard and is no longer maintained. PowerShell Universal Documentation can be found [here](https://docs.ironmansoftware.com).
{% endhint %}

## Toasts

`Show-UDToast` is used to show toasts to the end user. You can show a toast message from any endpoint \(dynamic\) component. You cannot show toasts from Scheduled Endpoints.

### Showing a Basic Toast

```text
 New-UDButton -Text "Show Toast" -OnClick {
    Show-UDToast -Message "Hello"
 }
```

![Basic Toast](../.gitbook/assets/image%20%2835%29.png)

### Customizing the Colors

```text
New-UDButton -Text "Show Toast" -OnClick {
  Show-UDToast -Message "Hello" -BackgroundColor red -MessageColor white
}
```

![Custom Colors](../.gitbook/assets/image%20%2858%29.png)

### Toast Title

```text
New-UDButton -Text "Show Toast" -OnClick {
    Show-UDToast -Message "World" -Title "Hello" 
}
```

![Toast with a Title](../.gitbook/assets/image%20%2844%29.png)

### Changing Positions

```text
New-UDButton -Text "Show Toast" -OnClick {
   Show-UDToast -Message "Hello" -Position topLeft
}
```

![Toast in the Top Left](../.gitbook/assets/image%20%2828%29.png)

### Balloon Toast

```text
New-UDButton -Text "Show Toast" -OnClick {
   Show-UDToast -Message "Hello" -Balloon
}
```

![Showing a balloon toast](../.gitbook/assets/image%20%2818%29.png)

### Duration of Toasts

```text
New-UDButton -Text "Show Toast" -OnClick {
   Show-UDToast -Message "Hello" -Duration 30000
}
```

![30 Second Toast](../.gitbook/assets/image%20%2815%29.png)

### Transitions

```text
New-UDButton -Text "Show Toast" -OnClick {
   Show-UDToast -Message "Hello" -TransitionIn bounceInRight
}
```

![Bounce in Transition](../.gitbook/assets/ieuugq2gmh.gif)

