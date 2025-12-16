# The Happiness Equation: A Deep Dive into Predictors of Global Well-Being 🌍😊

A comprehensive machine learning project that analyzes economic, social, and environmental indicators to identify the primary drivers of national happiness. This project utilizes data from the World Happiness Report (WHR) and global socio-economic datasets to build predictive models and extract actionable insights.

## Table of Contents
* [Project Overview](#project-overview)
* [Dataset](#dataset)
* [Features](#features)
* [Installation](#installation)
* [Usage](#usage)
* [Model Performance](#model-performance)
* [Results](#results)
* [Future Work](#future-work)
* [License](#license)

## Project Overview
This project explores the factors that influence why some societies are happier than others. Moving beyond just GDP, the study incorporates psychological frameworks like Maslow's hierarchy of needs and economic theories like the Easterlin Paradox to evaluate subjective well-being.

**Key steps include:**

* Merging disparate datasets (CO2 emissions, World Bank indicators, and WHR data) into a unified global dataset.
* Feature engineering, including factor analysis for maternal health indicators and handling multi-collinearity via VIF.
* Analyzing predictors such as social support, freedom of choice, and environmental impact (CO2 per capita).
* Training multiple regression models to predict national "Ladder Scores" (Happiness).

## Dataset
The project aggregates data from four primary sources:

* **World Happiness Report 2024:** National ladder scores and social factors.
* **World Data 2023:** Socio-economic indicators like minimum wage, education, and health expenditure.
* **Annual CO₂ Emissions:** Per-country emissions data from 2013 to 2023.
* **World Population Data:** Historical population stats for per-capita calculations.

## Features
* **Advanced Preprocessing:** Automated handling of special characters, standardized country naming across datasets, and multi-source merging.
* **Factor Analysis:** Dimensionality reduction on maternal health (mortality ratios and fertility rates) to create a single "Maternal Health Factor".
* **Statistical Guardrails:** Implementation of Bonferroni correction for multiple hypothesis testing to guard against false positives.
* **Scaling Comparisons:** Comparative analysis of model performance using `StandardScaler`, `RobustScaler`, and `MinMaxScaler`.

## Installation
```bash
# Clone the repository
git clone https://github.com/yourusername/happiness-equation.git
cd happiness-equation

# Create a virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install catboost pandas numpy scikit-learn matplotlib seaborn statsmodels
```
## Usage

1. **Data Preparation:**  
   Place the CSV files (`annual-co2-emissions-per-country.csv`, `world-data-2023.csv`, etc.) in the `/content/` directory or update the paths in the code.

2. **Run Analysis:**  
   * Execute the Jupyter Notebook `225A_Code - Final Version.ipynb` to process data and train models.  
   * Alternatively, use the script version to generate the EDA report.

```python
# To generate the automated EDA report (requires ydata-profiling)
from ydata_profiling import ProfileReport

report = ProfileReport(world_merged_df, title="Auto EDA Report")
report.to_file("eda_report.html")
```
## Model Performance

The project evaluates several regression algorithms. Based on the experimental results, **Ridge Regression with MinMaxScaler** provided the best fit:

| Model                | R² Score   | RMSE       |
| -------------------- | ---------- | ---------- |
| **Ridge Regression** | **0.8754** | **0.4698** |
| Random Forest        | 0.7076     | 0.7198     |
| Gradient Boosting    | 0.7268     | 0.6958     |
| HistGradientBoosting | 0.7411     | 0.6773     |

## Results

* **Top Predictors:** Social support (0.83 correlation), Log GDP per capita (0.78), and Healthy life expectancy (0.74) are the strongest positive drivers of happiness.
* **Negative Impactors:** Higher birth rates and maternal health risks are strongly correlated with lower national happiness scores.
* **Regional Findings:** Sub-Saharan Africa shows the strongest negative regional correlation with ladder scores, while Western Europe and North America show positive correlations.

## Future Work

* **Temporal Analysis:** Incorporate time-series data to see how happiness trends change after major global events.
* **Deep Learning:** Experiment with Neural Networks to capture non-linear relationships between social freedom and corruption.
* **Environmental Focus:** Deepen the investigation into how climate change policies (beyond CO2) impact national well-being.

## License

This project is licensed under the MIT License. See the [LICENSE](https://www.google.com/search?q=LICENSE) file for details.
