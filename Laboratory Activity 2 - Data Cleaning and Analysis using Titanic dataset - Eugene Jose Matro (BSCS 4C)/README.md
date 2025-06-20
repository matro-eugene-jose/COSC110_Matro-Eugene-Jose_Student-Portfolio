# Laboratory Activity 2: Data Cleaning and Analysis using Titanic dataset

### 1. Introduction

This activity details a structured data-preparation and exploratory-analysis workflow applied to the Titanic training dataset. The lab covers:

1. Data acquisition and initial inspection.
2. Missing-value analysis and imputation.
3. Duplicate detection and removal.
4. Data-type conversion and column standardization.
5. Saving the cleaned dataset.
6. Two creative exploratory analyses using cleaned data.

---

### 2. Materials & Environment

* **Platform**: Google Colab / Jupyter Notebook
* **Languages & Libraries**:

  * Python 3.x
  * pandas
  * matplotlib
* **Files**:

  * `train.csv` (original dataset)
  * `titanic_cleaned.csv` (output of cleaning step)

---

### 3. Methods

#### 3.1 Data Acquisition & Inspection

**Goal**: Load the dataset and examine its structure.

`
import pandas as pd
df = pd.read_csv('train.csv')
df.head()
df.info()
`

*Pseudocode*:

`
Load CSV into DataFrame
Display first five rows
Show column data types and count non-null values
`

---

#### 3.2 Missing-Value Analysis & Imputation

**Goal**: Identify columns with nulls and apply imputation or removal.

| Column   | Null Count | Action                       |
| -------- | ---------- | ---------------------------- |
| Cabin    | 687        | Drop column (sparse data)    |
| Age      | 177        | Fill missing with median age |
| Embarked | 2          | Fill missing with mode value |

`
# Drop sparse column
df.drop(columns=['Cabin'], inplace=True)

# Impute Age & Embarked
df['Age'].fillna(df['Age'].median(), inplace=True)
df['Embarked'].fillna(df['Embarked'].mode()[0], inplace=True)
`

*Flowchart*:

```
Start -> count nulls per column -> if >50% drop -> elif >0% fill -> End
```

---

#### 3.3 Duplicate Detection & Removal

**Goal**: Ensure unique records.

`
dup_count = df.duplicated().sum()
if dup_count > 0:
    df.drop_duplicates(inplace=True)
`

---

#### 3.4 Data-Type Conversion & Standardization

**Goal**: Optimize memory and ensure consistency.

`
# Convert categorical fields
df['Survived'] = df['Survived'].astype('category')
df['Pclass']   = df['Pclass'].astype('category')

# Standardize column names
df.columns = df.columns.str.lower()
`

---

#### 3.5 Saving the Cleaned Dataset

`
df.to_csv('titanic_cleaned.csv', index=False)
`

---

### 4. Exploratory Analyses

#### 4.1 Survival Rate by Family Size

**Objective**: Investigate how traveling alone vs. with family affected survival.

`
# Compute family size as sibsp + parch
 df['family_size'] = df['sibsp'] + df['parch']
 
# Group and plot
survival_by_family = df.groupby('family_size')['survived'].mean()
survival_by_family.plot(kind='bar')
plt.xlabel('Family Size')
plt.ylabel('Survival Rate')
plt.title('Survival Rate vs. Family Size')
plt.show()
`

**Insight**: Passengers traveling with 1–3 family members had higher survival rates, while large families fared worse.

---

#### 4.2 Fare vs. Ticket Class Analysis

**Objective**: Examine fare distribution across passenger classes and its relation to survival.

`
import matplotlib.pyplot as plt

# Boxplot of fare by class
 df.boxplot(column='fare', by='pclass')
plt.title('Fare Distribution by Pclass')
plt.suptitle('')
plt.xlabel('Passenger Class')
plt.ylabel('Fare')
plt.show()

# Survival rates per class
survival_by_class = df.groupby('pclass')['survived'].mean()
survival_by_class.plot(kind='bar')
plt.title('Survival Rate by Pclass')
plt.xlabel('Passenger Class')
plt.ylabel('Survival Rate')
plt.show()
`

**Insight**: Higher classes paid steeper fares and enjoyed significantly higher survival rates, illustrating class-based evacuation priority.

---

### 5. Summary & Insights

* **Cleaning**: Dropped `Cabin`, imputed `Age` and `Embarked`, removed duplicates, converted types, standardized names.
* **Explorations**:

  1. Family size influences survival: small families fare best.
  2. Fare and class correlate: wealthier passengers had a clear survival advantage.

*This report framework can be adapted to other datasets requiring rigorous cleaning and targeted exploratory analyses.*
