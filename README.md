# Titanic - Exploratory Data Analysis (EDA)

This repository contains a comprehensive Exploratory Data Analysis (EDA) and Feature Engineering project on the classic Kaggle Titanic dataset. The goal of this project is to uncover the underlying patterns and socio-demographic factors that determined passenger survival rates during the shipwreck.

## Project Overview
The project explores the historic passenger manifest to understand the driving dynamics behind the "Women and children first" protocol and socio-economic disparities in survival outcomes. 

### Key Project Phases:
1. **Data Cleaning & Imputation:** Dynamically handling missing values and structural inconsistencies.
2. **Feature Engineering:** Extracting meaningful contextual features from raw passenger data to increase predictive signal.
3. **Exploratory Data Analysis (EDA):** Utilizing advanced data visualizations (`Seaborn` and `Matplotlib`) to draw concrete historical and statistical insights.

---

## Data Cleaning & Transformation

Before visualization, the dataset underwent rigorous preprocessing to ensure data integrity and fix historical anomalies:

* **Missing Value Imputation (`Age`):** Rather than using a generic median/mean, missing ages were dynamically imputed using the group means clustered by passenger class (`Pclass`) and gender (`Sex`).
* **Handling Sparse Columns:** The `Cabin` column was dropped due to high sparsity (~77% missing data), and rows with missing `Embarked` tokens were filtered out.
* **Label Mapping:** Continuous representations of categorical fields like `Survived` and `Pclass` were mapped to descriptive string labels (`Survived`/`Died`, `1st Class`/`2nd Class`/`3rd Class`) to optimize visualization readability and layout aesthetics.
* **Historical Name Rectification:** Outdated entry naming conventions where married women were listed under their husband's name (e.g., *Mrs. John Bradley (Florence Briggs Thayer)*) were parsed using targeted regular expressions and custom mapping functions. This successfully restored the women's actual names while preserving their surnames and titles (e.g., *Cumings, Mrs. Florence Briggs Thayer*).

---

## Feature Engineering

New structural features were generated to encapsulate multi-variable interactions into single robust indicators:
* **Family Size:** Combined `SibSp` (siblings/spouses) and `Parch` (parents/children) along with the passenger themselves to calculate total `FamilySize`.
* **IsAlone:** A binary indicator (`1` or `0`) isolating individuals traveling without any family members on board.

---

## Key Visualizations & Insights

The EDA phase was structured around three main analytical angles:

### 1. The Demographics Protocol ("Women and Children First")
Using combined boxplots and distribution plots, the analysis maps out how gender and age interacted. 
* **Insight:** Survival rates heavily favored female passengers across almost all age brackets. Young male children also saw slightly higher rescue rates than adult males, aligning with the historical evacuation protocols.

### 2. Socio-Economic Disparities
Using categorical countplots, passenger outcomes were stratified across ticket tiers.
* **Insight:** A drastic correlation exists between socio-economic standing and survival. Passengers in **First Class** had significantly higher absolute and relative survival rates, whereas the vast majority of casualties occurred in **Third Class**.

### 3. Family Size Dynamics
Using point plots and line trends, survival probabilities were charted against total family counts.
* **Insight:** Passengers traveling alone (`FamilySize == 1`) or with very large families (5+ members) experienced notably low survival probabilities. Conversely, individuals traveling in moderate nuclear groups of 2 to 4 people showed the highest rates of survival.

---

## Technologies Used
* **Python 3.x**
* **Pandas:** Data manipulation and structural cleaning
* **NumPy:** Vectorized operations and array transformations
* **Matplotlib & Seaborn:** Advanced statistical data visualization

---

## Getting Started

### Prerequisites
Ensure you have the required packages installed:
```bash
pip install pandas numpy matplotlib seaborn
