# Card

{% hint style="info" %}
Universal Dashboard is now a part of PowerShell Universal. This documentation is for reference to the v2 version of Universal Dashboard and is no longer maintained. PowerShell Universal Documentation can be found [here](https://docs.ironmansoftware.com).
{% endhint %}

## Card

### Card Body

The content can contain any UD element.

```text
New-UDMuCard -Body (
    New-UDMuCardBody -Content {
        New-UDHeading -Text 'Card'
    }
)
```

![Card with body](../../.gitbook/assets/image%20%2858%29%20%281%29.png)

### Card Header

```text
New-UDMuCard -Header (
    New-UDMuCardHeader -Content {
        New-UDMuCardMedia -Component video -Source "http://media.w3.org/2010/05/bunny/movie.mp4" 
    }
) -Body (
    New-UDMuCardBody -Content {
        New-UDHeading -Text 'Card'
    }
)
```

![Card with header media](../../.gitbook/assets/image%20%2845%29.png)

