---
name: Bullet Charts
permalink: r/bullet-charts/
description: How to create a Bullet Chart in R with Plotly
layout: base
thumbnail: thumbnail/bullet.png
language: r
display_as: financial
order: 8
output:
  html_document:
    keep_md: true
---


### Basic Bullet Charts

  Stephen Few's Bullet Chart was invented to replace dashboard [gauges](https://plotly.com/r/gauge-charts/) and meters, combining both types of charts into simple bar charts with qualitative bars (steps), quantitative bar (bar) and performance line (threshold); all into one simple layout.
  Steps typically are broken into several values, which are defined with an array. The bar represent the actual value that a particular variable reached, and the threshold usually indicate a goal point relative to the value achieved by the bar. See [indicator page](https://plotly.com/r/gauge-charts/) for more detail.


```r
library(plotly)

fig <- plot_ly(
  type = "indicator",
  mode = "number+gauge+delta",
  gauge = list(shape = "bullet"),
  delta = list(reference = 300),
  value = 220,
  domain = list(x = c(0, 1), y = c(0, 1)),
  title= list(text = "Profit"),
  height = 150)

fig
```

<div id="htmlwidget-c371ee42274beeb5f285" style="width:672px;height:150px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-c371ee42274beeb5f285">{"x":{"visdat":{"21c36c960c16":["function () ","plotlyVisDat"]},"cur_data":"21c36c960c16","attrs":{"21c36c960c16":{"mode":"number+gauge+delta","gauge":{"shape":"bullet"},"delta":{"reference":300},"value":220,"domain":{"x":[0,1],"y":[0,1]},"title":{"text":"Profit"},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"indicator"}},"layout":{"height":150,"margin":{"b":40,"l":60,"t":25,"r":10},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"mode":"number+gauge+delta","gauge":{"shape":"bullet"},"delta":{"reference":300},"value":220,"domain":{"x":[0,1],"y":[0,1]},"title":{"text":"Profit"},"type":"indicator","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Add Steps, and Threshold

Below is the same example using "steps" attribute, which is shown as shading, and "threshold" to determine boundaries that visually alert you if the value cross a defined threshold.


```r
library(plotly)

fig <- plot_ly(
  type = "indicator",
  mode = "number+gauge+delta",
  value = 220,
  domain = list(x = c(0, 1), y= c(0, 1)),
  title = list(text = "<b>Profit</b>"),
  delta = list(reference = 200),
  gauge = list(
    shape = "bullet",
    axis = list(range = list(NULL, 300)),
    threshold = list(
      line = list(color = "red", width = 2),
      thickness = 0.75,
      value = 280),
    steps = list(
      list(range = c(0, 150), color = "lightgray"),
      list(range = c(150, 250), color = "gray"))),
  height = 150, width = 600) 
fig <- fig %>%
  layout(margin = list(l= 100, r= 10))

fig
```

<div id="htmlwidget-87a690568d45a6e8006e" style="width:600px;height:150px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-87a690568d45a6e8006e">{"x":{"visdat":{"21c378e54e4":["function () ","plotlyVisDat"]},"cur_data":"21c378e54e4","attrs":{"21c378e54e4":{"mode":"number+gauge+delta","value":220,"domain":{"x":[0,1],"y":[0,1]},"title":{"text":"<b>Profit<\/b>"},"delta":{"reference":200},"gauge":{"shape":"bullet","axis":{"range":[null,300]},"threshold":{"line":{"color":"red","width":2},"thickness":0.75,"value":280},"steps":[{"range":[0,150],"color":"lightgray"},{"range":[150,250],"color":"gray"}]},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"indicator"}},"layout":{"width":600,"height":150,"margin":{"b":40,"l":100,"t":25,"r":10},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"mode":"number+gauge+delta","value":220,"domain":{"x":[0,1],"y":[0,1]},"title":{"text":"<b>Profit<\/b>"},"delta":{"reference":200},"gauge":{"shape":"bullet","axis":{"range":[[],300]},"threshold":{"line":{"color":"red","width":2},"thickness":0.75,"value":280},"steps":[{"range":[0,150],"color":"lightgray"},{"range":[150,250],"color":"gray"}]},"type":"indicator","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Custom Bullet Chart

The following example shows how to customize your charts. For more information about all possible options check our [reference page](https://plotly.com/r/reference/#indicator).


```r
library(plotly)

fig <- plot_ly(
  type = "indicator",
  mode = "number+gauge+delta",
  value = 220,
  domain = list(x = c(0, 1), y = c(0, 1)),
  delta = list(reference = 280, position = "top"),
  title = list(
    text = "<b>Profit</b><br><span style='color: gray; font-size:0.8em'>U.S. $</span>",
    font = list(size = 14)),
  gauge = list(
    shape = "bullet",
    axis = list(range = c(NULL, 300)),
    threshold = list(
      line = list(color = "red", width = 2, gradient = list(yanchor = "vertical")),
      thickness = 0.75,
      value = 270),
    bgcolor = "white",
    steps = list(list(range = c(0, 150), color = "cyan")),
    bar = list(color = "darkblue")),
  height = 150)

fig
```

<div id="htmlwidget-b79ce884e1e7478cf460" style="width:672px;height:150px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-b79ce884e1e7478cf460">{"x":{"visdat":{"21c35378db96":["function () ","plotlyVisDat"]},"cur_data":"21c35378db96","attrs":{"21c35378db96":{"mode":"number+gauge+delta","value":220,"domain":{"x":[0,1],"y":[0,1]},"delta":{"reference":280,"position":"top"},"title":{"text":"<b>Profit<\/b><br><span style='color: gray; font-size:0.8em'>U.S. $<\/span>","font":{"size":14}},"gauge":{"shape":"bullet","axis":{"range":300},"threshold":{"line":{"color":"red","width":2,"gradient":{"yanchor":"vertical"}},"thickness":0.75,"value":270},"bgcolor":"white","steps":[{"range":[0,150],"color":"cyan"}],"bar":{"color":"darkblue"}},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"indicator"}},"layout":{"height":150,"margin":{"b":40,"l":60,"t":25,"r":10},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"mode":"number+gauge+delta","value":220,"domain":{"x":[0,1],"y":[0,1]},"delta":{"reference":280,"position":"top"},"title":{"text":"<b>Profit<\/b><br><span style='color: gray; font-size:0.8em'>U.S. $<\/span>","font":{"size":14}},"gauge":{"shape":"bullet","axis":{"range":300},"threshold":{"line":{"color":"red","width":2,"gradient":{"yanchor":"vertical"}},"thickness":0.75,"value":270},"bgcolor":"white","steps":[{"range":[0,150],"color":"cyan"}],"bar":{"color":"darkblue"}},"type":"indicator","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
### Multi Bullet

Bullet charts can be stacked for comparing several values at once as illustrated below:


```r
library(plotly)

fig <- plot_ly() 
fig <- fig %>%
  add_trace(
    type = "indicator",
    mode = "number+gauge+delta",
    value = 180,
    delta = list(reference = 200),
    domain = list(x = c(0.25, 1), y = c(0.08, 0.25)),
    title =list(text = "Revenue"),
    gauge = list(
      shape = "bullet",
      axis = list(range = c(NULL, 300)),
      threshold = list(
        line= list(color = "black", width = 2),
        thickness = 0.75,
        value = 170),
      steps = list(
        list(range = c(0, 150), color = "gray"),
        list(range = c(150, 250), color = "lightgray")),
      bar = list(color = "black"))) 
fig <- fig %>%
  add_trace(
    type = "indicator",
    mode = "number+gauge+delta",
    value = 35,
    delta = list(reference = 200),
    domain = list(x = c(0.25, 1), y = c(0.4, 0.6)),
    title = list(text = "Profit"),
    gauge = list(
      shape = "bullet",
      axis = list(range = list(NULL, 100)),
      threshold = list(
        line = list(color = "black", width= 2),
        thickness = 0.75,
        value = 50),
      steps = list(
        list(range = c(0, 25), color = "gray"),
        list(range = c(25, 75), color = "lightgray")),
      bar = list(color = "black"))) 
fig <- fig %>%
  add_trace(
    type =  "indicator",
    mode = "number+gauge+delta",
    value = 220,
    delta = list(reference = 300 ),
    domain = list(x = c(0.25, 1), y = c(0.7, 0.9)),
    title = list(text = "Satisfaction"),
    gauge = list(
      shape = "bullet",
      axis = list(range = list(NULL, 300)),
      threshold = list(
        line = list(color = "black", width = 2),
        thickness = 0.75,
        value = 210),
      steps = list(
        list(range = c(0, 100), color = "gray"),
        list(range = c(100, 250), color = "lightgray")),
      bar = list(color = "black")))

fig
```

<div id="htmlwidget-094584c1e1a6bcac3950" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-094584c1e1a6bcac3950">{"x":{"visdat":{"21c34de815a0":["function () ","plotlyVisDat"]},"cur_data":"21c34de815a0","attrs":{"21c34de815a0":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"indicator","mode":"number+gauge+delta","value":180,"delta":{"reference":200},"domain":{"x":[0.25,1],"y":[0.08,0.25]},"title":{"text":"Revenue"},"gauge":{"shape":"bullet","axis":{"range":300},"threshold":{"line":{"color":"black","width":2},"thickness":0.75,"value":170},"steps":[{"range":[0,150],"color":"gray"},{"range":[150,250],"color":"lightgray"}],"bar":{"color":"black"}},"inherit":true},"21c34de815a0.1":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"indicator","mode":"number+gauge+delta","value":35,"delta":{"reference":200},"domain":{"x":[0.25,1],"y":[0.4,0.6]},"title":{"text":"Profit"},"gauge":{"shape":"bullet","axis":{"range":[null,100]},"threshold":{"line":{"color":"black","width":2},"thickness":0.75,"value":50},"steps":[{"range":[0,25],"color":"gray"},{"range":[25,75],"color":"lightgray"}],"bar":{"color":"black"}},"inherit":true},"21c34de815a0.2":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"indicator","mode":"number+gauge+delta","value":220,"delta":{"reference":300},"domain":{"x":[0.25,1],"y":[0.7,0.9]},"title":{"text":"Satisfaction"},"gauge":{"shape":"bullet","axis":{"range":[null,300]},"threshold":{"line":{"color":"black","width":2},"thickness":0.75,"value":210},"steps":[{"range":[0,100],"color":"gray"},{"range":[100,250],"color":"lightgray"}],"bar":{"color":"black"}},"inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"hovermode":"closest","showlegend":true},"source":"A","config":{"showSendToCloud":false},"data":[{"type":"indicator","mode":"number+gauge+delta","value":180,"delta":{"reference":200},"domain":{"x":[0.25,1],"y":[0.08,0.25]},"title":{"text":"Revenue"},"gauge":{"shape":"bullet","axis":{"range":300},"threshold":{"line":{"color":"black","width":2},"thickness":0.75,"value":170},"steps":[{"range":[0,150],"color":"gray"},{"range":[150,250],"color":"lightgray"}],"bar":{"color":"black"}},"frame":null},{"type":"indicator","mode":"number+gauge+delta","value":35,"delta":{"reference":200},"domain":{"x":[0.25,1],"y":[0.4,0.6]},"title":{"text":"Profit"},"gauge":{"shape":"bullet","axis":{"range":[[],100]},"threshold":{"line":{"color":"black","width":2},"thickness":0.75,"value":50},"steps":[{"range":[0,25],"color":"gray"},{"range":[25,75],"color":"lightgray"}],"bar":{"color":"black"}},"frame":null},{"type":"indicator","mode":"number+gauge+delta","value":220,"delta":{"reference":300},"domain":{"x":[0.25,1],"y":[0.7,0.9]},"title":{"text":"Satisfaction"},"gauge":{"shape":"bullet","axis":{"range":[[],300]},"threshold":{"line":{"color":"black","width":2},"thickness":0.75,"value":210},"steps":[{"range":[0,100],"color":"gray"},{"range":[100,250],"color":"lightgray"}],"bar":{"color":"black"}},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

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
