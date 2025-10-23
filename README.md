# DATA607_project3

Data Cleaning (Mehreen)

Users Data Cleaning Summary code(Users_data_cleaning.rmd)

  1. Missing Value Handling

  Identified: Missing values in age (11.93%), monthly_spend (9.87%), and household_size (15%)
  Imputed: Used Multiple Imputation (MICE) with PMM method to preserve data relationships
  Verified: Distribution patterns maintained across all variables after imputation
  
2. Duplicate Removal

  Identified: 2.34% duplicate user records
  Removed: All duplicate rows using distinct() function
  Result: Unique user profiles for analysis
  
3. Data Type Conversion

  Dates: Converted subscription_start_date to Date format and created_at to POSIXct
  Logical: Converted is_active from character to proper boolean values
  Ordered Factor: Applied logical hierarchy to subscription_plan (Basic → Premium+)
  Factors: Converted categorical variables (gender, country, state_province, etc.)
  Numeric: Ensured age and household_size as integers, monthly_spend as numeric
  
4. Data Quality Fixes

  Negative Ages: Replaced negative age values with median age
  Gender Categories: Consolidated empty strings and similar categories into "Unknown" and "Other"
  Factor Ordering: Applied proper ordering to subscription plans
  
5. Outlier Treatment

  Applied: IQR-based capping for all numeric variables (age, monthly_spend, household_size)
  Preserved: All data points while handling extreme values appropriately
  Verified: Box plots show cleaned distributions without losing data integrity
  
6. Text Cleaning

  Standardized: All text to lowercase for consistency
  Cleaned: Removed whitespace and multiple spaces
  Handled: Converted empty strings to NA values
  
7. Data Validation

  Achieved: No impossible values (negative ages, unrealistic household sizes)
  Verified: All data types correctly converted and ranges validated
  Confirmed: Clean categorical variables with proper factor levels
  
Final Output
Cleaned dataset: users_clean.csv
Records: Complete, consistent user profiles ready for analysis
Ready for: Customer segmentation, subscription analysis, user behavior studies, and demographic insights

Data Cleaning Summary for movies.csv code(movies_data_cleaning.rmd)

1. Missing Value Handling
  High missingness variables (>60%): Set number_of_seasons and number_of_episodes to 0 for movies, used median for TV shows
  Financial data: Created missing indicators (budget_missing, revenue_missing) and set missing values to 0
  IMDB ratings (14.4% missing): Used multiple imputation (MICE) with PMM method using duration_minutes and rating as predictors

2. Duplicate Removal
  Identified and removed 34 duplicate rows (3.36% of data)
  Kept first occurrence of each duplicate

3. Data Type Conversion
  Logical: Converted is_netflix_original and content_warning from character to logical
  Date: Converted added_to_platform to proper Date format
  Factors: Converted categorical variables (content_type, genre_primary, rating, etc.) to factors
  Ordered factor: Applied proper rating hierarchy from TV-Y to TV-MA

4. Outlier Treatment
  Applied column-specific capping strategies:
  Years: 1900 to current year+5
  Duration: 1 minute to 99th percentile
  Ratings: 0.5 to 10.0 (actual IMDB scale)
  Financial data: 0 to 95th percentile
  Seasons/Episodes: 0 to 99th percentile

5. Text Cleaning

  Converted all text to lowercase
  Removed leading/trailing whitespace
  Replaced multiple spaces with single space
  Converted empty strings to NA
  
6. Data Validation

Quality Score: 97.8% (EXCELLENT)
Uniqueness: 100% unique rows

Final Output

Cleaned dataset saved as movies_clean.csv
  1005 observations × 20 variables  
  string conversion for text data
  
Watch_history Data Cleaning Summary code(watch_history_data_cleaning.rmd)

1. Missing Value Handling
  Removed: user_rating column (79.9% missing - too high for meaningful analysis)
  Imputed: watch_duration_minutes (11.7% missing) and progress_percentage (8.11% missing) using Multiple Imputation (MICE) with PMM method
  Replaced NA values in action and quality with "unknown" category
  Verified: Distribution preserved with minimal statistical changes (<1% mean difference)

2. Duplicate Removal
  Identified: 4.07% duplicate rows
  Removed: All duplicate records using distinct() function
  Result: Clean, unique watch sessions

3. Data Type Conversion
  Date: Converted watch_date from character to Date format
  Logical: Converted is_download from character to logical
  Ordered Factors:
  
  device_type (Mobile → Smart TV hierarchy)
  action (unknown → completed hierarchy)
  quality (unknown → HDR hierarchy)
  Regular Factors: location_country
  
