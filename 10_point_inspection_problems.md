# Week 3 Practice Problems: The 10-Point Inspection
## Healthcare Stroke Prediction Dataset

**Course:** I 320D: Data Science for Biomedical Informatics  
**Mantra:** "Every Column Tells a Story"

---

## Introduction

You have been provided with a healthcare dataset containing patient information used to predict stroke risk. Your task is to demonstrate mastery of the **10-Point Inspection** by completing the problems below.

**Instructions:**
- Add new cells to your Jupyter notebook for each problem
- Include both the code AND your interpretation/analysis in markdown cells
- Remember: understanding WHY matters as much as HOW

---

## PART 1: The 10-Point Inspection (Problems 1-10)

Each problem corresponds to one step of the 10-Point Inspection from the pre-class video.

---

### Problem 1: Shape
**What It Tells You:** How many rows (observations) and columns (features)

**Task:** Write code to determine the shape of the dataset and answer the following questions:

```python
# YOUR CODE HERE
```

**Questions to Answer in a Markdown Cell:**
1. How many patient records are in this dataset?
2. How many features/variables are captured for each patient?
3. Compare this to the healthcare dataset discussed in the video (55,500 records, 15 columns). What might explain the difference in size?

---

### Problem 2: Column Names
**What It Tells You:** What information is captured

**Task:** Display all column names and categorize them by type.

```python
# YOUR CODE HERE
```

**Questions to Answer in a Markdown Cell:**
1. List all column names
2. Organize columns into the following categories:
   - **Patient Demographics:** (which columns?)
   - **Clinical Information:** (which columns?)
   - **Lifestyle Factors:** (which columns?)
   - **Outcome Variable:** (which column?)
3. Which column do you think is the **target variable** for prediction? Why?

---

### Problem 3: Data Types
**What It Tells You:** Numeric, categorical, datetime, text

**Task:** Display the data types for each column.

```python
# YOUR CODE HERE
```

**Questions to Answer in a Markdown Cell:**
1. Which columns are numeric (int64 or float64)?
2. Which columns are stored as "object" type (text/categorical)?
3. Is `hypertension` stored as the appropriate type? Explain why or why not.
4. Why might `age` be stored as float64 instead of int64? (Hint: Look at the minimum age value)

---

### Problem 4: First Look (Head)
**What It Tells You:** Sample of actual values

**Task:** Display the first 10 rows of the dataset.

```python
# YOUR CODE HERE
```

**Questions to Answer in a Markdown Cell:**
1. Look at the `bmi` column. Do you notice anything unusual?
2. What values appear in the `smoking_status` column?
3. Based on the first 10 rows, do you see mostly stroke patients (stroke=1) or non-stroke patients (stroke=0)?

---

### Problem 5: Last Look (Tail)
**What It Tells You:** Check if data ends cleanly

**Task:** Display the last 10 rows of the dataset.

```python
# YOUR CODE HERE
```

**Questions to Answer in a Markdown Cell:**
1. Does the data end cleanly or are there any obvious issues?
2. What is the youngest patient in the last 10 rows? Does this seem reasonable?
3. Are there any rows with children in the dataset? (Hint: Look at `work_type`)

---

### Problem 6: Memory Usage
**What It Tells You:** Size in MB, scalability concerns

**Task:** Calculate the memory usage of the dataframe in megabytes (MB).

```python
# YOUR CODE HERE
# Hint: Use df.memory_usage(deep=True).sum() and divide by 1e6 for MB
```

**Questions to Answer in a Markdown Cell:**
1. How many megabytes does this dataset use?
2. Would this dataset fit comfortably in memory on a laptop with 8GB RAM?
3. If you had a dataset 1,000 times larger, would you need a different approach?

---

### Problem 7: Missing Values
**What It Tells You:** Gaps in data collection

**Task:** Count the missing values in each column AND calculate the percentage missing.

```python
# YOUR CODE HERE
# Part A: Count missing values per column
# Part B: Calculate percentage missing per column
# Hint: (df.isnull().sum() / len(df) * 100)
```

**Questions to Answer in a Markdown Cell:**
1. Which column has missing values? How many are missing?
2. What percentage of records are missing this value?
3. **Clinical Thinking:** Why might BMI be missing more often than other variables? (Think about how data is collected in healthcare settings)
4. Is this missing data likely **MCAR, MAR, or MNAR**? Justify your answer.

---

### Problem 8: Duplicates
**What It Tells You:** Data quality issues

**Task:** Check for and count duplicate rows.

```python
# YOUR CODE HERE
# Part A: Count total duplicates
# Part B: If duplicates exist, display them
```

