---
title: "Spatial autocorrelation tutorial"
permalink: "/about/"
layout: page
output: html_notebook
---


This is an [R Markdown](http://rmarkdown.rstudio.com) Notebook. When you execute code within the notebook, the results appear beneath the code. 

Try executing this chunk by clicking the *Run* button within the chunk or by placing your cursor inside it and pressing *Ctrl+Shift+Enter*. 


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



<!-- ## Installation -->

<!-- Just fork this [repository](https://github.com/niklasbuschmann/contrast) and adjust the `_config.yml` to use with [Github Pages](https://pages.github.com/) and your page is done. -->

<!-- ## Features -->

<!--  - supports dark mode on macOS Mojave -->
<!--  - optional sidebar -->
<!--  - MathJax support -->
<!--  - no external ressources -->
<!--  - included archive page -->
<!--  - supports pagination -->
<!--  - feed generation -->
<!--  - responsive -->
<!--  - syntax highlighting -->
<!--  - supports comments via [disqus](https://disqus.com/) or [isso](http://posativ.org/isso/) -->

<!-- ## Based on -->

<!-- - [Hyde](https://github.com/poole/hyde) -->
<!-- - [Minima](https://github.com/jekyll/minima) -->
<!-- - [Lagrange](https://github.com/LeNPaul/Lagrange) -->
<!-- - [Font Awesome](http://fontawesome.io/) -->
<!-- - [KaTeX](https://katex.org/) -->
<!-- - [Pygments](https://github.com/richleland/pygments-css) -->

<!-- ## Installation (jekyll-remote-theme method) -->

<!-- You can use this theme with the `jekyll-remote-theme` plugin. Just create an empty repo, copy over the `index.html` file and add this to your `_config.yml`: -->

<!-- ```yaml -->
<!-- remote_theme: niklasbuschmann/contrast@v2.11 -->

<!-- plugins: -->
<!--   - jekyll-remote-theme -->
<!-- ``` -->

<!-- Note: to enable icons you also need to copy over the `_data` folder. -->

<!-- ## Config -->

<!-- Your `_config.yml` could for example look like this: -->

<!-- ```yaml -->
<!-- title: "Blog Title" -->
<!-- author: "Blog Author" -->
<!-- description: "My personal blog about ... something" -->
<!-- permalink: /:title/ -->
<!-- lang: "en" -->
<!-- excerpt_separator: "\n\n\n" -->
<!-- date_format: "%B %d, %Y" -->

<!-- # Layout -->

<!-- show_excerpts: true        # show article excerpts on the home page -->
<!-- show_frame: true           # adds a gray frame to the site -->
<!-- show_sidebar: false        # show a sidebar instead of the usual header -->

<!-- # Menu -->

<!-- navigation:                # accepts {file, title, url, icon, sidebaricon} -->
<!--   - {file: "index.html"} -->
<!--   - {file: "README.md"} -->

<!-- external:                  # shows a footer with social links - for available icons see fontawesome.com/icons -->
<!--   - {title: Mail, icon: envelope, url: "mailto:niklasbuschmann@users.noreply.github.com"} -->
<!--   - {title: Github, icon: github, url: "https://github.com/niklasbuschmann/contrast"} -->
<!--   - {title: Subscribe, icon: rss, url: "/feed.xml"} -->

<!-- comments: -->
<!-- #  disqus_shortname: ""    # see https://disqus.com/ -->
<!-- #  isso_domain: ""         # see https://posativ.org/isso/ -->

<!-- plugins: -->
<!--  - jekyll-feed -->

<!-- ``` -->

<!-- ## MathJax -->

<!-- Contrast comes preinstalled with a leightweight alternative to MathJax called [KaTeX](https://katex.org/). To display equations in a post simply set `mathjax: true` in the article's front matter. -->

<!-- ## License -->

<!-- [public domain](http://unlicense.org/) -->

<!-- ## Screenshots -->

<!-- ![screenshot](https://user-images.githubusercontent.com/4943215/109431850-cd711780-7a08-11eb-8601-2763f2ee6bb4.png) -->

<!-- ![screenshot](https://user-images.githubusercontent.com/4943215/109431832-b6cac080-7a08-11eb-9c5e-a058680c23a1.png) -->

<!-- ![screenshot](https://user-images.githubusercontent.com/4943215/73125194-5f0b8b80-3fa4-11ea-805c-8387187503ad.png) -->
