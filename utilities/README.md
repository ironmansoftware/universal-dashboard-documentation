# Utilities

{% hint style="info" %}
Universal Dashboard is now a part of PowerShell Universal. This documentation is for reference to the v2 version of Universal Dashboard and is no longer maintained. PowerShell Universal Documentation can be found [here](https://docs.ironmansoftware.com).
{% endhint %}

## Utilities

### Clipboard

You can copy data to the clipboard using the `Set-UDClipboard` cmdlet. It needs to be used within an Endpoint and cannot be called from a top-level content block.

```text
New-UDButton -Text 'Copy to Clipboard' -OnClick {
    Set-UDClipboard -Data 'Copied text'
}
```

### Redirection

You can redirect users to different pages using `Invoke-UDRedirect`. It needs to be used within an Endpoint and cannot be called from a top-level content block. If you specify the `-OpenInNewWindow` switch parameter, it will open in a new tab or window.

```text
New-UDButton -Text 'Open Google' -OnClick {
    Invoke-UDRedirect -Url https://google.com -OpenInNewWindow
}
```

### Anchor / Focus

You can focus an HTML by the ID selector using `Select-UDElement`. This will help the tab-heavy users navigate your site, and allows for dynamic moving of focus.

If you specify the `-ScrollToElement` the browser will scroll the element into sight. Example `To the top` button:

```text
New-UDButton -Text 'To the top' -OnClick {
    Select-UDElement -ID "FirstRow" -ScrollToElement
}
```

Where "FirstRow" is the ID of any element in the top. Any HTML element with a specified ID can be used as an anchor.

