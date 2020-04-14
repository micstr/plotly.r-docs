---
name: geom_errorbar
permalink: ggplot2/geom_errorbar/
description: Examples of geom_errobar in R and ggplot2
layout: base
thumbnail: thumbnail/error-bar.jpg
language: ggplot2
page_type: example_index
display_as: statistics
order: 2
output:
  html_document:
    keep_md: true
---


### Basic Error Bar


```r
library(plotly)

df <- data.frame(x = 1:10,
                 y = 1:10,
                 ymin = (1:10) - runif(10),
                 ymax = (1:10) + runif(10),
                 xmin = (1:10) - runif(10),
                 xmax = (1:10) + runif(10))

p <- ggplot(data = df,aes(x = x,y = y)) + 
    geom_point() + 
    geom_errorbar(aes(ymin = ymin,ymax = ymax)) + 
    geom_errorbarh(aes(xmin = xmin,xmax = xmax))

fig <- ggplotly(p)

fig
```

<div id="htmlwidget-b227bb4047d3ac3993a1" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-b227bb4047d3ac3993a1">{"x":{"data":[{"x":[1,2,3,4,5,6,7,8,9,10],"y":[1,2,3,4,5,6,7,8,9,10],"text":["x:  1<br />y:  1","x:  2<br />y:  2","x:  3<br />y:  3","x:  4<br />y:  4","x:  5<br />y:  5","x:  6<br />y:  6","x:  7<br />y:  7","x:  8<br />y:  8","x:  9<br />y:  9","x: 10<br />y: 10"],"type":"scatter","mode":"markers","marker":{"autocolorscale":false,"color":"rgba(0,0,0,1)","opacity":1,"size":5.66929133858268,"symbol":"circle","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)"}},"hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null},{"x":[1,2,3,4,5,6,7,8,9,10],"y":[1,2,3,4,5,6,7,8,9,10],"text":["ymin: 0.2879392<br />ymax:  1.199934<br />x:  1<br />y:  1","ymin: 1.9308826<br />ymax:  2.133082<br />x:  2<br />y:  2","ymin: 2.0576541<br />ymax:  3.125598<br />x:  3<br />y:  3","ymin: 3.1264602<br />ymax:  4.552784<br />x:  4<br />y:  4","ymin: 4.4679372<br />ymax:  5.296219<br />x:  5<br />y:  5","ymin: 5.5784326<br />ymax:  6.149972<br />x:  6<br />y:  6","ymin: 6.9467473<br />ymax:  7.626682<br />x:  7<br />y:  7","ymin: 7.2391796<br />ymax:  8.200376<br />x:  8<br />y:  8","ymin: 8.1945145<br />ymax:  9.794369<br />x:  9<br />y:  9","ymin: 9.5174809<br />ymax: 10.649553<br />x: 10<br />y: 10"],"type":"scatter","mode":"lines","opacity":1,"line":{"color":"transparent"},"error_y":{"array":[0.199934092117473,0.133081699023023,0.125598124694079,0.55278414580971,0.296219421550632,0.149971681647003,0.626681681489572,0.200375987915322,0.794368676375598,0.64955339836888],"arrayminus":[0.712060758145526,0.0691174424719065,0.94234586507082,0.87353980797343,0.532062825514004,0.421567351091653,0.0532527319155633,0.760820385068655,0.805485512129962,0.482519058510661],"type":"data","width":17.6659735391842,"symmetric":false,"color":"rgba(0,0,0,1)"},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null},{"x":[1,2,3,4,5,6,7,8,9,10],"y":[1,2,3,4,5,6,7,8,9,10],"text":["xmin: 0.1669652<br />xmax:  1.404895<br />x:  1<br />y:  1","xmin: 1.8159159<br />xmax:  2.299366<br />x:  2<br />y:  2","xmin: 2.2349644<br />xmax:  3.663450<br />x:  3<br />y:  3","xmin: 3.3993137<br />xmax:  4.293910<br />x:  4<br />y:  4","xmin: 4.4715360<br />xmax:  5.501833<br />x:  5<br />y:  5","xmin: 5.6316295<br />xmax:  6.129659<br />x:  6<br />y:  6","xmin: 6.9919069<br />xmax:  7.938243<br />x:  7<br />y:  7","xmin: 7.1752149<br />xmax:  8.519924<br />x:  8<br />y:  8","xmin: 8.5172503<br />xmax:  9.012494<br />x:  9<br />y:  9","xmin: 9.8537929<br />xmax: 10.541300<br />x: 10<br />y: 10"],"type":"scatter","mode":"lines","opacity":1,"line":{"color":"transparent"},"error_x":{"array":[0.404895480489358,0.299366419902071,0.663450321182609,0.293909638887271,0.501832909882069,0.129659111378714,0.938242682488635,0.519924079533666,0.0124938106164336,0.541300175013021],"arrayminus":[0.833034806651995,0.184084069915116,0.765035620424896,0.600686345715076,0.528463962953538,0.368370518554002,0.00809311587363482,0.824785135686398,0.482749716611579,0.146207130048424],"type":"data","width":12.6340441683777,"symmetric":false,"color":"rgba(0,0,0,1)"},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null}],"layout":{"margin":{"t":26.2283105022831,"r":7.30593607305936,"b":40.1826484018265,"l":31.4155251141553},"plot_bgcolor":"rgba(235,235,235,1)","paper_bgcolor":"rgba(255,255,255,1)","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[-0.351751555735245,11.0600169240963],"tickmode":"array","ticktext":["0.0","2.5","5.0","7.5","10.0"],"tickvals":[0,2.5,5,7.5,10],"categoryorder":"array","categoryarray":["0.0","2.5","5.0","7.5","10.0"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":{"text":"x","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[-0.230141465971246,11.1676341061946],"tickmode":"array","ticktext":["0","3","6","9"],"tickvals":[0,3,6,9],"categoryorder":"array","categoryarray":["0","3","6","9"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":{"text":"y","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":"rgba(255,255,255,1)","bordercolor":"transparent","borderwidth":1.88976377952756,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","showSendToCloud":false},"source":"A","attrs":{"281f7403f40":{"x":{},"y":{},"type":"scatter"},"281f63a76a86":{"ymin":{},"ymax":{},"x":{},"y":{}},"281f422b2555":{"xmin":{},"xmax":{},"x":{},"y":{}}},"cur_data":"281f7403f40","visdat":{"281f7403f40":["function (y) ","x"],"281f63a76a86":["function (y) ","x"],"281f422b2555":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Margin Error Bar


```r
library(plotly)

population <- data.frame(Year=seq(1790, 1970, length.out=length(uspop)), 
                         Population=uspop, 
                         Error=rnorm(length(uspop), 5))

library(ggplot2)
p <- ggplot(population, aes(x=Year, y=Population, 
                       ymin=Population-Error, ymax=Population+Error))+
  geom_line()+
  geom_point(pch=2)+
  geom_errorbar(width=0.9)

fig <- ggplotly(p)

fig
```

<div id="htmlwidget-d389bc6f8dbaa2214690" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-d389bc6f8dbaa2214690">{"x":{"data":[{"x":[1790,1800,1810,1820,1830,1840,1850,1860,1870,1880,1890,1900,1910,1920,1930,1940,1950,1960,1970],"y":[3.93,5.31,7.24,9.64,12.9,17.1,23.2,31.4,39.8,50.2,62.9,76,92,105.7,122.8,131.7,151.3,179.3,203.2],"text":["Year: 1790<br />Population:   3.93<br />Population - Error:  -1.2840702<br />Population + Error:   9.14407","Year: 1800<br />Population:   5.31<br />Population - Error:   0.5802492<br />Population + Error:  10.03975","Year: 1810<br />Population:   7.24<br />Population - Error:   0.4159241<br />Population + Error:  14.06408","Year: 1820<br />Population:   9.64<br />Population - Error:   4.0530614<br />Population + Error:  15.22694","Year: 1830<br />Population:  12.90<br />Population - Error:   8.5797262<br />Population + Error:  17.22027","Year: 1840<br />Population:  17.10<br />Population - Error:  10.0506555<br />Population + Error:  24.14934","Year: 1850<br />Population:  23.20<br />Population - Error:  18.4701860<br />Population + Error:  27.92981","Year: 1860<br />Population:  31.40<br />Population - Error:  26.0445449<br />Population + Error:  36.75546","Year: 1870<br />Population:  39.80<br />Population - Error:  34.2707149<br />Population + Error:  45.32929","Year: 1880<br />Population:  50.20<br />Population - Error:  45.9209955<br />Population + Error:  54.47900","Year: 1890<br />Population:  62.90<br />Population - Error:  58.7721638<br />Population + Error:  67.02784","Year: 1900<br />Population:  76.00<br />Population - Error:  69.5877919<br />Population + Error:  82.41221","Year: 1910<br />Population:  92.00<br />Population - Error:  88.6684079<br />Population + Error:  95.33159","Year: 1920<br />Population: 105.70<br />Population - Error:  99.7897565<br />Population + Error: 111.61024","Year: 1930<br />Population: 122.80<br />Population - Error: 118.4326553<br />Population + Error: 127.16734","Year: 1940<br />Population: 131.70<br />Population - Error: 126.6659378<br />Population + Error: 136.73406","Year: 1950<br />Population: 151.30<br />Population - Error: 146.8887453<br />Population + Error: 155.71125","Year: 1960<br />Population: 179.30<br />Population - Error: 172.8875728<br />Population + Error: 185.71243","Year: 1970<br />Population: 203.20<br />Population - Error: 197.2932702<br />Population + Error: 209.10673"],"type":"scatter","mode":"lines+markers","line":{"width":1.88976377952756,"color":"transparent","dash":"solid"},"hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","marker":{"autocolorscale":false,"color":"rgba(0,0,0,1)","opacity":1,"size":5.66929133858268,"symbol":"triangle-up-open","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)"}},"opacity":1,"error_y":{"array":[5.21407017859704,4.72975084935153,6.82407587025236,5.58693862886874,4.32027379446517,7.04934448657666,4.72981398349743,5.35545509049223,5.52928505933392,4.27900445586052,4.12783619932009,6.41220813206402,3.33159210537687,5.91024352804978,4.36734474808442,5.03406217573496,4.41125467282711,6.41242723976274,5.90672978236569],"arrayminus":[5.21407017859704,4.72975084935153,6.82407587025236,5.58693862886874,4.32027379446517,7.04934448657666,4.72981398349743,5.35545509049223,5.52928505933392,4.27900445586052,4.1278361993201,6.41220813206402,3.33159210537687,5.91024352804978,4.36734474808442,5.03406217573495,4.41125467282711,6.41242723976274,5.90672978236569],"type":"data","width":1.01311623699693,"symmetric":false,"color":"rgba(0,0,0,1)"},"frame":null}],"layout":{"margin":{"t":26.2283105022831,"r":7.30593607305936,"b":40.1826484018265,"l":43.1050228310502},"plot_bgcolor":"rgba(235,235,235,1)","paper_bgcolor":"rgba(255,255,255,1)","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[1780.505,1979.495],"tickmode":"array","ticktext":["1800","1850","1900","1950"],"tickvals":[1800,1850,1900,1950],"categoryorder":"array","categoryarray":["1800","1850","1900","1950"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":{"text":"Year","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[-11.8036101766452,219.626269780414],"tickmode":"array","ticktext":["0","50","100","150","200"],"tickvals":[0,50,100,150,200],"categoryorder":"array","categoryarray":["0","50","100","150","200"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":{"text":"Population","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":"rgba(255,255,255,1)","bordercolor":"transparent","borderwidth":1.88976377952756,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","showSendToCloud":false},"source":"A","attrs":{"281f666661eb":{"x":{},"y":{},"ymin":{},"ymax":{},"type":"scatter"},"281f42c84aaa":{"x":{},"y":{},"ymin":{},"ymax":{}},"281f6a32c496":{"x":{},"y":{},"ymin":{},"ymax":{}}},"cur_data":"281f666661eb","visdat":{"281f666661eb":["function (y) ","x"],"281f42c84aaa":["function (y) ","x"],"281f6a32c496":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

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
