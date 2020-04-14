---
description: How to add text labels and annotations to plots in R.
display_as: file_settings
language: r
layout: base
name: Text and Annotations
order: 10
output:
  html_document:
    keep_md: true
page_type: u-guide
permalink: r/text-and-annotations/
thumbnail: thumbnail/text-and-annotations.png
---


### Text Mode


```r
library(plotly)

Primates <- c('Potar monkey', 'Gorilla', 'Human', 'Rhesus monkey', 'Chimp')
Bodywt <- c(10.0, 207.0, 62.0, 6.8, 52.2)
Brainwt <- c(115, 406, 1320, 179, 440)
data <- data.frame(Primates, Bodywt, Brainwt)

fig <- plot_ly(data, x = ~Bodywt, y = ~Brainwt, type = 'scatter',
        mode = 'text', text = ~Primates, textposition = 'middle right',
        textfont = list(color = '#000000', size = 16))
fig <- fig %>% layout(title = 'Primates Brain and Body Weight',
         xaxis = list(title = 'Body Weight (kg)',
                      zeroline = TRUE,
                      range = c(0, 250)),
         yaxis = list(title = 'Brain Weight (g)',
                      range = c(0,1400)))

fig
```

<div id="htmlwidget-c3c5698ca926bbbf8e11" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-c3c5698ca926bbbf8e11">{"x":{"visdat":{"c6b28cc48a1":["function () ","plotlyVisDat"]},"cur_data":"c6b28cc48a1","attrs":{"c6b28cc48a1":{"x":{},"y":{},"mode":"text","text":{},"textposition":"middle right","textfont":{"color":"#000000","size":16},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"Primates Brain and Body Weight","xaxis":{"domain":[0,1],"automargin":true,"title":"Body Weight (kg)","zeroline":true,"range":[0,250]},"yaxis":{"domain":[0,1],"automargin":true,"title":"Brain Weight (g)","range":[0,1400]},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"x":[10,207,62,6.8,52.2],"y":[115,406,1320,179,440],"mode":"text","text":["Potar monkey","Gorilla","Human","Rhesus monkey","Chimp"],"textposition":["middle right","middle right","middle right","middle right","middle right"],"textfont":{"color":"#000000","size":16},"type":"scatter","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

