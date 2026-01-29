# Week 3 Assignment: Stroke Prediction Dataset Analysis

## I 320D: Data Science for Biomedical Informatics | Spring 2026

### 📋 Assignment Version D

---

## 🎯 This Week's Mantra

> **"Every Column Tells a Story"**

In this assignment, you'll apply the 10-Point Data Inspection to a real-world healthcare dataset focused on stroke prediction. By the end, you'll understand not just *what* the data contains, but *why* each variable matters for clinical decision-making.

---

## Learning Objectives

By completing this assignment, you will be able to:

1. ✅ Apply the systematic 10-Point Inspection to a new healthcare dataset
2. ✅ Identify and classify feature types (continuous, discrete, categorical, ordinal)
3. ✅ Detect and document data quality issues (missing values, unexpected values)
4. ✅ Research and document clinical meaning for healthcare variables
5. ✅ Create meaningful data groupings based on clinical standards
6. ✅ Formulate answerable research questions about stroke risk factors

---

## About the Dataset

**Dataset:** Healthcare Dataset - Stroke Prediction  
**Source:** Kaggle  
**File:** `healthcare-dataset-stroke-data.csv`  
**Target Variable:** `stroke` (whether the patient had a stroke)

### Clinical Context

Stroke is the second leading cause of death globally, responsible for approximately 11% of total deaths according to the World Health Organization (WHO). This dataset contains patient information that healthcare professionals use to predict stroke risk. Understanding these variables is crucial for:

- Early identification of high-risk patients
- Preventive care planning
- Resource allocation in healthcare settings
- Clinical decision support systems

---

## Getting Started

First, load the dataset and import your libraries:

```python
# Import libraries


# Load the dataset


# Display first few rows to confirm it loaded

```

---

## Part 1: The 10-Point Data Inspection (40 points)

Complete each inspection step and document your findings.

### Step 1: Shape (4 points)

**Your Code:**
```python

```

**Your Findings:**
- How many rows (observations)? _______________
- How many columns (features)? _______________
- What does each row represent in clinical terms? _______________

---

### Step 2: Column Names (4 points)

**Your Code:**
```python

```

**Your Findings:**
- List all column names:

- Which columns might need further research to understand?

---

### Step 3: Data Types (4 points)

**Your Code:**
```python

```

**Your Findings:**
- Which columns are numeric?

- Which columns are categorical (object/string)?

- Are there any data types that seem incorrect?

---

### Step 4: First Look (4 points)

**Your Code:**
```python

```

**Your Findings:**
- What do the actual values look like?

- Do you notice anything unusual or unexpected?

- Are there any values that look like they might be placeholders for missing data?

---

### Step 5: Last Look (4 points)

**Your Code:**
```python

```

**Your Findings:**
- Does the data end cleanly?

- Are the last rows consistent with the first rows?

---

### Step 6: Memory Usage (4 points)

**Your Code:**
```python

```

**Your Findings:**
- How much memory does the dataset use? _______________ MB
- Is this a "small" or "large" dataset by data science standards?

---

### Step 7: Missing Values (4 points)

**Your Code:**
```python

```

**Your Findings:**
- Which columns have missing values (according to `.isnull()`)?

- What percentage of each column is missing?

- ⚠️ **IMPORTANT:** Are there any values that *look* like data but actually represent missing information? (Hint: Look carefully at the actual values in each column)

---

### Step 8: Duplicates (4 points)

**Your Code:**
```python

```

**Your Findings:**
- Are there any duplicate rows? _______________
- Are all patient IDs unique? _______________

---

### Step 9: Basic Statistics (4 points)

**Your Code:**
```python

```

**Your Findings:**
- What is the age range in the dataset? _______________ to _______________
- What is the range of average glucose levels? _______________ to _______________
- What is the range of BMI values? _______________ to _______________
- Do any min/max values seem impossible or clinically unlikely?

---

### Step 10: Unique Counts (4 points)

**Your Code:**
```python

```

**Your Findings:**
- Which columns have very few unique values (likely categorical)?

- Which columns have many unique values (likely continuous or IDs)?

- Does the number of unique IDs match the number of rows? _______________

---

## Part 2: Data Dictionary (20 points)

Complete the following data dictionary. For each column, you must:
1. **Research** the clinical meaning
2. **Identify** the feature type (Continuous, Discrete, Categorical-Nominal, Categorical-Ordinal, Binary, Identifier)
3. **Document** the valid values/range you observe
4. **Note** any issues or questions

