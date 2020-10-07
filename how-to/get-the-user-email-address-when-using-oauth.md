# Get the user email address when using OAuth

{% hint style="info" %}
Universal Dashboard is now a part of PowerShell Universal. This documentation is for reference to the v2 version of Universal Dashboard and is no longer maintained. PowerShell Universal Documentation can be found [here](https://docs.ironmansoftware.com).
{% endhint %}

## Get the user email address when using OAuth

When creating a login page with an OAuth provider \(Facebook, Google, Microsoft or Twitter\), you can get additional information about the user logging.

To get an email address, use the `$ClaimsPrinciple` variable and find the claim for the email address.

```text
($ClaimsPrinciple.claims | where type -like "*emailaddress" ).Value
```

