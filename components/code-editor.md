# Code Editor

{% hint style="info" %}
Universal Dashboard is now a part of PowerShell Universal. This documentation is for reference to the v2 version of Universal Dashboard and is no longer maintained. PowerShell Universal Documentation can be found [here](https://docs.ironmansoftware.com).
{% endhint %}

### description: Documentation for the Code Editor component.

## Code Editor

{% hint style="info" %}
This component requires a [Universal Dashboard Enterprise License](https://ironmansoftware.com/powershell-universal-dashboard/).
{% endhint %}

![Code Editor Control in Universal Dashboard.](../.gitbook/assets/image%20%2856%29.png)

### Installation

The Code Editor component is published to the PowerShell Gallery. You can install it with the following command line.

```text
Install-Module UniversalDashboard.CodeEditor -AllowPrerelease
```

### Usage

Creating an editor

```text
New-UDCodeEditor -Language 'powershell' -Height '100ch' -Width '100cw' -Code 'Start-Process'
```

Read only editor

```text
New-UDCodeEditor -Language 'powershell' -Height '100ch' -Width '100ch' -Theme vs-dark -Code "Get-Process" -ReadOnly
```

Dynamically adding content to the editor

```text
New-UDCodeEditor -Id 'editor' -Language 'powershell' -Height '100ch' -Width '100ch' -Theme vs-dark -Code "Get-Process" -ReadOnly
New-UDButton -Text 'Add Text' -OnClick {
    Add-UDElement -ParentId 'editor' -Content {
        'Get-Process'
    }
}
```

Dynamically getting content from the editor

```text
New-UDCodeEditor -Id 'editor' -Language 'powershell' -Height '100ch' -Width '100ch' -Theme vs-dark
New-UDButton -Text "Get Text" -OnClick {
    Show-UDToast -Message (Get-UDElement -Id 'editor').Attributes["code"]
}
```

Dynamically setting the content of the editor

```text
New-UDCodeEditor -Id 'editor' -Language 'powershell' -Height '100ch' -Width '100ch' -Theme vs-dark
 New-UDButton -Text "Set Text" -OnClick {
    Set-UDElement -Id 'editor' -Attributes @{
        code = 'Get-Service'
    }
}
```