| Column | Description | Feature Type | Valid Values/Range | Notes/Issues |
|--------|-------------|--------------|-------------------|--------------|
| `id` | | | | |
| `gender` | | | | |
| `age` | | | | |
| `hypertension` | | | | |
| `heart_disease` | | | | |
| `ever_married` | | | | |
| `work_type` | | | | |
| `Residence_type` | | | | |
| `avg_glucose_level` | | | | |
| `bmi` | | | | |
| `smoking_status` | | | | |
| `stroke` | | | | |

### Clinical Research Questions for Version D

Answer these questions based on your research (you may need to use Google):

**1. What is "metabolic syndrome" and how do the variables in our dataset relate to it? (Consider glucose, BMI, and hypertension)**

Your answer:

---

**2. What is the difference between ischemic stroke and hemorrhagic stroke? Does our dataset tell us which type of stroke patients had? Why might this matter?**

Your answer:

---

**3. How does "ever_married" potentially serve as a proxy for social support? What does research say about social isolation and stroke risk?**

Your answer:

---

**4. What is the "obesity paradox" in stroke outcomes? How might this affect the interpretation of BMI data in our dataset?**

Your answer:

---

## Part 3: Data Validation (15 points)

### 3.1 Age Validation (5 points)

Write code to check:
- How many ages are below 0?
- How many ages are above 120?
- What is the actual age range?
- How many patients are under 18?
- How many patients are under 1 year old?

**Your Code:**
```python

```

**Your Findings:**

- Are there any impossible age values?

- Does it make clinical sense to have very young patients (infants) in a stroke dataset?

- What might ages like "0.72" or "1.24" represent?

---

### 3.2 BMI Validation (5 points)

Write code to examine BMI values closely. Look at value counts and check for any unusual values.

**Your Code:**
```python

```

**Your Findings:**

- Did you find any BMI values that aren't numbers?

- How many of these non-numeric values are there?

- Is this detected by `.isnull()`? Why or why not?

- What would happen if you tried to calculate the mean BMI without handling this?

---

### 3.3 Smoking Status Validation (5 points)

Write code to see all unique values and their counts for smoking status.

**Your Code:**
```python

```

**Your Findings:**

- What are all the possible smoking status values?

- How many records have "Unknown" smoking status?

- Should "Unknown" be treated as missing data or as a valid category? Explain your reasoning.

---

## Part 4: Create Clinical Age Groups (10 points)

Create a new column called `age_group` that categorizes patients into clinically-meaningful groups.

### Version D: Cardiovascular Risk Categories

Use these categories based on cardiovascular screening guidelines:

| Age Group | Range | Clinical Rationale |
|-----------|-------|-------------------|
| Pediatric | 0-17 | Not typically screened for CV risk |
| Low Risk Age | 18-39 | Baseline screening, low absolute risk |
| Screening Age | 40-49 | Begin regular cholesterol/BP screening |
| Elevated Risk | 50-64 | 10-year CV risk calculation recommended |
| High Risk | 65-74 | Aggressive risk factor management |
| Very High Risk | 75+ | Balance treatment benefit vs. frailty |

### Your Code:

```python
# Create the age_group column
# You can use a custom function with .apply() OR pd.cut()
# Remember: if using pd.cut(), use include_lowest=True!


```

### Verify your groupings worked:

```python
# Show counts per age group

```

### Calculate stroke rate by age group:

```python
# Calculate the percentage of patients who had a stroke in each age group

```

### Analysis Questions:

**1. How many patients are in each cardiovascular risk category?**

Your answer:

---

**2. What is the stroke rate (percentage) for each risk category?**

Your answer:

---

**3. The "Screening Age" (40-49) group is when cardiovascular screening typically begins. What is the stroke rate in this group compared to the previous group? Does this support starting screening at age 40?**

Your answer:

---

## Part 5: Research Questions (15 points)

### 5.1 Write Three Answerable Questions (9 points)

Write three questions that THIS dataset can answer. Remember: the data can show relationships and patterns, but cannot prove causation.

**Your questions must explore these specific areas:**

1. **A question about the combination of multiple risk factors (create a "risk count" variable):**


---

2. **A question comparing "never smoked" vs "formerly smoked" vs "smokes":**


---

3. **A question about ever_married status and age:**


---

### 5.2 Identify One Question the Data CANNOT Answer (3 points)

Write one question about **time or disease progression** that this dataset cannot answer, and explain why.

