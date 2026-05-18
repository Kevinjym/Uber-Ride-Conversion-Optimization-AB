# Uber Surge Pricing and Revenue Analysis

## Project Overview

This project analyzes how Uber ride prices, completed ride volume, and total observed revenue vary across different surge multiplier levels.

The goal is to understand whether higher surge pricing is associated with better revenue outcomes, or whether increased prices are offset by lower completed ride volume.

This is an exploratory data analysis project based on observational ride-sharing data, not a randomized A/B test.

---

## Objective

The main objective is to examine the relationship between:

- Surge multiplier
- Average ride price
- Completed ride volume
- Total observed revenue

The project focuses on answering the following business question:

> Does higher surge pricing lead to higher observed revenue, or does reduced ride volume offset the price increase?

---

## Dataset

The dataset contains Uber/Lyft-style ride-sharing records with information such as:

- Ride price
- Surge multiplier
- Distance
- Cab type
- Ride type
- Timestamp
- Location
- Weather-related variables

The original dataset contains approximately 693,000 rows and 57 features, covering ride activity from November 26, 2018 to December 18, 2018.

---

## Data Cleaning

The main data quality issue is missing values in the `price` column.

- Missing values only appear in the `price` column
- `price` has 55,095 missing records, approximately 7.95% of the dataset
- All missing `price` values occur when `surge_multiplier = 1.0`

Since `price` is the key variable for this analysis, rows with missing `price` values were removed before conducting price-related exploratory analysis.

Dropping these rows reduces the number of non-surge observations, but avoids introducing artificial fare values through imputation.

---

## Analysis Approach

This project uses exploratory data analysis to compare ride behavior across surge multiplier levels.

The analysis focuses on:

- Completed ride volume by surge multiplier
- Average price by surge multiplier
- Total observed revenue by surge multiplier
- The relationship between price increases and ride volume decreases

Because the dataset only contains completed ride records, ride count is used as a proxy for observed demand. It does not represent total market demand, user searches, ride requests, abandoned bookings, or conversion rates.

---

## Key Findings

### 1. Completed ride volume decreases as surge multiplier increases

Most completed rides occur when `surge_multiplier = 1.0`.  
Higher surge multiplier levels are associated with much lower completed ride volume.

This suggests that users may be sensitive to higher prices, although this should be interpreted as an association rather than causal evidence.

### 2. Average price increases under surge pricing

Average ride price generally increases as the surge multiplier increases.

However, the relationship is not perfectly linear, suggesting that other factors such as distance, ride type, location, and time may also influence final fare prices.

### 3. Total observed revenue is highest at non-surge pricing

Although surge pricing increases average price per ride, the decline in completed ride volume is large enough that total observed revenue decreases at higher surge levels.

In this dataset, revenue appears to be driven more by ride volume than by higher price per ride.

---

## Business Insight

Higher surge multipliers may increase the price of individual rides, but they are also associated with lower completed ride volume.

As a result, aggressive surge pricing does not appear to be revenue-optimal in this observed dataset.

From a business perspective, pricing strategy should balance:

- Higher price per ride
- Customer willingness to complete rides
- Overall completed ride volume
- Total observed revenue

This highlights the importance of considering demand sensitivity when designing dynamic pricing systems.

---

## Conclusion

Extreme surge pricing does not appear to improve total observed revenue in this dataset.

The main pattern is:

- Average price per ride increases
- Completed ride volume decreases sharply
- Total observed revenue declines at higher surge multiplier levels

Therefore, a moderate pricing strategy may be more effective than aggressive surge pricing.

---

## Recommendation

Instead of maximizing price per ride, the platform should optimize for total revenue by maintaining sufficient completed ride volume.

A more balanced dynamic pricing strategy may help preserve customer demand while still capturing additional revenue during high-demand periods.

---

## How to Run






---

## Project Structure

```text
uber-ride-conversion-analysis/
├── data/
│   └── rideshare_kaggle.csv
├── notebooks/
│   └── 01_data_overview.ipynb
├── README.md
├── requirements.txt
├── LICENSE
└── .gitignore
