---
title:  "Spatial autocorrelation tutorial"
mathjax: true
layout: post
categories: media
---


# Sample Covariance
Range of values -Infinitive to + Infinitive
Standart deviation is the SQUARE
mEASURES Dispersion

#Correlation


```{r}
library(maptools)
library(spdep)
library(rgdal)
library(spData)
library(GISTools)

```


The first data set contains census tract data for eight central NY counties:

```{r}
owd <- getwd()
setwd(system.file("shapes", package="spData"))
NYcounties <- readShapeSpatial("NY8_utm18")
plot(NYcounties)
names(NYcounties)
```
Let's work on a subset of the map by focusing on Syracuse:
```{r}
unique(NYcounties$AREANAME)
syracuse <- NYcounties[NYcounties$AREANAME == "Syracuse city",]
plot(syracuse)
```
```{r}
coords <- coordinates(syracuse)
par(mfrow=c(1,1))
choropleth(syracuse, syracuse$PCTOWNHOME)
```

coords <- coordinates(syracuse)

Add a new chunk by clicking the *Insert Chunk* button on the toolbar or by pressing *Ctrl+Alt+I*.

When you save the notebook, an HTML file containing the code and output will be saved alongside it (click the *Preview* button or press *Ctrl+Shift+K* to preview the HTML file).

The preview shows you a rendered HTML copy of the contents of the editor. Consequently, unlike *Knit*, *Preview* does not run any R code chunks. Instead, the output of the chunk when it was last run in the editor is displayed.

## Images

Upload an image to the *assets* folder and embed it with `![title](/assets/name.jpg))`. Keep in mind that the path needs to be adjusted if Jekyll is run inside a subfolder.

A wrapper `div` with the class `large` can be used to increase the width of an image or iframe.

![Flower](https://user-images.githubusercontent.com/4943215/55412447-bcdb6c80-5567-11e9-8d12-b1e35fd5e50c.jpg)

[Flower](https://unsplash.com/photos/iGrsa9rL11o) by Tj Holowaychuk

## Embedded content

You can also embed a lot of stuff, for example from YouTube, using the `embed.html` include.

{% include embed.html url="https://www.youtube.com/embed/_C0A5zX-iqM" %}
