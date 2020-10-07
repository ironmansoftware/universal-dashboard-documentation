# Card

{% hint style="info" %}
Universal Dashboard is now a part of PowerShell Universal. This documentation is for reference to the v2 version of Universal Dashboard and is no longer maintained. PowerShell Universal Documentation can be found [here](https://docs.ironmansoftware.com).
{% endhint %}

## Card

Cards are a convenient means of displaying content composed of different types of objects. They're also well-suited for presenting similar objects whose size or supported actions can vary considerably, like photos with captions of variable length.

### Basic Cards

![](../.gitbook/assets/basic-card.png)

```text
New-UDCard -Title 'Card Title' -Content {
    New-UDParagraph -Text 'I am a very simple card. I am good at containing small bits of information. I am convenient because I require little markup to use effectively.'
} -Links @(
    New-UDLink -Text 'This is a link' -Url '#!'
    New-UDLink -Text 'This is a link' -Url '#!'
) -Size 'small'
```

