# Heatmap

A heat map shows a set of data in a grid in line with other vectors of data. You will need to define an array of hashtables. One axis will be the property to index by while the other vector will be a set of keys as defined by other properties of the hash table. 

```text
$Data = @(
    @{
        state = "idaho"
        cats = 72307
        dogs = 23429
        moose = 23423
        bears = 784
    }
    @{
        state = "wisconsin"
        cats = 2343342
        dogs = 3453623
        moose = 1
        bears = 23423
    }
    @{
        state = "montana"
        cats = 9234
        dogs = 3973457
        moose = 23472
        bears = 347303
    }
    @{
        state = "colorado"
        cats = 345973789
        dogs = 0237234
        moose = 2302
        bears = 2349772
    }
)
New-UDNivoChart -Heatmap -Data $Data -IndexBy 'state' -keys @('cats', 'dogs', 'moose', 'bears')  -Height 500 -Width 1000 -MarginTop 50 -MarginRight 130 -MarginBottom 50 -MarginLeft 60 

```

![Heatmap](../../../.gitbook/assets/image%20%2819%29.png)



