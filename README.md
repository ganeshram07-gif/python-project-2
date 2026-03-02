# Titanic Dataset Analysis Using Pandas Series and DataFrames

## Project Overview
This project analyzes the Titanic test dataset (`tested.csv`) using Python **Pandas** to demonstrate Series and DataFrame operations. The notebook performs data cleaning, exploration, and statistical analysis to uncover survival patterns across passenger demographics and travel details.

This educational project showcases real-world Pandas techniques including indexing, grouping, pivot tables, missing data handling, and data merging - perfect for data analysis students and Python learners.

***

## Problem Statement
Analyze Titanic test dataset (418 passengers) to understand survival patterns through Pandas operations:

- Handle missing values in Age, Fare, and Embarked columns
- Examine survival trends by Gender, Pclass, and Embarkation port
- Create pivot tables crossing Pclass × Gender survival rates
- Calculate key statistics: survival rate (36.36%), highest fare ($512.33)

***

## Technologies Used
- **Python 3.8+**
- **Pandas** (Data manipulation & analysis)
- **Jupyter Notebook / Google Colab**
- **NumPy** (Numerical operations)

***

## Dataset Description
**`tested.csv`** - Titanic test dataset (418 entries, 12 columns):

| Column | Description | Missing Values |
|--------|-------------|----------------|
| PassengerId | Unique ID | 0 |
| Survived | 0=No, 1=Yes | 0 |
| Pclass | Passenger class (1,2,3) | 0 |
| Name | Passenger name | 0 |
| Sex | Gender | 0 |
| Age | Age in years | 86 |
| SibSp | Siblings/Spouses aboard | 0 |
| Parch | Parents/Children aboard | 0 |
| Ticket | Ticket number | 0 |
| Fare | Passenger fare | 1 |
| Cabin | Cabin number | 327 |
| Embarked | Port: C/Q/S | 0 |

***

## Implementation Details

### 1. Data Loading & Series Creation
```python
import pandas as pd
df = pd.read_csv("tested.csv")
age_series = df["Age"]
fare_series = df["Fare"]
survived_series = df["Survived"]
```

### 2. Data Inspection
```python
df.head()        # First 10 rows
df.info()        # Data types & missing values
df.describe()    # Statistical summary
```

### 3. Missing Data Handling
```python
df["Age"].fillna(df["Age"].mean(), inplace=True)      # Age: 30.27 mean
df["Fare"].fillna(df["Fare"].median(), inplace=True)  # Fare: median
df["Embarked"].fillna(df["Embarked"].mode()[0], inplace=True)
```

### 4. Advanced Analysis
```python
# Pivot: Survival by Pclass × Gender
pivot = df.pivot_table(values="Survived", index="Pclass", 
                      columns="Gender", aggfunc="mean")

# Groupby insights
df.groupby("Gender")["Survived"].mean()
df.groupby("Pclass")["Age"].mean()
df.groupby("Embarked")["Survived"].sum()
```

### 5. Key Calculations
```python
survival_rate = (df["Survived"].mean() * 100)  # 36.36%
max_fare = df["Fare"].max()                   # 512.33
```

***

## Key Findings

| Analysis | Result |
|----------|--------|
| **Survival Rate** | 36.36% |
| **Highest Fare** | $512.33 |
| **Avg Age by Class** | 1st: 40.0, 2nd: 28.9, 3rd: 26.1 |
| **Gender Survival** | Female: 100%, Male: 0% (sample) |
| **Embarked Survivors** | C: 40, Q: 24, S: 88 |

***

## Project Objectives Achieved
- ✅ Loaded & inspected Titanic test dataset (418 passengers)
- ✅ Cleaned missing values using mean/median/mode
- ✅ Created Series for Age, Fare, Survived columns
- ✅ Applied `loc/iloc` indexing and slicing
- ✅ Built pivot tables for Pclass × Gender analysis
- ✅ Performed groupby aggregations (mean, sum)
- ✅ Merged class labels (1→First, 2→Second, 3→Third)
- ✅ Calculated survival statistics and patterns

***

## Key Learning Outcomes
- **Data Cleaning**: `fillna()`, mean/median/mode imputation
- **Indexing**: `loc[]`, `iloc[]`, boolean filtering
- **Reshaping**: `pivot_table()`, column renaming
- **Grouping**: `groupby()` with multiple aggregations
- **Merging**: `pd.merge()` for dataset enrichment
- **Insights**: Extracting business value from raw data

***

## 🚀 Quick Start

```bash
# Clone repository
git clone https://github.com/ganeshram/titanic-analysis.git
cd titanic-analysis

# Install dependencies
pip install pandas jupyter

# Launch notebook
jupyter notebook titanic_analysis.ipynb
```

**Requirements**: Place `tested.csv` in project root or update Colab path.

***

## 📁 Repository Structure
```
titanic-analysis/
├── titanic_analysis.ipynb     # Main analysis notebook
├── tested.csv                # Titanic test dataset
├── README.md                 # This file
└── requirements.txt          # pip install -r requirements.txt
```

***

## Future Enhancements
- [ ] **Visualizations**: Seaborn histograms, correlation heatmap
- [ ] **Feature Engineering**: Family size, age bins, title extraction
- [ ] **Machine Learning**: Logistic Regression survival prediction
- [ ] **Model Validation**: Train/test split, cross-validation

***

## 📄 License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file.

***

## 👨‍💻 Author
**Ganesh Ram S**  
*College Student | kamaraj college, Thoothukudi , Tamil Nadu, India*  
💻 Python Data Analysis 


