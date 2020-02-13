---
title: "Lab Crossover Event"
author: "Daniel Fuller"
date: "11/02/2020"
output:
  slidy_presentation: default
  ioslides_presentation: default
  beamer_presentation: default
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = FALSE)
```

## R: The Swiss Army Knife of Science

- The R project for statistical computing is a free open source statistical programming language and project. Follow these steps to get started. 
- The main advantages of R are the fact that R is freeware and that there is a lot of help available online.

## Why use R?

- Strengths
    - free and open source, supported by a strong user community
    - highly extensible and flexible
    - implementation of modern statistical methods
    - assists with replication and extension of your work
- Weaknesses
    - slow with very large data sets (>1GB)
    - non-standard programming paradigms

## Why use R?

- RStudio is the primary Integrated Develop Environment (IDE) for R
- We will be using RStudio for the tutorial 

## RStudio IDE

#![](create_new_content.gif)

## Packages/Libraries

- Packages are the main R tools
- There are 15388 packages. It's probable that if you have thought about the analysis, there is a package that is able to do it already. There are two basic steps to using a package:

`Installing the package install.packages("tidyverse")`

`Loading the package library(tidyverse)`

## Packages/Libraries

- Packages include functions that do things. 

data <- `read_csv`("/The/Path/To/Your/File.csv")   

- `data` = where you want to save the data
- `<-` = tell the function where to put the output
- `read_csv` = the name of the function
- `()` = what you input into the function

## Doing simple things in R


```{r}
2+2

a <- 2+2

a + a
```

## Reading in some data

```{r}
library(readr)

# data <- read_excel("/Your/File/Path/data.xls⁩")

#nl_candidates <- read_csv("nl_candidates.csv")

nl_candidates <- read_csv("https://github.com/walkabillylab/lab_crossover_r/raw/master/nl_candidates.csv")
```

## Some quick descriptive statistics

```{r}
nl_candidates$`Number of Votes Obtained` <- as.numeric(nl_candidates$`Number of Votes Obtained`)

summary(nl_candidates$`Number of Votes Obtained`)
```

## Recoding a variable

```{r}
library(tidyverse)
nl_candidates <- nl_candidates %>%
                    mutate(sex = case_when(
                            Sex == 1 ~ "Male",
                            Sex == 2 ~ "Female"))
```

## Recoding a variable
```{r}
ggplot(nl_candidates, aes(sex, `Number of Votes Obtained`, fill = sex)) + 
        geom_boxplot() +  
        theme_classic()
```


## The great R wars

Two similar but different methods for many common tasks  

- [Tidyverse](https://www.tidyverse.org/)
- [Base R](https://tavareshugo.github.io/data_carpentry_extras/base-r_tidyverse_equivalents/base-r_tidyverse_equivalents.html)

## Where to find packages

- [CRAN Task View](https://cran.r-project.org/web/views/)
- [META Cran](https://www.r-pkg.org/)
- Follow prominent voices
    - [JennyBryan](https://twitter.com/JennyBryan)
    - [Hadley Wickham](https://twitter.com/hadleywickham)
    - [Amelia MN](https://twitter.com/AmeliaMN)
    
## Ocean Plastic Sciences

- [`marelac`](https://cran.r-project.org/web/packages/marelac/index.html)
- [`oce`](https://cran.r-project.org/web/packages/oce/)

## Political Sciences

- [http://m-clark.github.io/docs/RSocialScience.pdf](http://m-clark.github.io/docs/RSocialScience.pdf)
- Twitter Sentiment Analysis
    - [https://dataaspirant.com/2018/03/22/twitter-sentiment-analysis-using-r/](https://dataaspirant.com/2018/03/22/twitter-sentiment-analysis-using-r/)

## Workflow Revolution

- RStudio + [Github](https://happygitwithr.com/)
    - [https://github.com/TeamINTERACT/onboarding](https://github.com/TeamINTERACT/onboarding)
- Full Scientific Paper with R and RMarkdown
    - [Example1](https://libscie.github.io/rmarkdown-workshop/handout.html)
    - [Example2](https://daijiang.name/en/2017/04/05/writing-academic-papers-with-rmarkdown/)