**Questions to Answer in a Markdown Cell:**
1. How many duplicate rows exist in the dataset?
2. If there were duplicates, what might cause them in a healthcare context?
3. Check if the `id` column is truly unique (i.e., no duplicate IDs)

---

### Problem 9: Basic Statistics
**What It Tells You:** Min, max, mean, quartiles

**Task:** Generate descriptive statistics for all numeric columns.

```python
# YOUR CODE HERE
```

**Questions to Answer in a Markdown Cell:**

1. **Age Analysis:**
   - What is the age range (min to max)?
   - What does a minimum age of 0.08 represent? (Hint: 0.08 years ≈ 1 month)
   - Is this dataset appropriate for pediatric stroke research? Why or why not?

2. **BMI Analysis:**
   - What is the BMI range?
   - Is a BMI of 97.6 medically plausible? What might this indicate?
   - According to CDC guidelines, what BMI range is considered "healthy"?

3. **Glucose Analysis:**
   - What is the average glucose level?
   - What is considered a normal fasting glucose level? (Hint: Research this!)
   - What percentage of patients might have values indicating diabetes (>126 mg/dL)?

4. **Target Variable (Stroke):**
   - What percentage of patients had a stroke? (mean of binary variable = proportion)
   - Is this dataset **balanced** or **imbalanced**? Why does this matter for machine learning?

---

### Problem 10: Unique Counts
**What It Tells You:** Cardinality of each column

**Task:** Count the unique values in each column.

```python
# YOUR CODE HERE
```

