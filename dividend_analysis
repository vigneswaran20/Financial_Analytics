library(tidyverse)
library(tidyquant)
library(janitor)
library(plotly)
library(ggstatsplot)
library(gganimate)
library(gifski)
library(png)


##---------------------------

barrons_tickers <- 
  c("SUNPHARMA.NS", "DIVISLAB.NS", "CIPLA.NS","DRREDDY.NS")

#Getting Dividends
barrons_dividends <- 
  barrons_tickers %>% 
  tq_get(get = "dividends")

head(barrons_dividends)

#Help file
??tq_get

#What data can we get
#1... "stock.prices"
#2... "dividends"
#3...  "splits"



  myanimate <-barrons_dividends %>% 
    group_by(symbol) %>%
    ggplot(aes(x = date, 
               y = value, 
               color = symbol)) + 
    geom_point(size = 5) + scale_y_continuous(labels = function(x) paste0(x, " rs.")) +
    scale_x_date(breaks = scales::pretty_breaks(n = 5)) +
    labs(x = "", y = "div/share", title = "Pharma dividends - vigneswaran.E.R", caption = "vigneswaran.E.R") +
    theme(plot.title = element_text(hjust = 0.5)) + theme_ggstatsplot() + 
    transition_reveal(date)

  animate(myanimate, height = 500, width =700)
  
  ###---------------------------------------------
  
  
