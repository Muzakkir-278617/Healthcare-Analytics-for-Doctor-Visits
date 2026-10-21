# doctor-visits-healthcare-analytic

# Healthcare Analytics for Doctor Visits

An end-to-end data analytics and machine learning project that explores factors associated with the number of doctor visits in a patient dataset. The project uses Python to clean and profile healthcare data, perform exploratory data analysis, investigate statistical associations, and evaluate baseline predictive models.

> **Important:** This project analyzes observational healthcare data. Associations do not establish causation, and model predictions are not clinical advice.

## Project Objectives

- Understand the distribution of doctor visits, including the prevalence of zero visits.
- Explore how visit frequency varies by age, gender, income, illness, reduced-activity days, health status, chronic conditions, and healthcare coverage where those fields are available.
- Quantify relationships between numerical variables and the number of doctor visits.
- Establish reproducible baseline regression models and compare their held-out performance.
- Identify features that contribute to predictive performance using permutation importance.
- Export cleaned data, evaluation metrics, figures, model artifacts, and summary outputs.

## Dataset

The analysis notebook is designed for a CSV dataset containing patient-level doctor-visit records. The accompanying project presentation describes a dataset of approximately **5,190 records and 13 columns**. These figures should be verified against the actual dataset before being reported as confirmed statistics.

Expected variables include:

- `visits` — number of doctor visits (target variable)
- `gender` — gender
- `age` — age
- `income` — income
- `illness` — number of illnesses reported
- `reduced` — number of reduced-activity days
- `health` — health score or status
- `private` — private healthcare coverage indicator
- `freepoor` — free healthcare coverage indicator for low-income individuals
- `freerepat` — free repatriation coverage indicator
- `nchronic` — chronic condition indicator or count
- `lchronic` — long-term chronic condition indicator

Column names may vary by dataset version. The notebook normalizes common aliases and checks for the required `visits` target. Review the schema-audit output and update the alias mapping if your CSV uses different names.

**Dataset not included:** Add the dataset to your local working directory or update the `DATA_PATH` setting in the notebook. Ensure that you have permission to use and share the data, and never commit identifiable patient information.

## Repository Contents

```text
.
├── Doctor_Visits_Healthcare_Analytics.ipynb
├── DoctorVisits.csv                 # Add locally; not included by default
├── README.md
├── outputs/                         # Generated tables, plots, and summaries
└── models/                          # Saved model and metadata
```

The `outputs/` and `models/` directories are created when the notebook runs.

## Technology Stack

- Python 3
- Jupyter Notebook
- Pandas and NumPy — data handling and numerical analysis
- Matplotlib and Seaborn — data visualization
- SciPy — statistical tests and correlations
- Statsmodels — statistical modelling
- Scikit-learn — preprocessing, regression models, and evaluation
- Joblib — model serialization
- Git and GitHub — version control and project hosting

## Getting Started

