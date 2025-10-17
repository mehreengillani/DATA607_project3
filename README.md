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

Data transformation (Paula)

Data analysis (Taha)

Data visualization (Mehreen, Paula, Taha)
