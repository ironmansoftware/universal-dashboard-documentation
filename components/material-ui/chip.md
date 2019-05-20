# Chip

## Label

```text
New-UDMuChip -Label "my Label" -Id "chip"
```

![Chip with label](../../.gitbook/assets/image%20%2822%29.png)

## Icon

```text
$Icon = New-UDMuIcon -Icon 'user' -Size sm -Style @{color = '#fff'}
New-UDMuChip -Label "Demo User" -Icon $Icon
```

![Chip with Icon](../../.gitbook/assets/image%20%2837%29.png)

## OnClick

```text
 New-UDMuChip -Label "my Label" -OnClick {
     Show-UDToast 'Clicked' -Position topLeft
 }
```

![Clickable Chip](../../.gitbook/assets/chip.gif)

## OnDelete

```text
 New-UDMuChip -Label "my Label" -OnDelete {
     Show-UDToast 'Deleted' -Position topLeft
 }
```

![Delete Chip](../../.gitbook/assets/chipdelete.gif)

