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
