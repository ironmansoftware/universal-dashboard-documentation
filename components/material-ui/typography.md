# Typography

{% hint style="info" %}
Universal Dashboard is now a part of PowerShell Universal. This documentation is for reference to the v2 version of Universal Dashboard and is no longer maintained. PowerShell Universal Documentation can be found [here](https://docs.ironmansoftware.com).
{% endhint %}

## Typography

### Variants

```text
New-UDMuTypography -Variant h1 -Text "Header"
New-UDMuTypography -Variant h2 -Text "Header"
New-UDMuTypography -Variant h3 -Text "Header"
New-UDMuTypography -Variant h4 -Text "Header"
New-UDMuTypography -Variant h5 -Text "Header"
New-UDMuTypography -Variant headline -Text "Header"
New-UDMuTypography -Variant subtitle1 -Text "Subtitle"
```

![Typography Variants](../../.gitbook/assets/image%20%283%29.png)

### No Wrap

```text
New-UDMuTypography -NoWrap -Text "This is a very long line that does not wrap. This is a very long line that does not wrap.This is a very long line that does not wrap.This is a very long line that does not wrap.This is a very long line that does not wrap.This is a very long line that does not wrap.This is a very long line that does not wrap.This is a very long line that does not wrap.This is a very long line that does not wrap."
```

![Long line that does not wrap](../../.gitbook/assets/image%20%2819%29.png)

### Alignment

```text
New-UDMuTypography -Align right -Text "Alignment"
```

![Text aligned right](../../.gitbook/assets/image%20%2831%29.png)

