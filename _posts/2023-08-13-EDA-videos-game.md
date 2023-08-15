---
title: "Analyze on video game - explore patterns and insights"
date: 2022-08-13
categories: [blog]
tags: ['Data Analyst', 'Data Insight', 'EDA']
---

# Well... actually, what are we doing now?
Last month I found a dataset on kaggle, this dataset provides a wealth of information about each game, including its title, release date, genre, platform(s), summary, among other data. That is enought for entry level like me to do some analyze. you can find it here =>
<a href="https://www.kaggle.com/datasets/matheusfonsecachaves/popular-video-games">video game dataset</a>


Something about this dataset
- Over 60.000 row that cotain data about game that release since 1980 up to now
- This data collect by scrap the data on game analyze game platform call Backloggd
- The data was collected in June 2023

That how the data set look like:

    title: Title of the game

    releaseDate: Release date of the game

    developers: Companies/Developers of the game

    summary: Summary of the game

    gamePlatforms: Platforms of the game

    gameGenres: Game genres

    gameRating - Rating of the game from 0 to 5

    number_of_reviews: Number of user reviews about the game

    number_of_play - Number of plays that the game has

    number_of_player - Number of people playing the game

    backlogs - Number of people who own the game but haven't played it

    wishlist - Number of times the game has been wishlisted

    lists - Number of times the game has been mentioned in a game list

We will use R to process the data and drawing chart using ggplot2. 

Let's do it


## Clean data

Do some basic query

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
## Wishlist and Lists:

Investigate if games with higher wishlist counts or mentions in game lists tend to have better ratings or more plays.
## Rating vs. Engagement:

Examine if there's a correlation between game ratings and player engagement (plays, players, backlogs).
## Trends Over Time:

Observe how player engagement, wishlist counts, and other metrics change over time, potentially reflecting changes in gaming trends.

# Conclution

Thanks for your reading!