# Modal

{% hint style="info" %}
Universal Dashboard is now a part of PowerShell Universal. This documentation is for reference to the v2 version of Universal Dashboard and is no longer maintained. PowerShell Universal Documentation can be found [here](https://docs.ironmansoftware.com).
{% endhint %}

## Modal

Modals are popup windows that appear above the website. You can show a modal from an endpoint using `Show-UDModal`.

### Displaying Modals

In the below example, when you click the button a modal will be shown that contains the text specified. You can place any UD controls within the header and content script blocks.

```text
New-UDButton -Text "Show Modal" -OnClick {
    Show-UDModal -Content {
        New-UDHeading -Text "Hello, Modal"
    }
}
```

Clicking the button will bring up a modal that looks like this.

![Modal with a Heading in the Content](../.gitbook/assets/image%20%2861%29.png)

### Hiding Modals

You can also hide modals using the `Hide-UDModal` cmdlet. This cmdlet takes no arguments and simply hides the modal. This could be done after showing progress. In this example, we create a persistent modal that cannot be hidden by the user. Once the `Start-Sleep` cmdlet timer elapses, the modal will close with `Hide-UDModal`.

```text
New-UDButton -Text "Show Modal" -OnClick {
    Show-UDModal -Content {
        New-UDHeading -Text "Loading some stuff..."
    } -Persistent
    Start-Sleep -Seconds 4
    Hide-UDModal
}
```

### Adjusting Modal Size

You can adjust the height and width of a modal using the `-Height` and `-Width` parameters of `Show-UDModal`. These parameters accept any valid HTML\CSS sizing such as px or em.

Here is an example of setting a modal to a certain pixel size.

```text
New-UDButton -Text "Show Modal" -OnClick {
    Show-UDModal -Content {
        New-UDHeading -Text "Hello, Modal"
    } -Height '500px' -Width '1500px'
}
```

![Large modal](../.gitbook/assets/image%20%2832%29.png)

### Color

You can change the color of a modal using the `-BackgroundColor` and `-FontColor` parameters of `Show-UDModal`.

```text
New-UDButton -Text "Show Modal" -OnClick {
    Show-UDModal -Content {
        New-UDHeading -Text "Hello, Modal" -Color 'white'
    } -BackgroundColor green 
}
```

![Green Modal](../.gitbook/assets/image%20%2833%29.png)

