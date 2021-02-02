---
layout: post
title: TidyTuesday - Tate Art
author: Oliver C. Stringham
date: 2021-01-15
tags: tidy-tuesday ggplot R
categories: data-visualization R
---

#TidyTuesday dataset of the week is the art collection of [Tate Art Museum](https://github.com/tategallery/collection). I made a visual of the number of acquisitions made by Tate by decade taking into account what decade the art was created. The top plot tracks the number of acquisition made by Tate per decade. In the bottom plot, the x-axis is the decade Tate acquired a piece, the y-axis is the decade the piece was created, and each rectangle represents the number of acquisitions made. Hover over the data points to see their values. I used ggplot in R to generate the plot and ggiraph to convert it to a HTML widget. Code [here](https://github.com/ocstringham/tidy_tuesday/blob/main/scripts/2021-01-12-art.R).

<div class="container">    
    <div class="columns is-centered is-mobile">
    <div class="column"> 
        <figure class="image is-5by4">
            <iframe class='has-ratio' width="715" height="837" src="assets/html-widgets/art.html"> </iframe>
        </figure>
    </div>
    </div>
</div>