**Question:**


**Why it cannot be answered with this data:**


---

### 5.3 Grouping Analysis (3 points)

Answer this question using a groupby analysis:

**"What percentage of patients have hypertension in each work_type category?"**

**Your Code:**
```python

```

**Your Interpretation:**

Which work type has the highest rate of hypertension? Which has the lowest? What might explain these differences (consider age distribution, stress, lifestyle)?


---

## Part 6: Target Variable Analysis (Bonus - 5 points)

The `stroke` column is our **target variable** - what we're trying to predict. Analyze its distribution.

**Your Code:**
```python
# Show the count and percentage of stroke vs no-stroke

```

### Bonus Questions:

**1. What percentage of patients in this dataset had a stroke?**

Your answer:

---

**2. Is this dataset balanced or imbalanced? (A balanced dataset has roughly equal classes)**

Your answer:

---

**3. Why does class imbalance matter for machine learning? (You may need to research this)**

Your answer:

---

**4. In the real world, would you expect stroke rates to be this high or this low? What might this tell you about how this dataset was collected?**

Your answer:

---

## Submission Checklist

Before submitting, verify you have completed:

- [ ] **Part 1:** All 10 inspection steps with code AND written findings
- [ ] **Part 2:** Complete data dictionary with all 12 columns filled in
- [ ] **Part 2:** Answered all 4 clinical research questions
- [ ] **Part 3:** All 3 validation checks with code and answers
- [ ] **Part 4:** Created `age_group` column using the **Cardiovascular Risk Categories**
- [ ] **Part 4:** Calculated stroke rate by age group with interpretation
- [ ] **Part 5:** Three research questions (risk count, smoking comparison, marriage+age)
- [ ] **Part 5:** One unanswerable question about time/progression
- [ ] **Part 5:** Hypertension by work_type groupby analysis
- [ ] **Bonus (Optional):** Target variable analysis

---

## Grading Rubric

| Component | Points | Requirements for Full Credit |
|-----------|--------|------------------------------|
| Part 1: 10-Point Inspection | 40 | All 10 steps complete with working code AND thoughtful written analysis |
| Part 2: Data Dictionary | 20 | All 12 columns documented with correct feature types and clinical research |
| Part 3: Data Validation | 15 | All validation checks complete with working code and insightful answers |
| Part 4: Age Groups | 10 | Working code that creates correct groups AND meaningful interpretation |
| Part 5: Research Questions | 15 | Three good questions in specified areas, one clear limitation, groupby analysis complete |
| **Bonus:** Target Analysis | +5 | Thoughtful analysis of class imbalance with real-world connection |
| **Total** | 100 (+5 bonus) | |

---

## Hints (Read Before You Get Stuck!)

### ⚠️ Common Pitfalls:

1. **One column has "N/A" as a STRING, not as a true null value**
   - The `.isnull()` method won't detect it
   - Look at your data carefully with `value_counts()`
   - You'll need to handle it before any numeric calculations on that column

2. **"Unknown" in one column** - is it missing data or a valid category? There's no single right answer, but you need to justify your choice.

3. **Very small ages** - if you see ages like 0.72 or 1.24, think about what these represent (hint: it's not an error!)

4. **Class imbalance** - pay attention to how many patients actually had strokes versus didn't.

### 💡 Pro Tips:

- Use `value_counts()` liberally to understand categorical columns
- Use `value_counts(dropna=False)` to see if there are any null values
- When something seems weird, investigate it—don't assume it's an error
- Read your data's "Data Card" on Kaggle for additional context
- Always state what the data CAN tell you vs. what would require additional information

---

## Useful Resources

- **Kaggle Dataset Page:** https://www.kaggle.com/datasets/fedesoriano/stroke-prediction-dataset
- **Metabolic Syndrome:** https://www.heart.org/en/health-topics/metabolic-syndrome
- **Cardiovascular Screening Guidelines:** https://www.uspreventiveservicestaskforce.org/uspstf/recommendation/cardiovascular-disease-risk-screening-with-electrocardiography
- **Obesity Paradox:** https://www.ahajournals.org/doi/10.1161/STROKEAHA.111.632489
- **Pandas Documentation:** https://pandas.pydata.org/docs/

---

*Remember: "Every Column Tells a Story" - your job is to figure out what that story is!*

---

**Due Date:** [See Canvas]

**Submission:** Upload your completed Jupyter notebook (.ipynb) to Canvas
