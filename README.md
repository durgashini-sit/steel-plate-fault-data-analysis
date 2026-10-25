# Steel Plate Surface Fault Data Analysis

Python-based data cleaning, preprocessing and statistical analysis of steel plate surface-fault data across three defect classes.

## Project Overview

This project was completed as part of the **Data Analytics** module at the Singapore Institute of Technology (SIT).

The project analysed a steel plate surface-fault dataset containing:

- **1,254 observations**
- **27 numerical input features**
- **3 fault classes**
  - `K_Scratch`
  - `Z_Scratch`
  - `Other_Faults`

The objective was to clean and validate the dataset before performing statistical analysis to identify differences between the three fault classes.

> This repository focuses on my individual contribution to the group project: **data cleaning and preprocessing**, followed by **statistical analysis of 13 assigned parameters**.

---

## My Contribution

### Data Cleaning & Preprocessing

I performed the data-quality assessment and preprocessing of the dataset, including:

- Checked all input features for missing values
- Identified **125 missing values** in `Minimum_of_Luminosity`
- Identified **100 missing values** in `Maximum_of_Luminosity`
- Checked for:
  - Duplicate rows
  - Invalid numerical formatting
  - Infinite values
  - Invalid coordinate relationships
  - Non-positive physical measurements
  - Invalid luminosity ranges
  - Invalid steel-type encoding
- Analysed feature distributions before selecting suitable imputation methods
- Applied **class-specific mean or median imputation** depending on the distribution of each fault class
- Preserved all **1,254 observations** without removing rows

### Post-Imputation Validation

After the initial imputation, I identified **11 rows** where:

```text
Minimum_of_Luminosity > Maximum_of_Luminosity
```

These values were logically invalid.

I implemented a constraint-based correction method that recalculated the affected values using valid observations from the same fault class while maintaining the required minimum–maximum relationship.

After correction:

```text
Remaining luminosity conflicts: 0
Missing Minimum_of_Luminosity values: 0
Missing Maximum_of_Luminosity values: 0
```

The final cleaned dataset contained no missing values, duplicate rows, infinite values or identified logical violations.

---

## Statistical Analysis

I performed descriptive statistical analysis on **13 assigned parameters** across the three fault classes.

For each parameter and fault class, I calculated:

- Mean
- Median
- Range
- Standard deviation

These statistics were used to compare:

- Typical parameter values
- Variation within each fault class
- Differences between defect classes
- Parameters that may help distinguish different surface faults

---

## Key Findings

Several differences were identified between the fault classes.

### K_Scratch

- Generally had much larger defect areas and perimeters
- Had substantially higher total luminosity
- Had lower minimum-luminosity values
- Was associated mainly with thinner **A400 steel plates**
- Showed greater variation in several size-related parameters

### Z_Scratch

- Generally contained smaller defects
- Showed lower variation in several size and luminosity parameters
- Was strongly associated with **A300 steel**

### Other_Faults

- Showed the greatest variation in horizontal and vertical defect position
- Covered a wider range of steel-plate thicknesses
- Had more varied production-related characteristics

The analysis also showed that relying only on the mean could be misleading for strongly skewed features, making the **median** an important statistic when interpreting the dataset.

---

## Data Cleaning Workflow

```text
Load Dataset
     ↓
Inspect Dataset Structure
     ↓
Check Missing Values
     ↓
Validate Numerical & Logical Conditions
     ↓
Analyse Feature Distributions
     ↓
Select Mean / Median Imputation
     ↓
Perform Class-Specific Imputation
     ↓
Check for Logical Conflicts
     ↓
Correct Invalid Imputed Values
     ↓
Final Dataset Validation
     ↓
Statistical Analysis
```

---

## Technologies Used

- **Python**
- **Pandas**
- **NumPy**
- **Matplotlib**
- **Jupyter Notebook**
- Descriptive Statistics
- Data Cleaning
- Data Preprocessing
- Data Validation
- Exploratory Data Analysis

---

## Repository Structure

```text
steel-plate-fault-data-analysis/
│
├── README.md
├── steel_plate_analysis.ipynb
└── .gitignore
```

---

## Running the Notebook

1. Clone this repository:

```bash
git clone https://github.com/durgashini-sit/steel-plate-fault-data-analysis.git
```

2. Open the project directory.

3. Launch Jupyter Notebook or JupyterLab.

4. Open:

```text
steel_plate_analysis.ipynb
```

5. Ensure the required dataset is available in the expected file path before running the notebook.

---

## Skills Demonstrated

- Data Cleaning
- Data Preprocessing
- Missing-Value Analysis
- Data Validation
- Statistical Analysis
- Exploratory Data Analysis
- Python Programming
- Pandas
- Jupyter Notebook
- Engineering Data Analysis

---

## Academic Context
This was completed as a group academic project. This repository documents the portions of the project that I personally worked on, primarily **data cleaning, preprocessing, validation and statistical analysis**.