### 1. Clone the Repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd <YOUR_REPOSITORY_FOLDER>
```

Replace the placeholders with your actual GitHub repository URL and folder name.

### 2. Create a Virtual Environment (Recommended)

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

### 3. Install Dependencies

Upgrade pip:

```bash
python -m pip install --upgrade pip
```

Install the required packages:

```bash
pip install pandas numpy matplotlib seaborn scipy scikit-learn statsmodels joblib jupyter
```

### 4. Add the Dataset

Place your CSV file in the project directory. By default, the notebook looks for:

```text
DoctorVisits.csv
```

If the file has another name or is stored elsewhere, edit `DATA_PATH` in Section 2 of the notebook.

### 5. Launch Jupyter Notebook

```bash
jupyter notebook
```

Open `Doctor_Visits_Healthcare_Analytics.ipynb` and run the cells from top to bottom.

## Analysis Workflow

1. **Environment setup and configuration** — configure reproducibility settings and output directories.
2. **Data loading and schema audit** — inspect columns, data types, missing values, and unique values.
3. **Data quality and cleaning** — remove exact duplicate rows, validate the target, and prepare numerical fields.
4. **Exploratory data analysis** — examine the visit-count distribution and feature distributions.
5. **Group comparisons** — compare mean visit counts across available demographic, health, and healthcare coverage variables.
6. **Association analysis** — calculate correlation matrices and perform exploratory statistical tests.
7. **Predictive modelling** — compare a mean baseline, Random Forest, and HistGradientBoosting regressor.
8. **Model evaluation** — evaluate using MAE, RMSE, and R² on a held-out test set.
9. **Model interpretation** — estimate permutation feature importance.
10. **Artifact export** — save the selected pipeline, metadata, cleaned data, charts, and summary tables.

## Models and Evaluation

The notebook compares the following models:

| Model | Purpose |
|---|---|
| Dummy Regressor | Baseline that predicts the training-set mean |
| Random Forest Regressor | Captures nonlinear patterns and feature interactions |
| HistGradientBoosting Regressor | Provides a gradient-boosted tree baseline |

Performance is compared using:

- **MAE (Mean Absolute Error):** Measures the average absolute difference between actual and predicted visit counts. Lower values are better.
- **RMSE (Root Mean Squared Error):** Penalizes larger prediction errors more heavily. Lower values are better.
- **R² (Coefficient of Determination):** Measures predictive performance relative to a mean baseline. Higher values are generally better, and R² can be negative on held-out data.

The notebook selects the model with the lowest held-out MAE for further inspection and saves it as a pipeline with preprocessing included.

Results depend on the dataset, data cleaning, model configuration, and train/test split. For stronger evidence, evaluate with cross-validation and compare count-specific approaches such as Poisson regression, Negative Binomial regression, or hurdle models.

## Output Files

After a successful run, the notebook writes artifacts to `outputs/` and `models/`, including:

```text
outputs/
├── target_distribution.png
├── numeric_distributions.png
├── correlation_matrix.png
├── model_metrics.csv
├── permutation_importance.csv
├── permutation_importance.png
├── best_model_diagnostics.png
├── data_quality_profile.csv
├── cleaned_doctor_visits.csv
└── executive_summary.json

models/
├── doctor_visits_model.joblib
└── model_metadata.json
```

Some plots are generated only when the corresponding columns are available. Exact outputs may vary depending on the dataset schema and successful execution of the relevant notebook cells.

## Key Questions

- What proportion of people recorded zero doctor visits?
- How does the average number of visits vary by age, gender, and income?
- How are illnesses and reduced-activity days associated with visit frequency?
- Do chronic conditions or healthcare coverage categories correspond to different visit patterns?
- Which available features contribute most to the baseline model's predictive performance?
- Which regression model achieves the lowest held-out MAE?

The project presentation reports patterns such as a high proportion of zero visits and higher average visit counts among people with more reduced-activity days. The notebook is intended to validate these patterns against the actual CSV. Do not treat presentation figures as verified analytical results until the notebook has been executed.

## Limitations and Responsible Use

- The analysis is observational and cannot establish causal relationships.
- The dataset may contain sampling, reporting, and measurement biases.
- Correlation and feature importance do not prove that a variable causes doctor visits.
- A random train/test split may not reflect performance on future or external populations.
- Predictive errors may differ across demographic and healthcare coverage groups.
- Do not use this project to deny healthcare, determine eligibility, or replace professional clinical judgment.
- Protect patient privacy and avoid committing sensitive or identifiable data to version control.
- Verify the dataset's source, license, and permitted uses before sharing it.

## Future Improvements

- Add a formal data dictionary and dataset source/version information.
- Use cross-validation and uncertainty intervals for model evaluation.
- Compare Poisson and Negative Binomial count regression, including overdispersion checks.
- Evaluate a two-part or hurdle model for the high proportion of zero visits.
- Add subgroup performance and fairness diagnostics.
- Package the workflow into reusable Python modules and add automated tests.
- Add a dashboard for exploring aggregate results.
- Improve reproducibility with configuration files and automated data validation.

## Author

**Mohammad Ahmed Muzakkir**

Project: **Healthcare Analytics for Doctor Visits**

---

*Developed using Python for healthcare data analytics, statistical exploration, and reproducible machine learning.*
