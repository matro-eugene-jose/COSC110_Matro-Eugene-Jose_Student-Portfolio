# Laboratory Activity 1: Computational Thinking with the Titanic Dataset using Python

### 1. Introduction

This activity documents a step‑by‑step computational thinking approach to analyze the Titanic dataset. We cover data loading, exploration, cleaning, statistical computation, and visualization in a structured lab‑report format.

---

### 2. Materials & Environment

* **Software**: Google Colab or Jupyter Notebook
* **Libraries**:

  * pandas
  * matplotlib
  
* **Data file**: `titanic.csv`

---

### 3. Methods

#### 3.1 Data Acquisition & Initial Inspection

**Goal**: Load the data and grasp its structure.

```
import pandas as pd

# 1. Load the CSV into a DataFrame
df = pd.read_csv('titanic.csv')

# 2. Preview rows and schema
df.head()
df.info()
df.describe()
```

**Pseudocode**:

```
Load dataset from CSV
Show first 5 records
display data types and null counts
compute basic summary statistics
```

---

#### 3.2 Missing‐Value Analysis & Imputation

**Goal**: Identify and resolve nulls.

| Column   | # Nulls | Action Taken                     |
| -------- | ------- | -------------------------------- |
| Cabin    | 687     | **DROP** (too sparse)            |
| Age      | 177     | **FILL** with median             |
| Embarked | 2       | **FILL** with mode (most common) |

```
# Drop and impute
cols_to_drop = ['Cabin']
df.drop(columns=cols_to_drop, inplace=True)
df['Age'].fillna(df['Age'].median(), inplace=True)
df['Embarked'].fillna(df['Embarked'].mode()[0], inplace=True)
df.info()
```

**Flowchart**:

```
Start -> count nulls per column -> if null_count > 50% then drop -> else if null_count > 0 then fill -> verify no nulls -> End
```

---

#### 3.3 Survival Rate Calculation

**Goal**: Determine overall survival probability.

```
survival_rate = df['Survived'].mean()
print(f"Overall Survival Rate: {survival_rate:.2%}")
```

**Interpretation**: At \~38.4%, fewer than half of the passengers survived.

---

#### 3.4 Age vs. Survival Analysis

**Goal**: Compare age distributions for survivors and non‑survivors.

```
import matplotlib.pyplot as plt

# Histogram overlay
plt.hist(df[df['Survived']==1]['Age'], bins=20, label='Survived', alpha=0.5)
plt.hist(df[df['Survived']==0]['Age'], bins=20, label='Did Not Survive', alpha=0.5)
plt.xlabel('Age')
plt.ylabel('Count')
plt.legend()
plt.show()

# Average ages
avg_survived = df[df['Survived']==1]['Age'].mean()
avg_nonsurv = df[df['Survived']==0]['Age'].mean()
print(f"Avg Age (Survived): {avg_survived:.1f}")
print(f"Avg Age (Did Not Survive): {avg_nonsurv:.1f}")
```

**Results**:

* **Avg Age of Survivors**: 28.29 years
* **Avg Age of Non‑Survivors**: 30.03 years

**Conclusion**: Younger passengers had a slightly higher chance of survival, consistent with "women and children first" policy.

---

### 4. Summary & Insights

1. **Data completeness**: Dropped `Cabin`, imputed `Age` & `Embarked`.
2. **Survival rate**: \~38% survived.
3. **Age effect**: Survivors were marginally younger on average.

**Generalization**: This pipeline—load → inspect → clean → compute → visualize—applies broadly to tabular datasets in data science.
