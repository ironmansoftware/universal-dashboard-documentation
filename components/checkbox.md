# Checkbox

{% hint style="info" %}
Universal Dashboard is now a part of PowerShell Universal. This documentation is for reference to the v2 version of Universal Dashboard and is no longer maintained. PowerShell Universal Documentation can be found [here](https://docs.ironmansoftware.com).
{% endhint %}

## Checkbox

### Properties

![](../.gitbook/assets/checkbox.png)

```text
New-UDCheckbox -Label Unchecked
New-UDCheckbox -Label Checked -Checked
New-UDCheckbox -Label 'Filled In' -Checked -FilledIn
New-UDCheckbox -Label 'Disabled' -Checked -FilledIn -Disabled
```

### OnChange Handler

{% hint style="info" %}
See [Event Handler Endpoints ](https://docs.universaldashboard.io/endpoints/event-handler-endpoints)for more information about how event handlers work.
{% endhint %}

To handle changes in the checkbox value, you can add a script block or `UDEndpoint` to the `-OnChange` parameter.

```text
New-UDElement -Id "CheckboxState" -Tag "span" 
New-UDCheckbox -Id CheckBox -Label "Check me" -OnChange {
    $Element = Get-UDElement -Id CheckBox
    Set-UDElement -Id "CheckboxState" -Content $Element.Attributes["checked"]
}
```

### Get the value of the Checkbox

To get checkbox value \($true, $false\), you can utilize the `Get-UDElement` cmdlet to retrieve the bool checked value.

```text New-UDCheckbox -Id MyCheckBox -Label "Check me" $CheckboxValue = ((Get-UDElement -Id "MyCheckBox").Attributes["checked"])``

