---
description: How to make interactive 3D mesh plots in R.
display_as: 3d_charts
language: r
layout: base
name: 3D Mesh Plots
order: 4
output:
  html_document:
    keep_md: true
page_type: example_index
permalink: r/3d-mesh/
redirect_from: r/3d-mesh-plots/
thumbnail: thumbnail/3d-mesh.jpg
---


### Basic 3D Mesh Plot


```r
library(plotly)

x <- runif(50, 0, 1)
y <- runif(50, 0, 1)
z <- runif(50, 0, 1)

fig <- plot_ly(x = ~x, y = ~y, z = ~z, type = 'mesh3d')

fig
```

<div id="htmlwidget-87bffc6e6cb27bef6af1" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-87bffc6e6cb27bef6af1">{"x":{"visdat":{"f992a379e2b":["function () ","plotlyVisDat"]},"cur_data":"f992a379e2b","attrs":{"f992a379e2b":{"x":{},"y":{},"z":{},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"mesh3d"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"scene":{"xaxis":{"title":"x"},"yaxis":{"title":"y"},"zaxis":{"title":"z"}},"hovermode":"closest","showlegend":false,"legend":{"yanchor":"top","y":0.5}},"source":"A","config":{"showSendToCloud":false},"data":[{"colorbar":{"title":"z","ticklen":2,"len":0.5,"lenmode":"fraction","y":1,"yanchor":"top"},"colorscale":[["0","rgba(68,1,84,1)"],["0.0416666666666667","rgba(70,19,97,1)"],["0.0833333333333333","rgba(72,32,111,1)"],["0.125","rgba(71,45,122,1)"],["0.166666666666667","rgba(68,58,128,1)"],["0.208333333333333","rgba(64,70,135,1)"],["0.25","rgba(60,82,138,1)"],["0.291666666666667","rgba(56,93,140,1)"],["0.333333333333333","rgba(49,104,142,1)"],["0.375","rgba(46,114,142,1)"],["0.416666666666667","rgba(42,123,142,1)"],["0.458333333333333","rgba(38,133,141,1)"],["0.5","rgba(37,144,140,1)"],["0.541666666666667","rgba(33,154,138,1)"],["0.583333333333333","rgba(39,164,133,1)"],["0.625","rgba(47,174,127,1)"],["0.666666666666667","rgba(53,183,121,1)"],["0.708333333333333","rgba(79,191,110,1)"],["0.75","rgba(98,199,98,1)"],["0.791666666666667","rgba(119,207,85,1)"],["0.833333333333333","rgba(147,214,70,1)"],["0.875","rgba(172,220,52,1)"],["0.916666666666667","rgba(199,225,42,1)"],["0.958333333333333","rgba(226,228,40,1)"],["1","rgba(253,231,37,1)"]],"showscale":true,"x":[0.562904397025704,0.61286539118737,0.273366011679173,0.871045097941533,0.0354063999839127,0.612128284294158,0.0224657079670578,0.00106454128399491,0.0949870280455798,0.902655605226755,0.552131637232378,0.21993773849681,0.459219819866121,0.171144339255989,0.136912422953174,0.280808836454526,0.83287003566511,0.566695512970909,0.867599622579291,0.854829961434007,0.753151639131829,0.296064152382314,0.890581086510792,0.877500122413039,0.933688659919426,0.0615120066795498,0.488159677246585,0.707754667382687,0.280672240070999,0.772182993590832,0.0570531049743295,0.202805965906009,0.5529805123806,0.195869449991733,0.341363430256024,0.535043153911829,0.776670421473682,0.910460252081975,0.392010492272675,0.187073809793219,0.647654851898551,0.601764906663448,0.555365884676576,0.0369349068496376,0.615510008996353,0.392361697740853,0.888993358705193,0.0720484105404466,0.823857479728758,0.602392306551337],"y":[0.744880095589906,0.915189020801336,0.891919394955039,0.912179737817496,0.924143110634759,0.30663554253988,0.953382660867646,0.502220439258963,0.93795573245734,0.142547773197293,0.877795893698931,0.507886170875281,0.555695224087685,0.334460522281006,0.140882956096902,0.919535072520375,0.876480563776568,0.310295361792669,0.806410817196593,0.726377480430529,0.549796566367149,0.812044747406617,0.764160610036924,0.384766028262675,0.0851722385268658,0.274913010420278,0.11928897164762,0.74439473845996,0.872302713338286,0.425882167881355,0.274383448529989,0.485760230571032,0.0541087684687227,0.566009936621413,0.916592977941036,0.554220008663833,0.341985263396055,0.665888841031119,0.700517095625401,0.0393269238993526,0.741830206243321,0.469984771450981,0.555864514783025,0.721683398354799,0.837343745166436,0.705755433067679,0.216762149240822,0.25359455565922,0.0651878609787673,0.0330293213482946],"z":[0.369386469013989,0.141176518052816,0.840443936642259,0.447894747834653,0.425802264595404,0.0259951122570783,0.781645802315325,0.424882929306477,0.122674122918397,0.746263926615939,0.265714271692559,0.434958264464512,0.297758841887116,0.739314978010952,0.509457157924771,0.960621397942305,0.730342887109146,0.64803558611311,0.97815947025083,0.555386584950611,0.437175720231608,0.032620744779706,0.251416902057827,0.807325581787154,0.567679732106626,0.437026014085859,0.529199206968769,0.468258331529796,0.690582374576479,0.458428497891873,0.323372863698751,0.0579115364234895,0.675907932920381,0.760006417986006,0.896310328040272,0.444684766232967,0.874534889589995,0.600756685482338,0.639531097142026,0.295330718625337,0.321749059017748,0.195235860068351,0.982966859359294,0.339946583611891,0.108384797349572,0.593456004280597,0.554626681609079,0.137071539415047,0.188900999259204,0.446407357230783],"type":"mesh3d","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Tetrahedron Mesh Plot


