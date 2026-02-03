# Olympic Sports Analysis - Project Documentation (PRD)

## 1. Project Overview (PRD)

**Project Name:** Olympic Games Analytics: 120 Years of Historical Insights
**Project Type:** Data Science & Exploratory Data Analysis (EDA)
**Objective:** To analyze historical Olympic data (Summer & Winter) to uncover trends in athlete performance, country dominance, and sport evolution over time.

## 2. SEO Optimization

**SEO Project Name:** Olympic Games History Analysis & Visualization (1896-2014)
**SEO Description:** A comprehensive data scienced project analyzing 120 years of Olympic Games history. Discover trends in medal counts, athlete demographics, and country performance using Python, Pandas, and Plotly.
**Keywords:** Olympic Games, Sports Analytics, Data Science, EDA, Visualization, Python, Pandas, Historical Data, Summer Olympics, Winter Olympics.

## 3. Kaggle Suitability & Tags

**Suitable for Kaggle:** Yes, this dataset is highly suitable for Kaggle as it allows for rich visualization, time-series analysis, and geospatial plotting.
**Top 5 Tags:**

1. `sports`
2. `history`
3. `exploratory-data-analysis`
4. `visualization`
5. `geospatial-analysis`

## 4. Dataset Metadata

### Coverage

The dataset covers all Olympic Games from Athens 1896 to Sochi 2014. It includes data on athletes, events, medals, and participating countries, supplemented by economic (GDP) and demographic (Population) data for country analysis.

### Temporal and Geospatial Scope

- **Start Date:** 04/06/1896 (First Modern Olympics)
- **End Date:** 02/23/2014 (Sochi Winter Olympics)
- **Geospatial Scope:** Global (All participating countries and host cities).
- **Temporal Range:**
  - Summer: 1896 - 2012
  - Winter: 1924 - 2014

### Provenance

**Source:** The data is a historical compilation of Olympic records.
**Origin:** Likely derived from [Sports-Reference.com](https://www.sports-reference.com/), which was the primary source for the well-known "120 Years of Olympic History" dataset on Kaggle.
**Transformations:**

- Split into `SummerSD.csv` and `WinterSD.csv`.
- `CountriesSD.csv` likely added from World Bank or similar sources to provide context (Population, GDP).

### Collection Methodology

**Methodology:** Archival research and scraping of public historical sports records. The data aggregates official results from the International Olympic Committee (IOC) archives.

### Source Link

**Primary Source:** [Kaggle: 120 Years of Olympic History](https://www.kaggle.com/heesoo37/120-years-of-olympic-history-athletes-and-results) (Note: The specific CSVs in this project are a modified subset of this larger dataset).

## 5. Dataset Dictionary (Schema)

### `SummerSD.csv`

Contains details of Summer Olympic Games.

- `Year` (Integer): Year of the Olympics.
- `City` (String): Host city.
- `Sport` (String): Main sport category (e.g., Aquatics).
- `Discipline` (String): Specific discipline (e.g., Swimming).
- `Athlete` (String): Name of the athlete.
- `Code` (String): 3-letter Country Code (IOC code).
- `Gender` (String): Gender of the athlete (Men/Women).
- `Event` (String): Specific event name (e.g., 100M Freestyle).
- `Medal` (String): Medal won (Gold, Silver, Bronze).
- `Country` (String): Full country name.

### `WinterSD.csv`

Contains details of Winter Olympic Games.

- `Year` (Integer): Year of the Olympics.
- `City` (String): Host city.
- `Sport` (String): Main sport category.
- `Discipline` (String): Specific discipline.
- `Athlete` (String): Name of the athlete.
- `Country` (String): **Warning:** In this file, this column acts as the **3-letter Code** (e.g., FRA), not the full name.
- `Gender` (String): Gender of the athlete.
- `Event` (String): Specific event name.
- `Medal` (String): Medal won.

### `CountriesSD.csv`

Supplementary country information.

- `Country` (String): Full country name.
- `Code` (String): 3-letter IOC/ISO Code.
- `Population` (Float): Population count (Year variable dependent, likely recent).
- `GDP per Capita` (Float): GDP per capita in USD.

## 6. Project Challenges

1. **Schema Mismatch:** `SummerSD.csv` shares the country name in the `Country` column, while `WinterSD.csv` uses the `Country` column for the 3-letter code. This requires careful merging and renaming during preprocessing.
2. **Missing Data:** Historical records (especially pre-1950) may have missing or inconsistent formatting for athlete names.
3. **Country Name Changes:** Countries change names and borders (e.g., USSR -> Russia, Yugoslavia). Mapping these historical entities to modern GDP/Population data in `CountriesSD.csv` will result in null matches for historical empires.
4. **Data Granularity:** The dataset focuses on medalists (implied by the `Medal` column presence in sample rows). If non-medalists are excluded, it biases the "participation" analysis.
5. **Economic Correlations:** Correlating modern GDP (from ONE specific year in `CountriesSD`) with historical medal performance (e.g., 1900) is methodologically flawed but acceptable for high-level "modern strength" comparisons.
