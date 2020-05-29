# Icons

Universal Dashboard uses the [Font Awesome](https://fontawesome.com/icons?from=io) library to provide icons throughout the product. Many controls accept icons and you can create stand alone icons with `New-UDIcon`.

## Basic Icon

You can specify an icon name. Tab complete is available for icon names.

```text
New-UDIcon -Icon rocket -Size 5x
New-UDIcon -Icon bandcamp -Size 5x
New-UDIcon -Icon palette  -Size 5x
New-UDIcon -Icon apple -Size 5x
```

![](../.gitbook/assets/image%20%2827%29.png)

## Size

Many icon sizes are available. You can create larger icons by specifying sizes from 2x to 10x.

```text
2..10 | ForEach-Object {
    New-UDIcon -Icon sign_language -Size "$($_)x"
}
```

![Icon Sizes](../.gitbook/assets/image%20%2851%29.png)

## Colors

You can use standard HTML and color names for colors.

```text
New-UDIcon -Icon socks -Size 5x -Color red
```

![](../.gitbook/assets/image%20%2818%29%20%281%29.png)

## Spinning Icons

You can create spinning icons. These can be useful as loading icons.

```text
New-UDIcon -Spin -Icon linux -Size 5x
```

![](../.gitbook/assets/image%20%2813%29.png)

