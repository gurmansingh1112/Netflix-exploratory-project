# Netflix Catalogue Analysis (2015–2020)

An exploratory data analysis of the Netflix catalogue in Python: how did the mix of movies and TV shows, countries, audience ratings and genres change as Netflix grew?

## Question
How did the composition of the Netflix catalogue change between 2015 and 2020?

## Data
- **Source:** [Netflix Movies and TV Shows](https://www.kaggle.com/datasets/shivamb/netflix-shows) on Kaggle (collected from the third-party search engine Flixable).
- **Size:** 8,807 titles, 12 columns (`netflix_titles.csv`).
- **Coverage:** snapshot ending September 2021. 2021 is therefore a partial year and is excluded from trend charts.

## Approach
1. **Inspected** missing values and duplicates.
2. **Cleaned** the data:
   - moved 3 runtimes that were stored in the `rating` column back to `duration`
   - filled missing `director`, `cast` and `country` with one consistent label ("Unknown") and excluded it from country analysis
   - parsed `date_added` into dates and extracted the year
   - split `duration` into `movie_minutes` and `tv_seasons`
   - grouped ratings into audience levels (Kids, Family, Teens, Adults)
3. **Split multi-value columns** (`country`, `listed_in`) with `explode()` so every country and genre is counted.
4. **Analysed** catalogue mix, yearly additions, countries, audience ratings, genres, movie runtimes and TV seasons.

## Key findings
- **Mix:** about 70% movies (6,131) and 30% TV shows (2,676).
- **Growth:** yearly additions grew from roughly 80 titles in 2015 to about 2,000 in 2019, then dipped to about 1,880 in 2020.
- **TV shows:** their share of new additions fell to about 25% in 2018 and recovered to about 32% by 2020.
- **Countries:** the United States appears in 46.3% of titles with a known country, followed by India (13.1%) and the United Kingdom (10.1%).
- **Audience:** adult-rated content is the largest group (45.5% overall). Its share of new additions rose from 39.0% in 2015 to a peak of about 47% in 2018 and was 45.7% in 2020, while kids' content fell sharply.
- **Genres:** International Movies (2,752 titles), Dramas and Comedies are the most common.
- **Length:** the median movie runs 98 minutes; most TV shows have just one season.

## Limitations
- The data is a snapshot ending in September 2021.
- `date_added` is when a title joined Netflix, not when it was released.
- It describes the catalogue (what is available), not viewership (what people watch).
- About 9% of titles have no country, so country results cover only titles with a known country.
- Titles with several countries or genres are counted once per country or genre, so those totals add up to more than the number of titles.

## How to run
1. Clone this repository (the CSV is included, keep it in the same folder as the notebook).
2. Install the requirements: `pip install -r requirements.txt`
3. Open the notebook with `jupyter notebook` and run all cells.

## Tools
Python 3, pandas, NumPy, matplotlib, Jupyter
