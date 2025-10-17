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
