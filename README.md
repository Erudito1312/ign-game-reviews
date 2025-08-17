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

## Data cleaning
- Verified that the dataset has no null values.
- Checked for duplicates (`ign_data.duplicated().sum()`) and removed any potential ones with `ign_data = ign_data.drop_duplicates()`.
- No additional cleaning was required.

## Methods
**Goal:** Find the best platform for each genre based on average IGN review scores.

**Steps**
1) Filtered to popular, contemporary platforms (PC, PlayStation family, Xbox family, major Nintendo consoles).
2) Simplified genre -> main_genre by taking the first label before a comma (e.g., “Action, Adventure” -> “Action”).
3) Kept the top 10 genres by review count to avoid noisy, low-sample categories.
4) Aggregated mean scores for each (platform, main_genre) pair.
5) Pivoted to a main_genre × platform matrix and plotted a heatmap.
6) Selected the best platform per genre using column-wise maximum (and saved the table).
   Note: Scores are shown to 1 decimal place; missing platform–genre combos appear blank.

## Results
**Heatmap — Average score by genre and platform**

<img width="2207" height="1402" alt="avg_score_heatmap" src="https://github.com/user-attachments/assets/ab97013a-4a5d-4859-9f62-5a3239d4c1e9" />

| Main Genre | Best Platform | Best Avg |
|------------|---------------|----------|
|Platformer  |PlayStation 4  | 8.5      |
|Puzzle      |Xbox One       | 8.3      |
|RPG         |Xbox           | 8.3      |
|Strategy    |Xbox One       | 8.2      |
|Shooter     |Nintendo 64    | 8.0      |
|Racing      |Xbox One       | 8.0      |
|Sports      |Xbox           | 7.9      |
|Action      |PlayStation 4  | 7.7      |
|Fighting    |PlayStation 3  | 7.6      |
|Adventure   |PlayStation 4  | 7.4      |

## Findings
- Platformer titles reviewed highest on PlayStation 4 on average in this sample.
- PC is absent from the top row for these 10 genres, which may reflect console exclusives and/or the genre mix kept in this slice.
- Some classics inflate averages on legacy consoles (e.g., Nintendo 64 shooters).

## Data quality
- Genres were simplified to a single label, which can hide nuance from multi-genre titles.
- Results reflect **IGN’s** scoring only.
- Ties across platforms within a genre are broken by the first max encountered.
