---
description: How to change the size of graphs in R.
display_as: file_settings
language: r
layout: base
name: Setting Graph Size
order: 20
output:
  html_document:
    keep_md: true
page_type: u-guide
permalink: r/setting-graph-size/
thumbnail: thumbnail/sizing.png
---


### Customize Margins and Plot Size

```r
library(plotly)
m <- list(
  l = 50,
  r = 50,
  b = 100,
  t = 100,
  pad = 4
)
fig <- plot_ly(x = seq(0, 8), y = seq(0, 8))
fig <- fig %>% layout(autosize = F, width = 500, height = 500, margin = m)

fig
```

<div id="htmlwidget-7dd4aa9347a944fdcfb7" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-7dd4aa9347a944fdcfb7">{"x":{"visdat":{"bd843406389":["function () ","plotlyVisDat"]},"cur_data":"bd843406389","attrs":{"bd843406389":{"x":[0,1,2,3,4,5,6,7,8],"y":[0,1,2,3,4,5,6,7,8],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20]}},"layout":{"width":500,"height":500,"margin":{"b":100,"l":50,"t":100,"r":50,"pad":4},"autosize":false,"xaxis":{"domain":[0,1],"automargin":true,"title":[]},"yaxis":{"domain":[0,1],"automargin":true,"title":[]},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"x":[0,1,2,3,4,5,6,7,8],"y":[0,1,2,3,4,5,6,7,8],"type":"scatter","mode":"markers","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Automatically Adjust Margins

```r
library(plotly)
yaxis <- list(
  title = 'Y-axis Title',
  ticktext = list('long label','Very long label','3','label'),
  tickvals = list(1, 2, 3, 4),
  tickmode = "array",
  automargin = TRUE,
  titlefont = list(size=30)
)
fig <- plot_ly(x = c('Apples', 'Oranges', 'Watermelon', 'Pears'), y = c(3, 1, 2, 4), width = 500, height = 500, type = 'bar')
fig <- fig %>% layout(autosize = F, yaxis = yaxis)

fig
```

<div id="htmlwidget-4313586dd695237bc35a" style="width:500px;height:500px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-4313586dd695237bc35a">{"x":{"visdat":{"bd86a3aa904":["function () ","plotlyVisDat"]},"cur_data":"bd86a3aa904","attrs":{"bd86a3aa904":{"x":["Apples","Oranges","Watermelon","Pears"],"y":[3,1,2,4],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"bar"}},"layout":{"width":500,"height":500,"margin":{"b":40,"l":60,"t":25,"r":10},"autosize":false,"yaxis":{"domain":[0,1],"automargin":true,"title":"Y-axis Title","ticktext":["long label","Very long label","3","label"],"tickvals":[1,2,3,4],"tickmode":"array","titlefont":{"size":30}},"xaxis":{"domain":[0,1],"automargin":true,"title":[],"type":"category","categoryorder":"array","categoryarray":["Apples","Oranges","Pears","Watermelon"]},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"x":["Apples","Oranges","Watermelon","Pears"],"y":[3,1,2,4],"type":"bar","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
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
