# Button

{% hint style="info" %}
Universal Dashboard is now a part of PowerShell Universal. This documentation is for reference to the v2 version of Universal Dashboard and is no longer maintained. PowerShell Universal Documentation can be found [here](https://docs.ironmansoftware.com).
{% endhint %}

## Button

### Contained

```text
New-UDMuButton -Text 'Submit' -Variant contained
```

![Contained Button](../../.gitbook/assets/image%20%2847%29.png)

### Flat

```text
New-UDMuButton -Text 'Submit' -Variant flat
```

![Flat button](../../.gitbook/assets/button.gif)

### Outlined

```text
New-UDMuButton -Text 'Submit' -Variant outlined
```

![Outlined Button](../../.gitbook/assets/image%20%2838%29.png)

### Icons

```text
New-UDMuButton -Text 'Buy' -Variant contained -Icon (New-UDMuIcon -Icon bitcoin -Size '4x')
```

![Icon Button](../../.gitbook/assets/image%20%2865%29.png)

### Full Width

```text
New-UDMuButton -Text 'Submit' -Variant contained -FullWidth
```

![Full Width Button](../../.gitbook/assets/image%20%2848%29.png)

### OnClick Handler

```text
New-UDMuButton -Text 'Submit' -Variant contained -OnClick { 
    Show-UDToast -Message "You clicked me!" -Position topLeft
}
```

![Button onClick Handler](../../.gitbook/assets/buttononclick.gif)

### Custom Colors

```text
New-UDMuButton -Text 'Submit' -Variant contained -Style @{ backgroundColor = "blue"; color = "white" }
```

![Colored Button](../../.gitbook/assets/image%20%2835%29%20%281%29.png)

