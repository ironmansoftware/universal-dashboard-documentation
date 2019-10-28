# Colors

## Colors

Many controls offer the ability to change colors like the font and background colors. You can specify colors in a couple of different ways thanks to the DashboardColor class.

## Named Colors

You can use any of the named colors found in the [.NET Color struct](https://docs.microsoft.com/en-us/dotnet/api/system.drawing.color?view=netframework-4.7.2).

```text
New-UDCard -BackgroundColor 'red'
```

## HEX Colors

You can use standard HEX color specifiers.

```text
New-UDCard -BackgroundColor "#E82C0C"
```

You can also include an alpha channel value.

```text
New-UDCard -BackgroundColor "#E82C0CFA"
```

## RGB Colors

You can also specify colors using an ARGB value.

```text
New-UDCard -BackgroundColor 16777215
```

