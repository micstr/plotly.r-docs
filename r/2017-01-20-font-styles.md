---
description: How to create font styles in R with Plotly.
display_as: file_settings
language: r
layout: base
name: Font Styles
order: 11
output:
  html_document:
    keep_md: true
page_type: u-guide
permalink: r/font/
thumbnail: thumbnail/text-and-annotations.png
---


### Global Font Properties


```r
library(plotly)

t <- list(
  family = "sans serif",
  size = 14,
  color = 'blue')

fig <- plot_ly(x=c(1,2,3,4,5), y=c(1,2,3,2,1))
fig <- fig %>% layout(title="Font Styling",
         font=t)


fig
```

<div id="htmlwidget-3ad04b1713229ace25d2" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-3ad04b1713229ace25d2">{"x":{"visdat":{"1450152036fa":["function () ","plotlyVisDat"]},"cur_data":"1450152036fa","attrs":{"1450152036fa":{"x":[1,2,3,4,5],"y":[1,2,3,2,1],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20]}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"Font Styling","font":{"family":"sans serif","size":14,"color":"blue"},"xaxis":{"domain":[0,1],"automargin":true,"title":[]},"yaxis":{"domain":[0,1],"automargin":true,"title":[]},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"x":[1,2,3,4,5],"y":[1,2,3,2,1],"type":"scatter","mode":"markers","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

#Reference

See [https://plotly.com/r/reference/#layout-font](https://plotly.com/r/reference/#layout-font) for more information and options!
### What About Dash?

[Dash for R](https://dashr.plot.ly/) is an open-source framework for building analytical applications, with no Javascript required, and it is tightly integrated with the Plotly graphing library. 

Learn about how to install Dash for R at https://dashr.plot.ly/installation.

Everywhere in this page that you see `fig`, you can display the same figure in a Dash for R application by passing it to the `figure` argument of the [`Graph` component](https://dashr.plot.ly/dash-core-components/graph) from the built-in `dashCoreComponents` package like this:


```r
library(plotly)

fig <- plot_ly() 
# fig <- fig %>% add_trace( ... )
# fig <- fig %>% layout( ... ) 

library(dash)
library(dashCoreComponents)
library(dashHtmlComponents)

app <- Dash$new()
app$layout(
    htmlDiv(
        list(
            dccGraph(figure=fig) 
        )
     )
)

app$run_server(debug=TRUE, dev_tools_hot_reload=FALSE)
```