See more options on the textposition argument [here](https://plotly.com/r/reference/#scatter-textposition).

### Styling Text


```r
library(plotly)

data <- mtcars[which(mtcars$am == 1 & mtcars$gear == 4),]

t <- list(
  family = "sans serif",
  size = 14,
  color = toRGB("grey50"))

fig <- plot_ly(data, x = ~wt, y = ~mpg, text = rownames(data))
fig <- fig %>% add_markers()
fig <- fig %>% add_text(textfont = t, textposition = "top right")
fig <- fig %>% layout(xaxis = list(range = c(1.6, 3.2)),
         showlegend = FALSE)

fig
```

<div id="htmlwidget-c8cd0fe17e0880cd9022" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-c8cd0fe17e0880cd9022">{"x":{"visdat":{"c6b16a5c4c5":["function () ","plotlyVisDat"]},"cur_data":"c6b16a5c4c5","attrs":{"c6b16a5c4c5":{"x":{},"y":{},"text":["Mazda RX4","Mazda RX4 Wag","Datsun 710","Fiat 128","Honda Civic","Toyota Corolla","Fiat X1-9","Volvo 142E"],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter","mode":"markers","inherit":true},"c6b16a5c4c5.1":{"x":{},"y":{},"text":["Mazda RX4","Mazda RX4 Wag","Datsun 710","Fiat 128","Honda Civic","Toyota Corolla","Fiat X1-9","Volvo 142E"],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter","mode":"text","textfont":{"family":"sans serif","size":14,"color":"rgba(127,127,127,1)"},"textposition":"top right","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"xaxis":{"domain":[0,1],"automargin":true,"range":[1.6,3.2],"title":"wt"},"showlegend":false,"yaxis":{"domain":[0,1],"automargin":true,"title":"mpg"},"hovermode":"closest"},"source":"A","config":{"showSendToCloud":false},"data":[{"x":[2.62,2.875,2.32,2.2,1.615,1.835,1.935,2.78],"y":[21,21,22.8,32.4,30.4,33.9,27.3,21.4],"text":["Mazda RX4","Mazda RX4 Wag","Datsun 710","Fiat 128","Honda Civic","Toyota Corolla","Fiat X1-9","Volvo 142E"],"type":"scatter","mode":"markers","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[2.62,2.875,2.32,2.2,1.615,1.835,1.935,2.78],"y":[21,21,22.8,32.4,30.4,33.9,27.3,21.4],"text":["Mazda RX4","Mazda RX4 Wag","Datsun 710","Fiat 128","Honda Civic","Toyota Corolla","Fiat X1-9","Volvo 142E"],"type":"scatter","mode":"text","textfont":{"family":"sans serif","size":14,"color":"rgba(127,127,127,1)"},"textposition":["top right","top right","top right","top right","top right","top right","top right","top right"],"marker":{"color":"rgba(255,127,14,1)","line":{"color":"rgba(255,127,14,1)"}},"error_y":{"color":"rgba(255,127,14,1)"},"error_x":{"color":"rgba(255,127,14,1)"},"line":{"color":"rgba(255,127,14,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Controlling text fontsize with uniformtext

For the [pie](/r/pie-charts), [bar](/r/bar-charts), [sunburst](/r/sunburst-charts) and [treemap](/r/treemap-charts) traces, it is possible to force all the text labels to have the same size thanks to the `uniformtext` layout parameter. The `minsize` attribute sets the font size, and the `mode` attribute sets what happens for labels which cannot fit with the desired fontsize: either `hide` them or `show` them with overflow.


```r
library(plotly)

df <- read.csv("https://raw.githubusercontent.com/plotly/datasets/master/gapminderDataFiveYear.csv", stringsAsFactors = FALSE)
df <- df[which(df$year==2007 & df$continent=='Europe' & df$pop > 2.e6),]

fig <- plot_ly(df, type='bar', x = ~country, y = ~pop, text = ~lifeExp, name="",
               hovertemplate = paste('%{x}', '<br>lifeExp: %{text:.2s}<br>'),
               texttemplate = '%{y:.2s}', textposition = 'outside')

fig <- fig %>% layout(uniformtext=list(minsize=8, mode='hide'))
fig
```

<div id="htmlwidget-4bfeb842b79e5978878e" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-4bfeb842b79e5978878e">{"x":{"visdat":{"c6b4b0117fb":["function () ","plotlyVisDat"]},"cur_data":"c6b4b0117fb","attrs":{"c6b4b0117fb":{"x":{},"y":{},"text":{},"hovertemplate":"%{x} <br>lifeExp: %{text:.2s}<br>","texttemplate":"%{y:.2s}","textposition":"outside","name":"","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"bar"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"uniformtext":{"minsize":8,"mode":"hide"},"xaxis":{"domain":[0,1],"automargin":true,"title":"country","type":"category","categoryorder":"array","categoryarray":["Albania","Austria","Belgium","Bosnia and Herzegovina","Bulgaria","Croatia","Czech Republic","Denmark","Finland","France","Germany","Greece","Hungary","Ireland","Italy","Netherlands","Norway","Poland","Portugal","Romania","Serbia","Slovak Republic","Slovenia","Spain","Sweden","Switzerland","Turkey","United Kingdom"]},"yaxis":{"domain":[0,1],"automargin":true,"title":"pop"},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"x":["Albania","Austria","Belgium","Bosnia and Herzegovina","Bulgaria","Croatia","Czech Republic","Denmark","Finland","France","Germany","Greece","Hungary","Ireland","Italy","Netherlands","Norway","Poland","Portugal","Romania","Serbia","Slovak Republic","Slovenia","Spain","Sweden","Switzerland","Turkey","United Kingdom"],"y":[3600523,8199783,10392226,4552198,7322858,4493312,10228744,5468120,5238460,61083916,82400996,10706290,9956108,4109086,58147733,16570613,4627926,38518241,10642836,22276056,10150265,5447502,2009245,40448191,9031088,7554661,71158647,60776238],"text":[76.423,79.829,79.441,74.852,73.005,75.748,76.486,78.332,79.313,80.657,79.406,79.483,73.338,78.885,80.546,79.762,80.196,75.563,78.098,72.476,74.002,74.663,77.926,80.941,80.884,81.701,71.777,79.425],"hovertemplate":["%{x} <br>lifeExp: %{text:.2s}<br>","%{x} <br>lifeExp: %{text:.2s}<br>","%{x} <br>lifeExp: %{text:.2s}<br>","%{x} <br>lifeExp: %{text:.2s}<br>","%{x} <br>lifeExp: %{text:.2s}<br>","%{x} <br>lifeExp: %{text:.2s}<br>","%{x} <br>lifeExp: %{text:.2s}<br>","%{x} <br>lifeExp: %{text:.2s}<br>","%{x} <br>lifeExp: %{text:.2s}<br>","%{x} <br>lifeExp: %{text:.2s}<br>","%{x} <br>lifeExp: %{text:.2s}<br>","%{x} <br>lifeExp: %{text:.2s}<br>","%{x} <br>lifeExp: %{text:.2s}<br>","%{x} <br>lifeExp: %{text:.2s}<br>","%{x} <br>lifeExp: %{text:.2s}<br>","%{x} <br>lifeExp: %{text:.2s}<br>","%{x} <br>lifeExp: %{text:.2s}<br>","%{x} <br>lifeExp: %{text:.2s}<br>","%{x} <br>lifeExp: %{text:.2s}<br>","%{x} <br>lifeExp: %{text:.2s}<br>","%{x} <br>lifeExp: %{text:.2s}<br>","%{x} <br>lifeExp: %{text:.2s}<br>","%{x} <br>lifeExp: %{text:.2s}<br>","%{x} <br>lifeExp: %{text:.2s}<br>","%{x} <br>lifeExp: %{text:.2s}<br>","%{x} <br>lifeExp: %{text:.2s}<br>","%{x} <br>lifeExp: %{text:.2s}<br>","%{x} <br>lifeExp: %{text:.2s}<br>"],"texttemplate":["%{y:.2s}","%{y:.2s}","%{y:.2s}","%{y:.2s}","%{y:.2s}","%{y:.2s}","%{y:.2s}","%{y:.2s}","%{y:.2s}","%{y:.2s}","%{y:.2s}","%{y:.2s}","%{y:.2s}","%{y:.2s}","%{y:.2s}","%{y:.2s}","%{y:.2s}","%{y:.2s}","%{y:.2s}","%{y:.2s}","%{y:.2s}","%{y:.2s}","%{y:.2s}","%{y:.2s}","%{y:.2s}","%{y:.2s}","%{y:.2s}","%{y:.2s}"],"textposition":["outside","outside","outside","outside","outside","outside","outside","outside","outside","outside","outside","outside","outside","outside","outside","outside","outside","outside","outside","outside","outside","outside","outside","outside","outside","outside","outside","outside"],"name":"","type":"bar","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>


```r
library(plotly)

df <- read.csv("https://raw.githubusercontent.com/plotly/datasets/master/gapminderDataFiveYear.csv", stringsAsFactors = FALSE)
df <- df[which(df$year==2007 & df$continent=='Asia'),]

fig <- plot_ly(df, type='pie', labels = ~country, values = ~pop, textposition = 'inside')
fig <- fig %>% layout(uniformtext=list(minsize=12, mode='hide'))
fig
```

<div id="htmlwidget-8acb3516d032925802a1" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-8acb3516d032925802a1">{"x":{"visdat":{"c6bd1bb05c":["function () ","plotlyVisDat"]},"cur_data":"c6bd1bb05c","attrs":{"c6bd1bb05c":{"labels":{},"values":{},"textposition":"inside","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"pie"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"uniformtext":{"minsize":12,"mode":"hide"},"hovermode":"closest","showlegend":true},"source":"A","config":{"showSendToCloud":false},"data":[{"labels":["Afghanistan","Bahrain","Bangladesh","Cambodia","China","Hong Kong, China","India","Indonesia","Iran","Iraq","Israel","Japan","Jordan","Korea, Dem. Rep.","Korea, Rep.","Kuwait","Lebanon","Malaysia","Mongolia","Myanmar","Nepal","Oman","Pakistan","Philippines","Saudi Arabia","Singapore","Sri Lanka","Syria","Taiwan","Thailand","Vietnam","West Bank and Gaza","Yemen, Rep."],"values":[31889923,708573,150448339,14131858,1318683096,6980412,1110396331,223547000,69453570,27499638,6426679,127467972,6053193,23301725,49044790,2505559,3921278,24821286,2874127,47761980,28901790,3204897,169270617,91077287,27601038,4553009,20378239,19314747,23174294,65068149,85262356,4018332,22211743],"textposition":["inside","inside","inside","inside","inside","inside","inside","inside","inside","inside","inside","inside","inside","inside","inside","inside","inside","inside","inside","inside","inside","inside","inside","inside","inside","inside","inside","inside","inside","inside","inside","inside","inside"],"type":"pie","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(255,255,255,1)"}},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
### Adding Informations to Default Hover Text


```r
library(plotly)

fig <- plot_ly(iris, x = ~Petal.Length, y = ~Petal.Width, type = 'scatter', mode = 'markers',
        text = ~paste('Species: ', Species))

fig
```

<div id="htmlwidget-bbabdb67bea30e0ecbba" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-bbabdb67bea30e0ecbba">{"x":{"visdat":{"c6b6abee36b":["function () ","plotlyVisDat"]},"cur_data":"c6b6abee36b","attrs":{"c6b6abee36b":{"x":{},"y":{},"mode":"markers","text":{},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"xaxis":{"domain":[0,1],"automargin":true,"title":"Petal.Length"},"yaxis":{"domain":[0,1],"automargin":true,"title":"Petal.Width"},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"x":[1.4,1.4,1.3,1.5,1.4,1.7,1.4,1.5,1.4,1.5,1.5,1.6,1.4,1.1,1.2,1.5,1.3,1.4,1.7,1.5,1.7,1.5,1,1.7,1.9,1.6,1.6,1.5,1.4,1.6,1.6,1.5,1.5,1.4,1.5,1.2,1.3,1.4,1.3,1.5,1.3,1.3,1.3,1.6,1.9,1.4,1.6,1.4,1.5,1.4,4.7,4.5,4.9,4,4.6,4.5,4.7,3.3,4.6,3.9,3.5,4.2,4,4.7,3.6,4.4,4.5,4.1,4.5,3.9,4.8,4,4.9,4.7,4.3,4.4,4.8,5,4.5,3.5,3.8,3.7,3.9,5.1,4.5,4.5,4.7,4.4,4.1,4,4.4,4.6,4,3.3,4.2,4.2,4.2,4.3,3,4.1,6,5.1,5.9,5.6,5.8,6.6,4.5,6.3,5.8,6.1,5.1,5.3,5.5,5,5.1,5.3,5.5,6.7,6.9,5,5.7,4.9,6.7,4.9,5.7,6,4.8,4.9,5.6,5.8,6.1,6.4,5.6,5.1,5.6,6.1,5.6,5.5,4.8,5.4,5.6,5.1,5.1,5.9,5.7,5.2,5,5.2,5.4,5.1],"y":[0.2,0.2,0.2,0.2,0.2,0.4,0.3,0.2,0.2,0.1,0.2,0.2,0.1,0.1,0.2,0.4,0.4,0.3,0.3,0.3,0.2,0.4,0.2,0.5,0.2,0.2,0.4,0.2,0.2,0.2,0.2,0.4,0.1,0.2,0.2,0.2,0.2,0.1,0.2,0.2,0.3,0.3,0.2,0.6,0.4,0.3,0.2,0.2,0.2,0.2,1.4,1.5,1.5,1.3,1.5,1.3,1.6,1,1.3,1.4,1,1.5,1,1.4,1.3,1.4,1.5,1,1.5,1.1,1.8,1.3,1.5,1.2,1.3,1.4,1.4,1.7,1.5,1,1.1,1,1.2,1.6,1.5,1.6,1.5,1.3,1.3,1.3,1.2,1.4,1.2,1,1.3,1.2,1.3,1.3,1.1,1.3,2.5,1.9,2.1,1.8,2.2,2.1,1.7,1.8,1.8,2.5,2,1.9,2.1,2,2.4,2.3,1.8,2.2,2.3,1.5,2.3,2,2,1.8,2.1,1.8,1.8,1.8,2.1,1.6,1.9,2,2.2,1.5,1.4,2.3,2.4,1.8,1.8,2.1,2.4,2.3,1.9,2.3,2.5,2.3,1.9,2,2.3,1.8],"mode":"markers","text":["Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  setosa","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  versicolor","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica","Species:  virginica"],"type":"scatter","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Custom Hover Text


```r
library(plotly)

fig <- plot_ly(iris, x = ~Petal.Length, y = ~Petal.Width, type = 'scatter', mode = 'markers',
        hoverinfo = 'text',
        text = ~paste('</br> Species: ', Species,
                      '</br> Petal Length: ', Petal.Length,
                      '</br> Petal Width: ', Petal.Width))

fig
```

<div id="htmlwidget-890f976349e916cb3f8c" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-890f976349e916cb3f8c">{"x":{"visdat":{"c6b6a9dfd7e":["function () ","plotlyVisDat"]},"cur_data":"c6b6a9dfd7e","attrs":{"c6b6a9dfd7e":{"x":{},"y":{},"mode":"markers","hoverinfo":"text","text":{},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"xaxis":{"domain":[0,1],"automargin":true,"title":"Petal.Length"},"yaxis":{"domain":[0,1],"automargin":true,"title":"Petal.Width"},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"x":[1.4,1.4,1.3,1.5,1.4,1.7,1.4,1.5,1.4,1.5,1.5,1.6,1.4,1.1,1.2,1.5,1.3,1.4,1.7,1.5,1.7,1.5,1,1.7,1.9,1.6,1.6,1.5,1.4,1.6,1.6,1.5,1.5,1.4,1.5,1.2,1.3,1.4,1.3,1.5,1.3,1.3,1.3,1.6,1.9,1.4,1.6,1.4,1.5,1.4,4.7,4.5,4.9,4,4.6,4.5,4.7,3.3,4.6,3.9,3.5,4.2,4,4.7,3.6,4.4,4.5,4.1,4.5,3.9,4.8,4,4.9,4.7,4.3,4.4,4.8,5,4.5,3.5,3.8,3.7,3.9,5.1,4.5,4.5,4.7,4.4,4.1,4,4.4,4.6,4,3.3,4.2,4.2,4.2,4.3,3,4.1,6,5.1,5.9,5.6,5.8,6.6,4.5,6.3,5.8,6.1,5.1,5.3,5.5,5,5.1,5.3,5.5,6.7,6.9,5,5.7,4.9,6.7,4.9,5.7,6,4.8,4.9,5.6,5.8,6.1,6.4,5.6,5.1,5.6,6.1,5.6,5.5,4.8,5.4,5.6,5.1,5.1,5.9,5.7,5.2,5,5.2,5.4,5.1],"y":[0.2,0.2,0.2,0.2,0.2,0.4,0.3,0.2,0.2,0.1,0.2,0.2,0.1,0.1,0.2,0.4,0.4,0.3,0.3,0.3,0.2,0.4,0.2,0.5,0.2,0.2,0.4,0.2,0.2,0.2,0.2,0.4,0.1,0.2,0.2,0.2,0.2,0.1,0.2,0.2,0.3,0.3,0.2,0.6,0.4,0.3,0.2,0.2,0.2,0.2,1.4,1.5,1.5,1.3,1.5,1.3,1.6,1,1.3,1.4,1,1.5,1,1.4,1.3,1.4,1.5,1,1.5,1.1,1.8,1.3,1.5,1.2,1.3,1.4,1.4,1.7,1.5,1,1.1,1,1.2,1.6,1.5,1.6,1.5,1.3,1.3,1.3,1.2,1.4,1.2,1,1.3,1.2,1.3,1.3,1.1,1.3,2.5,1.9,2.1,1.8,2.2,2.1,1.7,1.8,1.8,2.5,2,1.9,2.1,2,2.4,2.3,1.8,2.2,2.3,1.5,2.3,2,2,1.8,2.1,1.8,1.8,1.8,2.1,1.6,1.9,2,2.2,1.5,1.4,2.3,2.4,1.8,1.8,2.1,2.4,2.3,1.9,2.3,2.5,2.3,1.9,2,2.3,1.8],"mode":"markers","hoverinfo":["text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text"],"text":["<\/br> Species:  setosa <\/br> Petal Length:  1.4 <\/br> Petal Width:  0.2","<\/br> Species:  setosa <\/br> Petal Length:  1.4 <\/br> Petal Width:  0.2","<\/br> Species:  setosa <\/br> Petal Length:  1.3 <\/br> Petal Width:  0.2","<\/br> Species:  setosa <\/br> Petal Length:  1.5 <\/br> Petal Width:  0.2","<\/br> Species:  setosa <\/br> Petal Length:  1.4 <\/br> Petal Width:  0.2","<\/br> Species:  setosa <\/br> Petal Length:  1.7 <\/br> Petal Width:  0.4","<\/br> Species:  setosa <\/br> Petal Length:  1.4 <\/br> Petal Width:  0.3","<\/br> Species:  setosa <\/br> Petal Length:  1.5 <\/br> Petal Width:  0.2","<\/br> Species:  setosa <\/br> Petal Length:  1.4 <\/br> Petal Width:  0.2","<\/br> Species:  setosa <\/br> Petal Length:  1.5 <\/br> Petal Width:  0.1","<\/br> Species:  setosa <\/br> Petal Length:  1.5 <\/br> Petal Width:  0.2","<\/br> Species:  setosa <\/br> Petal Length:  1.6 <\/br> Petal Width:  0.2","<\/br> Species:  setosa <\/br> Petal Length:  1.4 <\/br> Petal Width:  0.1","<\/br> Species:  setosa <\/br> Petal Length:  1.1 <\/br> Petal Width:  0.1","<\/br> Species:  setosa <\/br> Petal Length:  1.2 <\/br> Petal Width:  0.2","<\/br> Species:  setosa <\/br> Petal Length:  1.5 <\/br> Petal Width:  0.4","<\/br> Species:  setosa <\/br> Petal Length:  1.3 <\/br> Petal Width:  0.4","<\/br> Species:  setosa <\/br> Petal Length:  1.4 <\/br> Petal Width:  0.3","<\/br> Species:  setosa <\/br> Petal Length:  1.7 <\/br> Petal Width:  0.3","<\/br> Species:  setosa <\/br> Petal Length:  1.5 <\/br> Petal Width:  0.3","<\/br> Species:  setosa <\/br> Petal Length:  1.7 <\/br> Petal Width:  0.2","<\/br> Species:  setosa <\/br> Petal Length:  1.5 <\/br> Petal Width:  0.4","<\/br> Species:  setosa <\/br> Petal Length:  1 <\/br> Petal Width:  0.2","<\/br> Species:  setosa <\/br> Petal Length:  1.7 <\/br> Petal Width:  0.5","<\/br> Species:  setosa <\/br> Petal Length:  1.9 <\/br> Petal Width:  0.2","<\/br> Species:  setosa <\/br> Petal Length:  1.6 <\/br> Petal Width:  0.2","<\/br> Species:  setosa <\/br> Petal Length:  1.6 <\/br> Petal Width:  0.4","<\/br> Species:  setosa <\/br> Petal Length:  1.5 <\/br> Petal Width:  0.2","<\/br> Species:  setosa <\/br> Petal Length:  1.4 <\/br> Petal Width:  0.2","<\/br> Species:  setosa <\/br> Petal Length:  1.6 <\/br> Petal Width:  0.2","<\/br> Species:  setosa <\/br> Petal Length:  1.6 <\/br> Petal Width:  0.2","<\/br> Species:  setosa <\/br> Petal Length:  1.5 <\/br> Petal Width:  0.4","<\/br> Species:  setosa <\/br> Petal Length:  1.5 <\/br> Petal Width:  0.1","<\/br> Species:  setosa <\/br> Petal Length:  1.4 <\/br> Petal Width:  0.2","<\/br> Species:  setosa <\/br> Petal Length:  1.5 <\/br> Petal Width:  0.2","<\/br> Species:  setosa <\/br> Petal Length:  1.2 <\/br> Petal Width:  0.2","<\/br> Species:  setosa <\/br> Petal Length:  1.3 <\/br> Petal Width:  0.2","<\/br> Species:  setosa <\/br> Petal Length:  1.4 <\/br> Petal Width:  0.1","<\/br> Species:  setosa <\/br> Petal Length:  1.3 <\/br> Petal Width:  0.2","<\/br> Species:  setosa <\/br> Petal Length:  1.5 <\/br> Petal Width:  0.2","<\/br> Species:  setosa <\/br> Petal Length:  1.3 <\/br> Petal Width:  0.3","<\/br> Species:  setosa <\/br> Petal Length:  1.3 <\/br> Petal Width:  0.3","<\/br> Species:  setosa <\/br> Petal Length:  1.3 <\/br> Petal Width:  0.2","<\/br> Species:  setosa <\/br> Petal Length:  1.6 <\/br> Petal Width:  0.6","<\/br> Species:  setosa <\/br> Petal Length:  1.9 <\/br> Petal Width:  0.4","<\/br> Species:  setosa <\/br> Petal Length:  1.4 <\/br> Petal Width:  0.3","<\/br> Species:  setosa <\/br> Petal Length:  1.6 <\/br> Petal Width:  0.2","<\/br> Species:  setosa <\/br> Petal Length:  1.4 <\/br> Petal Width:  0.2","<\/br> Species:  setosa <\/br> Petal Length:  1.5 <\/br> Petal Width:  0.2","<\/br> Species:  setosa <\/br> Petal Length:  1.4 <\/br> Petal Width:  0.2","<\/br> Species:  versicolor <\/br> Petal Length:  4.7 <\/br> Petal Width:  1.4","<\/br> Species:  versicolor <\/br> Petal Length:  4.5 <\/br> Petal Width:  1.5","<\/br> Species:  versicolor <\/br> Petal Length:  4.9 <\/br> Petal Width:  1.5","<\/br> Species:  versicolor <\/br> Petal Length:  4 <\/br> Petal Width:  1.3","<\/br> Species:  versicolor <\/br> Petal Length:  4.6 <\/br> Petal Width:  1.5","<\/br> Species:  versicolor <\/br> Petal Length:  4.5 <\/br> Petal Width:  1.3","<\/br> Species:  versicolor <\/br> Petal Length:  4.7 <\/br> Petal Width:  1.6","<\/br> Species:  versicolor <\/br> Petal Length:  3.3 <\/br> Petal Width:  1","<\/br> Species:  versicolor <\/br> Petal Length:  4.6 <\/br> Petal Width:  1.3","<\/br> Species:  versicolor <\/br> Petal Length:  3.9 <\/br> Petal Width:  1.4","<\/br> Species:  versicolor <\/br> Petal Length:  3.5 <\/br> Petal Width:  1","<\/br> Species:  versicolor <\/br> Petal Length:  4.2 <\/br> Petal Width:  1.5","<\/br> Species:  versicolor <\/br> Petal Length:  4 <\/br> Petal Width:  1","<\/br> Species:  versicolor <\/br> Petal Length:  4.7 <\/br> Petal Width:  1.4","<\/br> Species:  versicolor <\/br> Petal Length:  3.6 <\/br> Petal Width:  1.3","<\/br> Species:  versicolor <\/br> Petal Length:  4.4 <\/br> Petal Width:  1.4","<\/br> Species:  versicolor <\/br> Petal Length:  4.5 <\/br> Petal Width:  1.5","<\/br> Species:  versicolor <\/br> Petal Length:  4.1 <\/br> Petal Width:  1","<\/br> Species:  versicolor <\/br> Petal Length:  4.5 <\/br> Petal Width:  1.5","<\/br> Species:  versicolor <\/br> Petal Length:  3.9 <\/br> Petal Width:  1.1","<\/br> Species:  versicolor <\/br> Petal Length:  4.8 <\/br> Petal Width:  1.8","<\/br> Species:  versicolor <\/br> Petal Length:  4 <\/br> Petal Width:  1.3","<\/br> Species:  versicolor <\/br> Petal Length:  4.9 <\/br> Petal Width:  1.5","<\/br> Species:  versicolor <\/br> Petal Length:  4.7 <\/br> Petal Width:  1.2","<\/br> Species:  versicolor <\/br> Petal Length:  4.3 <\/br> Petal Width:  1.3","<\/br> Species:  versicolor <\/br> Petal Length:  4.4 <\/br> Petal Width:  1.4","<\/br> Species:  versicolor <\/br> Petal Length:  4.8 <\/br> Petal Width:  1.4","<\/br> Species:  versicolor <\/br> Petal Length:  5 <\/br> Petal Width:  1.7","<\/br> Species:  versicolor <\/br> Petal Length:  4.5 <\/br> Petal Width:  1.5","<\/br> Species:  versicolor <\/br> Petal Length:  3.5 <\/br> Petal Width:  1","<\/br> Species:  versicolor <\/br> Petal Length:  3.8 <\/br> Petal Width:  1.1","<\/br> Species:  versicolor <\/br> Petal Length:  3.7 <\/br> Petal Width:  1","<\/br> Species:  versicolor <\/br> Petal Length:  3.9 <\/br> Petal Width:  1.2","<\/br> Species:  versicolor <\/br> Petal Length:  5.1 <\/br> Petal Width:  1.6","<\/br> Species:  versicolor <\/br> Petal Length:  4.5 <\/br> Petal Width:  1.5","<\/br> Species:  versicolor <\/br> Petal Length:  4.5 <\/br> Petal Width:  1.6","<\/br> Species:  versicolor <\/br> Petal Length:  4.7 <\/br> Petal Width:  1.5","<\/br> Species:  versicolor <\/br> Petal Length:  4.4 <\/br> Petal Width:  1.3","<\/br> Species:  versicolor <\/br> Petal Length:  4.1 <\/br> Petal Width:  1.3","<\/br> Species:  versicolor <\/br> Petal Length:  4 <\/br> Petal Width:  1.3","<\/br> Species:  versicolor <\/br> Petal Length:  4.4 <\/br> Petal Width:  1.2","<\/br> Species:  versicolor <\/br> Petal Length:  4.6 <\/br> Petal Width:  1.4","<\/br> Species:  versicolor <\/br> Petal Length:  4 <\/br> Petal Width:  1.2","<\/br> Species:  versicolor <\/br> Petal Length:  3.3 <\/br> Petal Width:  1","<\/br> Species:  versicolor <\/br> Petal Length:  4.2 <\/br> Petal Width:  1.3","<\/br> Species:  versicolor <\/br> Petal Length:  4.2 <\/br> Petal Width:  1.2","<\/br> Species:  versicolor <\/br> Petal Length:  4.2 <\/br> Petal Width:  1.3","<\/br> Species:  versicolor <\/br> Petal Length:  4.3 <\/br> Petal Width:  1.3","<\/br> Species:  versicolor <\/br> Petal Length:  3 <\/br> Petal Width:  1.1","<\/br> Species:  versicolor <\/br> Petal Length:  4.1 <\/br> Petal Width:  1.3","<\/br> Species:  virginica <\/br> Petal Length:  6 <\/br> Petal Width:  2.5","<\/br> Species:  virginica <\/br> Petal Length:  5.1 <\/br> Petal Width:  1.9","<\/br> Species:  virginica <\/br> Petal Length:  5.9 <\/br> Petal Width:  2.1","<\/br> Species:  virginica <\/br> Petal Length:  5.6 <\/br> Petal Width:  1.8","<\/br> Species:  virginica <\/br> Petal Length:  5.8 <\/br> Petal Width:  2.2","<\/br> Species:  virginica <\/br> Petal Length:  6.6 <\/br> Petal Width:  2.1","<\/br> Species:  virginica <\/br> Petal Length:  4.5 <\/br> Petal Width:  1.7","<\/br> Species:  virginica <\/br> Petal Length:  6.3 <\/br> Petal Width:  1.8","<\/br> Species:  virginica <\/br> Petal Length:  5.8 <\/br> Petal Width:  1.8","<\/br> Species:  virginica <\/br> Petal Length:  6.1 <\/br> Petal Width:  2.5","<\/br> Species:  virginica <\/br> Petal Length:  5.1 <\/br> Petal Width:  2","<\/br> Species:  virginica <\/br> Petal Length:  5.3 <\/br> Petal Width:  1.9","<\/br> Species:  virginica <\/br> Petal Length:  5.5 <\/br> Petal Width:  2.1","<\/br> Species:  virginica <\/br> Petal Length:  5 <\/br> Petal Width:  2","<\/br> Species:  virginica <\/br> Petal Length:  5.1 <\/br> Petal Width:  2.4","<\/br> Species:  virginica <\/br> Petal Length:  5.3 <\/br> Petal Width:  2.3","<\/br> Species:  virginica <\/br> Petal Length:  5.5 <\/br> Petal Width:  1.8","<\/br> Species:  virginica <\/br> Petal Length:  6.7 <\/br> Petal Width:  2.2","<\/br> Species:  virginica <\/br> Petal Length:  6.9 <\/br> Petal Width:  2.3","<\/br> Species:  virginica <\/br> Petal Length:  5 <\/br> Petal Width:  1.5","<\/br> Species:  virginica <\/br> Petal Length:  5.7 <\/br> Petal Width:  2.3","<\/br> Species:  virginica <\/br> Petal Length:  4.9 <\/br> Petal Width:  2","<\/br> Species:  virginica <\/br> Petal Length:  6.7 <\/br> Petal Width:  2","<\/br> Species:  virginica <\/br> Petal Length:  4.9 <\/br> Petal Width:  1.8","<\/br> Species:  virginica <\/br> Petal Length:  5.7 <\/br> Petal Width:  2.1","<\/br> Species:  virginica <\/br> Petal Length:  6 <\/br> Petal Width:  1.8","<\/br> Species:  virginica <\/br> Petal Length:  4.8 <\/br> Petal Width:  1.8","<\/br> Species:  virginica <\/br> Petal Length:  4.9 <\/br> Petal Width:  1.8","<\/br> Species:  virginica <\/br> Petal Length:  5.6 <\/br> Petal Width:  2.1","<\/br> Species:  virginica <\/br> Petal Length:  5.8 <\/br> Petal Width:  1.6","<\/br> Species:  virginica <\/br> Petal Length:  6.1 <\/br> Petal Width:  1.9","<\/br> Species:  virginica <\/br> Petal Length:  6.4 <\/br> Petal Width:  2","<\/br> Species:  virginica <\/br> Petal Length:  5.6 <\/br> Petal Width:  2.2","<\/br> Species:  virginica <\/br> Petal Length:  5.1 <\/br> Petal Width:  1.5","<\/br> Species:  virginica <\/br> Petal Length:  5.6 <\/br> Petal Width:  1.4","<\/br> Species:  virginica <\/br> Petal Length:  6.1 <\/br> Petal Width:  2.3","<\/br> Species:  virginica <\/br> Petal Length:  5.6 <\/br> Petal Width:  2.4","<\/br> Species:  virginica <\/br> Petal Length:  5.5 <\/br> Petal Width:  1.8","<\/br> Species:  virginica <\/br> Petal Length:  4.8 <\/br> Petal Width:  1.8","<\/br> Species:  virginica <\/br> Petal Length:  5.4 <\/br> Petal Width:  2.1","<\/br> Species:  virginica <\/br> Petal Length:  5.6 <\/br> Petal Width:  2.4","<\/br> Species:  virginica <\/br> Petal Length:  5.1 <\/br> Petal Width:  2.3","<\/br> Species:  virginica <\/br> Petal Length:  5.1 <\/br> Petal Width:  1.9","<\/br> Species:  virginica <\/br> Petal Length:  5.9 <\/br> Petal Width:  2.3","<\/br> Species:  virginica <\/br> Petal Length:  5.7 <\/br> Petal Width:  2.5","<\/br> Species:  virginica <\/br> Petal Length:  5.2 <\/br> Petal Width:  2.3","<\/br> Species:  virginica <\/br> Petal Length:  5 <\/br> Petal Width:  1.9","<\/br> Species:  virginica <\/br> Petal Length:  5.2 <\/br> Petal Width:  2","<\/br> Species:  virginica <\/br> Petal Length:  5.4 <\/br> Petal Width:  2.3","<\/br> Species:  virginica <\/br> Petal Length:  5.1 <\/br> Petal Width:  1.8"],"type":"scatter","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Single Annotation


```r
library(plotly)

m <- mtcars[which.max(mtcars$mpg), ]

a <- list(
  x = m$wt,
  y = m$mpg,
  text = rownames(m),
  xref = "x",
  yref = "y",
  showarrow = TRUE,
  arrowhead = 7,
  ax = 20,
  ay = -40
)

fig <- plot_ly(mtcars, x = ~wt, y = ~mpg)
fig <- fig %>% add_markers()
fig <- fig %>% layout(annotations = a)

fig
```

<div id="htmlwidget-22ae30733256a4ff3c0b" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-22ae30733256a4ff3c0b">{"x":{"visdat":{"c6b36ebaefb":["function () ","plotlyVisDat"]},"cur_data":"c6b36ebaefb","attrs":{"c6b36ebaefb":{"x":{},"y":{},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter","mode":"markers","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"annotations":[{"x":1.835,"y":33.9,"text":"Toyota Corolla","xref":"x","yref":"y","showarrow":true,"arrowhead":7,"ax":20,"ay":-40}],"xaxis":{"domain":[0,1],"automargin":true,"title":"wt"},"yaxis":{"domain":[0,1],"automargin":true,"title":"mpg"},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"x":[2.62,2.875,2.32,3.215,3.44,3.46,3.57,3.19,3.15,3.44,3.44,4.07,3.73,3.78,5.25,5.424,5.345,2.2,1.615,1.835,2.465,3.52,3.435,3.84,3.845,1.935,2.14,1.513,3.17,2.77,3.57,2.78],"y":[21,21,22.8,21.4,18.7,18.1,14.3,24.4,22.8,19.2,17.8,16.4,17.3,15.2,10.4,10.4,14.7,32.4,30.4,33.9,21.5,15.5,15.2,13.3,19.2,27.3,26,30.4,15.8,19.7,15,21.4],"type":"scatter","mode":"markers","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Multiple Annotations


```r
library(plotly)

data <- mtcars[which(mtcars$am == 1 & mtcars$gear == 4),]

fig <- plot_ly(data, x = ~wt, y = ~mpg, type = 'scatter', mode = 'markers',
        marker = list(size = 10))
fig <- fig %>% add_annotations(x = data$wt,
                  y = data$mpg,
                  text = rownames(data),
                  xref = "x",
                  yref = "y",
                  showarrow = TRUE,
                  arrowhead = 4,
                  arrowsize = .5,
                  ax = 20,
                  ay = -40)

fig
```

<div id="htmlwidget-006149e55048eaf04922" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-006149e55048eaf04922">{"x":{"visdat":{"c6b7b6201af":["function () ","plotlyVisDat"]},"cur_data":"c6b7b6201af","attrs":{"c6b7b6201af":{"x":{},"y":{},"mode":"markers","marker":{"size":10},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"annotations":[{"text":"Mazda RX4","x":2.62,"y":21,"xref":"x","yref":"y","showarrow":true,"arrowhead":4,"arrowsize":0.5,"ax":20,"ay":-40},{"text":"Mazda RX4 Wag","x":2.875,"y":21,"xref":"x","yref":"y","showarrow":true,"arrowhead":4,"arrowsize":0.5,"ax":20,"ay":-40},{"text":"Datsun 710","x":2.32,"y":22.8,"xref":"x","yref":"y","showarrow":true,"arrowhead":4,"arrowsize":0.5,"ax":20,"ay":-40},{"text":"Fiat 128","x":2.2,"y":32.4,"xref":"x","yref":"y","showarrow":true,"arrowhead":4,"arrowsize":0.5,"ax":20,"ay":-40},{"text":"Honda Civic","x":1.615,"y":30.4,"xref":"x","yref":"y","showarrow":true,"arrowhead":4,"arrowsize":0.5,"ax":20,"ay":-40},{"text":"Toyota Corolla","x":1.835,"y":33.9,"xref":"x","yref":"y","showarrow":true,"arrowhead":4,"arrowsize":0.5,"ax":20,"ay":-40},{"text":"Fiat X1-9","x":1.935,"y":27.3,"xref":"x","yref":"y","showarrow":true,"arrowhead":4,"arrowsize":0.5,"ax":20,"ay":-40},{"text":"Volvo 142E","x":2.78,"y":21.4,"xref":"x","yref":"y","showarrow":true,"arrowhead":4,"arrowsize":0.5,"ax":20,"ay":-40}],"xaxis":{"domain":[0,1],"automargin":true,"title":"wt"},"yaxis":{"domain":[0,1],"automargin":true,"title":"mpg"},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"x":[2.62,2.875,2.32,2.2,1.615,1.835,1.935,2.78],"y":[21,21,22.8,32.4,30.4,33.9,27.3,21.4],"mode":"markers","marker":{"color":"rgba(31,119,180,1)","size":10,"line":{"color":"rgba(31,119,180,1)"}},"type":"scatter","error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Subplot Annotations


```r
library(plotly)

m <- economics[which.max(economics$unemploy), ]
n <- economics[which.max(economics$uempmed), ]

# annotations
a <- list(
  x = m$date,
  y = m$unemploy,
  text = "annotation a",
  xref = "x",
  yref = "y",
  showarrow = TRUE,
  arrowhead = 7,
  ax = 20,
  ay = -40
)

b <- list(
  x = n$date,
  y = n$uempmed,
  text = "annotation b",
  xref = "x2",
  yref = "y2",
  showarrow = TRUE,
  arrowhead = 7,
  ax = 20,
  ay = -40
)

# figure labels
f <- list(
  family = "Courier New, monospace",
  size = 18,
  color = "#7f7f7f ")
x <- list(
  title = "x Axis",
  titlefont = f)
y <- list(
  title = "y Axis",
  titlefont = f)

fig1 <- plot_ly(economics, x = ~date, y = ~unemploy)
fig1 <- fig1 %>% add_lines(name = ~"unemploy")
fig1 <- fig1 %>% layout(annotations = a, xaxis = x, yaxis = y)
fig2 <- plot_ly(economics, x = ~date, y = ~uempmed)
fig2 <- fig2 %>% add_lines(name = ~"uempmed")
fig2 <- fig2 %>% layout(annotations = b, xaxis = x, yaxis = y)
fig <- subplot(fig1, fig2, titleX = TRUE, titleY = TRUE)
fig2 <- fig2 %>% layout(showlegend = FALSE)

fig
```

<div id="htmlwidget-d726a1e3f297b7868c9d" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-d726a1e3f297b7868c9d">{"x":{"data":[{"x":["1967-07-01","1967-08-01","1967-09-01","1967-10-01","1967-11-01","1967-12-01","1968-01-01","1968-02-01","1968-03-01","1968-04-01","1968-05-01","1968-06-01","1968-07-01","1968-08-01","1968-09-01","1968-10-01","1968-11-01","1968-12-01","1969-01-01","1969-02-01","1969-03-01","1969-04-01","1969-05-01","1969-06-01","1969-07-01","1969-08-01","1969-09-01","1969-10-01","1969-11-01","1969-12-01","1970-01-01","1970-02-01","1970-03-01","1970-04-01","1970-05-01","1970-06-01","1970-07-01","1970-08-01","1970-09-01","1970-10-01","1970-11-01","1970-12-01","1971-01-01","1971-02-01","1971-03-01","1971-04-01","1971-05-01","1971-06-01","1971-07-01","1971-08-01","1971-09-01","1971-10-01","1971-11-01","1971-12-01","1972-01-01","1972-02-01","1972-03-01","1972-04-01","1972-05-01","1972-06-01","1972-07-01","1972-08-01","1972-09-01","1972-10-01","1972-11-01","1972-12-01","1973-01-01","1973-02-01","1973-03-01","1973-04-01","1973-05-01","1973-06-01","1973-07-01","1973-08-01","1973-09-01","1973-10-01","1973-11-01","1973-12-01","1974-01-01","1974-02-01","1974-03-01","1974-04-01","1974-05-01","1974-06-01","1974-07-01","1974-08-01","1974-09-01","1974-10-01","1974-11-01","1974-12-01","1975-01-01","1975-02-01","1975-03-01","1975-04-01","1975-05-01","1975-06-01","1975-07-01","1975-08-01","1975-09-01","1975-10-01","1975-11-01","1975-12-01","1976-01-01","1976-02-01","1976-03-01","1976-04-01","1976-05-01","1976-06-01","1976-07-01","1976-08-01","1976-09-01","1976-10-01","1976-11-01","1976-12-01","1977-01-01","1977-02-01","1977-03-01","1977-04-01","1977-05-01","1977-06-01","1977-07-01","1977-08-01","1977-09-01","1977-10-01","1977-11-01","1977-12-01","1978-01-01","1978-02-01","1978-03-01","1978-04-01","1978-05-01","1978-06-01","1978-07-01","1978-08-01","1978-09-01","1978-10-01","1978-11-01","1978-12-01","1979-01-01","1979-02-01","1979-03-01","1979-04-01","1979-05-01","1979-06-01","1979-07-01","1979-08-01","1979-09-01","1979-10-01","1979-11-01","1979-12-01","1980-01-01","1980-02-01","1980-03-01","1980-04-01","1980-05-01","1980-06-01","1980-07-01","1980-08-01","1980-09-01","1980-10-01","1980-11-01","1980-12-01","1981-01-01","1981-02-01","1981-03-01","1981-04-01","1981-05-01","1981-06-01","1981-07-01","1981-08-01","1981-09-01","1981-10-01","1981-11-01","1981-12-01","1982-01-01","1982-02-01","1982-03-01","1982-04-01","1982-05-01","1982-06-01","1982-07-01","1982-08-01","1982-09-01","1982-10-01","1982-11-01","1982-12-01","1983-01-01","1983-02-01","1983-03-01","1983-04-01","1983-05-01","1983-06-01","1983-07-01","1983-08-01","1983-09-01","1983-10-01","1983-11-01","1983-12-01","1984-01-01","1984-02-01","1984-03-01","1984-04-01","1984-05-01","1984-06-01","1984-07-01","1984-08-01","1984-09-01","1984-10-01","1984-11-01","1984-12-01","1985-01-01","1985-02-01","1985-03-01","1985-04-01","1985-05-01","1985-06-01","1985-07-01","1985-08-01","1985-09-01","1985-10-01","1985-11-01","1985-12-01","1986-01-01","1986-02-01","1986-03-01","1986-04-01","1986-05-01","1986-06-01","1986-07-01","1986-08-01","1986-09-01","1986-10-01","1986-11-01","1986-12-01","1987-01-01","1987-02-01","1987-03-01","1987-04-01","1987-05-01","1987-06-01","1987-07-01","1987-08-01","1987-09-01","1987-10-01","1987-11-01","1987-12-01","1988-01-01","1988-02-01","1988-03-01","1988-04-01","1988-05-01","1988-06-01","1988-07-01","1988-08-01","1988-09-01","1988-10-01","1988-11-01","1988-12-01","1989-01-01","1989-02-01","1989-03-01","1989-04-01","1989-05-01","1989-06-01","1989-07-01","1989-08-01","1989-09-01","1989-10-01","1989-11-01","1989-12-01","1990-01-01","1990-02-01","1990-03-01","1990-04-01","1990-05-01","1990-06-01","1990-07-01","1990-08-01","1990-09-01","1990-10-01","1990-11-01","1990-12-01","1991-01-01","1991-02-01","1991-03-01","1991-04-01","1991-05-01","1991-06-01","1991-07-01","1991-08-01","1991-09-01","1991-10-01","1991-11-01","1991-12-01","1992-01-01","1992-02-01","1992-03-01","1992-04-01","1992-05-01","1992-06-01","1992-07-01","1992-08-01","1992-09-01","1992-10-01","1992-11-01","1992-12-01","1993-01-01","1993-02-01","1993-03-01","1993-04-01","1993-05-01","1993-06-01","1993-07-01","1993-08-01","1993-09-01","1993-10-01","1993-11-01","1993-12-01","1994-01-01","1994-02-01","1994-03-01","1994-04-01","1994-05-01","1994-06-01","1994-07-01","1994-08-01","1994-09-01","1994-10-01","1994-11-01","1994-12-01","1995-01-01","1995-02-01","1995-03-01","1995-04-01","1995-05-01","1995-06-01","1995-07-01","1995-08-01","1995-09-01","1995-10-01","1995-11-01","1995-12-01","1996-01-01","1996-02-01","1996-03-01","1996-04-01","1996-05-01","1996-06-01","1996-07-01","1996-08-01","1996-09-01","1996-10-01","1996-11-01","1996-12-01","1997-01-01","1997-02-01","1997-03-01","1997-04-01","1997-05-01","1997-06-01","1997-07-01","1997-08-01","1997-09-01","1997-10-01","1997-11-01","1997-12-01","1998-01-01","1998-02-01","1998-03-01","1998-04-01","1998-05-01","1998-06-01","1998-07-01","1998-08-01","1998-09-01","1998-10-01","1998-11-01","1998-12-01","1999-01-01","1999-02-01","1999-03-01","1999-04-01","1999-05-01","1999-06-01","1999-07-01","1999-08-01","1999-09-01","1999-10-01","1999-11-01","1999-12-01","2000-01-01","2000-02-01","2000-03-01","2000-04-01","2000-05-01","2000-06-01","2000-07-01","2000-08-01","2000-09-01","2000-10-01","2000-11-01","2000-12-01","2001-01-01","2001-02-01","2001-03-01","2001-04-01","2001-05-01","2001-06-01","2001-07-01","2001-08-01","2001-09-01","2001-10-01","2001-11-01","2001-12-01","2002-01-01","2002-02-01","2002-03-01","2002-04-01","2002-05-01","2002-06-01","2002-07-01","2002-08-01","2002-09-01","2002-10-01","2002-11-01","2002-12-01","2003-01-01","2003-02-01","2003-03-01","2003-04-01","2003-05-01","2003-06-01","2003-07-01","2003-08-01","2003-09-01","2003-10-01","2003-11-01","2003-12-01","2004-01-01","2004-02-01","2004-03-01","2004-04-01","2004-05-01","2004-06-01","2004-07-01","2004-08-01","2004-09-01","2004-10-01","2004-11-01","2004-12-01","2005-01-01","2005-02-01","2005-03-01","2005-04-01","2005-05-01","2005-06-01","2005-07-01","2005-08-01","2005-09-01","2005-10-01","2005-11-01","2005-12-01","2006-01-01","2006-02-01","2006-03-01","2006-04-01","2006-05-01","2006-06-01","2006-07-01","2006-08-01","2006-09-01","2006-10-01","2006-11-01","2006-12-01","2007-01-01","2007-02-01","2007-03-01","2007-04-01","2007-05-01","2007-06-01","2007-07-01","2007-08-01","2007-09-01","2007-10-01","2007-11-01","2007-12-01","2008-01-01","2008-02-01","2008-03-01","2008-04-01","2008-05-01","2008-06-01","2008-07-01","2008-08-01","2008-09-01","2008-10-01","2008-11-01","2008-12-01","2009-01-01","2009-02-01","2009-03-01","2009-04-01","2009-05-01","2009-06-01","2009-07-01","2009-08-01","2009-09-01","2009-10-01","2009-11-01","2009-12-01","2010-01-01","2010-02-01","2010-03-01","2010-04-01","2010-05-01","2010-06-01","2010-07-01","2010-08-01","2010-09-01","2010-10-01","2010-11-01","2010-12-01","2011-01-01","2011-02-01","2011-03-01","2011-04-01","2011-05-01","2011-06-01","2011-07-01","2011-08-01","2011-09-01","2011-10-01","2011-11-01","2011-12-01","2012-01-01","2012-02-01","2012-03-01","2012-04-01","2012-05-01","2012-06-01","2012-07-01","2012-08-01","2012-09-01","2012-10-01","2012-11-01","2012-12-01","2013-01-01","2013-02-01","2013-03-01","2013-04-01","2013-05-01","2013-06-01","2013-07-01","2013-08-01","2013-09-01","2013-10-01","2013-11-01","2013-12-01","2014-01-01","2014-02-01","2014-03-01","2014-04-01","2014-05-01","2014-06-01","2014-07-01","2014-08-01","2014-09-01","2014-10-01","2014-11-01","2014-12-01","2015-01-01","2015-02-01","2015-03-01","2015-04-01"],"y":[2944,2945,2958,3143,3066,3018,2878,3001,2877,2709,2740,2938,2883,2768,2686,2689,2715,2685,2718,2692,2712,2758,2713,2816,2868,2856,3040,3049,2856,2884,3201,3453,3635,3797,3919,4071,4175,4256,4456,4591,4898,5076,4986,4903,4987,4959,4996,4949,5035,5134,5042,4954,5161,5154,5019,4928,5038,4959,4922,4923,4913,4939,4849,4875,4602,4543,4326,4452,4394,4459,4329,4363,4305,4305,4350,4144,4396,4489,4644,4731,4634,4618,4705,4927,5063,5022,5437,5523,6140,6636,7501,7520,7978,8210,8433,8220,8127,7928,7923,7897,7794,7744,7534,7326,7230,7330,7053,7322,7490,7518,7380,7430,7620,7545,7280,7443,7307,7059,6911,7134,6829,6925,6751,6763,6815,6386,6489,6318,6337,6180,6127,6028,6309,6080,6125,5947,6077,6228,6109,6173,6109,6069,5840,5959,5996,6320,6190,6296,6238,6325,6683,6702,6729,7358,7984,8098,8363,8281,8021,8088,8023,7718,8071,8051,7982,7869,8174,8098,7863,8036,8230,8646,9029,9267,9397,9705,9895,10244,10335,10538,10849,10881,11217,11529,11938,12051,11534,11545,11408,11268,11154,11246,10548,10623,10282,9887,9499,9331,9008,8791,8746,8762,8456,8226,8537,8519,8367,8381,8198,8358,8423,8321,8339,8395,8302,8460,8513,8196,8248,8298,8128,8138,7795,8402,8383,8364,8439,8508,8319,8135,8310,8243,8159,7883,7892,7865,7862,7542,7574,7398,7268,7261,7102,7227,7035,6936,6953,6929,6876,6601,6779,6546,6605,6843,6604,6568,6537,6518,6682,6359,6205,6468,6375,6577,6495,6511,6590,6630,6725,6667,6752,6651,6598,6797,6742,6590,6922,7188,7368,7459,7764,7901,8015,8265,8586,8439,8736,8692,8586,8666,8722,8842,8931,9198,9283,9454,9460,9415,9744,10040,9850,9787,9781,9398,9565,9557,9325,9183,9056,9110,9149,9121,8930,8763,8714,8750,8542,8477,8630,8583,8470,8331,7915,7927,7946,7933,7734,7632,7375,7230,7375,7187,7153,7645,7430,7427,7527,7484,7478,7328,7426,7423,7491,7313,7318,7415,7423,7095,7337,6882,6979,7031,7236,7253,7158,7102,7000,6873,6655,6799,6655,6608,6656,6454,6308,6476,6368,6306,6422,5941,6047,6212,6259,6179,6300,6280,6100,6032,5976,6111,5783,6004,5796,5951,6025,5838,5915,5778,5716,5653,5708,5858,5733,5481,5758,5651,5747,5853,5625,5534,5639,5634,6023,6089,6141,6271,6226,6484,6583,7042,7142,7694,8003,8258,8182,8215,8304,8599,8399,8393,8390,8304,8251,8307,8520,8640,8520,8618,8588,8842,8957,9266,9011,8896,8921,8732,8576,8317,8370,8167,8491,8170,8212,8286,8136,7990,7927,8061,7932,7934,7784,7980,7737,7672,7651,7524,7406,7345,7553,7453,7566,7279,7064,7184,7072,7120,6980,7001,7175,7091,6847,6727,6872,6762,7116,6927,6731,6850,6766,6979,7149,7067,7170,7237,7240,7645,7685,7497,7822,7637,8395,8575,8937,9438,9494,10074,10538,11286,12058,12898,13426,13853,14499,14707,14601,14814,15009,15352,15219,15098,15046,15113,15202,15325,14849,14474,14512,14648,14579,14516,15081,14348,14013,13820,13737,13957,13855,13962,13763,13818,13948,13594,13302,13093,12797,12813,12713,12646,12660,12692,12656,12471,12115,12124,12005,12298,12471,11950,11689,11760,11654,11751,11335,11279,11270,11136,10787,10404,10202,10349,10380,9702,9859,9460,9608,9599,9262,8990,9090,8717,8903,8610,8504,8526],"type":"scatter","mode":"lines","name":"unemploy","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":["1967-07-01","1967-08-01","1967-09-01","1967-10-01","1967-11-01","1967-12-01","1968-01-01","1968-02-01","1968-03-01","1968-04-01","1968-05-01","1968-06-01","1968-07-01","1968-08-01","1968-09-01","1968-10-01","1968-11-01","1968-12-01","1969-01-01","1969-02-01","1969-03-01","1969-04-01","1969-05-01","1969-06-01","1969-07-01","1969-08-01","1969-09-01","1969-10-01","1969-11-01","1969-12-01","1970-01-01","1970-02-01","1970-03-01","1970-04-01","1970-05-01","1970-06-01","1970-07-01","1970-08-01","1970-09-01","1970-10-01","1970-11-01","1970-12-01","1971-01-01","1971-02-01","1971-03-01","1971-04-01","1971-05-01","1971-06-01","1971-07-01","1971-08-01","1971-09-01","1971-10-01","1971-11-01","1971-12-01","1972-01-01","1972-02-01","1972-03-01","1972-04-01","1972-05-01","1972-06-01","1972-07-01","1972-08-01","1972-09-01","1972-10-01","1972-11-01","1972-12-01","1973-01-01","1973-02-01","1973-03-01","1973-04-01","1973-05-01","1973-06-01","1973-07-01","1973-08-01","1973-09-01","1973-10-01","1973-11-01","1973-12-01","1974-01-01","1974-02-01","1974-03-01","1974-04-01","1974-05-01","1974-06-01","1974-07-01","1974-08-01","1974-09-01","1974-10-01","1974-11-01","1974-12-01","1975-01-01","1975-02-01","1975-03-01","1975-04-01","1975-05-01","1975-06-01","1975-07-01","1975-08-01","1975-09-01","1975-10-01","1975-11-01","1975-12-01","1976-01-01","1976-02-01","1976-03-01","1976-04-01","1976-05-01","1976-06-01","1976-07-01","1976-08-01","1976-09-01","1976-10-01","1976-11-01","1976-12-01","1977-01-01","1977-02-01","1977-03-01","1977-04-01","1977-05-01","1977-06-01","1977-07-01","1977-08-01","1977-09-01","1977-10-01","1977-11-01","1977-12-01","1978-01-01","1978-02-01","1978-03-01","1978-04-01","1978-05-01","1978-06-01","1978-07-01","1978-08-01","1978-09-01","1978-10-01","1978-11-01","1978-12-01","1979-01-01","1979-02-01","1979-03-01","1979-04-01","1979-05-01","1979-06-01","1979-07-01","1979-08-01","1979-09-01","1979-10-01","1979-11-01","1979-12-01","1980-01-01","1980-02-01","1980-03-01","1980-04-01","1980-05-01","1980-06-01","1980-07-01","1980-08-01","1980-09-01","1980-10-01","1980-11-01","1980-12-01","1981-01-01","1981-02-01","1981-03-01","1981-04-01","1981-05-01","1981-06-01","1981-07-01","1981-08-01","1981-09-01","1981-10-01","1981-11-01","1981-12-01","1982-01-01","1982-02-01","1982-03-01","1982-04-01","1982-05-01","1982-06-01","1982-07-01","1982-08-01","1982-09-01","1982-10-01","1982-11-01","1982-12-01","1983-01-01","1983-02-01","1983-03-01","1983-04-01","1983-05-01","1983-06-01","1983-07-01","1983-08-01","1983-09-01","1983-10-01","1983-11-01","1983-12-01","1984-01-01","1984-02-01","1984-03-01","1984-04-01","1984-05-01","1984-06-01","1984-07-01","1984-08-01","1984-09-01","1984-10-01","1984-11-01","1984-12-01","1985-01-01","1985-02-01","1985-03-01","1985-04-01","1985-05-01","1985-06-01","1985-07-01","1985-08-01","1985-09-01","1985-10-01","1985-11-01","1985-12-01","1986-01-01","1986-02-01","1986-03-01","1986-04-01","1986-05-01","1986-06-01","1986-07-01","1986-08-01","1986-09-01","1986-10-01","1986-11-01","1986-12-01","1987-01-01","1987-02-01","1987-03-01","1987-04-01","1987-05-01","1987-06-01","1987-07-01","1987-08-01","1987-09-01","1987-10-01","1987-11-01","1987-12-01","1988-01-01","1988-02-01","1988-03-01","1988-04-01","1988-05-01","1988-06-01","1988-07-01","1988-08-01","1988-09-01","1988-10-01","1988-11-01","1988-12-01","1989-01-01","1989-02-01","1989-03-01","1989-04-01","1989-05-01","1989-06-01","1989-07-01","1989-08-01","1989-09-01","1989-10-01","1989-11-01","1989-12-01","1990-01-01","1990-02-01","1990-03-01","1990-04-01","1990-05-01","1990-06-01","1990-07-01","1990-08-01","1990-09-01","1990-10-01","1990-11-01","1990-12-01","1991-01-01","1991-02-01","1991-03-01","1991-04-01","1991-05-01","1991-06-01","1991-07-01","1991-08-01","1991-09-01","1991-10-01","1991-11-01","1991-12-01","1992-01-01","1992-02-01","1992-03-01","1992-04-01","1992-05-01","1992-06-01","1992-07-01","1992-08-01","1992-09-01","1992-10-01","1992-11-01","1992-12-01","1993-01-01","1993-02-01","1993-03-01","1993-04-01","1993-05-01","1993-06-01","1993-07-01","1993-08-01","1993-09-01","1993-10-01","1993-11-01","1993-12-01","1994-01-01","1994-02-01","1994-03-01","1994-04-01","1994-05-01","1994-06-01","1994-07-01","1994-08-01","1994-09-01","1994-10-01","1994-11-01","1994-12-01","1995-01-01","1995-02-01","1995-03-01","1995-04-01","1995-05-01","1995-06-01","1995-07-01","1995-08-01","1995-09-01","1995-10-01","1995-11-01","1995-12-01","1996-01-01","1996-02-01","1996-03-01","1996-04-01","1996-05-01","1996-06-01","1996-07-01","1996-08-01","1996-09-01","1996-10-01","1996-11-01","1996-12-01","1997-01-01","1997-02-01","1997-03-01","1997-04-01","1997-05-01","1997-06-01","1997-07-01","1997-08-01","1997-09-01","1997-10-01","1997-11-01","1997-12-01","1998-01-01","1998-02-01","1998-03-01","1998-04-01","1998-05-01","1998-06-01","1998-07-01","1998-08-01","1998-09-01","1998-10-01","1998-11-01","1998-12-01","1999-01-01","1999-02-01","1999-03-01","1999-04-01","1999-05-01","1999-06-01","1999-07-01","1999-08-01","1999-09-01","1999-10-01","1999-11-01","1999-12-01","2000-01-01","2000-02-01","2000-03-01","2000-04-01","2000-05-01","2000-06-01","2000-07-01","2000-08-01","2000-09-01","2000-10-01","2000-11-01","2000-12-01","2001-01-01","2001-02-01","2001-03-01","2001-04-01","2001-05-01","2001-06-01","2001-07-01","2001-08-01","2001-09-01","2001-10-01","2001-11-01","2001-12-01","2002-01-01","2002-02-01","2002-03-01","2002-04-01","2002-05-01","2002-06-01","2002-07-01","2002-08-01","2002-09-01","2002-10-01","2002-11-01","2002-12-01","2003-01-01","2003-02-01","2003-03-01","2003-04-01","2003-05-01","2003-06-01","2003-07-01","2003-08-01","2003-09-01","2003-10-01","2003-11-01","2003-12-01","2004-01-01","2004-02-01","2004-03-01","2004-04-01","2004-05-01","2004-06-01","2004-07-01","2004-08-01","2004-09-01","2004-10-01","2004-11-01","2004-12-01","2005-01-01","2005-02-01","2005-03-01","2005-04-01","2005-05-01","2005-06-01","2005-07-01","2005-08-01","2005-09-01","2005-10-01","2005-11-01","2005-12-01","2006-01-01","2006-02-01","2006-03-01","2006-04-01","2006-05-01","2006-06-01","2006-07-01","2006-08-01","2006-09-01","2006-10-01","2006-11-01","2006-12-01","2007-01-01","2007-02-01","2007-03-01","2007-04-01","2007-05-01","2007-06-01","2007-07-01","2007-08-01","2007-09-01","2007-10-01","2007-11-01","2007-12-01","2008-01-01","2008-02-01","2008-03-01","2008-04-01","2008-05-01","2008-06-01","2008-07-01","2008-08-01","2008-09-01","2008-10-01","2008-11-01","2008-12-01","2009-01-01","2009-02-01","2009-03-01","2009-04-01","2009-05-01","2009-06-01","2009-07-01","2009-08-01","2009-09-01","2009-10-01","2009-11-01","2009-12-01","2010-01-01","2010-02-01","2010-03-01","2010-04-01","2010-05-01","2010-06-01","2010-07-01","2010-08-01","2010-09-01","2010-10-01","2010-11-01","2010-12-01","2011-01-01","2011-02-01","2011-03-01","2011-04-01","2011-05-01","2011-06-01","2011-07-01","2011-08-01","2011-09-01","2011-10-01","2011-11-01","2011-12-01","2012-01-01","2012-02-01","2012-03-01","2012-04-01","2012-05-01","2012-06-01","2012-07-01","2012-08-01","2012-09-01","2012-10-01","2012-11-01","2012-12-01","2013-01-01","2013-02-01","2013-03-01","2013-04-01","2013-05-01","2013-06-01","2013-07-01","2013-08-01","2013-09-01","2013-10-01","2013-11-01","2013-12-01","2014-01-01","2014-02-01","2014-03-01","2014-04-01","2014-05-01","2014-06-01","2014-07-01","2014-08-01","2014-09-01","2014-10-01","2014-11-01","2014-12-01","2015-01-01","2015-02-01","2015-03-01","2015-04-01"],"y":[4.5,4.7,4.6,4.9,4.7,4.8,5.1,4.5,4.1,4.6,4.4,4.4,4.5,4.2,4.6,4.8,4.4,4.4,4.4,4.9,4,4,4.2,4.4,4.4,4.4,4.7,4.5,4.8,4.6,4.6,4.5,4.6,4.1,4.7,4.9,5.1,5.4,5.2,5.2,5.6,5.9,6.2,6.3,6.4,6.5,6.7,5.7,6.2,6.4,5.8,6.5,6.4,6.2,6.2,6.6,6.6,6.7,6.6,5.4,6.1,6,5.6,5.7,5.7,6.1,5.7,5.2,5.5,5,4.9,5,5.2,4.9,5.4,5.5,5.1,4.7,5,5.1,4.8,5,4.6,5.3,5.7,5,5.3,5.5,5.2,5.7,6.3,7.1,7.2,8.7,9.4,8.8,8.6,9.2,9.2,8.6,9.5,9,9,8.2,8.7,8.2,8.3,7.8,7.7,7.9,7.8,7.7,8.4,8,7.5,7.2,7.2,7.3,7.9,6.2,7.1,7,6.7,6.9,7,6.8,6.5,6.7,6.2,6.1,5.7,6,5.8,5.8,5.6,5.9,5.5,5.6,5.9,5.9,5.9,5.4,5.6,5.6,5.9,4.8,5.5,5.5,5.3,5.7,5.3,5.8,6,5.8,5.7,6.4,7,7.5,7.7,7.5,7.7,7.5,7.4,7.1,7.1,7.4,6.9,6.6,7.1,7.2,6.8,6.8,6.9,6.9,7.1,7.5,7.7,8.1,8.5,9.5,8.5,8.7,9.5,9.7,10,10.2,11.1,9.8,10.4,10.9,12.3,11.3,10.1,9.3,9.3,9.4,9.3,8.7,9.1,8.3,8.3,8.2,9.1,7.5,7.5,7.3,7.6,7.2,7.2,7.3,6.8,7.1,7.1,6.9,6.9,6.6,6.9,7.1,6.9,7.1,7,6.8,6.7,6.9,6.8,6.7,6.8,7,6.9,7.1,7.4,7,7.1,7.1,6.9,6.6,6.6,7.1,6.6,6.5,6.5,6.4,6,6.3,6.2,6,6.2,6.3,6.4,5.9,5.9,5.8,6.1,5.9,5.7,5.6,5.7,5.9,5.6,5.4,5.4,5.4,5.3,5.4,5.6,5,4.9,4.9,4.8,4.9,5.1,5.3,5.1,4.8,5.2,5.2,5.4,5.4,5.6,5.8,5.7,5.9,6,6.2,6.7,6.6,6.4,6.9,7,7.3,6.8,7.2,7.5,7.8,8.1,8.2,8.3,8.5,8.8,8.7,8.6,8.8,8.6,9,9,9.3,8.6,8.5,8.5,8.4,8.1,8.3,8.2,8.2,8.3,8,8.3,8.3,8.6,9.2,9.3,9.1,9.2,9.3,9,8.9,9.2,10,9,8.7,8,8.1,8.3,8.3,9.1,7.9,8.5,8.3,7.9,8.2,8,8.3,8.3,7.8,8.3,8.6,8.6,8.3,8.3,8.4,8.5,8.3,7.7,7.8,7.8,8.1,7.9,8.3,8,8,8.3,7.8,8.2,7.7,7.6,7.5,7.4,7,6.8,6.7,6,6.9,6.7,6.8,6.7,5.8,6.6,6.8,6.9,6.8,6.8,6.2,6.5,6.3,5.8,6.5,6,6.1,6.2,5.8,5.8,6.1,6,6.1,5.8,5.7,6,6.3,5.2,6.1,6.1,6,5.8,6.1,6.6,5.9,6.3,6,6.8,6.9,7.2,7.3,7.7,8.2,8.4,8.3,8.4,8.9,9.5,11,8.9,9,9.5,9.6,9.3,9.6,9.6,9.5,9.7,10.2,9.9,11.5,10.3,10.1,10.2,10.4,10.3,10.4,10.6,10.2,10.2,9.5,9.9,11,8.9,9.2,9.6,9.5,9.7,9.5,9.4,9.2,9.3,9,9.1,9,8.8,9.2,8.4,8.6,8.5,8.7,8.6,9.1,8.7,8.4,8.5,7.3,8,8.4,8,7.9,8.3,7.5,8.3,8.5,9.1,8.6,8.2,7.7,8.7,8.8,8.7,8.4,8.6,8.4,9,8.7,8.7,9.4,7.9,9,9.7,9.7,10.2,10.4,9.8,10.5,10.7,11.7,12.3,13.1,14.2,17.2,16,16.3,17.8,18.9,19.8,20.1,20,19.9,20.4,22.1,22.3,25.2,22.3,21,20.3,21.2,21,21.9,21.5,21.1,21.5,20.9,21.6,22.4,22,22.4,22,20.6,20.8,20.5,20.8,19.7,19.2,19.1,19.9,20.4,17.5,18.4,18.8,19.9,18.6,17.7,15.8,17.2,17.6,17.1,17.1,17,16.2,16.5,16.5,16.3,17.1,17.3,15.4,15.9,15.8,15.7,14.6,13.8,13.1,12.9,13.4,13.6,13,12.9,13.2,12.9,12,11.5],"type":"scatter","mode":"lines","name":"uempmed","marker":{"color":"rgba(255,127,14,1)","line":{"color":"rgba(255,127,14,1)"}},"error_y":{"color":"rgba(255,127,14,1)"},"error_x":{"color":"rgba(255,127,14,1)"},"line":{"color":"rgba(255,127,14,1)"},"xaxis":"x2","yaxis":"y2","frame":null}],"layout":{"xaxis":{"domain":[0,0.48],"automargin":true,"title":"x Axis","titlefont":{"family":"Courier New, monospace","size":18,"color":"#7f7f7f "},"anchor":"y"},"xaxis2":{"domain":[0.52,1],"automargin":true,"title":"x Axis","titlefont":{"family":"Courier New, monospace","size":18,"color":"#7f7f7f "},"anchor":"y2"},"yaxis2":{"domain":[0,1],"automargin":true,"title":"y Axis","titlefont":{"family":"Courier New, monospace","size":18,"color":"#7f7f7f "},"anchor":"x2"},"yaxis":{"domain":[0,1],"automargin":true,"title":"y Axis","titlefont":{"family":"Courier New, monospace","size":18,"color":"#7f7f7f "},"anchor":"x"},"annotations":[{"x":"2009-10-01","y":15352,"text":"annotation a","xref":"x","yref":"y","showarrow":true,"arrowhead":7,"ax":20,"ay":-40},{"x":"2010-06-01","y":25.2,"text":"annotation b","xref":"x2","yref":"y2","showarrow":true,"arrowhead":7,"ax":20,"ay":-40}],"shapes":[],"images":[],"margin":{"b":40,"l":60,"t":25,"r":10},"hovermode":"closest","showlegend":true},"attrs":{"c6b5af0c6ca":{"x":{},"y":{},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter","mode":"lines","name":{},"inherit":true},"c6b40e827fb":{"x":{},"y":{},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter","mode":"lines","name":{},"inherit":true}},"source":"A","config":{"showSendToCloud":false},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"subplot":true,"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### 3D Annotations


```r
library(plotly)

fig <- plot_ly()
fig <- fig %>% add_trace(
    x = c("2017-01-01", "2017-02-10", "2017-03-20"), 
    y = c("A", "B", "C"), 
    z = c(1, 1000, 100000), 
    name = "z", 
    type = "scatter3d"
  )
fig <- fig %>% layout(
    scene = list(
      aspectratio = list(
        x = 1,
        y = 1,
        z = 1
      ),
      camera = list(
        center = list(
          x = 0,
          y = 0,
          z = 0
        ),
        eye = list(
          x = 1.96903462608,
          y = -1.09022831971,
          z = 0.405345349304
        ),
        up = list(
          x = 0,
          y = 0,
          z = 1
        )
      ),
      dragmode = "turntable",
      xaxis = list(
        title = "",
        type = "date"
      ),
      yaxis = list(
        title = "",
        type = "category"
      ),
      zaxis = list(
        title = "",
        type = "log"
      ),
      annotations = list(list(
        showarrow = F,
        x = "2017-01-01",
        y = "A",
        z = 0,
        text = "Point 1",
        xanchor = "left",
        xshift = 10,
        opacity = 0.7
      ), list(
        x = "2017-02-10",
        y = "B",
        z = 4,
        text = "Point 2",
        textangle = 0,
        ax = 0,
        ay = -75,
        font = list(
          color = "black",
          size = 12
        ),
        arrowcolor = "black",
        arrowsize = 3,
        arrowwidth = 1,
        arrowhead = 1
      ), list(
        x = "2017-03-20",
        y = "C",
        z = 5,
        ax = 50,
        ay = 0,
        text = "Point 3",
        arrowhead = 1,
        xanchor = "left",
        yanchor = "bottom"
      )
    )),
    xaxis = list(title = "x"),
    yaxis = list(title = "y")
  )

fig
```

<div id="htmlwidget-98f7c86ee14f75b19cc0" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-98f7c86ee14f75b19cc0">{"x":{"visdat":{"c6b3cc3f0a9":["function () ","plotlyVisDat"]},"cur_data":"c6b3cc3f0a9","attrs":{"c6b3cc3f0a9":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"x":["2017-01-01","2017-02-10","2017-03-20"],"y":["A","B","C"],"z":[1,1000,100000],"name":"z","type":"scatter3d","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"scene":{"aspectratio":{"x":1,"y":1,"z":1},"camera":{"center":{"x":0,"y":0,"z":0},"eye":{"x":1.96903462608,"y":-1.09022831971,"z":0.405345349304},"up":{"x":0,"y":0,"z":1}},"dragmode":"turntable","xaxis":{"title":"","type":"date"},"yaxis":{"title":"","type":"category"},"zaxis":{"title":"","type":"log"},"annotations":[{"showarrow":false,"x":"2017-01-01","y":"A","z":0,"text":"Point 1","xanchor":"left","xshift":10,"opacity":0.7},{"x":"2017-02-10","y":"B","z":4,"text":"Point 2","textangle":0,"ax":0,"ay":-75,"font":{"color":"black","size":12},"arrowcolor":"black","arrowsize":3,"arrowwidth":1,"arrowhead":1},{"x":"2017-03-20","y":"C","z":5,"ax":50,"ay":0,"text":"Point 3","arrowhead":1,"xanchor":"left","yanchor":"bottom"}]},"xaxis":{"title":"x","type":"category","categoryorder":"array","categoryarray":["2017-01-01","2017-02-10","2017-03-20"]},"yaxis":{"title":"y","type":"category","categoryorder":"array","categoryarray":["A","B","C"]},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"x":["2017-01-01","2017-02-10","2017-03-20"],"y":["A","B","C"],"z":[1,1000,100000],"name":"z","type":"scatter3d","mode":"markers","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Styling Annotations


```r
library(plotly)

data <- mtcars[which(mtcars$am == 1 & mtcars$gear == 4),]

fig <- plot_ly(data, x = ~wt, y = ~mpg, type = 'scatter', mode = 'markers',
        marker = list(size = 10))
fig <- fig %>% add_annotations(x = data$wt,
                  y = data$mpg,
                  text = rownames(data),
                  xref = "x",
                  yref = "y",
                  showarrow = TRUE,
                  arrowhead = 4,
                  arrowsize = .5,
                  ax = 20,
                  ay = -40,
                  # Styling annotations' text:
                  font = list(color = '#264E86',
                              family = 'sans serif',
                              size = 14))

fig
```

<div id="htmlwidget-aac567232a3a02b8d51f" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-aac567232a3a02b8d51f">{"x":{"visdat":{"c6b1673a7a5":["function () ","plotlyVisDat"]},"cur_data":"c6b1673a7a5","attrs":{"c6b1673a7a5":{"x":{},"y":{},"mode":"markers","marker":{"size":10},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"annotations":[{"text":"Mazda RX4","x":2.62,"y":21,"xref":"x","yref":"y","showarrow":true,"arrowhead":4,"arrowsize":0.5,"ax":20,"ay":-40,"font":{"color":"#264E86","family":"sans serif","size":14}},{"text":"Mazda RX4 Wag","x":2.875,"y":21,"xref":"x","yref":"y","showarrow":true,"arrowhead":4,"arrowsize":0.5,"ax":20,"ay":-40,"font":{"color":"#264E86","family":"sans serif","size":14}},{"text":"Datsun 710","x":2.32,"y":22.8,"xref":"x","yref":"y","showarrow":true,"arrowhead":4,"arrowsize":0.5,"ax":20,"ay":-40,"font":{"color":"#264E86","family":"sans serif","size":14}},{"text":"Fiat 128","x":2.2,"y":32.4,"xref":"x","yref":"y","showarrow":true,"arrowhead":4,"arrowsize":0.5,"ax":20,"ay":-40,"font":{"color":"#264E86","family":"sans serif","size":14}},{"text":"Honda Civic","x":1.615,"y":30.4,"xref":"x","yref":"y","showarrow":true,"arrowhead":4,"arrowsize":0.5,"ax":20,"ay":-40,"font":{"color":"#264E86","family":"sans serif","size":14}},{"text":"Toyota Corolla","x":1.835,"y":33.9,"xref":"x","yref":"y","showarrow":true,"arrowhead":4,"arrowsize":0.5,"ax":20,"ay":-40,"font":{"color":"#264E86","family":"sans serif","size":14}},{"text":"Fiat X1-9","x":1.935,"y":27.3,"xref":"x","yref":"y","showarrow":true,"arrowhead":4,"arrowsize":0.5,"ax":20,"ay":-40,"font":{"color":"#264E86","family":"sans serif","size":14}},{"text":"Volvo 142E","x":2.78,"y":21.4,"xref":"x","yref":"y","showarrow":true,"arrowhead":4,"arrowsize":0.5,"ax":20,"ay":-40,"font":{"color":"#264E86","family":"sans serif","size":14}}],"xaxis":{"domain":[0,1],"automargin":true,"title":"wt"},"yaxis":{"domain":[0,1],"automargin":true,"title":"mpg"},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"x":[2.62,2.875,2.32,2.2,1.615,1.835,1.935,2.78],"y":[21,21,22.8,32.4,30.4,33.9,27.3,21.4],"mode":"markers","marker":{"color":"rgba(31,119,180,1)","size":10,"line":{"color":"rgba(31,119,180,1)"}},"type":"scatter","error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Set Annotation Text Anchors


```r
library(plotly)

fig <- plot_ly()
fig <- fig %>% add_markers(
    x = 1,
    y = 1,
    showlegend = F
  )
fig <- fig %>% add_markers(
    x = 1,
    y = 2,
    showlegend = F
  )
fig <- fig %>% add_markers(
    x = 1,
    y = 3,
    showlegend = F
  )
fig <- fig %>% add_annotations(
    x=1,
    y=1,
    xref = "x",
    yref = "y",
    text = "Right Anchor",
    xanchor = 'right',
    showarrow = F
  )
fig <- fig %>% add_annotations(
    x=1,
    y=2,
    xref = "x",
    yref = "y",
    text = "Center Anchor",
    xanchor = 'center',
    showarrow = F
  )
fig <- fig %>% add_annotations(
    x=1,
    y=3,
    xref = "x",
    yref = "y",
    text = "Left Anchor",
    xanchor = 'left',
    showarrow = F
  )

fig
```

<div id="htmlwidget-f27641632a7395aed208" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-f27641632a7395aed208">{"x":{"visdat":{"c6b499c6ffd":["function () ","plotlyVisDat"]},"cur_data":"c6b499c6ffd","attrs":{"c6b499c6ffd":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"x":1,"y":1,"type":"scatter","mode":"markers","showlegend":false,"inherit":true},"c6b499c6ffd.1":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"x":1,"y":2,"type":"scatter","mode":"markers","showlegend":false,"inherit":true},"c6b499c6ffd.2":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"x":1,"y":3,"type":"scatter","mode":"markers","showlegend":false,"inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"annotations":[{"text":"Right Anchor","x":1,"y":1,"xref":"x","yref":"y","xanchor":"right","showarrow":false},{"text":"Center Anchor","x":1,"y":2,"xref":"x","yref":"y","xanchor":"center","showarrow":false},{"text":"Left Anchor","x":1,"y":3,"xref":"x","yref":"y","xanchor":"left","showarrow":false}],"xaxis":{"domain":[0,1],"automargin":true,"title":[]},"yaxis":{"domain":[0,1],"automargin":true,"title":[]},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"x":[1],"y":[1],"type":"scatter","mode":"markers","showlegend":false,"marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[1],"y":[2],"type":"scatter","mode":"markers","showlegend":false,"marker":{"color":"rgba(255,127,14,1)","line":{"color":"rgba(255,127,14,1)"}},"error_y":{"color":"rgba(255,127,14,1)"},"error_x":{"color":"rgba(255,127,14,1)"},"line":{"color":"rgba(255,127,14,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[1],"y":[3],"type":"scatter","mode":"markers","showlegend":false,"marker":{"color":"rgba(44,160,44,1)","line":{"color":"rgba(44,160,44,1)"}},"error_y":{"color":"rgba(44,160,44,1)"},"error_x":{"color":"rgba(44,160,44,1)"},"line":{"color":"rgba(44,160,44,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
### Customize Displayed Text with a Text Template

To show an arbitrary text in your chart you can use [texttemplate](https://plotly.com/r/reference/#pie-texttemplate), which is a template string used for rendering the information, and will override [textinfo](https://plotly.com/r/reference/#treemap-textinfo).
This template string can include `variables` in %{variable} format, `numbers` in [d3-format's syntax](https://github.com/d3/d3-3.x-api-reference/blob/master/Formatting.md#d3_forma), and `date` in [d3-time-fomrat's syntax](https://github.com/d3/d3-3.x-api-reference/blob/master/Time-Formatting.md#format).
`texttemplate` customizes the text that appears on your plot vs. [hovertemplate](https://plotly.com/r/reference/#pie-hovertemplate) that customizes the tooltip text.


```r
library(plotly)

fig <- plot_ly(
  type='pie',
  values=c(40000000, 20000000, 30000000, 10000000),
  labels=c("Wages", "Operating expenses", "Cost of sales", "Insurance"),
  texttemplate="%{label}: %{value:$,s} <br>(%{percent})",
  textposition="inside")
fig
```

<div id="htmlwidget-1b879659a9609c876d40" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-1b879659a9609c876d40">{"x":{"visdat":{"c6b5f678f2e":["function () ","plotlyVisDat"]},"cur_data":"c6b5f678f2e","attrs":{"c6b5f678f2e":{"values":[40000000,20000000,30000000,10000000],"labels":["Wages","Operating expenses","Cost of sales","Insurance"],"texttemplate":"%{label}: %{value:$,s} <br>(%{percent})","textposition":"inside","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"pie"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"hovermode":"closest","showlegend":true},"source":"A","config":{"showSendToCloud":false},"data":[{"values":[40000000,20000000,30000000,10000000],"labels":["Wages","Operating expenses","Cost of sales","Insurance"],"texttemplate":["%{label}: %{value:$,s} <br>(%{percent})","%{label}: %{value:$,s} <br>(%{percent})","%{label}: %{value:$,s} <br>(%{percent})","%{label}: %{value:$,s} <br>(%{percent})"],"textposition":["inside","inside","inside","inside"],"type":"pie","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(255,255,255,1)"}},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Customize Text Template

The following example uses [textfont](https://plotly.com/r/reference/#scatterternary-textfont) to customize the added text.


```r
library(plotly)

fig <- plot_ly(
  type='scatterternary',
  a = c(3, 2, 5),
  b = c(2, 5, 2),
  c = c(5, 2, 2),
  mode = "markers+text",
  text = c("A", "B", "C"),
  texttemplate = "%{text}<br>(%{a:.2f}, %{b:.2f}, %{c:.2f})",
  textposition = "bottom center",
  textfont = list(family= "Times", size= c(18, 21, 20), color= c("IndianRed", "MediumPurple", "DarkOrange"))
)
fig
```

<div id="htmlwidget-f1d35fdfa35a3bc266d3" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-f1d35fdfa35a3bc266d3">{"x":{"visdat":{"c6b2ee26a13":["function () ","plotlyVisDat"]},"cur_data":"c6b2ee26a13","attrs":{"c6b2ee26a13":{"a":[3,2,5],"b":[2,5,2],"c":[5,2,2],"mode":"markers+text","text":["A","B","C"],"texttemplate":"%{text}<br>(%{a:.2f}, %{b:.2f}, %{c:.2f})","textposition":"bottom center","textfont":{"family":"Times","size":[18,21,20],"color":["IndianRed","MediumPurple","DarkOrange"]},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterternary"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"a":[3,2,5],"b":[2,5,2],"c":[5,2,2],"mode":"markers+text","text":["A","B","C"],"texttemplate":["%{text}<br>(%{a:.2f}, %{b:.2f}, %{c:.2f})","%{text}<br>(%{a:.2f}, %{b:.2f}, %{c:.2f})","%{text}<br>(%{a:.2f}, %{b:.2f}, %{c:.2f})"],"textposition":["bottom center","bottom center","bottom center"],"textfont":{"family":"Times","size":[18,21,20],"color":["IndianRed","MediumPurple","DarkOrange"]},"type":"scatterternary","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"line":{"color":"rgba(31,119,180,1)"},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
### Set Date in Text Template

The following example shows how to show date by setting [axis.type](https://plotly.com/r/reference/#layout-yaxis-type) in [funnel charts](https://plotly.com/r/funnel-charts/).
As you can see [textinfo](https://plotly.com/r/reference/#funnel-textinfo) and [texttemplate](https://plotly.com/r/reference/#funnel-texttemplate) have the same functionality when you want to determine 'just' the trace information on the graph.


```r
fig <- plot_ly()

fig <- fig %>% add_trace(
  type='funnel',
  name = 'Montreal',
  orientation = "h",
  y = c("2018-01-01", "2018-07-01", "2019-01-01", "2020-01-01"),
  x = c(100, 60, 40, 20),
  textposition = "inside",
  texttemplate = "%{y| %a. %_d %b %Y}")

fig <- fig %>% add_trace(
  type='funnel',
  name = 'Vancouver',
  orientation = "h",
  y = c("2018-01-01", "2018-07-01", "2019-01-01", "2020-01-01"),
  x = c(90, 70, 50, 10),
  textposition = "inside",
  textinfo = "label")

fig <- fig %>% layout(yaxis = list(type= 'date'))
fig
```

<div id="htmlwidget-9bb169f92782883f4619" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-9bb169f92782883f4619">{"x":{"visdat":{"c6b1359ce57":["function () ","plotlyVisDat"]},"cur_data":"c6b1359ce57","attrs":{"c6b1359ce57":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"funnel","name":"Montreal","orientation":"h","y":["2018-01-01","2018-07-01","2019-01-01","2020-01-01"],"x":[100,60,40,20],"textposition":"inside","texttemplate":"%{y| %a. %_d %b %Y}","inherit":true},"c6b1359ce57.1":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"funnel","name":"Vancouver","orientation":"h","y":["2018-01-01","2018-07-01","2019-01-01","2020-01-01"],"x":[90,70,50,10],"textposition":"inside","textinfo":"label","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"yaxis":{"domain":[0,1],"automargin":true,"type":"date","title":[],"categoryorder":"array","categoryarray":["2018-01-01","2018-07-01","2019-01-01","2020-01-01"]},"xaxis":{"domain":[0,1],"automargin":true,"title":[]},"hovermode":"closest","showlegend":true},"source":"A","config":{"showSendToCloud":false},"data":[{"type":"funnel","name":"Montreal","orientation":"h","y":["2018-01-01","2018-07-01","2019-01-01","2020-01-01"],"x":[100,60,40,20],"textposition":["inside","inside","inside","inside"],"texttemplate":["%{y| %a. %_d %b %Y}","%{y| %a. %_d %b %Y}","%{y| %a. %_d %b %Y}","%{y| %a. %_d %b %Y}"],"marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"xaxis":"x","yaxis":"y","frame":null},{"type":"funnel","name":"Vancouver","orientation":"h","y":["2018-01-01","2018-07-01","2019-01-01","2020-01-01"],"x":[90,70,50,10],"textposition":["inside","inside","inside","inside"],"textinfo":"label","marker":{"color":"rgba(255,127,14,1)","line":{"color":"rgba(255,127,14,1)"}},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
### Set Annotation Coordinate References


```r
library(plotly)

fig <- plot_ly()
fig <- fig %>% add_markers(
    x = 0.5,
    y = 1,
    showlegend = F
  )
fig <- fig %>% add_annotations(
    x= 0.5,
    y= 1,
    xref = "paper",
    yref = "paper",
    text = "<b>paper reference = [0.5, 1]</b>",
    showarrow = F
  )
fig <- fig %>% add_annotations(
    x= 0.5,
    y= 1,
    xref = "x",
    yref = "y",
    text = "x + y reference = [0.5, 1]",
    showarrow = T,
    ax = 20,
    ay = -40
  )
fig <- fig %>% layout(
    xaxis = list(zeroline = F),
    yaxis = list(zeroline = F)
  )

fig
```

<div id="htmlwidget-4c1e7729cc5c8c10c436" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-4c1e7729cc5c8c10c436">{"x":{"visdat":{"c6b1f6aeb4f":["function () ","plotlyVisDat"]},"cur_data":"c6b1f6aeb4f","attrs":{"c6b1f6aeb4f":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"x":0.5,"y":1,"type":"scatter","mode":"markers","showlegend":false,"inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"annotations":[{"text":"<b>paper reference = [0.5, 1]<\/b>","x":0.5,"y":1,"xref":"paper","yref":"paper","showarrow":false},{"text":"x + y reference = [0.5, 1]","x":0.5,"y":1,"xref":"x","yref":"y","showarrow":true,"ax":20,"ay":-40}],"xaxis":{"domain":[0,1],"automargin":true,"zeroline":false,"title":[]},"yaxis":{"domain":[0,1],"automargin":true,"zeroline":false,"title":[]},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"x":[0.5],"y":[1],"type":"scatter","mode":"markers","showlegend":false,"marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

#Reference

See [https://plotly.com/r/reference/#layout-annotations](https://plotly.com/r/reference/#layout-annotations) for more information and chart attribute options!
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
