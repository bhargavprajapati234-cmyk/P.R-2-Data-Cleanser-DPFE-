# Patient Health Records – Data Cleaning & Preprocessing

A Python-based data preprocessing project that explores patient health records, handles missing values, detects and treats outliers, and exports a cleaned dataset for further analysis or machine learning.

## Project Overview

This project demonstrates practical data-cleaning techniques using **Pandas, NumPy, Matplotlib, Seaborn, and Scikit-learn**. The Jupyter Notebook compares multiple imputation strategies, applies outlier detection methods, and builds a final cleaning workflow.

## Dataset Information

The provided cleaned Excel dataset contains:

- **Rows:** 1,000 patient records
- **Columns:** 9
- **File:** `cleaned_patient_health_records.csv(1).xlsx`
- **Sheet:** `cleaned_patient_health_records`

### Dataset Columns

| Column | Description |
|---|---|
| `patient_id` | Unique patient identifier |
| `age` | Patient age |
| `gender` | Patient gender |
| `region` | Patient region |
| `bmi` | Body Mass Index |
| `blood_pressure` | Blood pressure measurement |
| `cholesterol` | Cholesterol measurement |
| `glucose` | Glucose measurement |
| `disease_risk` | Disease-risk indicator |

> The notebook uses a raw input file named `patient_health_records.csv`. Make sure this source CSV is available in the project folder before running the notebook from the beginning. The uploaded Excel file is the cleaned dataset, not that raw input file.

## Project Workflow

### Part A – Handling Missing Values

The notebook examines missing-value counts and percentages, then demonstrates several approaches:

- Mean imputation
- Median imputation
- Most-frequent (mode) imputation for categorical features
- Missing-value indicator flags
- Random-sample imputation
- K-Nearest Neighbors (KNN) imputation with 5 neighbors
- Iterative imputation (MICE-style) with 10 iterations

It also compares BMI distributions and descriptive statistics across imputation methods.

### Part B – Handling Outliers

The notebook demonstrates:

- **Z-score method:** identifies cholesterol and glucose values where the absolute Z-score is greater than 3.
- **IQR method:** identifies BMI values outside the 1.5 × IQR bounds.
- **Trimming:** removes rows identified as outliers.
- **Percentile capping:** clips BMI, cholesterol, and glucose to their 1st and 99th percentiles.
- **Winsorization:** clips the same variables to their 5th and 95th percentiles.

### Part C – Final Clean Dataset

The final cleaning pipeline:

1. Fills missing `gender` and `region` values using the mode.
2. Uses `IterativeImputer` for `age`, `bmi`, `blood_pressure`, `cholesterol`, `glucose`, and `disease_risk`.
3. Caps `bmi`, `cholesterol`, and `glucose` at the 1st and 99th percentiles.
4. Rounds selected numeric values to one decimal place.
5. Converts `disease_risk` to an integer.
6. Checks the remaining missing values.
7. Exports the cleaned records to `cleaned_patient_health_records.csv`.
8. Compares raw and cleaned distributions using density plots and boxplots.

## Technologies & Libraries

- Python
- Jupyter Notebook
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn

## Installation

Install the required libraries:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn openpyxl jupyter
```

## How to Run

1. Clone or download this repository.
2. Place the raw source file `patient_health_records.csv` in the project folder.
3. Install the required libraries.
4. Open Jupyter Notebook:

   ```bash
   jupyter notebook
   ```

5. Open `Data Cleanser(1).ipynb`.
6. Run the notebook cells in order.
7. The final cleaned CSV will be generated as `cleaned_patient_health_records.csv`.

## Project Structure

```text
Patient-Health-Records-Data-Cleaning/
│
├── Data Cleanser(1).ipynb
├── cleaned_patient_health_records.csv(1).xlsx
├── patient_health_records.csv              # Required raw input
├── cleaned_patient_health_records.csv      # Generated output
└── README.md
```

## Output

The main output is:

`cleaned_patient_health_records.csv`

The notebook also displays:

- Missing-value summary
- Imputation comparison table
- Outlier counts and IQR bounds
- Final dataset dimensions
- Descriptive statistics
- Before-and-after density plots and boxplots

## Important Notes

- The notebook expects `patient_health_records.csv` as its raw input. That raw CSV was not among the two uploaded files used to prepare this README.
- The uploaded Excel file is a cleaned dataset with 1,000 rows and 9 columns.
- The notebook demonstrates alternative imputation and outlier-treatment methods; the final pipeline specifically uses mode imputation, iterative imputation, and 1st–99th percentile capping.
- `disease_risk` is treated as a numeric field during iterative imputation and converted to an integer afterward. For a production machine-learning workflow, review this choice and validate the resulting target labels.
- This is a data-preprocessing exercise, not a clinical diagnostic tool.

## Author
PRAJAPATI BHARGAV


If you found this project useful, feel free to ⭐ the repository.