4. Outlier Treatment
  Identified: Right-skewed distribution in watch_duration_minutes
  Applied: 0 to 8-hour capping (0-480 minutes) for realistic watch durations
  Created: duration_category column with 8 ordered time buckets
  Preserved: Data integrity while handling extreme values

5. Text Cleaning
  Standardized: All text columns to lowercase
  Removed: Leading/trailing whitespace and multiple spaces
  Handled: Empty strings by converting to NA

6. Data Validation

  Achieved: 95% complete cases with no missing values
  Verified: All data types correctly converted
  Confirmed: Realistic value ranges (0-480 minutes for duration, 0-100% for progress)
  Quality Score: EXCELLENT (high data quality achieved)
  
Final Output
  Cleaned dataset: watch_history_clean.csv
  Records: All watch sessions with complete, consistent, and analysis-ready data
  Ready for: User behavior analysis, content recommendation systems, and streaming pattern insights
  
Recommendation Logs Data Cleaning Summary code file: (recommendation_logs_data_cleaning.rmd)

1. Missing Value Handling

  Identified: Only one column with missing values - recommendation_score (10% missing)
  Imputed: Used Multiple Imputation (MICE) with PMM method using was_clicked, position_in_list, and device_type as predictors
  Verified: Distribution preserved with minimal statistical impact (0.9% mean change, 1.7% SD change)

2. Duplicate Removal

  Identified: 3.525% duplicate rows
  Removed: All duplicate records using distinct() function
  Result: Clean, unique recommendation records
  
3. Data Type Conversion

  Date: Converted recommendation_date from character to Date format
  Logical: Converted was_clicked from character to logical (True/False)
  Ordered Factors:
  recommendation_type (personalized → similar_users hierarchy)
  device_type (Mobile → Smart TV hierarchy)
  time_of_day (morning → night hierarchy)
  Regular Factor: algorithm_version
  
4. Outlier Analysis

  Examined: recommendation_score (0-1 scale) and position_in_list
  Found: No significant outliers in either numeric variable
  Confirmed: All values within expected ranges
  
5. Text Cleaning

  Standardized: All text columns to lowercase
  Cleaned: Removed leading/trailing whitespace and multiple spaces
  Handled: Converted empty strings to NA
  
6. Data Validation

  Achieved: 100% complete cases with no missing values
  Verified: All data types correctly converted
  Confirmed: Valid value ranges:

  recommendation_score: 0-1 (appropriate for probability scores)
  position_in_list: Positive integers only
  Quality Score: EXCELLENT (high data quality achieved)
  
Final Output

  Cleaned dataset: recommendation_logs_clean.csv
  Records: All recommendation interactions with complete, consistent data
  Ready for: Recommendation system analysis

Data transformation (Paula)

Data analysis (Taha)

Data visualization (Mehreen, Paula, Taha)

----Taha----
# Platform Content and User Analysis

A reproducible analysis of platform content, user demographics, watch behavior, and the recommendation system using cleaned operational data.

## Summary

This project analyzes cleaned operational CSVs to evaluate:
- The content catalog (movies): composition, quality, and financials.
- User demographics and activity patterns.
- Watch-session behavior and temporal patterns.
- The recommendation system's performance and its impact on engagement.
- Correlations between content features (e.g., budgets and revenues).

Key dataset sizes and metrics:
- Titles (movies): n = 1,005
- Users: n = 10,000
- Watch sessions: n = 100,727
- Recommendation system overall CTR: 15.096%
- Recommendation model AUC (click prediction): ≈ 0.505
- Successful links between recommendations and watches (within 24h): n = 2

---

## Repository / Analysis Structure

The analysis is organized into numbered sections that match the narrative and output in the final report:

0. Data Loading and Quality Control
1. Content Catalog (Movies) Analysis
2. User Demographics and Activity
3. Watch History and Temporal Patterns
4. Recommendation System — Performance
5. Recommendation System — Impact on Engagement
6. Content Feature Correlations

Each section contains code and narrative that:
- Loads the relevant cleaned CSV(s) from the configured data directory.
- Runs sanity checks and generates summary tables/visualizations.
- Produces the text conclusions and figures included in the final report.

---

## Data

Expected cleaned CSVs (examples):
- movies_clean.csv
- users_clean.csv
- watch_sessions_clean.csv
- recommendations_clean.csv
- (Other cleaned datasets as used in the analysis)

Data directory is provided via a parameter (e.g., `params$data_dir` in a pipeline or notebook).

Notes about loading:
- A safe read helper (safe_read) prefers the faster `vroom` package but falls back gracefully if files are missing. Missing files are skipped with warnings so the overall report still runs.
- A Data Dictionary is produced during QC that lists each column, its type, and number of missing values.

