# IGN Game Reviews Analysis

## Introduction
The dataset used in this project is “IGN Games”, which contains over 18,000 data points about video games, including features such as release dates, platforms, genres, review scores given by IGN, etc.

The main goal of this project is to answer the question:
Which platform is the best for each genre based on average review scores?

In addition to identifying the best platform for each genre, I will also explore whether these preferences have remained consistent over time or if certain genres have shifted in popularity across platforms.

## Data inspection
After importing the dataset, I checked the first few rows using .head() to confirm the structure. The dataset has the following columns:

- **index** – unique identifier for each entry  
- **score_phrase** – text version of the review score (e.g., “Great”, “Amazing”)  
- **title** – name of the game  
- **url** – address for the game on IGN website  
- **platform** – gaming platform (e.g., PC, PlayStation Vita, Xbox 360)  
- **score** – numerical review score (main variable of interest)  
- **genre** – game genre (e.g., RPG, Action, Shooter)  
- **editors_choice** – whether IGN labeled it as “Editor’s Choice” (Y/N)  
- **release_year, release_month, release_day** – release date information

## Sample of the dataset

| index | score_phrase | title                   | platform        | score | genre      | editors_choice | release_year |
|-------|--------------|-------------------------|-----------------|-------|------------|----------------|--------------|
| 0     | Amazing      | LittleBigPlanet PS Vita | PlayStation Vita| 9.0   | Platformer | Y              | 2012         |
| 1     | Amazing      | LittleBigPlanet PS Vita | PlayStation Vita| 9.0   | Platformer | Y              | 2012         |
| 2     | Great        | Splice: Tree of Life    | iPad            | 8.5   | Puzzle     | N              | 2012         |
| 3     | Great        | NHL 13                  | Xbox 360        | 8.5   | Sports     | N              | 2012         |
| 4     | Great        | NHL 13                  | PlayStation 3   | 8.5   | Sports     | N              | 2012         |

Dataset has no null values.
