# Card

## Card Body

The content can contain any UD element.

```text
New-UDMuCard -Body (
    New-UDMuCardBody -Content {
        New-UDHeading -Text 'Card'
    }
)
```

![Card with body](../../.gitbook/assets/image%20%2857%29.png)

## Card Header

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

