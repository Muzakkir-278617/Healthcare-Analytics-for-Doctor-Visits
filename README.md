# 🏥 Doctor Visits — Healthcare Analytics & Machine Learning

**An end-to-end data analytics and machine learning project for understanding doctor visit frequency using Python.**

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg?logo=python&logoColor=white)](https://www.python.org/)
[![Jupyter Notebook](https://img.shields.io/badge/Jupyter-Notebook-orange.svg?logo=jupyter&logoColor=white)](https://jupyter.org/)
[![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458.svg?logo=pandas)](https://pandas.pydata.org/)
[![Scikit-learn](https://img.shields.io/badge/Scikit--learn-Machine%20Learning-F7931E.svg?logo=scikitlearn&logoColor=white)](https://scikit-learn.org/)
[![Status](https://img.shields.io/badge/Project-Academic%20%7C%20Portfolio-success.svg)]()

## 📌 Project Overview

**Doctor Visits — Healthcare Analytics** is an end-to-end data analytics and machine learning project that investigates factors associated with the frequency of doctor visits in a patient-level healthcare dataset.

The project uses Python to perform data cleaning, data quality assessment, exploratory data analysis (EDA), statistical association analysis, predictive modelling, and model interpretation.

It examines how doctor visit frequency varies with demographic characteristics, income, illness, reduced-activity days, health status, chronic conditions, and healthcare coverage, depending on the availability of these variables in the dataset.

The project also establishes reproducible baseline regression models, evaluates their performance on held-out data, identifies influential predictive features using permutation importance, and exports the resulting analytical artifacts.

**Important:** This project analyzes observational healthcare data. Statistical associations do not establish causation, and predictions are not clinical advice.

## 🎯 Project Objectives

- Analyze the distribution of doctor visits, including the proportion of observations with zero visits.
- Investigate visit frequency across demographic, socioeconomic, health-related, and healthcare coverage variables.
- Examine relationships between numerical variables and the target variable.
- Identify missing values, duplicate records, inconsistent data types, and schema issues.
- Build and compare baseline regression models.
- Evaluate predictive performance using MAE, RMSE, and R².
- Interpret model behavior using permutation feature importance.
- Generate visualizations, evaluation tables, cleaned data, and model artifacts.
- Maintain a reproducible and modular analytical workflow.

## 📊 Dataset Description

The notebook is designed for a CSV dataset containing patient-level doctor visit records.

The accompanying project presentation describes a dataset of approximately **5,190 records and 13 columns**. These figures should be verified against the actual CSV file before reporting them as final dataset statistics.

### Expected Features

| Feature | Description |
|---|---|
| `visits` | Number of doctor visits; prediction target |
| `gender` | Gender category |
| `age` | Patient age or age category |
| `income` | Income measure or income category |
| `illness` | Number of illnesses reported |
| `reduced` | Number of reduced-activity days |
| `health` | Self-reported health measure or status |
| `private` | Private healthcare coverage indicator |
| `freepoor` | Free healthcare coverage indicator for low-income individuals |
| `freerepat` | Free repatriation coverage indicator |
| `nchronic` | Chronic condition indicator or count |
| `lchronic` | Long-term chronic condition indicator |

The exact number and names of columns may vary between dataset versions. The notebook performs a schema audit and normalizes common column aliases.

**Dataset availability:** The dataset is not included in this repository by default. You must obtain a dataset that you have permission to use and place it in the project directory.

### Expected Target Variable

`visits` — the number of doctor visits recorded for each observation.

This is a **regression problem** because the target represents a numerical count rather than a binary class.

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| Jupyter Notebook | Interactive analysis and experimentation |
| Pandas | Data manipulation and cleaning |
| NumPy | Numerical computation |
| Matplotlib | Data visualization |
| Seaborn | Statistical visualization |
| SciPy | Statistical tests and correlation analysis |
| Statsmodels | Statistical modelling and diagnostics |
| Scikit-learn | Preprocessing, regression models, and evaluation |
| Joblib | Saving and loading trained model pipelines |
| Git and GitHub | Version control and project hosting |

## ⚙️ Project Workflow

```text
                  Doctor Visits Dataset
                           |
                           v
                 Environment Configuration
                           |
                           v
                   Data Loading & Audit
                           |
                           v
                 Data Cleaning & Validation
                           |
                           v
             Exploratory Data Analysis (EDA)
                           |
                           v
                Statistical Association Analysis
                           |
                           v
                   Feature Preparation
                           |
                           v
                 Regression Model Training
                           |
              +------------+------------+
              |            |            |
              v            v            v
           Dummy       Random Forest   Histogram-Based
         Regressor      Regressor      Gradient Boosting
              |            |            |
              +------------+------------+
                           |
                           v
                  Held-Out Evaluation
                    MAE, RMSE, R²
                           |
                           v
                Permutation Importance
                           |
                           v
                Export Results & Models
```

## 🔍 Analysis Modules

### 1. Environment Setup and Configuration

- Configure reproducibility settings.
- Define dataset paths and analysis parameters.
- Create output and model directories automatically.
- Prepare the notebook environment.

### 2. Data Loading and Schema Audit

- Load the CSV dataset using Pandas.
- Inspect column names and data types.
- Identify missing values and duplicate observations.
- Examine unique values and target-variable validity.
- Normalize common column-name aliases.

### 3. Data Cleaning and Validation

- Remove exact duplicate rows where appropriate.
- Handle missing values using suitable preprocessing strategies.
- Validate numerical fields and the `visits` target.
- Identify invalid values and inconsistent data types.
- Prepare data for exploratory analysis and modelling.

### 4. Exploratory Data Analysis (EDA)

Investigate the distribution of doctor visits and the characteristics of available features.

Questions include:

- What proportion of observations have zero doctor visits?
- How does visit frequency vary across age and gender categories?
- How are income and illness associated with doctor visits?
- Do reduced-activity days correspond to different visit frequencies?
- How do chronic conditions and healthcare coverage relate to visit patterns?

### 5. Statistical Association Analysis

- Generate correlation matrices for numerical variables.
- Compare visit counts across available demographic and health groups.
- Conduct appropriate exploratory statistical tests.
- Summarize relationships between the target and available features.

Statistical methods must be selected according to the data types, distributional assumptions, and sample sizes.

### 6. Predictive Modelling

The notebook compares three regression approaches.

| Model | Purpose |
|---|---|
| Dummy Regressor | Establishes a simple mean-prediction baseline |
| Random Forest Regressor | Captures nonlinear relationships and feature interactions |
| HistGradientBoosting Regressor | Learns complex patterns through gradient-boosted decision trees |

The models are trained and evaluated using a held-out test set. Preprocessing steps are incorporated into the model pipeline where applicable to improve reproducibility and prevent data leakage.

### 7. Model Evaluation

The following metrics are used to compare model performance.

**Mean Absolute Error (MAE)**

Measures the average absolute difference between actual and predicted visit counts. Lower values indicate smaller average prediction errors.

**Root Mean Squared Error (RMSE)**

Measures prediction error while penalizing larger errors more strongly. Lower values indicate better performance.

**Coefficient of Determination (R²)**

Measures how much variation in the target is explained relative to a mean-prediction baseline. Higher values are generally preferable; a negative test-set R² indicates performance worse than that baseline.

The model with the lowest held-out MAE is selected for further inspection. Actual results depend on the dataset, preprocessing decisions, and evaluation split.

### 8. Model Interpretation

Permutation feature importance estimates how much predictive performance changes when the values of an individual feature are shuffled.

This helps identify which features contribute most to the selected model's predictive performance.

**Note:** Feature importance does not establish causality and can be affected by correlated features and the evaluation metric used.

### 9. Artifact Export

The notebook saves cleaned data, evaluation metrics, plots, model artifacts, and summary information for further analysis and reporting.

## 📁 Repository Structure

```text
Doctor-Visits-Healthcare-Analytics/
│
├── Doctor_Visits_Healthcare_Analytics.ipynb
├── DoctorVisits.csv                  # Add locally; not included by default
├── README.md
├── .gitignore
│
├── outputs/                          # Generated during execution
│   ├── target_distribution.png
│   ├── numeric_distributions.png
│   ├── correlation_matrix.png
│   ├── model_metrics.csv
│   ├── permutation_importance.csv
│   ├── permutation_importance.png
│   ├── best_model_diagnostics.png
│   ├── data_quality_profile.csv
│   ├── cleaned_doctor_visits.csv
│   └── executive_summary.json
│
└── models/                           # Generated during execution
    ├── doctor_visits_model.joblib
    └── model_metadata.json
```

*The `outputs/` and `models/` directories are generated when the notebook runs. Individual files may be absent if their corresponding analysis steps cannot be completed or the required columns are unavailable.*

## 🚀 Getting Started

Follow these steps to run the project locally.

### Prerequisites

- Python 3.10 or a compatible Python version.
- Git installed on your system.
- Jupyter Notebook.
- A compatible doctor visits CSV dataset.
- Sufficient memory and storage for the dataset and generated outputs.

### Step 1: Clone the Repository

Replace the placeholder URL with your actual GitHub repository URL.

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd <YOUR_REPOSITORY_FOLDER>
```

### Step 2: Create a Virtual Environment

**Windows**

```bash
py -m venv .venv
.venv\Scripts\activate
```

**macOS / Linux**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### Step 3: Install Dependencies

Upgrade pip:

```bash
python -m pip install --upgrade pip
```

Install the required packages:

```bash
pip install pandas numpy matplotlib seaborn scipy scikit-learn statsmodels joblib jupyter
```

### Step 4: Add the Dataset

Place your dataset in the project directory and name it:

```text
DoctorVisits.csv
```

If the CSV has a different name or location, update the `DATA_PATH` setting in Section 2 of the notebook.

Verify that the CSV contains a valid `visits` target column or a supported alias that the notebook can normalize.

### Step 5: Launch Jupyter Notebook

```bash
jupyter notebook
```

Open:

```text
Doctor_Visits_Healthcare_Analytics.ipynb
```

Run the cells from top to bottom, following any instructions or warnings displayed by the notebook.

### Step 6: Review the Results

After successful execution, inspect:

- The target distribution and feature visualizations.
- The data quality profile.
- The model evaluation metrics.
- The permutation feature importance results.
- The selected model and metadata.
- The executive summary.

## 📈 Expected Outputs

| Output | Description |
|---|---|
| `target_distribution.png` | Distribution of doctor visits |
| `numeric_distributions.png` | Distributions of numerical features |
| `correlation_matrix.png` | Correlations between numerical variables |
| `model_metrics.csv` | Held-out regression evaluation results |
| `permutation_importance.csv` | Feature importance values |
| `permutation_importance.png` | Visualization of feature importance |
| `best_model_diagnostics.png` | Diagnostic plots for the selected model |
| `data_quality_profile.csv` | Missing values and data quality information |
| `cleaned_doctor_visits.csv` | Processed dataset |
| `executive_summary.json` | Summary of the analysis |
| `doctor_visits_model.joblib` | Serialized model pipeline |
| `model_metadata.json` | Saved model and configuration metadata |

The exact outputs depend on the columns available and the execution results. **No performance scores are claimed in advance; the reported metrics should come from an actual notebook run.**

## ❓ Key Research Questions

1. What proportion of individuals recorded zero doctor visits?
2. How does the average number of visits vary across age, gender, and income groups?
3. Are illness counts and reduced-activity days associated with visit frequency?
4. Do chronic conditions correspond to different doctor visit patterns?
5. How does healthcare coverage relate to observed visit frequency?
6. Which features contribute most to predictive performance?
7. Which baseline regression model achieves the lowest held-out MAE?
8. How well do the models generalize to unseen observations?

## 🔬 Evaluation and Potential Improvements

The current workflow provides a reproducible baseline. Further work could strengthen the analysis through:

- **Cross-validation:** Estimate performance stability across multiple data splits.
- **Count regression:** Compare Poisson and Negative Binomial regression.
- **Overdispersion analysis:** Check whether the variance of visit counts exceeds the mean.
- **Hurdle models:** Separately model whether any visit occurs and how many visits occur among observations with visits.
- **Subgroup evaluation:** Examine performance differences across demographic and healthcare coverage groups.
- **Uncertainty estimation:** Report confidence intervals or other appropriate uncertainty measures.
- **Automated testing:** Validate preprocessing, schema handling, and model behavior.
- **Dashboard development:** Build an interactive dashboard for aggregate healthcare analytics.
- **Reproducible data sourcing:** Document the dataset source, version, license, and data dictionary.

## ⚠️ Limitations and Responsible Use

- The dataset represents observational data; associations do not establish causation.
- Sampling, reporting, and measurement biases may affect findings.
- Results may not generalize to other populations or healthcare systems.
- A random train/test split may not represent future or external populations.
- Model performance can vary across demographic and healthcare coverage groups.
- Feature importance does not demonstrate that a variable causes a change in doctor visits.
- Predictions must not be used to deny healthcare, determine eligibility, or replace professional clinical judgment.
- Do not publish identifiable patient information or commit sensitive datasets to GitHub.
- Confirm the dataset's license and usage restrictions before redistribution.

## 🔮 Future Scope

- Add a formal data dictionary and dataset provenance documentation.
- Evaluate Poisson, Negative Binomial, and hurdle-based models.
- Add cross-validation and uncertainty intervals.
- Implement subgroup performance and fairness diagnostics.
- Refactor notebook code into reusable Python modules.
- Introduce automated data validation and unit tests.
- Build a dashboard for exploring aggregate patterns.
- Package the project for reproducible execution and deployment.

## 👨‍💻 Author

**Mohammad Ahmed Muzakkir**

Project: **Healthcare Analytics for Doctor Visits**

## 📄 License

A license has not yet been specified. Add a `LICENSE` file before describing this repository as open source. Also verify that the dataset license permits the intended use and redistribution.

## 🙌 Acknowledgements

This project uses the Python data science ecosystem, including Pandas, NumPy, Matplotlib, Seaborn, SciPy, Statsmodels, Scikit-learn, and Joblib.

---

*Built with Python for healthcare data analytics, statistical exploration, and reproducible machine learning.*
