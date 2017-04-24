---
title: "Untitled"
author: ""
date: ""
output: 
  html_document:
    fig_height: 5
    fig_width: 8
---
<!-- Don't edit in between this line and the one below -->
```{r include=FALSE}
# Don't delete this chunk if you are using the DataComputing package
library(DataComputing)
```
*Source file* 
```{r, results='asis', echo=FALSE}
includeSourceDocuments()
```
<!-- Don't edit the material above this line -->


```{r}
s133df <- read.csv('C:/Users/Shiva/Downloads/annual_all_2016/annual_all_2016.csv')
head(s133df,200)
s133df2 <- s133df %>% filter(Parameter.Name == "Ozone") %>% filter(Metric.Used == "Daily maxima of observed hourly values (between 9:00 AM and 8:00 PM)") %>% filter(State.Name == "California")
head(s133df2,20)
map<-ggmap::get_map(location='bay area', zoom=6, maptype = "terrain",
             source='google',color='color')
ggmap(map) + geom_point(aes(x = Longitude, y = Latitude, size = 0.1, col=sqrt(Arithmetic.Mean)), data = s133df2, alpha = 1)
```

