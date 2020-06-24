---
layout: page
title: My Research
permalink: /my_research/
---


# Here are examples of my work.

[Visualization of Twitter data on the 2020 AP Exams](AP_exam_wordcloud.pdf)

![Graphic of number of tweets written by Seattle Mayor Jenny Durkan](Mayor_Jenny_Tweets.pdf)


We see here spikes in the number of tweets based on the response to the Floyd death as well as a Twitter spat with the President regarding the Capitol Hill Autonomous Zone.

# Texas Tax Revenue changes
```{r Texas}
##Visualising Sales Tax data

###########################################################
##INSTALL DEPENDENCIES & PACKAGES
###########################################################

preload <- function(x)
{
  as.character(x)
  if (!require(x,character.only = T))
  {
    install.packages(pkgs=x, repos="http://cran.r-project.org")
    require(x,character.only=T)
  }
}

preload("haven")
preload("ggplot2")
preload("ggmap")
preload("maps")
preload("mapdata")
preload("leaflet")
preload("usmap")
preload("dplyr")

############################################################
##load data


mst <- as.data.frame(read_dta("mean_sales_tax.dta"))
View(mst)

##subset into the various years

X <- subset(mst, Year==2013)
Y <- subset(mst, Year==2014)
Z <- subset(mst, Year==2015)
A <- subset(mst, Year==2016)
B <- subset(mst, Year==2017)
C <- subset(mst, Year==2018)
D <- subset(mst, Year==2019)
E <- subset(mst, Year==2020)


##create a map for each year

#2013
plot_usmap(data = X, values = "PercentChangeFromPriorYear", include = c("TX"), regions = "counties", color = "black") + 
  scale_fill_continuous(low = "white", high = "blue", name = "2013") + 
  labs(title = "Percentage change in Tax Revenue") +
  theme(legend.position = "right")

#2014
plot_usmap(data = Y, values = "PercentChangeFromPriorYear", include = c("TX"), regions = "counties", color = "black") + 
  scale_fill_continuous(low = "white", high = "blue", name = "2014", label = scales::comma) + 
  labs(title = "Percentage change in Tax Revenue") +
  theme(legend.position = "right")

#2015
plot_usmap(data = Z, values = "PercentChangeFromPriorYear", include = c("TX"), regions = "counties", color = "black") + 
  scale_fill_continuous(low = "white", high = "blue", name = "2015", label = scales::comma) +
  labs(title = "Percentage change in Tax Revenue") +
  theme(legend.position = "right")

#2016
plot_usmap(data = A, values = "PercentChangeFromPriorYear", include = c("TX"), regions = "counties", color = "black") + 
  scale_fill_continuous(low = "white", high = "blue", name = "2016", label = scales::comma) + 
  labs(title = "Percentage change in Tax Revenue") +
  theme(legend.position = "right")

#2017
plot_usmap(data = B, values = "PercentChangeFromPriorYear", include = c("TX"), regions = "counties", color = "black") + 
  scale_fill_continuous(low = "white", high = "blue", name = "2017", label = scales::comma) + 
  labs(title = "Percentage change in Tax Revenue") +
  theme(legend.position = "right")

#2018
plot_usmap(data = C, values = "PercentChangeFromPriorYear", include = c("TX"), regions = "counties", color = "black") + 
  scale_fill_continuous(low = "white", high = "blue", name = "2018", label = scales::comma) + 
  labs(title = "Percentage change in Tax Revenue") +
  theme(legend.position = "right")

#2019
plot_usmap(data = D, values = "PercentChangeFromPriorYear", include = c("TX"), regions = "counties", color = "black") + 
  scale_fill_continuous(low = "white", high = "blue", name = "2019", label = scales::comma) + 
  labs(title = "Percentage change in Tax Revenue") +
  theme(legend.position = "right")

#2020
plot_usmap(data = E, values = "PercentChangeFromPriorYear", include = c("TX"), regions = "counties", color = "black") + 
  scale_fill_continuous(low = "white", high = "blue", name = "2020", label = scales::comma) + 
  labs(title = "Percentage change in Tax Revenue") +
  theme(legend.position = "right")
```

