---
Title: RMarkdown and Leaflet Practice
Author: Jose Montero
Date: Apr 21st, 2018
output: 
  html_document:
    keep_md: true
---

### 0.Executive summary

In this practice, we will create a web page using R Markdown that features a map created with Leaflet.

### 1.Create Markers
First of all it is needed to create the markers with the metadata we want to show.


```r
library(knitr); library(leaflet)
```

```
## Warning: package 'knitr' was built under R version 3.4.3
```

```
## Warning: package 'leaflet' was built under R version 3.4.4
```

```r
uniLatLong <- data.frame(
   lat = c(40.45280869673105, 40.45066969280751, 40.44570563511516),
   lng = c(-3.733452405711205, -3.730727281352074, -3.7283669374189685))

uniIcon<- makeIcon(
   iconUrl = "http://cursosinformatica.ucm.es/img/icons/ucm.png",
   iconWidth = 31*215/230, iconHeight = 31,
   iconAnchorX =31*215/230, iconAnchorY = 16
)

uniSites <- c(
"<a href='http://informatica.ucm.es/'>UCM Faculty of Computer Science</a>",
"<a href='http://derecho.ucm.es/'>UCM Faculty of Law</a>",
"<a href='http://ccinformacion.ucm.es/'>UCM Faculty of Information Science</a>")
```


### 2 Generate Map

Now we wil lcreate the map using the markers defined above.


```r
uniLatLong %>%
   leaflet() %>%
   addTiles() %>%
   addMarkers(icon = uniIcon, popup = uniSites)
```

<!--html_preserve--><div id="htmlwidget-186927254f16f436caff" style="width:672px;height:480px;" class="leaflet html-widget"></div>
<script type="application/json" data-for="htmlwidget-186927254f16f436caff">{"x":{"options":{"crs":{"crsClass":"L.CRS.EPSG3857","code":null,"proj4def":null,"projectedBounds":null,"options":{}}},"calls":[{"method":"addTiles","args":["//{s}.tile.openstreetmap.org/{z}/{x}/{y}.png",null,null,{"minZoom":0,"maxZoom":18,"maxNativeZoom":null,"tileSize":256,"subdomains":"abc","errorTileUrl":"","tms":false,"continuousWorld":false,"noWrap":false,"zoomOffset":0,"zoomReverse":false,"opacity":1,"zIndex":null,"unloadInvisibleTiles":null,"updateWhenIdle":null,"detectRetina":false,"reuseTiles":false,"attribution":"&copy; <a href=\"http://openstreetmap.org\">OpenStreetMap<\/a> contributors, <a href=\"http://creativecommons.org/licenses/by-sa/2.0/\">CC-BY-SA<\/a>"}]},{"method":"addMarkers","args":[[40.452808696731,40.4506696928075,40.4457056351152],[-3.7334524057112,-3.73072728135207,-3.72836693741897],{"iconUrl":{"data":"http://cursosinformatica.ucm.es/img/icons/ucm.png","index":0},"iconWidth":28.9782608695652,"iconHeight":31,"iconAnchorX":28.9782608695652,"iconAnchorY":16},null,null,{"clickable":true,"draggable":false,"keyboard":true,"title":"","alt":"","zIndexOffset":0,"opacity":1,"riseOnHover":false,"riseOffset":250},["<a href='http://informatica.ucm.es/'>UCM Faculty of Computer Science<\/a>","<a href='http://derecho.ucm.es/'>UCM Faculty of Law<\/a>","<a href='http://ccinformacion.ucm.es/'>UCM Faculty of Information Science<\/a>"],null,null,null,null,null,null]}],"limits":{"lat":[40.4457056351152,40.452808696731],"lng":[-3.7334524057112,-3.72836693741897]}},"evals":[],"jsHooks":[]}</script><!--/html_preserve-->
