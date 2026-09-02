# Data Analysis Portfolio — Assignments 1, 2 & 3

This repository contains three independent data analysis assignments covering customer segmentation, retail sales analysis, and clinical data preprocessing.

---

## Assignment 1 — Online Retail Customer Segmentation (RFM Analysis)
**Notebook:** `Assignment1.ipynb` | **Data:** `online_retail_II.xlsx`

### Objective
Segment customers of a UK-based online retailer using RFM (Recency, Frequency, Monetary) analysis to identify customer value tiers from transactional data.

### Dataset
Invoice-level transactions: `Invoice`, `StockCode`, `Description`, `Quantity`, `InvoiceDate`, `Price`, `Customer ID`, `Country`.

### Pipeline
1. Load Excel file with `CustomerID`/`InvoiceID` as strings
2. Exploratory analysis — country distribution (UK dominates), summary stats
3. Filter to UK transactions; remove non-positive `Quantity`
4. Feature engineering — `TotalPrice` = `Quantity` × `Price`
5. RFM calculation — Recency (days since last invoice), Frequency (invoice count), Monetary (total spend), all per customer
6. Quartile scoring for R, F, M individually
7. Combined 3-digit RFM Score (e.g., `'111'` = best customers)
8. Identify top customers by monetary value within the best segment

### Key Findings
- UK customers make up the overwhelming majority of the customer base
- RFM segmentation identifies a clear top-tier group (`RFM_Score = '111'`), with the top customer generating over £349,000 in spend
- Framework provides a foundation for targeted marketing or loyalty program design

---

## Assignment 2 — Walmart Sales EDA (Store Performance & Seasonal Trends)
**Notebook:** `ASSIGNMENT2_TAKE3_.ipynb` | **Data:** `walmart-sales-dataset-of-45stores.csv`

### Objective
Exploratory analysis of weekly sales across 45 Walmart stores to uncover trends in store performance, holiday effects, seasonality, and the relationship between sales and economic indicators.

### Dataset
Weekly sales records with `Store`, `Weekly_Sales`, `Date`, `Holiday_Flag`, `Temperature`, `Fuel_Price`, `CPI`, `Unemployment`.

### Pipeline
1. Data quality checks — missing values, duplicates (none found)
2. Type conversion — coerce sales/economic columns to numeric
3. Outlier detection via boxplots
4. Distribution analysis — histograms, holiday vs. non-holiday pie chart
5. Sales vs. numeric features (Temperature, Fuel Price, CPI, Unemployment)
6. Store performance — total sales and sales volatility (std. dev.) by store
7. Holiday analysis — Super Bowl, Labour Day, Thanksgiving, Christmas vs. non-holiday
8. Time-based trends — monthly and semesterly sales

### Key Findings
- **Store 20** has the highest total weekly sales; **Store 14** the most volatile
- **Thanksgiving** produces the highest average sales of any holiday
- Winter months underperform; summer/spring months peak; November notably lags
- Semester 1 slightly outsells Semester 2

---

## Assignment 3 — Heart Failure Prediction (Data Preprocessing & EDA)
**Notebook:** `DMP2.ipynb` | **Data:** `heart.csv`

### Objective
Clean, preprocess, and explore a clinical heart-failure dataset to understand feature distributions and their relationship to heart disease outcomes.

### Dataset
918 patient records with demographics (`Age`, `Sex`) and clinical measures (`ChestPainType`, `RestingBP`, `Cholesterol`, `FastingBS`, `RestingECG`, `MaxHR`, `ExerciseAngina`, `Oldpeak`, `ST_Slope`), target `HeartDisease` (renamed `HeartFailure`).

### Pipeline
1. Initial exploration — shape, dtypes, summary stats, unique values
2. Data cleaning — no nulls/duplicates found; categorical columns encoded to integers
3. Inconsistency removal — invalid `Cholesterol` values (outside 126–564) dropped
4. Outlier removal — IQR method on key numeric columns
5. Min-Max normalization for distance-based algorithms
6. EDA — distributions of Age, Sex, and heart failure across all clinical features; correlation matrix

### Key Findings
- No missing values or duplicates, but invalid cholesterol readings required cleaning
- Age distribution slightly right-skewed, concentrated in 40–70 range
- Chest pain type, ST slope, exercise-induced angina, and max heart rate show visibly different distributions by heart failure status — good candidate predictors for modeling

---

## Requirements (combined)
- pandas, numpy, matplotlib, seaborn, scikit-learn, datetime, openpyxl


## Usage
Each assignment is self-contained in its own notebook. Place the corresponding data file (`online_retail_II.xlsx`, `walmart-sales-dataset-of-45stores.csv`, or `heart.csv`) in the working directory and run the relevant notebook's cells in order.
