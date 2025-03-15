---
layout: default
title: "League of Legends Role Impact Statistical Analysis"
---

# League of Legends Role Impact Statistical Analysis

League of Legends Role Impact Analysis is a data science project conducted at UCSD. The project includes exploratory data analysis, data cleaning, an analysis of missingness on the dataset, hypothesis testing, a baseline model, final model, and a fairness analysis.

---

## Introduction

### General Introduction and Purpose

League of Legends is a popular online multiplayer video game created by Riot Games, featuring one of the largest esports scenes for over a decade. The dataset used in this project is a professional dataset developed by Oracle’s Elixir from professional League of Legends esports matches throughout 2025.

This dataset includes a wide variety of statistics from the matches played, making it useful for examining player tendencies, team interactions, and game results. It includes details on individual performance, strategic decisions, in-game metrics, and overall match progression.

In any given match, there are two teams that go against each other (red side and blue side), each team has 5 members, and each member is assigned to a specific role which they play throughout the game. The roles include top lane, jungle, mid lane, bot lane, and support. A key topic debated within League of Legends and its community is the balancing of these 5 roles. In other words, community members debate the impact of each role on the game's outcome and whether it is equal or not.

The question I'm aiming to explore is: **Which role in League of Legends has the greatest impact on game outcomes?** To answer this, I'll apply data analysis techniques to evaluate each role by examining key in-game metrics such as early gold and XP advantages, damage dealt by players, and kill participation.

By analyzing these factors, we seek to determine whether there is a singular role that has a greater impact on match results than other positions. Additionally, we aim to explore the extent to which early-game advantages translate into victories and whether certain statistical patterns about each role can be leveraged to predict game outcomes. This analysis allows for the ability to further understand the impact of roles and their contribution to the final result.

---

## Introduction of Columns

The dataset contains 19,068 rows and 161 columns featuring various statistical outcomes from professional matches. While each column provides key intel on gameplay, here are the columns relevant to our central question:

- **gameid**: A distinct label assigned to each match played.
- **side**: Represents the team affiliation of each player or team—red or blue.
- **position**: The role of each individual player within their team—top, mid, jng (for jungler), bot, sup, or team for team rows.
- **gamelength**: The length of each match played.
- **result**: The outcome of a match for a team or player—1 representing a win and 0 representing a loss.
- **kills**: The total number of enemy champions a player eliminates.
- **deaths**: The number of times each player is eliminated by an enemy champion.
- **assists**: The number of instances where a player helped an ally teammate eliminate an enemy champion without killing them.
- **damagetochampions**: The total amount of damage a player or team deals within a game.
- **visionscore**: Measures how effectively a player controls vision on the map by counting actions such as placing wards, clearing enemy wards, and revealing hidden areas.
- **golddiffat15**: The gold difference at 15 minutes between a player in a specific role and their corresponding opponent in the same role or team.
- **xpdiffat15**: The XP difference at 15 minutes between a player in a specific role and their corresponding opponent in the same role or team.

---

## Data Cleaning and Exploratory Data Analysis

### Data Cleaning

For simplicity, let's only keep the relevant columns introduced in the introduction. Each game completes **12 rows** in the dataset—**5 for each member of each team**, and the remaining **2** containing gameplay metrics of each team, different from individual players. For future analysis, I will mainly include **player rows only**, since many of the team rows are sums of the player roles, so they would just be repeated information. This **cleaned dataframe** will be used in our hypothesis testing and prediction model.

While the dataset included columns such as `goldat10`, `xpat10` for each feature up to **25 minutes** into the game, I chose to analyze data at the **15-minute mark** because the **average game length** was approximately **19 minutes and 39 seconds (19:39)**. Using multiple timestamps would introduce **redundancy**, and analyzing metrics at later points—such as **20 or 25 minutes**—would not be meaningful, given that many matches **end before reaching those times**.

Below is the head of the dataframe `df_cleaned`.

---

## Univariate Analysis

Here are some **univariate analyses** on features within the dataset:

### Gold at 15 Minutes
[Gold at 15 Minutes Histogram](assets/graphs/goldat15_histogram.html)
  *Description*

- [`damage_barchart.html`](damage_barchart.html)  
  *Description*

---

## Bivariate Analysis

Here are some **bivariate analyses** on features within the dataset.

I performed **bivariate analysis** on the **gold difference of winners and losers**:

- [`golddiff_outcome_boxplot.html`](golddiff_outcome_boxplot.html)  
  *Description*

---

## Hypothesis Testin