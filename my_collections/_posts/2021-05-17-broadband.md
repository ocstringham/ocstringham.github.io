---
layout: post
title: "Broadband Access [Data Visualization]"
author: Oliver C. Stringham
date: 2021-05-17
tags: tidy-tuesday ggplot R gis
categories: data-visualization
---

This week I used ggplot to create a map of [broadband internet access](https://github.com/rfordatascience/tidytuesday/tree/master/data/2021/2021-05-11) across Louisiana, USA. I then used the ggiraph package to convert the map to html. Hover over each subdivision to view the percentage of people with access to broadband internet as of 2017.

Full sized map [here](assets/html-widgets/broadband.html) and 
code [here](https://github.com/ocstringham/tidy_tuesday/blob/main/scripts/2021-05-11-broadband.R).


<div class="container">    
    <div class="columns is-centered is-mobile">
    <div class="column"> 
        <figure class="image is-5by4">
            <iframe class='has-ratio' 
                src="assets/html-widgets/broadband.html">
            </iframe>
        </figure>
    </div>
    </div>
</div>