```r
library(plotly)

fig <- plot_ly(type = 'mesh3d',
  x = c(0, 1, 2, 0),
  y = c(0, 0, 1, 2),
  z = c(0, 2, 0, 1),
  i = c(0, 0, 0, 1),
  j = c(1, 2, 3, 2),
  k = c(2, 3, 1, 3),
  intensity = c(0, 0.33, 0.66, 1),
  color = c(0, 0.33, 0.66, 1),
  colors = colorRamp(c("red", "green", "blue"))
)

fig
```

<div id="htmlwidget-e817319eab8bd47aa959" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-e817319eab8bd47aa959">{"x":{"visdat":{"f9968d1b658":["function () ","plotlyVisDat"]},"cur_data":"f9968d1b658","attrs":{"f9968d1b658":{"x":[0,1,2,0],"y":[0,0,1,2],"z":[0,2,0,1],"i":[0,0,0,1],"j":[1,2,3,2],"k":[2,3,1,3],"intensity":[0,0.33,0.66,1],"color":[0,0.33,0.66,1],"colors":["function (x) ","roundcolor(cbind(palette[[1L]](x), palette[[2L]](x), palette[[3L]](x), ","    if (alpha) palette[[4L]](x))) * 255"],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"mesh3d"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"scene":{"xaxis":{"title":[]},"yaxis":{"title":[]},"zaxis":{"title":[]}},"hovermode":"closest","showlegend":false,"legend":{"yanchor":"top","y":0.5}},"source":"A","config":{"showSendToCloud":false},"data":[{"colorbar":{"title":"","ticklen":2,"len":0.5,"lenmode":"fraction","y":1,"yanchor":"top"},"colorscale":[["0","rgba(255,0,0,1)"],["0.0416666666666667","rgba(234,21,0,1)"],["0.0833333333333333","rgba(212,42,0,1)"],["0.125","rgba(191,64,0,1)"],["0.166666666666667","rgba(170,85,0,1)"],["0.208333333333333","rgba(149,106,0,1)"],["0.25","rgba(128,128,0,1)"],["0.291666666666667","rgba(106,149,0,1)"],["0.333333333333333","rgba(85,170,0,1)"],["0.375","rgba(64,191,0,1)"],["0.416666666666667","rgba(43,212,0,1)"],["0.458333333333333","rgba(21,234,0,1)"],["0.5","rgba(0,255,0,1)"],["0.541666666666667","rgba(0,234,21,1)"],["0.583333333333333","rgba(0,213,42,1)"],["0.625","rgba(0,191,64,1)"],["0.666666666666667","rgba(0,170,85,1)"],["0.708333333333333","rgba(0,149,106,1)"],["0.75","rgba(0,128,128,1)"],["0.791666666666667","rgba(0,106,149,1)"],["0.833333333333333","rgba(0,85,170,1)"],["0.875","rgba(0,64,191,1)"],["0.916666666666667","rgba(0,43,212,1)"],["0.958333333333333","rgba(0,21,234,1)"],["1","rgba(0,0,255,1)"]],"showscale":true,"x":[0,1,2,0],"y":[0,0,1,2],"z":[0,2,0,1],"i":[0,0,0,1],"j":[1,2,3,2],"k":[2,3,1,3],"intensity":[0,0.33,0.66,1],"type":"mesh3d","marker":{"line":{"colorbar":{"title":"","ticklen":2},"cmin":0,"cmax":1,"colorscale":[["0","rgba(255,0,0,1)"],["0.0416666666666667","rgba(234,21,0,1)"],["0.0833333333333333","rgba(212,42,0,1)"],["0.125","rgba(191,64,0,1)"],["0.166666666666667","rgba(170,85,0,1)"],["0.208333333333333","rgba(149,106,0,1)"],["0.25","rgba(128,128,0,1)"],["0.291666666666667","rgba(106,149,0,1)"],["0.333333333333333","rgba(85,170,0,1)"],["0.375","rgba(64,191,0,1)"],["0.416666666666667","rgba(43,212,0,1)"],["0.458333333333333","rgba(21,234,0,1)"],["0.5","rgba(0,255,0,1)"],["0.541666666666667","rgba(0,234,21,1)"],["0.583333333333333","rgba(0,213,42,1)"],["0.625","rgba(0,191,64,1)"],["0.666666666666667","rgba(0,170,85,1)"],["0.708333333333333","rgba(0,149,106,1)"],["0.75","rgba(0,128,128,1)"],["0.791666666666667","rgba(0,106,149,1)"],["0.833333333333333","rgba(0,85,170,1)"],["0.875","rgba(0,64,191,1)"],["0.916666666666667","rgba(0,43,212,1)"],["0.958333333333333","rgba(0,21,234,1)"],["1","rgba(0,0,255,1)"]],"showscale":false,"color":[0,0.33,0.66,1]}},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Cube Mesh Plot


