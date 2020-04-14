---
name: Gauge Chart
permalink: r/gauge-charts/
description: How to create a Gauge Chart in R with Plotly
layout: base
thumbnail: thumbnail/gauge.jpg
language: r
redirect_from: r/gauge-meter
display_as: financial
order: 7
output:
  html_document:
    keep_md: true
---


### Basic Gauge

  A radial gauge chart has a circular arc, which displays a single value to estimate progress toward a goal.
  The bar shows the target value, and the shading represents the progress toward that goal. Gauge charts, known as
  speedometer charts as well. This chart type is usually used to illustrate key business indicators.

  The example below displays a basic gauge chart with default attributes. For more information about different added attributes check [indicator](https://plotly.com/r/indicator/) tutorial.


```r
library(plotly)

fig <- plot_ly(
    domain = list(x = c(0, 1), y = c(0, 1)),
    value = 270,
    title = list(text = "Speed"),
    type = "indicator",
    mode = "gauge+number") 
fig <- fig %>%
  layout(margin = list(l=20,r=30))

fig
```

<div id="htmlwidget-e17b4d168acd8be602e6" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-e17b4d168acd8be602e6">{"x":{"visdat":{"2204712a90f4":["function () ","plotlyVisDat"]},"cur_data":"2204712a90f4","attrs":{"2204712a90f4":{"domain":{"x":[0,1],"y":[0,1]},"value":270,"title":{"text":"Speed"},"mode":"gauge+number","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"indicator"}},"layout":{"margin":{"b":40,"l":20,"t":25,"r":30},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"domain":{"x":[0,1],"y":[0,1]},"value":270,"title":{"text":"Speed"},"mode":"gauge+number","type":"indicator","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
### Add Steps, Threshold, and Delta

The following examples include "steps" attribute shown as shading inside the radial arc, "delta" which is the
  difference of the value and goal (reference - value), and "threshold" to determine boundaries that visually alert you if the value cross a defined threshold.


```r
library(plotly)

fig <- plot_ly(
  domain = list(x = c(0, 1), y = c(0, 1)),
  value = 450,
  title = list(text = "Speed"),
  type = "indicator",
  mode = "gauge+number+delta",
  delta = list(reference = 380),
  gauge = list(
    axis =list(range = list(NULL, 500)),
    steps = list(
      list(range = c(0, 250), color = "lightgray"),
      list(range = c(250, 400), color = "gray")),
    threshold = list(
      line = list(color = "red", width = 4),
      thickness = 0.75,
      value = 490))) 
fig <- fig %>%
  layout(margin = list(l=20,r=30))

fig
```

<div id="htmlwidget-824bb98bb546ddb9fb1e" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-824bb98bb546ddb9fb1e">{"x":{"visdat":{"220470542755":["function () ","plotlyVisDat"]},"cur_data":"220470542755","attrs":{"220470542755":{"domain":{"x":[0,1],"y":[0,1]},"value":450,"title":{"text":"Speed"},"mode":"gauge+number+delta","delta":{"reference":380},"gauge":{"axis":{"range":[null,500]},"steps":[{"range":[0,250],"color":"lightgray"},{"range":[250,400],"color":"gray"}],"threshold":{"line":{"color":"red","width":4},"thickness":0.75,"value":490}},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"indicator"}},"layout":{"margin":{"b":40,"l":20,"t":25,"r":30},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"domain":{"x":[0,1],"y":[0,1]},"value":450,"title":{"text":"Speed"},"mode":"gauge+number+delta","delta":{"reference":380},"gauge":{"axis":{"range":[[],500]},"steps":[{"range":[0,250],"color":"lightgray"},{"range":[250,400],"color":"gray"}],"threshold":{"line":{"color":"red","width":4},"thickness":0.75,"value":490}},"type":"indicator","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Custom Gauge Chart
The following example shows how to style your gauge charts. For more information about all possible options check our [reference page](https://plotly.com/r/reference/#indicator).


```r
library(plotly)

fig <- plot_ly(
  type = "indicator",
  mode = "gauge+number+delta",
  value = 420,
  title = list(text = "Speed", font = list(size = 24)),
  delta = list(reference = 400, increasing = list(color = "RebeccaPurple")),
  gauge = list(
    axis = list(range = list(NULL, 500), tickwidth = 1, tickcolor = "darkblue"),
    bar = list(color = "darkblue"),
    bgcolor = "white",
    borderwidth = 2,
    bordercolor = "gray",
    steps = list(
      list(range = c(0, 250), color = "cyan"),
      list(range = c(250, 400), color = "royalblue")),
    threshold = list(
      line = list(color = "red", width = 4),
      thickness = 0.75,
      value = 490))) 
fig <- fig %>%
  layout(
    margin = list(l=20,r=30),
    paper_bgcolor = "lavender",
    font = list(color = "darkblue", family = "Arial"))

fig
```

<div id="htmlwidget-54efe964e6740fc738ec" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-54efe964e6740fc738ec">{"x":{"visdat":{"2204b11cee7":["function () ","plotlyVisDat"]},"cur_data":"2204b11cee7","attrs":{"2204b11cee7":{"mode":"gauge+number+delta","value":420,"title":{"text":"Speed","font":{"size":24}},"delta":{"reference":400,"increasing":{"color":"RebeccaPurple"}},"gauge":{"axis":{"range":[null,500],"tickwidth":1,"tickcolor":"darkblue"},"bar":{"color":"darkblue"},"bgcolor":"white","borderwidth":2,"bordercolor":"gray","steps":[{"range":[0,250],"color":"cyan"},{"range":[250,400],"color":"royalblue"}],"threshold":{"line":{"color":"red","width":4},"thickness":0.75,"value":490}},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"indicator"}},"layout":{"margin":{"b":40,"l":20,"t":25,"r":30},"paper_bgcolor":"lavender","font":{"color":"darkblue","family":"Arial"},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"mode":"gauge+number+delta","value":420,"title":{"text":"Speed","font":{"size":24}},"delta":{"reference":400,"increasing":{"color":"RebeccaPurple"}},"gauge":{"axis":{"range":[[],500],"tickwidth":1,"tickcolor":"darkblue"},"bar":{"color":"darkblue"},"bgcolor":"white","borderwidth":2,"bordercolor":"gray","steps":[{"range":[0,250],"color":"cyan"},{"range":[250,400],"color":"royalblue"}],"threshold":{"line":{"color":"red","width":4},"thickness":0.75,"value":490}},"type":"indicator","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

#Reference

See [https://plotly.com/r/reference/#indicator](https://plotly.com/r/reference/#indicator) for more information and chart attribute options!

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