Sanity checks include:
- Presence of required key columns (e.g., user_id, movie_id).
- Range constraints (e.g., `progress_percentage` ∈ [0, 100]).

---

## Section Highlights and Key Findings

1) Content Catalog (Movies)
- Catalog size: n = 1,005 titles.
- IMDb rating: distribution is left-skewed and concentrated between 6.0 and 8.5 (mean slightly below median).
- Release years: heavily features post-1990s content; growth in recent decades.
- Runtime: right-skewed; peak at standard feature length (90–120 min).
- Content rating: longer titles tend to have mature ratings (R, TV‑MA, PG‑13).
- Financials: positive correlation between log(Budget) and log(Revenue); non-Netflix originals show higher and wider revenue distributions.
- Popular genres: Adventure, Comedy, and War are most common primary genres.

2) User Demographics and Activity
- Users: n = 10,000.
- Age distribution: approximately normal, centered in the late 30s to early 40s.
- Geography: concentrated in the USA and Canada.
- Signups: acquisition rate slowed after an initial rapid growth period (proxied by first-watch dates).
- Power users: defined as users with 20+ sessions; aggregated metrics (e.g., average watch duration) are joined back to user profiles.

3) Watch History and Temporal Patterns
- Sessions: n = 100,727.
- Watch duration: highly right-skewed with a mode at 10–20 minutes.
- Progress percentage: bimodal — peaks at low progress (abandonment) and 100% (completion).
- Device usage: multi-platform (Desktop, Laptop, Mobile, Smart TV, Tablet) with relatively uniform session counts.
- Temporal patterns: session volume stable day-to-day; no significant weekday vs. weekend difference.
- Content engagement: Top-20 movies by views show a long-tail distribution; no clear correlation between IMDb rating and average watch duration.

4) Recommendation System — Performance
- Overall CTR: 15.096%.
- CTR is consistent across `recommendation_type` values.
- Strong position bias: CTR decays significantly after position ≈ 5 in the recommendation list.
- Logistic regression to predict clicks (features: algorithm_version, position_in_list, time_of_day) produced an AUC ≈ 0.505, indicating no meaningful predictive power.
- After controlling for covariates, none of the analyzed features had statistically significant effects on click odds.

5) Recommendation System — Impact on Engagement
- Attempted linkage of watch sessions to a recommendation delivered within 24 hours failed due to insufficient data; only n = 2 successful links.
- With such limited linkage, no statistically valid conclusion can be drawn about whether recommended titles lead to higher watch progress (`progress_percentage`).

6) Content Feature Correlations
- Strongest relationship observed: production_budget positively correlates with box_office_revenue.
- Missingness flags (e.g., `budget_missing`, `revenue_missing`) show expected inverse correlations with their respective numeric fields.

---

## Reproducibility & Running the Analysis

- Parameters:
  - data directory: set `params$data_dir` (or the equivalent parameter in the analysis environment).
  - The pipeline/notebook expects cleaned CSVs in that directory.

- Suggested software stack (used or compatible):
  - R with tidyverse (dplyr, ggplot2), vroom (or readr fallback), broom, and caret/ROCR for modeling/metrics
  - OR equivalent Python stack (pandas, seaborn/matplotlib, scikit-learn) if the analysis is ported

- Typical workflow:
  1. Place cleaned CSVs into the configured `data_dir`.
  2. Run the analysis notebook or pipeline (which executes sections 0–6).
  3. Review generated artifacts: data dictionary, summary tables, plots, and the final report.

- Handling missing files:
  - The safe reader will emit warnings and skip missing files so other analyses continue to run.

---

## Limitations

- Linking recommendations to subsequent watch sessions is limited by available instrumentation; only 2 successful recommendation-watch links were identified in this run, preventing causal or robust impact analysis.
- Logistic model for click prediction had near-random AUC (≈ 0.505); additional features or improved instrumentation may be required to build a meaningful predictive model.
- Financial data (budget/revenue) frequently contains missingness; analyses rely on missingness flags and log-transformations where appropriate.

---

## Outputs

Typical outputs produced by the analysis:
- Data Dictionary (CSV / table)
- Summary tables for movies, users, sessions
- Distribution plots (ratings, runtime, age, watch duration, progress)
- Time-series and temporal heatmaps
- Top-N lists (e.g., Top-20 movies by views)
- Recommendation system metrics and diagnostic plots (CTR by position, AUC, logistic regression outputs)
- Correlation matrix / scatter plots for financial features

---Taha End---
