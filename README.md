# Healthcare Data Analysis & Reporting

![banner](Images/banner.png)

**Author:** Floyd Steev Santhmayer  
**Original repository source:** Adapted from Singhss21/Healthcare-Data-Analysis-Reporting. See repository for original structure and sample files.  

---

## Table of Contents

1. [Project Overview](#project-overview)  
2. [Project Description](#project-description)  
3. [Key Features](#key-features)  
4. [Tools & Technologies](#tools--technologies)  
5. [Repository Structure](#repository-structure)  
6. [Installation & Setup](#installation--setup)  
7. [How to Run](#how-to-run)  
8. [Detailed: Python EDA Notebook (`HealthCare_EDA`)](#detailed-python-eda-notebook-healthcare_eda)  
   - 8.1 [Dataset Description](#dataset-description)  
   - 8.2 [Data Cleaning & Preparation](#data-cleaning--preparation)  
9. [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)  
   - 9.1 [Univariate Analysis](#univariate-analysis)  
   - 9.2 [Bivariate Analysis](#bivariate-analysis)  
   - 9.3 [Multivariate Analysis](#multivariate-analysis)  
   - 9.4 [Distribution & Correlation Analysis](#distribution--correlation-analysis)  
10. [Power BI Dashboard Overview](#power-bi-dashboard-overview)  
11. [Contributing](#contributing)  
12. [Author & Contact](#author--contact)  
13. [License](#license)

---

## Project Overview

This project demonstrates an end-to-end approach for preparing, analyzing, and visualizing healthcare operational and clinical datasets. It combines Python-based data engineering and exploratory analysis with Power BI dashboards to produce reproducible insights for healthcare operations, clinical review, and financial oversight.

---

## Project Description

The repository contains:
- A multi-sheet Excel dataset (patient, visit, provider, hospital data).
- A Jupyter Notebook (`Python/HealthCare_EDA.ipynb`) that documents the data ingestion, cleaning, and EDA steps.
- A Power BI file (`PowerBI/HealthCare_Dashboard.pbix`) that hosts interactive dashboards and executive summaries.
- Supporting images and a `.gitignore` and `LICENSE`.

The workflow:
1. Merge multiple Excel sheets into a single analysis-ready table.
2. Clean and standardize records (dates, categories, duplicates).
3. Compute derived indicators (length-of-stay, high-billing flags).
4. Perform EDA and create visualizations for operational insight.
5. Publish interactive Power BI dashboards for stakeholders.

---

## Key Features

- Programmatic merging of multiple Excel sheets into a unified dataset.  
- Standardization of patient, doctor, and hospital metadata.  
- Missing value strategies (numeric → median; categorical → mode).  
- Length-of-stay calculation and high-billing detection.  
- Admission-type mapping and categorical harmonization.  
- EDA using Pandas, Matplotlib, and Seaborn.  
- Power BI dashboards for interactive exploration and executive reporting.

---

## Tools & Technologies

- Python (Pandas, NumPy, Matplotlib, Seaborn)  
- Jupyter Notebook  
- Power BI Desktop (`.pbix`)  
- Microsoft Excel / CSV for raw data storage

---

## Repository Structure

```
├── Data/                      # Raw input Excel / CSV files
├── Images/                    # README & dashboard images (banner, screenshots)
│   ├── banner.png
│   ├── univariate-analysis.png
│   └── logo.png
├── Python/
│   ├── HealthCare_EDA.ipynb   # Notebook with data ingestion, cleaning, and EDA
│   └── requirements.txt
├── PowerBI/
│   └── HealthCare_Dashboard.pbix
├── .gitignore
├── LICENSE
└── README.md
```

---

## Installation & Setup

1. Clone the repository:
```bash
git clone https://github.com/<your-username>/Healthcare-Data-Analysis-Reporting.git
cd Healthcare-Data-Analysis-Reporting
```

2. Install Python dependencies:
```bash
pip install -r Python/requirements.txt
```

3. Launch the notebook:
```bash
jupyter notebook Python/HealthCare_EDA.ipynb
```

4. Open the Power BI dashboard:
- Open `PowerBI/HealthCare_Dashboard.pbix` in Power BI Desktop.

---

## How to Run

### Run Python EDA Notebook
1. Ensure `Data/healthcare_dataset.xlsx` (or CSVs) exist in `Data/`.  
2. Open `Python/HealthCare_EDA.ipynb` in Jupyter. The notebook is structured with clearly labeled sections:
   - Data ingestion and sheet merging
   - Data cleaning & transformation
   - Feature engineering (length-of-stay, billing flags)
   - EDA visualizations and summary tables
3. Export figures and key tables to `Images/` to include in documentation or dashboard.

### Open Power BI
- Launch Power BI Desktop and load `PowerBI/HealthCare_Dashboard.pbix`. Review each report page (Overview, Condition & Outcome Analysis, Billing & Insurance, Provider Performance, Time Series analysis) and connect to the cleaned dataset (or exported CSVs) if necessary.

---

## Detailed: Python EDA Notebook (`HealthCare_EDA`)

### Dataset Description
The dataset is a consolidated healthcare dataset containing:
- Patient demographics and identifiers
- Admission and discharge records
- Primary and secondary diagnosis codes / descriptions
- Billing amounts and insurance details
- Provider and hospital identifiers

The notebook documents column-level expectations and data types used for analysis.

### Data Cleaning & Preparation
Key steps implemented in the notebook:
1. **Merging All Datasets**: Read multiple sheets and join on patient / visit keys to produce a master table.  
2. **Standardizing Text**: Trim whitespace, lower-case where appropriate, and normalize categories.  
3. **Data Integrity Validation**: Check primary keys, detect impossible dates, and validate numeric ranges.  
4. **Handling Missing Values**: Use sensible imputations (median for continuous variables; mode or explicit 'Unknown' for categoricals).  
5. **Removing Duplicates**: Deduplicate by primary visit identifiers and timestamps.  
6. **Converting Datatypes**: Ensure date columns are `datetime64`, numeric columns are numeric types.  
7. **Derived Columns**: Length of stay (`discharge_date - admission_date`), age bins, high-billing flags.  
8. **Category Mapping**: Map admission codes to readable categories and harmonize insurance labels.

---

## Exploratory Data Analysis (EDA)

### Univariate Analysis
Univariate analysis inspects single variables to:
- Understand central tendency and dispersion (mean, median, std).  
- Visualize distributions with histograms and boxplots.  
- Detect missing values and outliers.  

![univariate-analysis](Images/univariate-analysis.png)

**Typical outputs:** Frequency tables, histograms, boxplots, and summary statistics.

### Bivariate Analysis
Investigate relationships between two variables:
- Categorical vs. categorical: contingency tables and stacked bar charts.  
- Categorical vs. numeric: boxplots grouped by category.  
- Numeric vs. numeric: scatter plots and correlation coefficients.

### Multivariate Analysis
Assess interactions among three or more variables using:
- Pair-wise scatterplot matrices
- Grouped aggregations and pivot tables
- Multivariate statistical summaries and dimensionality reduction (optional)

### Distribution & Correlation Analysis
- Distribution fitting and skewness checks.  
- Pearson / Spearman correlation matrices and heatmaps.  
- Identify highly correlated features for downstream modeling or dashboard filtering.

---

## Power BI Dashboard Overview

Pages and purposes:
1. **Overview Dashboard** — Admissions summary, demographics, & top-line KPIs.  
2. **Medical Condition & Outcomes** — Frequency of conditions, outcomes, and recovery indicators.  
3. **Billing & Insurance** — Billing distributions, insurance coverage mix, and high-cost case flags.  
4. **Provider & Hospital Performance** — Doctor-level and hospital-level KPIs (admissions, outcomes, billing).  
5. **Time-Based Analysis** — Admission/discharge trends, length-of-stay trends, and seasonal patterns.

---

## Contributing

Contributions are welcome. Suggested workflow:
1. Fork the repository.  
2. Create a branch for your feature or fix: `git checkout -b feature/your-feature`.  
3. Commit clear changes and push to your fork.  
4. Open a Pull Request describing the changes and rationale.

Please include test data or reproducible instructions for any new analyses.

---

## Author & Contact

**Floyd Steev Santhmayer**  
Prepared for GitHub import and polished for professional presentation.

If you wish to customize the README tone (concise technical, marketing-focused, or academic), add real notebook/PBIX screenshots, or include CI badges, tell me which items you want and I will update the package.

---

## License

This repository is made available under the MIT License. See the included `LICENSE` file for details.

---

*README assembled and refined using the public repository content as reference.*  
