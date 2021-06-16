---
layout: post
title: \[Data Visualization\] Global Deforestation Rates
author: Oliver C. Stringham
date: 2021-05-23
tags: tidy-tuesday ggplot R gis leaflet
categories: data-visualization
---


This week I took a deeper look at [@LeafletJS](https://twitter.com/LeafletJS) in R using the [leaflet](https://github.com/rstudio/leaflet) package. Leaflet renders maps using Javascript, making them viewable in a web browser and interactivity (like a popup) can be programmed in. The R package allows it all to be done neatly in R :) I'd like to get better at producing these types of maps for viewing on web pages, so you might see more in the future. Hopefully,  they become more aesthetically pleasing as I practice. I'd like to investigate CSS to customize the aesthetics of the maps, including the popups. This map has simple popup (hover over on desktop). Also, I changed the map projection to the Robinson projection, which better represents the actual shapes and sizes of countries compared to the commonly used projection in default web maps (Mercator projection).

The map shows the annual (de)forestation rate per country in hectares. 

Data from [TidyTuesday](https://github.com/rfordatascience/tidytuesday/blob/master/data/2021/2021-04-06/readme.md
), code [here](https://github.com/ocstringham/tidy_tuesday/blob/main/scripts/2021-04-06-deforestation.R), and full sized map [here](assets/html-widgets/deforestation.html).

<div class="container">    
    <div class="columns is-centered is-mobile">
    <div class="column"> 
        <figure class="image is-3by2">
            <iframe class='has-ratio' 
                src="assets/html-widgets/deforestation.html">
            </iframe>
        </figure>
    </div>
    </div>
</div>