# Floating Action Button

{% hint style="info" %}
Universal Dashboard is now a part of PowerShell Universal. This documentation is for reference to the v2 version of Universal Dashboard and is no longer maintained. PowerShell Universal Documentation can be found [here](https://docs.ironmansoftware.com).
{% endhint %}

## Floating Action Button

### Creating a floating action button

{% hint style="info" %}
See [Event Handler Endpoints ](https://docs.universaldashboard.io/endpoints/event-handler-endpoints)for more information about how event handlers work.
{% endhint %}

A floating action button will appear in the bottom right and can expand to multiple actions on hover.

```text
New-UDFab -ButtonColor 'orange' -Icon bathtub -Size Large -onClick {
    Show-UDToast -Message "Take a bath!"
} -Content {
    New-UDFabButton -ButtonColor 'blue' -Icon fax -onClick {
        Show-UDToast -Message "Send a fax!"
    }
}
```

![](../.gitbook/assets/fab%20%282%29.gif)

