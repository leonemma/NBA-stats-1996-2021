
# NBA Stats 1996-2021

## Authors

- [@leonemma](https://github.com/leonemma)

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

## Feature Overview
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
This dataset contains some individual players multiple times due to the collection of their statistics every year. Initially, we will analyze the NBA over the years, and secondly, we will transform the dataset to represent NBA player stats in a way that each player exists in the dataset only once.

#### The dataset does not contain any null values.  
```python
df.info()
```
- At first we remove the first column 'Unnamed: 0'.    
- Secondly,we will turn the 'draft_round' and 'draft_number' features into numeric.Hence,we replace the value Undrafted that represents the undrafted players with the number 0.Therefore when the value is 0 in these features it means that this player was undrafted.


## Exploring the Features


![Histograms of Numeric Variables](/plots/1plot.png)
```python
                age  player_height  player_weight   draft_round  draft_number  \
count  12844.000000   12844.000000   12844.000000  12844.000000  12844.000000   
mean      27.045313     200.555097     100.263279      1.059172     17.774914   
std        4.339211       9.111090      12.426628      0.683223     16.803276   
min       18.000000     160.020000      60.327736      0.000000      0.000000   
25%       24.000000     193.040000      90.718400      1.000000      3.000000   
50%       26.000000     200.660000      99.790240      1.000000     14.000000   
75%       30.000000     208.280000     108.862080      1.000000     29.000000   
max       44.000000     231.140000     163.293120      8.000000    165.000000   

                 gp           pts           reb           ast    net_rating  \
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
Initially, we will analyze the NBA stats over the years
- Let's explore the new feature ('SeasonsPlayed') we created :
![Count of players](/plots/3plot.png)  

Observing the data, it becomes apparent that three-quarters of the population participate in the NBA for up to 14 seasons, while the remaining one-quarter extends their playing careers beyond the 14-season mark  

![Count of players by years](/plots/4plot.png)  

The depicted plot highlights a pronounced increase in the number of NBA players, commencing from the year 2010.  

Following this, we will delve into key statistics over the course of time.  
```python 
df.groupby('season').mean().T
```
![Average Points by Season](/plots/5plot.png)
We observe a gradual and consistent rise in the average points scored by NBA players over the years.  
Let's apply the same analysis to rebounds and assists.

![Average Rebounds of NBA player by Season](/plots/6plot.png)  
![Average Assists of NBA player by Season](/plots/7plot.png)  
Next, our attention turns to scoring in the NBA. The subsequent plot shows the Maximum Points per Game by NBA season. While a discernible trend is not immediately apparent, it is noteworthy that in most seasons, the Points-Per-Game (PPG) leader consistently maintains a score of at least 28 points per game.
![Maximum PPG by Season](/plots/8plot.png)

Following we will focus on the players with the highest assist percentage.A player's assist percentage shows how often the player is assisting teammates. Since a player can only get an assist when his teammate makes a field goal, AST% looks at how many of these teammate made field goals were a result of that player's assists.  



