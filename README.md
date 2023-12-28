
# NBA Stats 1996-2021

## Authors

- [@leonemma](https://github.com/leonemma)

## Contents  
- ['Introduction'](#Introduction)
- ['Installation'](#Installation)
- ['Usage'](#Usage)
- ['Feature Explanation'](#FeatureExplanation)

## Introduction

In this project, we will conduct Exploratory Data Analysis (EDA) on NBA statistics spanning the seasons from 1996 through 2021. Our focus will be on identifying and exploring the standout players in the NBA during this period.

This project utilizes the following dataset:

1. **NBA Player Stats (1996-2021):**
   - The data set contains over two decades of data on each player who has been part of an NBA teams' roster.
   - Source: [NBA Players Stats on Kaggle](https://www.kaggle.com/datasets/justinas/nba-players-data)



## Installation

To install NBA-Stats-1996-2021, follow these steps:

1. Clone the repository:
   ```bash
   git clone https://github.com/leonemma/NBA-stats-1996-2021.git
cd NBA-Stats-1996-2021

## Usage

Once you have successfully installed NBA-Stats-1996-2021, you can use the following steps to interact with the project:

1. **Run the main Jupyter notebook:**
   ```bash
   jupyter notebook NBA players stats.ipynb

## Feature Explanation
This dataset contains 22 columns and 12844 observations.

- Unnamed 0: - 
- player_name : Name of the player  
- team_abbreviation : Name of the team the   player played for (at the end of the season)       
- age : Age of the player  
- player_height : Height of the player  
- player_weight : Weight of the player  
- college : Name of the college of the player attended  
- country : Name of the country the player was born in  
- draft_year : The year the player was drafted  
- draft_round : The draft round the player was picked  
- draft_number : The number at which the player was drafted in his draft round  
- gp : Games played throughout the season  
- pts : Average number of points scored  
- reb : Average number of rebounds grabbed  
- ast : Average number of assists distributed  
- net_rating : Team's point differential per 100 possessions while the player is on the court  
- oreb_pct : Percentage of available offensive rebounds the player grabbed while he was on the floor  
- dreb_pct : Percentage of available defensive rebounds the player grabbed while he was on the floor  
- usg_pct : Percentage of team plays used by the player while he was on the floor (FGA + Possession Ending FTA + TO) / POSS)  
- ts_pct : Measure of the player's shooting efficiency that takes into account free throws, 2 and 3 point shots (PTS / (2*(FGA + 0.44 FTA))  
- ast_pct : Percentage of teammate field goals the player assisted while he was on the floor  
- season : NBA season



## Data Cleaning
This dataset contains some individual players multiple times due to the collection of their statistics every year. Initially, we are going to analyze the NBA over the years, and secondly transform the dataset to represent NBA player statistics in a way that each player exists in the dataset only once.

#### The dataset does not contain any null values.  

- At first we are going to remove the first column 'Unnamed: 0'.    
- Secondly,we are going to turn the 'draft_round' and 'draft_number' features into numeric.Hence,we replace the value Undrafted that represents the undrafted players with the number 0.Therefore when the value is 0 in these features it means that this player was undrafted.
```python
df.drop('Unnamed: 0', axis = 1, inplace = True)

df['draft_round'] = df['draft_round'].replace('Undrafted', 0)
df['draft_number'] = df['draft_number'].replace('Undrafted', 0)
df['draft_round'] = df['draft_round'].astype(int)
df['draft_number'] = df['draft_number'].astype(int)
 ```
  
## Key Questions

- These questions will guide our exploration and uncover insights into the dynamics of NBA players's performance over the years.  

### 1. Total Number of NBA Players
- **Question:** What's the total number of NBA players over the years?
### 2. Trends in Average Points
- **Question:** Does the average points of NBA players exhibit a trend over the years?
### 3. Average Rebounds and Assists
- **Question:** How do the average rebounds and assists of NBA players change over the years?
### 4. Changes in Maximum Points per Game
- **Question:** How does the Maximum Points per Game change over the years?
### 5. Best Playmaking Seasons
- **Question:** Which NBA players had/have the best seasons in playmaking in the last 25 years?
### 6. Best Scoring Seasons
- **Question:** Which NBA players had/have the best scoring seasons in the last 25 years?
### 7. Consistent All-Star Level Players
- **Question:** How many NBA players performed at an All-Star level consistently?
### 8. Most Dominant Players
- **Question:** Who /were/are the most dominant players in the last 25 years?
### 9. Best Playmakers and Scorers
- **Question:** Who were/are the best playmakers and scorers in the last 25 years? 
### 10. Highest Shooting Performance
- **Question:** Which NBA players had/have the highest true shooting season?
### 11. Most Impactful Players
- **Question:** Which players had/have the most impactful contributions to their teams?

## Exploring the Features

![Histograms of Numeric Variables](/plots/1plot.png)
```python
                age  player_height  player_weight   draft_round  draft_number  
count  12844.000000   12844.000000   12844.000000  12844.000000  12844.000000   
mean      27.045313     200.555097     100.263279      1.059172     17.774914   
std        4.339211       9.111090      12.426628      0.683223     16.803276   
min       18.000000     160.020000      60.327736      0.000000      0.000000   
25%       24.000000     193.040000      90.718400      1.000000      3.000000   
50%       26.000000     200.660000      99.790240      1.000000     14.000000   
75%       30.000000     208.280000     108.862080      1.000000     29.000000   
max       44.000000     231.140000     163.293120      8.000000    165.000000   

                 gp           pts           reb           ast    net_rating  
count  12844.000000  12844.000000  12844.000000  12844.000000  12844.000000   
mean      51.154158      8.212582      3.558486      1.824681     -2.226339   
std       25.084904      6.016573      2.477885      1.800840     12.665124   
min        1.000000      0.000000      0.000000      0.000000   -250.000000   
25%       31.000000      3.600000      1.800000      0.600000     -6.400000   
50%       57.000000      6.700000      3.000000      1.200000     -1.300000   
75%       73.000000     11.500000      4.700000      2.400000      3.200000   
max       85.000000     36.100000     16.300000     11.700000    300.000000   

           oreb_pct      dreb_pct       usg_pct        ts_pct       ast_pct  
count  12844.000000  12844.000000  12844.000000  12844.000000  12844.000000  
mean       0.054073      0.140646      0.184641      0.513138      0.131595  
std        0.043335      0.062513      0.053545      0.101724      0.094172  
min        0.000000      0.000000      0.000000      0.000000      0.000000  
25%        0.021000      0.096000      0.149000      0.482000      0.066000  
50%        0.040000      0.130500      0.181000      0.525000      0.103000  
75%        0.083000      0.179000      0.217000      0.563000      0.179000  
max        1.000000      1.000000      1.000000      1.500000      1.000000  
```

### Correlation Matrix

![Correlation Matrix](/plots/2plot.png)  

- There exists a robust positive relationship between the height and weight of players, confirming our initial expectations
- "Evidently, player height exhibits a positive correlation with various rebounding metrics, including total rebounds ('reb'), offensive rebound percentage ('oreb_pct'), and defensive rebound percentage ('dreb_pct'). This implies that, on average, taller players tend to secure more rebounds
- Interestingly, there is a negative correlation between a player's height and assist percentage. This suggests that assist percentage serves as a noteworthy metric for guards, who typically have shorter statures and are more involved in playmaking.
- "The scoring variable ('pts') demonstrates positive correlations with both rebounding and passing metrics. Players who contribute significantly to scoring are likely to excel in rebounding and passing as well.
  
## Feature Engineering
- The 'country' feature encompasses numerous values. To enhance simplicity, we will transform this variable into a binary distinction, categorizing values as either 'USA' or 'Other.' This reduction aims to streamline the analysis by consolidating the diverse country values into a more manageable binary representation.
 ```python
df['country'] = np.where(df['country'] != 'USA', 'Other','USA')
 ```
-  We create a new column that is the total seasons a player had been playing in the NBA
 ```python
df['SeasonsPlayed'] = df.groupby('player_name')['season'].transform('nunique')
```
#### Define a function to extract the start year from the season string
 ```python 
 def extract_start_year(season_str):
    return int(season_str[:4])

df['season'] = df['season'].apply(extract_start_year)
```
## Exploratory Data Analysis
Initially, we are going to analyze the NBA stats over the years
- Let's explore the new feature ('SeasonsPlayed') we created :
![Count of players](/plots/3plot.png)  

Observing the data, it becomes apparent that three-quarters of the population participate in the NBA for up to 14 seasons, while the remaining one-quarter extends their playing careers beyond the 14-season mark  

### 1. Total Number of NBA players

![Count of players by years](/plots/4plot.png)  

The depicted plot highlights a pronounced increase in the number of NBA players, commencing from the year 2010.  

Following this, we will delve into key statistics over the course of time.  
```python 
df.groupby('season').mean().T
```
### 2. Trends in Average Points by an NBA player over the years
![Average Points by Season](/plots/5plot.png)
We observe a gradual and consistent rise in the average points scored by NBA players over the years.  
Let's apply the same analysis to rebounds and assists.

### 3. Average Rebounds and Assists by an NBA player over the years
![Average Rebounds of NBA player by Season](/plots/6plot.png)  
![Average Assists of NBA player by Season](/plots/7plot.png)  

### 4. Changes in Maximum Points Per Game 
Next, our attention turns to scoring in the NBA. The subsequent plot shows the Maximum Points per Game by NBA season. While a discernible trend is not immediately apparent, it is noteworthy that in most seasons, the Points-Per-Game (PPG) leader consistently maintains a score of at least 28 points per game.
![Maximum PPG by Season](/plots/8plot.png)

### 5. Best Playmaking Seasons
Following we are going to focus on the seasons with the highest assist percentage by a player. A player's assist percentage shows how often a player assist his teammates. Since a player can only get an assist when his teammate makes a field goal, AST% looks at how many of these teammate made field goals were a result of that player's assists.  

We identify the top playmakers in the league throughout the years, focusing on those who have participated in at least of the 25% of the NBA games (31 games) within a season, along with their corresponding passing statistics and the season they stood out.
```python
pass_skills = df.sort_values(by = 'ast_pct', ascending = False)[df['gp'] > 31]
pass_skills[['player_name','ast_pct','ast','season']].head(13)
```

|    player_name   | ast_pct |  ast  | season |
|------------------|---------|-------|--------|
|Russell Westbrook |   0.543 | 10.4  |  2016  |
|       Chris Paul |   0.512 | 11.0  |  2008  |
|     James Harden |   0.505 | 11.2  |  2016  |
|       Chris Paul |   0.500 | 11.6  |  2007  |
|      Rajon Rondo |   0.498 | 11.7  |  2011  |
|       Steve Nash |   0.498 | 11.4  |  2010  |
|       Chris Paul |   0.493 | 10.0  |  2015  |
|       Steve Nash |   0.491 | 10.7  |  2011  |
|      Rajon Rondo |   0.490 | 11.1  |  2012  |
|     Andre Miller |   0.484 | 10.9  |  2001  |
|       Steve Nash |   0.483 | 11.0  |  2009  |
|      Rajon Rondo |   0.480 |  9.8  |  2013  |
|Russell Westbrook |   0.477 | 11.7  |  2020  |   

![top_passers](/plots/9plot.png)

The above plot showcases the extraordinary and historic passing season that Russell Westbrook had in 2016, highlighting the profound impact he had on his teammates.  

### 6. Best Scoring Seasons
```python
best_scoring_seasons = df.sort_values(by = 'pts', ascending = False).head(15)
best_scoring_seasons[['player_name','pts','reb','ast','season','draft_number']]
```
We focus on the top 15 players with the best season in scoring and will explore some of their statistics.

|      player_name       | pts  |  reb  | ast |season|draft_number|
|------------------------|------|-------|-----|------|------------| 
|James Harden            | 36.1 |  6.6  | 7.5 | 2018 |     3      |
|Kobe Bryant             | 35.4 |  5.3  | 4.5 | 2005 |     13     |
|James Harden            | 34.3 |  6.6  | 7.5 | 2019 |     3      |
|Joel Embiid             | 33.1 | 10.2  | 4.2 | 2022 |     3      |
|Allen Iverson           | 33.0 |  3.2  | 7.4 | 2005 |     1      |
|Luka Doncic             | 32.4 |  8.6  | 8.0 | 2022 |     3      |
|Damian Lillard          | 32.2 |  4.8  | 7.3 | 2020 |     6      |
|Tracy McGrady           | 32.1 |  6.5  | 5.5 | 2002 |     9      |
|Stephen Curry           | 32.0 |  5.5  | 5.8 | 2020 |     7      |
|Kevin Durant            | 32.0 |  7.4  | 5.5 | 2013 |     2      |
|Russell Westbrook       | 31.6 | 10.7  | 10.4| 2016 |     4      |
|Kobe Bryant             | 31.6 |  5.7  | 5.4 | 2006 |     13     |
|LeBron James            | 31.4 |  7.0  | 6.6 | 2005 |     1      |
|Allen Iverson           | 31.4 |  4.5  | 5.5 | 2001 |     1      |
|Shai Gilgeous-Alexander | 31.4 |  4.8  | 5.5 | 2022 |     11     |

- James Harden had two historic back two back seasons in 2018 and 2019 in scoring. 
- The 1/3 of this list was after the 2019 season.
- Allen Iverson and Lebron James are the only players in this list that were first pick in their draft season.
- Kobe Bryant was 13-th in his draft season and exists in this special list twice.
- Russel Westbrook averaged a triple double in 2016.
  !['Top Scorers in the last 25 years'](/plots/10plot.png)



## Players Individual's Statistics
#### We are going to analyze the average statistics throughout their career.To facilitate this analysis we transform the dataset in such a way that every player exists in the dataset exactly once.
```python
players = df.groupby('player_name').mean()
```
Now we are able to evaluate a player's career and identify the players who had/have a measurable duration over time.

## Feature Engineering
We don't need the 'age' and 'season' features any more
```python
players.drop('season', axis = 1, inplace = True)
players.drop('age', axis = 1, inplace = True)
```
We are goint to create a new column that categorizes if a player was/is in all star level based on the following metrics:  
- Top 10% Scoring Low
- Top 10% Rebounding Low
- Top 10% Passing Low
```python
scoring = round(players['pts'].quantile(0.9),2)
rebounding = round(players['reb'].quantile(0.9),2)
passing = round(players['ast'].quantile(0.9),2)

players['all_star'] = np.where(((players['pts'] > scoring) & (players['reb'] > rebounding)) | ((players['pts'] > scoring) & (players['ast'] > passing)), 'Yes', 'No')
```
## Data Analysis
### 7. Consistent All-Star Level Players
Let's see the distribution of the new feature we created :  

!['All Star Distribution'](/plots/12plot.png)  

We notice that only the 7.8% of the NBA players in the last 25 years was/is in all star level **consistently**.

## 8. Most Dominant Players
We define a dominant player as the player who had/has at least 20 points per game and 9 rebounds throughout his career.  

```python
dom = players[(players['pts'] > 20) & (players['reb'] > 9)].sort_values(by = 'pts', ascending = False)
dom[['player_name','pts','reb','ast','SeasonPlayed','draft_number']]
```

|           player_name |  pts  |  reb  |  ast |SeasonsPlayed|draft_number|
|-----------------------|-------|-------|------|-------------|------------|
|           Joel Embiid | 26.54 | 10.92 | 3.31 |     7.0     |    3.0     |
|         Anthony Davis | 23.81 | 10.29 | 2.45 |     11.0    |    1.0     |
| Giannis Antetokounmpo | 23.25 |  9.81 | 4.79 |     10.0    |    15.0    |
|    Karl-Anthony Towns | 23.22 | 10.85 | 3.47 |     8.0     |    1.0     |
|           Karl Malone | 22.88 |  9.06 | 4.20 |     8.0     |    13.0    |
|      Shaquille O'Neal | 21.88 | 10.01 | 2.42 |     15.0    |    1.0     |
|          Nikola Jokic | 20.40 | 10.55 | 6.71 |     8.0     |    41.0    |

There are only 7 NBA players in the last 25 years with these stats.  
!['Dominant players'](/plots/13plot.png)  


## 9. Best Scorers - Playmakers (Combo-Guards)
We define a combo-guard as the player who had/has at least 20 points per game and 5 assists throughout his career  
```python
scor_pass = players[(players['pts'] > 20) & (players['ast'] > 5)]
scor_pass[['player_name','pts','ast','draft_number']]
```

|	player_name	   |  pts  | ast	|draft_number|
|-----------------|-------|------|------------|
|Allen Iverson	   | 26.06 | 6.00	|    1.0     |
|Damian Lillard   | 25.50 | 6.78	|    6.0     |
|De'Aaron Fox	   | 20.56 | 6.23	|    5.0     |
|Dwyane Wade	   | 21.83 | 5.38	|    5.0     |
|Ja Morant	      | 22.62 | 7.37	|    2.0     |
|James Harden	   | 24.57 | 7.20	|    3.0     |
|Kyrie Irving	   | 23.77 | 5.73	|    1.0     |
|LeBron James	   | 27.20 | 7.34	|    1.0     |
|Luka Doncic	   | 27.70 | 8.02	|    3.0     |
|Nikola Jokic	   | 20.40 | 6.71	|    41.0    |
|Russell Westbrook| 22.48 | 8.33	|    4.0     |
|Stephen Curry	   | 24.16 | 6.40	|    7.0     |
|Trae Young	      | 25.72 | 9.34	|    5.0     |

There are 13 players in this list.  
- Allen Iverson and Dwyane Wade are the only retired NBA players
- Nikola Jokic was the only player in dominant players list and in combo-guard list.He was the 41-st in his draft season too!

  !['Combo-guard'](/plots/15plot.png)  


## 10. Highest Shooting Performance

Let's analyze another statistic that is called True Shooting Percentage ('ts_pct').True shooting percentage is a measure of shooting efficiency that takes into account field goals and free throws.

** True Shooting Percentage = PTS / (2*(FGA + 0.44 * FTA) **  

 We will focus only on the top 10 NBA players with the highest true shooting percentages, considering only players who have played more than 30 games.  
 ```python
shooters = players[players['gp'] > 30].sort_values(by = 'ts_pct', ascending = False).head(10)
```
 
 |     player_name    |  ts_pct  |    pts    | player_height |
 |--------------------|----------|-----------|---------------|
 |Robert Williams III | 0.727400 |  6.740000 |   205.232000  |
 |       Jericho Sims | 0.727000 |  2.800000 |   207.010000  |
 |     Daniel Gafford | 0.707500 |  7.625000 |   207.645000  |
 |     Walker Kessler | 0.702000 |  9.200000 |   213.360000  |
 |  Mitchell Robinson | 0.686800 |  8.240000 |   213.868000  |
 |     Onyeka Okongwu | 0.682333 |  7.566667 |   204.046667  |
 |        Nic Claxton | 0.681500 | 10.650000 |   210.820000  |
 |       Jeremy Evans | 0.679429 |  2.942857 |   205.740000  |
 |       Jaxson Hayes | 0.662250 |  7.300000 |   211.455000  |
 |      Jarrett Allen | 0.660167 | 12.233333 |   209.550000  |

Given the distribution of the feature 'player_height', we can conclude that most players are taller than the 75% of the population.Hence these players are considered as tall and this metric is very meaningful for the players that play in center position or power forward.    
 !['True Shooting PCT'](/plots/17plot.png)   


## 11. Most Impactful Players  

There is a metric that can measure a player's impact when he is on the court, the net rating ('net_rating').When referring to a player's net rating, it usually involves the point differential when that player is on the court per 100 possessions  
For example, if a player has a net rating of +2.05, it means that, on average, they are scoring 2.05 more points per 100 possessions than their opponents. This suggests that the team is performing well, with a positive impact on both offense and defense.  

**Net Rating=Offensive Rating−Defensive Rating**    
We are going to explore the top 20 most impactful players that have played at least 30 games on average in an NBA season.

```python
impact_players = players[players['gp'] > 30].sort_values(by='net_rating', ascending=False).head(20)
impact_players[['player_name','net_rating','pts','all_star']]
```
   |     player_name  | net_rating|    pts    |all_star|
   |------------------|-----------|-----------|--------|
   |     Bruce Bowen  | 28.292308 |  5.376923 |    No  |
   |       Max Strus  | 25.850000 |  7.675000 |    No  |
   | Sekou Doumbouya  | 16.700000 |  6.166667 |    No  |
   |   Robert Parish  | 14.900000 |  3.700000 |    No  |
   |   David Wingate  | 11.620000 |  2.640000 |    No  |
   |  Dakari Johnson  | 10.900000 |  1.800000 |    No  |
   | Slava Medvedenko | 10.700000 |  4.257143 |    No  |
   |   Jeff Hornacek  | 10.675000 |  13.32500 |    Yes |
   |   Bryon Russell  | 10.420000 |  8.080000 |    No  |
   |   Kevin Johnson  | 10.333333 |  12.10000 |    No  |
   |   Manu Ginobili  | 10.225000 |  13.15000 |    Yes |
   |  Igor Rakocevic  | 10.200000 |  1.900000 |    No  |
   |  David Robinson  | 10.185714 |  15.42857 |    Yes |
   |     Tim Duncan   | 9.747368  |  18.88947 |    Yes |
   |  John Stockton   | 9.385714  |  12.18571 |    No  |
   |  Kawhi Leonard   | 9.281818  |  19.48181 |    Yes |
   | Christian Koloko | 9.000000  |  3.100000 |    No  |
   |   Terry Porter   | 8.316667  |  8.166667 |    No  |
   |  Miles McBride   | 8.300000  |  2.850000 |    No  |
   |    Joel Embiid   | 8.057143  |  26.54285 |    Yes |  

- Bruce Bowen is the most impactful player in the NBA in the last 25 years.
- Six players of this list were/are all star class.
- Joel Embiid is 4th in NBA Best Scoring season list (2022) and the most dominant NBA player in the last 25 years.He is also top 20 in the most impactful player with 8.05 net rating.
  

!['ImpactfulPlayers'](/plots/16plot.png)
 