**Questions to Answer in a Markdown Cell:**
1. Which column has the highest cardinality? Why?
2. How many unique values does `gender` have? Are they what you expected?
3. How many categories exist for `smoking_status`? What are they?
4. Based on cardinality, which columns would you classify as:
   - **Identifiers:** (shouldn't be used for analysis)
   - **Categorical (low cardinality):** 
   - **Continuous/High cardinality:**

---

## PART 2: Data Validation (Problems 11-14)

Now that you've completed the 10-Point Inspection, perform validation checks to ensure data quality.

---

### Problem 11: Age Validation

**Task:** Check for invalid age values.

```python
# YOUR CODE HERE
print("--- Age Validation ---")
# Check for negative ages
# Check for ages above 120 (implausible)
# Check for infants (age < 1) - how many?
```

**Questions to Answer:**
1. Are there any impossible age values (negative or >120)?
2. How many infants (age < 1 year) are in the dataset?
3. Should infants be included when studying stroke? Defend your position.

---

### Problem 12: BMI Validation

**Task:** Check for clinically implausible BMI values.

```python
# YOUR CODE HERE
print("--- BMI Validation ---")
# Check for BMI < 10 (likely error)
# Check for BMI > 60 (extreme but possible)
# Check for BMI > 80 (almost certainly error)
```

**Questions to Answer:**
1. How many patients have BMI > 60?
2. Are these errors or genuine extreme cases?
3. What would you recommend doing with these extreme values?

---

### Problem 13: Binary Variable Validation

**Task:** Verify that binary columns only contain 0 and 1.

```python
# YOUR CODE HERE
# Check unique values for: hypertension, heart_disease, stroke
```

**Questions to Answer:**
1. Do `hypertension`, `heart_disease`, and `stroke` only contain 0 and 1?
2. What would it mean if you found a value of 2 in `hypertension`?

---

### Problem 14: Categorical Consistency

**Task:** Check for unexpected categories in text columns.

```python
# YOUR CODE HERE
# Display value_counts() for: gender, ever_married, work_type, Residence_type, smoking_status
```

**Questions to Answer:**
1. Does `gender` contain only "Male" and "Female"? If not, what else?
2. What categories exist in `work_type`? Do they make sense?
3. What does "Unknown" in `smoking_status` mean? How many patients have this?

---

## PART 3: Feature Type Classification (Problem 15)

---

### Problem 15: Create a Data Dictionary

**Task:** Create a comprehensive data dictionary table with the following columns:
- Column Name
- Description (research what it means!)
- Feature Type (Continuous, Discrete, Categorical Nominal, Categorical Ordinal, Binary, Identifier)
- Range/Values
- Notes (any issues or considerations)

```python
# Create a markdown table or use pd.DataFrame to display your data dictionary
# Example structure:
data_dict = {
    'Column': [],
    'Description': [],
    'Feature_Type': [],
    'Range_Values': [],
    'Notes': []
}

# YOUR CODE HERE - Fill in for all 12 columns
```

**Hint for Feature Types:**
| Feature Type | Definition | Example |
|--------------|------------|---------|
| Continuous | Can take any value in a range | age, bmi, glucose |
| Discrete | Countable integers | room number |
| Categorical (Nominal) | Categories, no order | gender, work_type |
| Categorical (Ordinal) | Categories with order | education level |
| Binary | Only 0/1 or Yes/No | hypertension, stroke |
| Identifier | Unique ID, not for analysis | id |

---

## PART 4: Clinical Groupings (Problems 16-18)

Create meaningful groups using clinically-relevant categories.

---

### Problem 16: Age Groups (Clinical Categories)

**Task:** Create age groups using clinically relevant boundaries.

```python
# YOUR CODE HERE
# Create an 'AgeGroup' column with these clinical categories:
# - 'Infant' (0-1)
# - 'Child' (1-12)
# - 'Adolescent' (12-18)
# - 'Young Adult' (18-40)
# - 'Middle-Aged' (40-65)
# - 'Senior' (65+)

# Method 1: Using pd.cut() with include_lowest=True
# Method 2: Using a custom function with df.apply()

# Display the distribution of age groups
```

**Questions to Answer:**
1. Which age group has the most patients?
2. Which age group has the highest stroke rate? (Hint: use groupby)

---

### Problem 17: BMI Categories (WHO Standards)

**Task:** Create BMI categories using WHO classification.

```python
# YOUR CODE HERE
# Create a 'BMI_Category' column:
# - 'Underweight': BMI < 18.5
# - 'Normal': 18.5 <= BMI < 25
# - 'Overweight': 25 <= BMI < 30
# - 'Obese': BMI >= 30

# Handle missing BMI values appropriately

# Display the distribution and stroke rate by BMI category
```

---

### Problem 18: Glucose Categories (Clinical Thresholds)

**Task:** Create glucose categories based on clinical diabetes thresholds.

```python
# YOUR CODE HERE
# Create a 'Glucose_Category' column:
# - 'Normal': glucose < 100
# - 'Prediabetes': 100 <= glucose < 126
# - 'Diabetes Range': glucose >= 126

# Note: These thresholds are based on fasting glucose (which this may not be)

# Compare stroke rates across glucose categories
```

---

## PART 5: Research Questions (Problems 19-20)

---

### Problem 19: Questions Your Data CAN Answer

**Task:** Write THREE questions that this dataset can answer, then write code to answer one of them.

**Examples of answerable questions:**
- "Is there a relationship between age and stroke occurrence?"
- "Do patients with hypertension have higher stroke rates?"
- "What is the distribution of BMI among stroke patients vs. non-stroke patients?"

```python
# YOUR CODE HERE
# Answer one of your questions with code and visualization
```

---

### Problem 20: Questions Your Data CANNOT Answer

**Task:** Write TWO questions that this dataset CANNOT answer and explain why.

**Consider:**
- Causation vs. correlation
- Missing variables
- Temporal limitations
- Selection bias

**Example:**
> "Does smoking CAUSE strokes?" - This dataset shows correlation, not causation. We don't know if smokers have other risk factors, when they started smoking, or if quitting reduces risk.

---

## BONUS CHALLENGE: Target Variable Analysis

**Task:** Analyze the target variable (`stroke`) in depth.

```python
# YOUR CODE HERE
# 1. Calculate the stroke rate (% of patients who had stroke)
# 2. Create a function to compare any variable's distribution between stroke=0 and stroke=1
# 3. Identify which variable shows the biggest difference between stroke/no-stroke groups
```

**Questions:**
1. Is this an imbalanced classification problem?
2. What strategies might you use for modeling with imbalanced data?
3. Which single feature appears most predictive of stroke? (correlation ≠ causation!)

---

## Submission Checklist

Before submitting your notebook, verify:

- [ ] All 10 inspection steps are completed with code AND interpretation
- [ ] Validation checks identify any data quality issues
- [ ] Data dictionary includes all 12 columns with feature types
- [ ] At least 2 clinical groupings are created
- [ ] 3 answerable questions are identified
- [ ] 2 unanswerable questions are explained
- [ ] All markdown cells include thoughtful clinical interpretation

---

## Rubric Preview

| Component | Points | Criteria |
|-----------|--------|----------|
| 10-Point Inspection (1-10) | 40 | Complete code + interpretation for each step |
| Data Validation (11-14) | 15 | Identifies issues, explains clinical implications |
| Data Dictionary (15) | 15 | All columns documented with correct feature types |
| Clinical Groupings (16-18) | 15 | Uses appropriate clinical thresholds |
| Research Questions (19-20) | 15 | Distinguishes answerable from unanswerable |

---

**Remember:** "Every Column Tells a Story" — your job is to figure out what that story is!
