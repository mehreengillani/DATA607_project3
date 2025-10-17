# DATA607_project3

Data Cleaning (Mehreen)
Users data
  1. Handle missing data 
  2. Removing Duplicates (2.34% Duplicates)
  3. Data type conversion
      categorical variables
      Text to date format for created_at
      Removing negative values from age
    4. outliers detection and removal (performed cap with IQR, didn't remove values)
  factoring for categorical data
    5. String sonversion
    6. Data validation
Cleaned data saved in users_clean.csv file

Data Cleaning Summary for movies.csv

1. Missing Value Handling
  High missingness variables (>60%): Set number_of_seasons and number_of_episodes to 0 for movies, used median for TV shows
  Financial data: Created missing indicators (budget_missing, revenue_missing) and set missing values to 0
  IMDB ratings (14.4% missing): Used multiple imputation (MICE) with PMM method using duration_minutes and rating as predictors

2. Duplicate Removal
Identified and removed 34 duplicate rows (3.36% of data)
Kept first occurrence of each duplicate

4. Data Type Conversion
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

6. Text Cleaning

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
  
Watch_history Data Cleaning Summary

1. Missing Value Handling
  Removed: user_rating column (79.9% missing - too high for meaningful analysis)
  Imputed: watch_duration_minutes (11.7% missing) and progress_percentage (8.11% missing) using Multiple Imputation (MICE) with PMM method
  Replaced NA values in action and quality with "unknown" category
  Verified: Distribution preserved with minimal statistical changes (<1% mean difference)

3. Duplicate Removal
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

Data transformation (Paula)

Data analysis (Taha)

Data visualization (Mehreen, Paula, Taha)
