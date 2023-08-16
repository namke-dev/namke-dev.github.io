---
title: "Video games 👾👾 (1980 - July 2023) - Explore Data Insights"
date: 2022-08-13
categories: [blog]
tags: ['Data Analyst', 'Data Insight', 'EDA']
---

# Well... actually, what will we do?
Last month I found a dataset on kaggle, this dataset provides a wealth of information about each game, including its title, release date, genre, platform(s), summary, among other data. That is enought for entry level like me to do some analyze. you can find it here -
<a href="https://www.kaggle.com/datasets/matheusfonsecachaves/popular-video-games">video game dataset</a>

We'll engage with this data set and dive to the bottom of it to find data insight. In this data set I'ss devive to 3 part so you can follow easylly.  
1. Overiew and clean data
2. Finding collation between factors
3. Visual trend change overtime


Something about this dataset
- Over 60.000 row that cotain data about game that release since 1980 up to now
- This data collect by scrap the data on game analyze game platform call Backloggd
- The data was collected in June 2023
- That how the data set look like:
```
title:             Title of the game  
releaseDate:       Release date of the game  
developers:        Companies/Developers of the game  
summary:           Summary of the game  
gamePlatforms:     Platforms of the game  
gameGenres:        Game genres  
gameRating:        Rating of the game from 0 to 5  
number_of_reviews: Number of user reviews about the game  
number_of_play:    Number of plays that the game has  
number_of_player:  Number of people playing the game  
backlogs:          Number of people who own the game but haven't played it  
wishlist:          Number of times the game has been wishlisted  
lists:             Number of times the game has been mentioned in a game list
```

# Let's do it

### Repared tool: We will use R to process the data and drawing chart. 

## 1. Clean data
```R
#install package
install.packages("tidyverse")
install.packages("janitor")

#import library
library(tidyverse)
library(dplyr)
library(tidyr)
library(janitor)

#read input from file
input_df = read.csv("C:/Users/Namng/Downloads/Documents/Statistic-project/backloggd_games.csv")

#clean data frame
input_df <- clean_data_frame(input_df)

#Remove unnecessary column
input_df <-input_df %>% select(-c(summary))

#Rename column
input_df <- input_df %>% rename("id" = "x")

#convert data type
input_df$rating <- convert_units(input_df$rating)
input_df$plays <- convert_units(input_df$plays)
input_df$playing <- convert_units(input_df$playing)
input_df$backlogs <- convert_units(input_df$backlogs)
input_df$wishlist <- convert_units(input_df$wishlist)
input_df$lists <- convert_units(input_df$lists)
input_df$reviews <- convert_units(input_df$reviews)

#rename column
```
The function using above
```R
#function
clean_data_frame <- function(input_df){
  #Rename column
  input_df <- clean_names(input_df)
  colnames(input_df)
  
  #Remove empty rows and column
  input_df<- input_df %>% remove_empty(whic=c("rows"))
  input_df<- input_df%>% remove_empty(whic=c("cols"))
  
  #Check duplicate rows
  duplicate_rows <- get_dupes(input_df)
  print(duplicate_rows)
  
  #remove duplicate rows (not handle)
  return(input_df)
}

convert_units <- function(x) {
  if (is.null(x)) return(0)
  if (class(x) == "numeric") return(x)
  
  # named vector of scaling (you can add to this)
  unit_scale <- c("k" = 1e3, "m" = 1e6)
  
  # clean up some potential nuisances with the input
  x_str <- gsub(",", "", trimws(tolower(as.character(x))))
  
  # extract out the letters
  unit_char <- gsub("[^a-z]", "", x_str)
  
  # check if unit_char is empty
  if (length(unit_char) == 0) return(as.numeric(x_str))
  
  # extract out the numbers and convert to numeric
  x_num <- as.numeric(gsub("[^0-9.]", "", x_str))
  
  # develop a vector of multipliers
  multiplier <- unit_scale[match(unit_char, names(unit_scale))]
  multiplier[is.na(multiplier)] <- 1
  
  # multiply
  x_num * multiplier
}
```

## The result

## Do some basic query



## Genre and Rating Correlation:

Explore whether certain genres tend to have higher ratings or if there's a correlation between specific genres and higher/lower ratings.
## Release Date Trends:

Analyze if there's a relationship between release dates and game ratings or popularity. Are games released in certain months more likely to perform well?
## Developer Impact:

Investigate whether games developed by specific companies tend to have higher ratings, more plays, or better engagement.
## Platform Preferences:

Determine which platforms are most popular and assess if there's a correlation between platform choice and factors like rating, plays, or wishlist count.
## Player Engagement:

Examine the relationship between the number of plays, players, backlogs, and wishlist counts. Are games with high engagement more likely to have a larger player base?
## Genre Popularity:

Identify the most popular game genres based on plays, ratings, and other metrics. Do certain genres consistently perform better than others?

## Rating vs. Engagement:

Examine if there's a correlation between game ratings and player engagement (plays, players, backlogs).
## Trends Over Time:

Observe how player engagement, wishlist counts, and other metrics change over time, potentially reflecting changes in gaming trends.

# Conclution

Thanks for your reading!