```r
library(plotly)

fig <- plot_ly(type = 'mesh3d',
  x = c(0, 0, 1, 1, 0, 0, 1, 1),
  y = c(0, 1, 1, 0, 0, 1, 1, 0),
  z = c(0, 0, 0, 0, 1, 1, 1, 1),
  i = c(7, 0, 0, 0, 4, 4, 6, 6, 4, 0, 3, 2),
  j = c(3, 4, 1, 2, 5, 6, 5, 2, 0, 1, 6, 3),
  k = c(0, 7, 2, 3, 6, 7, 1, 1, 5, 5, 7, 6),
  intensity = seq(0, 1, length = 8),
  color = seq(0, 1, length = 8),
  colors = colorRamp(rainbow(8))
)

fig
```

<div id="htmlwidget-47f70d514b2131f7bdf9" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-47f70d514b2131f7bdf9">{"x":{"visdat":{"f99f329aef":["function () ","plotlyVisDat"]},"cur_data":"f99f329aef","attrs":{"f99f329aef":{"x":[0,0,1,1,0,0,1,1],"y":[0,1,1,0,0,1,1,0],"z":[0,0,0,0,1,1,1,1],"i":[7,0,0,0,4,4,6,6,4,0,3,2],"j":[3,4,1,2,5,6,5,2,0,1,6,3],"k":[0,7,2,3,6,7,1,1,5,5,7,6],"intensity":[0,0.142857142857143,0.285714285714286,0.428571428571429,0.571428571428571,0.714285714285714,0.857142857142857,1],"color":[0,0.142857142857143,0.285714285714286,0.428571428571429,0.571428571428571,0.714285714285714,0.857142857142857,1],"colors":["function (x) ","roundcolor(cbind(palette[[1L]](x), palette[[2L]](x), palette[[3L]](x), ","    if (alpha) palette[[4L]](x))) * 255"],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"mesh3d"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"scene":{"xaxis":{"title":[]},"yaxis":{"title":[]},"zaxis":{"title":[]}},"hovermode":"closest","showlegend":false,"legend":{"yanchor":"top","y":0.5}},"source":"A","config":{"showSendToCloud":false},"data":[{"colorbar":{"title":"","ticklen":2,"len":0.5,"lenmode":"fraction","y":1,"yanchor":"top"},"colorscale":[["0","rgba(255,0,0,1)"],["0.0416666666666667","rgba(255,56,0,1)"],["0.0833333333333333","rgba(255,111,0,1)"],["0.125","rgba(255,167,0,1)"],["0.166666666666667","rgba(234,202,0,1)"],["0.208333333333333","rgba(197,220,0,1)"],["0.25","rgba(160,239,0,1)"],["0.291666666666667","rgba(123,255,3,1)"],["0.333333333333333","rgba(85,255,21,1)"],["0.375","rgba(48,255,40,1)"],["0.416666666666667","rgba(11,255,59,1)"],["0.458333333333333","rgba(0,255,104,1)"],["0.5","rgba(0,255,160,1)"],["0.541666666666667","rgba(0,255,215,1)"],["0.583333333333333","rgba(0,239,255,1)"],["0.625","rgba(0,183,255,1)"],["0.666666666666667","rgba(0,128,255,1)"],["0.708333333333333","rgba(0,72,255,1)"],["0.75","rgba(32,48,255,1)"],["0.791666666666667","rgba(69,29,255,1)"],["0.833333333333333","rgba(107,11,255,1)"],["0.875","rgba(144,0,247,1)"],["0.916666666666667","rgba(181,0,228,1)"],["0.958333333333333","rgba(218,0,210,1)"],["1","rgba(255,0,191,1)"]],"showscale":true,"x":[0,0,1,1,0,0,1,1],"y":[0,1,1,0,0,1,1,0],"z":[0,0,0,0,1,1,1,1],"i":[7,0,0,0,4,4,6,6,4,0,3,2],"j":[3,4,1,2,5,6,5,2,0,1,6,3],"k":[0,7,2,3,6,7,1,1,5,5,7,6],"intensity":[0,0.142857142857143,0.285714285714286,0.428571428571429,0.571428571428571,0.714285714285714,0.857142857142857,1],"type":"mesh3d","marker":{"line":{"colorbar":{"title":"","ticklen":2},"cmin":0,"cmax":1,"colorscale":[["0","rgba(255,0,0,1)"],["0.0416666666666667","rgba(255,56,0,1)"],["0.0833333333333333","rgba(255,111,0,1)"],["0.125","rgba(255,167,0,1)"],["0.166666666666667","rgba(234,202,0,1)"],["0.208333333333333","rgba(197,220,0,1)"],["0.25","rgba(160,239,0,1)"],["0.291666666666667","rgba(123,255,3,1)"],["0.333333333333333","rgba(85,255,21,1)"],["0.375","rgba(48,255,40,1)"],["0.416666666666667","rgba(11,255,59,1)"],["0.458333333333333","rgba(0,255,104,1)"],["0.5","rgba(0,255,160,1)"],["0.541666666666667","rgba(0,255,215,1)"],["0.583333333333333","rgba(0,239,255,1)"],["0.625","rgba(0,183,255,1)"],["0.666666666666667","rgba(0,128,255,1)"],["0.708333333333333","rgba(0,72,255,1)"],["0.75","rgba(32,48,255,1)"],["0.791666666666667","rgba(69,29,255,1)"],["0.833333333333333","rgba(107,11,255,1)"],["0.875","rgba(144,0,247,1)"],["0.916666666666667","rgba(181,0,228,1)"],["0.958333333333333","rgba(218,0,210,1)"],["1","rgba(255,0,191,1)"]],"showscale":false,"color":[0,0.142857142857143,0.285714285714286,0.428571428571429,0.571428571428571,0.714285714285714,0.857142857142857,1]}},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

#Reference

See [https://plotly.com/r/reference/#mesh3d](https://plotly.com/r/reference/#mesh3d) for more information and chart attribute options!

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
