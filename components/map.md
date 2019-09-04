# Map

{% hint style="info" %}
This component is only available in [Premium](https://ironmansoftware.com/product/powershell-universal-dashboard/)
{% endhint %}

UDMap is a component to display interactive maps with all kinds of customizations. You’ll be able to add markers, draw routes and other polygons, toggle layers and even create heatmaps.

#### Map Features

To create a map, you’ll use the `New-UDMap` cmdlet and then define different features of that map. Maps support interactively adding and removing features so you can integrate into other Universal Dashboard components. Below are some of the components available in a map.

**Tile Layers**

UDMap supports defining one or more raster layers that can use standard tile servers. It supports both open tile servers, such as OpenStreetMaps, as well as the Bing Maps tile server \(requires API key\).

To define a base tile layer, use the `New-UDMapRasterLayer` cmdlet.

```text
New-UDMap -Endpoint {
   New-UDMapRasterLayer -TileServer 'https://tiles.wmflabs.org/bw-mapnik/{z}/{x}/{y}.png' 
} -Latitude 43.52107 -Longitude -114.31644 -Zoom 13 -Height '100ch'
```

![](https://i0.wp.com/ironmansoftware.com/wp-content/uploads/2019/06/raster-layer.png?w=1260&ssl=1)

**Markers**

You can create map markers using the `New-UDMapMarker` cmdlet. This allows you to place markers on the map to highlight points of interest. Markers allow you to customize the icon with `New-UDMapIcon`, add a popup with `New-UDMapPopup` or cluster them together by putting them into a `New-UDMapMarkerClusterLayer`. An example marker could be created like so.

```text
    New-UDMap -Endpoint {
        $BeerIcon = New-UDMapIcon -Url 'https://image.flaticon.com/icons/png/512/168/168557.png' -Height 32 -Width 32
        New-UDMapRasterLayer -TileServer 'https://tiles.wmflabs.org/bw-mapnik/{z}/{x}/{y}.png' 
        New-UDMapMarker -Icon $BeerIcon -Latitude 43.525328 -Longitude -114.318287 -Popup (New-UDMapPopup -Content { New-UDHeading -Text "Power House" })
        New-UDMapMarker -Icon $BeerIcon -Latitude 43.521246 -Longitude -114.315838 -Popup (New-UDMapPopup -Content { New-UDHeading -Text "Sun Valley Brewing Co." })
        New-UDMapMarker -Icon $BeerIcon -Latitude 43.519907 -Longitude -114.316542 -Popup (New-UDMapPopup -Content { New-UDHeading -Text "Sawtooth Brewery Tap Room" })
        New-UDMapMarker -Icon $BeerIcon -Latitude 43.681016 -Longitude -114.363854 -Popup (New-UDMapPopup -Content { New-UDHeading -Text "Warfield Distillery & Brewery" })
        New-UDMapMarker -Icon $BeerIcon -Latitude 43.682613 -Longitude -114.367027 -Popup (New-UDMapPopup -Content { New-UDHeading -Text "Sawtooth Brewery Public House" })
    } -Height '100ch'
```

![](https://i1.wp.com/ironmansoftware.com/wp-content/uploads/2019/06/markers.png?w=1260&ssl=1)

**Polylines, Polygons, Circles and Rectangles**

Using the `New-UDMapVectorLayer` cmdlet you can define various types of vectors that define areas of the map. Using this cmdlet you could create routes like Google Map directions or highlight areas of interest using polygons. This cmdlet supports arrays of latitude and longitude as well as GeoJSON. This means that you can hook it right up to your existing SQL Server and create vectors using standard GeoJSON columns.

In this example, we are defining a circle and rectangle around areas in Hailey.

```text
    New-UDMap -Endpoint {
        New-UDMapRasterLayer -TileServer 'https://tiles.wmflabs.org/bw-mapnik/{z}/{x}/{y}.png' 
        New-UDMapVectorLayer -Latitude 43.52107 -Longitude -114.31644 -Radius 400 -Color blue -FillColor blue -Circle
        New-UDMapVectorLayer -Rectangle -Color red -FillColor red -LatitudeBottomRight 43.52107 -LongitudeBottomRight -114.31644 -LatitudeTopLeft 43.68263 -LongitudeTopLeft -114.36373
    } -Height '100ch'
```

![](https://i2.wp.com/ironmansoftware.com/wp-content/uploads/2019/06/shapes.png?w=1260&ssl=1)

You can even more fancy, you could use a GeoJSON data set. In this example, we are using the Singapore National Parks Board’s GeoJSON for the [Park Connector Loop](https://data.gov.sg/dataset/park-connector-loop?resource_id=9ae978b4-0c97-413d-8728-4247e9a2de11).

```text
    $Cache:GeoJSON = Get-Content -Raw "C:\Users\adamr\Desktop\park-connector-loop-geojson.geojson"

    New-UDMap -Endpoint {
        New-UDMapRasterLayer -TileServer 'https://tiles.wmflabs.org/bw-mapnik/{z}/{x}/{y}.png' 
        $Json = $Cache:GeoJSON | ConvertFrom-Json 
        $Json.Features | ForEach-Object {
            New-UDMapVectorLayer -GeoJSON ($_ | ConvertTo-Json -Depth 10)
        }
    } -Height '100ch'
```

![](https://i1.wp.com/ironmansoftware.com/wp-content/uploads/2019/06/route.png?w=1260&ssl=1)

**Layer Controls**

Layer controls allow you to define layers within your map. You can add base layers, such as satellite or road views, and overlay layers, such as markers or polygons. Users can then use the layer control to toggled between base layers and enable and disable overlays.

```text
    New-UDMap -Endpoint {
        New-UDMapLayerControl -Content {
            $BeerIcon = New-UDMapIcon -Url 'https://image.flaticon.com/icons/png/512/168/168557.png' -Height 32 -Width 32

            New-UDMapBaseLayer -Name "Tiles" -Content {
                New-UDMapRasterLayer -TileServer 'https://tiles.wmflabs.org/bw-mapnik/{z}/{x}/{y}.png' 
            } -Checked
            New-UDMapOverlay -Name "Power House" -Content {
                New-UDMapMarker -Icon $BeerIcon -Latitude 43.525328 -Longitude -114.318287 -Popup (New-UDMapPopup -Content { New-UDHeading -Text "Power House" })
            }
            New-UDMapOverlay -Name "Sun Valley Brewing Co." -Content {
                New-UDMapMarker -Icon $BeerIcon -Latitude 43.521246 -Longitude -114.315838 -Popup (New-UDMapPopup -Content { New-UDHeading -Text "Sun Valley Brewing Co." })
            } -Checked 
            New-UDMapOverlay -Name "Sawtooth Brewery Tap Room" -Content {
                New-UDMapMarker -Icon $BeerIcon -Latitude 43.519907 -Longitude -114.316542 -Popup (New-UDMapPopup -Content { New-UDHeading -Text "Sawtooth Brewery Tap Room" })
            } -Checked 
        }
    } -Height '100ch'
```

![](https://i0.wp.com/ironmansoftware.com/wp-content/uploads/2019/06/layer-control.png?w=1260&ssl=1)

**Heatmaps**

A special type of layer that you can add to your map is a heatmap layer. The heatmap layer takes an array of latitude, longitude and intensity values to create a heatmap over the top of the base layer.

```text
    New-UDMap -Endpoint {
        New-UDMapRasterLayer -TileServer 'https://tiles.wmflabs.org/bw-mapnik/{z}/{x}/{y}.png'
            New-UDMapHeatmapLayer -Points @(
                @(-37.9019339833, 175.3879181167, "625"),
                @(-37.90920365, 175.4053418167, "397"),
                @(-37.9057407667, 175.39478875, "540"),
                @(-37.9243174333, 175.4220341833, "112"),
                @(-37.8992012333, 175.3666729333, "815"),
                @(-37.9110874833, 175.4102195833, "360"),
                @(-37.9027096, 175.3913196333, "591211"),
                @(-37.9027096, 175.3913196333, "59122"),
                @(-37.9027096, 175.3913196333, "979823"),
                @(-37.9027096, 175.3913196333, "09723"),
                @(-37.9027096, 175.3913196343, "097"),
                @(-37.9027096, 175.3913196363, "1223"),
                @(-37.9011183833, 175.38410915, "655"),
                @(-37.9234701333, 175.4155696333, "181"),
                @(-37.90254175, 175.3926162167, "582"),
                @(-37.92450575, 175.4246711167, "90"),
                @(-37.9242924167, 175.4289432833, "47"),
                @(-37.8986079833, 175.3685293333, "801")
            )
    } -Height '100ch'
```

![](https://i2.wp.com/ironmansoftware.com/wp-content/uploads/2019/06/heatmap.png?w=1260&ssl=1)

**Interactivity**

The UDMap components support many of the standard UD interactivity cmdlets. You can add features dynamically to the map using `Add-UDElement`. You can remove those features using `Remove-UDElement`. You can even pan and zoom the map using `Set-UDElement.`

```text
    New-UDButton -Text 'Add Marker to Cluster' -OnClick {
        Add-UDElement -ParentId 'cluster' -Content {
            New-UDMapMarker -Latitude 43.525328 -Longitude -114.318287 
        }
    }

    New-UDMap -Endpoint {
        New-UDMapRasterLayer -TileServer 'https://tiles.wmflabs.org/bw-mapnik/{z}/{x}/{y}.png'
        New-UDMapMarkerClusterLayer -Id 'cluster' -Markers @(
            New-UDMapMarker -Latitude 43.525328 -Longitude -114.318287 
        )
    } -Height '100ch'
```



