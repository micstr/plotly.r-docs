---
name: Multiple Axes
permalink: r/multiple-axes/
description: How to make a graph with multiple axes in R with Plotly.
layout: base
thumbnail: thumbnail/multiple-axes.jpg
language: r
page_type: example_index
display_as: multiple_axes
order: 1
output:
  html_document:
    keep_md: true
---


### Multiple Y Axes


```r
library(plotly)
ay <- list(
  tickfont = list(color = "red"),
  overlaying = "y",
  side = "right",
  title = "second y axis"
)
fig <- plot_ly()
fig <- fig %>% add_lines(x = ~1:3, y = ~10*(1:3), name = "slope of 10")
fig <- fig %>% add_lines(x = ~2:4, y = ~1:3, name = "slope of 1", yaxis = "y2")
fig <- fig %>% layout(
    title = "Double Y Axis", yaxis2 = ay,
    xaxis = list(title="x")
  )

fig
```

<div id="htmlwidget-572d2aa670557d131346" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-572d2aa670557d131346">{"x":{"visdat":{"a667fe3bd55":["function () ","plotlyVisDat"]},"cur_data":"a667fe3bd55","attrs":{"a667fe3bd55":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"x":{},"y":{},"type":"scatter","mode":"lines","name":"slope of 10","inherit":true},"a667fe3bd55.1":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"x":{},"y":{},"type":"scatter","mode":"lines","name":"slope of 1","yaxis":"y2","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"Double Y Axis","yaxis2":{"tickfont":{"color":"red"},"overlaying":"y","side":"right","title":"second y axis"},"xaxis":{"domain":[0,1],"automargin":true,"title":"x"},"yaxis":{"domain":[0,1],"automargin":true,"title":"10 * (1:3)"},"hovermode":"closest","showlegend":true},"source":"A","config":{"showSendToCloud":false},"data":[{"x":[1,2,3],"y":[10,20,30],"type":"scatter","mode":"lines","name":"slope of 10","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[2,3,4],"y":[1,2,3],"type":"scatter","mode":"lines","name":"slope of 1","yaxis":"y2","marker":{"color":"rgba(255,127,14,1)","line":{"color":"rgba(255,127,14,1)"}},"error_y":{"color":"rgba(255,127,14,1)"},"error_x":{"color":"rgba(255,127,14,1)"},"line":{"color":"rgba(255,127,14,1)"},"xaxis":"x","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

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
