
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

![stats](/plots/describe_output.txt)  

### Correlation Matrix

![Correlation Matrix](/plots/2plot.png)
