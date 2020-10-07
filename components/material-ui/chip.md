# Chip

{% hint style="info" %}
Universal Dashboard is now a part of PowerShell Universal. This documentation is for reference to the v2 version of Universal Dashboard and is no longer maintained. PowerShell Universal Documentation can be found [here](https://docs.ironmansoftware.com).
{% endhint %}

## Chip

### Label

```text
New-UDMuChip -Label "my Label" -Id "chip"
```

![Chip with label](../../.gitbook/assets/image%20%2829%29.png)

### Icon

```text
$Icon = New-UDMuIcon -Icon 'user' -Size sm -Style @{color = '#fff'}
New-UDMuChip -Label "Demo User" -Icon $Icon
```

![Chip with Icon](../../.gitbook/assets/image%20%2852%29.png)

### OnClick

```text
 New-UDMuChip -Label "my Label" -OnClick {
     Show-UDToast 'Clicked' -Position topLeft
 }
```

![Clickable Chip](../../.gitbook/assets/chip.gif)

### OnDelete

```text
 New-UDMuChip -Label "my Label" -OnDelete {
     Show-UDToast 'Deleted' -Position topLeft
 }
```

![Delete Chip](../../.gitbook/assets/chipdelete.gif)

