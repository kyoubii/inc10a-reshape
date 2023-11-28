# inc10a-reshape
------
title: "Reshape"
author: "Michelle Kim"
date: "2023-11-28"
output:html_document
----
library(tidyverse)



gdp <- read.delim("oecd-gdp.csv")
gdp %>%
  head(7)

gdpLong <-
  gdp %>%
  pivot_longer(!c(country, indicator),
              names_to = "year",
              values_to = "gdp") %>%
    mutate(year = as.numeric(year)) ##doesn't work at the moment because x character is in year
gdpLong %>%
  head(10)
  
p <- data.frame(pregnant = c("Yes", "No"),
            	male = c(NA, 25),
            	female = c(11, 18))
p

pl <- p %>%
  pivot_longer(c(male, female),
              names_to = "sex",
              values_to = "count")
pl

pl %>%
  pivot_wider(id_cols = pregnant, 
              names_from = sex, 
              values_from = count)
              