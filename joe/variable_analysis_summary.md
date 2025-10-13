# Variable Analysis Summary
## Student Habits vs Academic Performance Dataset

**Notebook:** `variable_analysis.ipynb`
**Purpose:** Comprehensive exploratory data analysis of all variables in the dataset following academic statistical standards.

---

## 1. Data Loading and Initial Inspection

**What was done:** Loaded the student habits dataset with 1,000 students and 16 variables, ensuring "None" strings in categorical variables are not treated as missing values.

**Practical interpretation:**
- Dataset contains **1,000 student records** with **16 variables**
- Variables include demographics, study habits, lifestyle factors, and exam performance
- All 1,000 observations are complete with proper data handling

---

## 2. Missing Value Analysis

**What was done:** Checked for missing values across all variables.

**Practical interpretation:**
- **No missing values detected** in the dataset
- The "None" category in parental education (91 students, 9.1%) represents students whose parents have no formal education beyond high school
- Data quality is excellent with 100% completeness

---

## 3. Variable Classification

**What was done:** Separated variables into numeric and categorical types.

**Practical interpretation:**
- **9 numeric variables:** age, study_hours_per_day, social_media_hours, netflix_hours, attendance_percentage, sleep_hours, exercise_frequency, mental_health_rating, exam_score
- **6 categorical variables:** gender, part_time_job, diet_quality, parental_education_level, internet_quality, extracurricular_participation
- Balanced mix allows for comprehensive statistical analysis

---

## 4. Descriptive Statistics for Numeric Variables

**What was done:** Calculated comprehensive descriptive statistics including central tendency, dispersion, and distribution shape measures.

**Practical interpretation:**

### Key Findings:

**Age:**
- Mean: 20.5 years (SD = 2.3)
- Range: 17-24 years
- Nearly symmetric distribution (skewness = 0.008)

**Study Hours per Day:**
- Mean: 3.6 hours (SD = 1.5)
- Range: 0-8.3 hours
- 50% of students study between 2.6-4.5 hours
- Nearly symmetric distribution (skewness = 0.054)

**Exam Score:**
- Mean: 69.6 points (SD = 16.9)
- Range: 18.4-100 points
- Median: 70.5 points
- Slightly left-skewed (skewness = -0.156), meaning slightly more high scores

**Mental Health Rating (1-10 scale):**
- Mean: 5.4 (SD = 2.8)
- Range: 1-10
- Wide spread indicates diverse mental health states

**Social Media Hours:**
- Mean: 2.5 hours (SD = 1.2)
- Range: 0-7.2 hours

**Netflix Hours:**
- Mean: 1.8 hours (SD = 1.1)
- Range: 0-5.4 hours

**Attendance Percentage:**
- Mean: 84.1% (SD = 9.4)
- Range: 56-100%
- Most students maintain good attendance

**Sleep Hours:**
- Mean: 6.5 hours (SD = 1.2)
- Range: 3.2-10 hours
- Many students sleep less than recommended 7-9 hours

**Exercise Frequency (days/week):**
- Mean: 3.0 days (SD = 2.0)
- Range: 0-6 days
- High variability in exercise habits

---

## 5. Distribution Analysis

**What was done:** Created histograms with kernel density estimation (KDE) curves and overlaid mean/median lines to visualize each variable's distribution.

**Practical interpretation:**
- Visualizations confirm most variables show relatively normal distributions
- Study hours and sleep hours show balanced distributions around their means
- Exam scores show slight clustering toward higher values
- No extreme clustering or unusual patterns detected

---

## 6. Normality Tests

**What was done:** Performed Shapiro-Wilk tests to assess whether each variable follows a normal distribution (α = 0.05).

**Practical interpretation:**

**Variables that ARE normally distributed (p > 0.05):**
1. **Study hours per day** (p = 0.106) ✓
2. **Sleep hours** (p = 0.089) ✓

**Variables that are NOT normally distributed (p ≤ 0.05):**
- Age, social media hours, netflix hours, attendance percentage, exercise frequency, mental health rating, exam score

**Implication:** For non-normal variables, non-parametric tests (like Spearman correlation) should be considered alongside parametric tests.

---

## 7. Outlier Detection

**What was done:** Used boxplots and z-score method (±3 SD) to identify extreme values.

**Practical interpretation:**

**Outliers detected (z-score > 3):**
- **Study hours per day:** 2 outliers (0.2%) - students with extreme study patterns
- **Social media hours:** 3 outliers (0.3%) - excessive social media use
- **Netflix hours:** 2 outliers (0.2%) - very high streaming consumption
- **Exam score:** 1 outlier (0.1%) - unusual performance

**Recommendation:** These represent only 0.8% of data (8 cases) and reflect genuine extreme behaviors rather than data errors. They can be retained for analysis.

---

## 8. Categorical Variables Analysis

**What was done:** Generated frequency counts and percentages for all categorical variables.

**Practical interpretation:**

**Gender:**
- Female: 481 (48.1%)
- Male: 477 (47.7%)
- Other: 42 (4.2%)
- Nearly balanced representation

**Part-time Job:**
- No: 785 (78.5%)
- Yes: 215 (21.5%)
- Most students don't work while studying

**Diet Quality:**
- Fair: 437 (43.7%)
- Good: 378 (37.8%)
- Poor: 185 (18.5%)
- Most students have fair to good dietary habits

**Parental Education Level:**
- High School: 392 (39.2%)
- Bachelor: 350 (35.0%)
- Master: 167 (16.7%)
- None: 91 (9.1%)
- Diverse educational backgrounds

**Internet Quality:**
- Good: 447 (44.7%)
- Average: 391 (39.1%)
- Poor: 162 (16.2%)
- Most students have adequate internet access

**Extracurricular Participation:**
- No: 682 (68.2%)
- Yes: 318 (31.8%)
- About 1/3 of students participate in activities

---

## 9. Correlation Analysis

**What was done:** Calculated Pearson correlation coefficients between all numeric variables and identified the strongest relationships.

**Practical interpretation:**

### Top 10 Strongest Correlations:

1. **Study hours per day ↔ Exam score: r = 0.825** (Very strong positive)
   - *This is the strongest predictor of exam performance*
   - Each additional study hour is associated with significantly higher scores

2. **Mental health rating ↔ Exam score: r = 0.322** (Moderate positive)
   - Better mental health associates with better academic performance
   - Mental wellness matters for student success

3. **Netflix hours ↔ Exam score: r = -0.172** (Weak negative)
   - More streaming time associates with lower scores

4. **Social media hours ↔ Exam score: r = -0.167** (Weak negative)
   - More social media use associates with lower scores

5. **Exercise frequency ↔ Exam score: r = 0.160** (Weak positive)
   - Regular exercise associates with better academic performance

6. **Sleep hours ↔ Exam score: r = 0.122** (Weak positive)
   - More sleep associates with better scores

7. **Attendance percentage ↔ Exam score: r = 0.090** (Very weak positive)
   - Surprisingly weak correlation, but still positive

**Other notable findings:**
- Most lifestyle variables show very weak correlations with each other
- Age shows essentially no correlation with exam scores (r = -0.009)
- Study hours is by far the dominant predictor

---

## 10. Variable Relationships with Target (Exam Score)

**What was done:** Specifically analyzed how each variable correlates with exam performance and created visualizations.

**Practical interpretation:**

### Factors that HELP exam performance (positive correlations):
1. Study hours per day: +0.825 (VERY STRONG)
2. Mental health rating: +0.322 (MODERATE)
3. Exercise frequency: +0.160 (WEAK)
4. Sleep hours: +0.122 (WEAK)
5. Attendance: +0.090 (VERY WEAK)

### Factors that HURT exam performance (negative correlations):
1. Netflix hours: -0.172 (WEAK)
2. Social media hours: -0.167 (WEAK)
3. Age: -0.009 (NEGLIGIBLE)

**Key insight:** Study habits (especially time spent studying) dwarf all other factors in predicting exam success. However, mental health emerges as the second-most important factor, suggesting holistic student wellness matters.

---

## 11. Q-Q Plots for Normality Assessment

**What was done:** Created Quantile-Quantile plots to visually assess whether data follows normal distributions.

**Practical interpretation:**
- Study hours and sleep hours show points closely following the 45° line, confirming normality
- Other variables show deviations from the line, confirming non-normal distributions
- Visual confirmation matches statistical test results from Section 6

---

## 12. Summary Report

### Dataset Overview:
- **Total observations:** 1,000 students
- **Total variables:** 16
- **Numeric variables:** 9
- **Categorical variables:** 6
- **Data quality:** Excellent (0% missing)

### Normality Assessment:
- **Normally distributed:** study_hours_per_day, sleep_hours (2 out of 9)
- **Require non-parametric tests:** age, social_media_hours, netflix_hours, attendance_percentage, exercise_frequency, mental_health_rating, exam_score

### Outlier Detection:
- **4 variables have outliers** (8 total cases, 0.8% of data)
- All outliers represent genuine extreme values, not errors
- Recommendation: Retain outliers in analysis

### Key Relationships with Exam Score:
**Top 5 Positive Correlations:**
1. Study hours per day: 0.825 (very strong)
2. Mental health rating: 0.322 (moderate)
3. Exercise frequency: 0.160 (weak)
4. Sleep hours: 0.122 (weak)
5. Attendance: 0.090 (very weak)

**Top 3 Negative Correlations:**
1. Netflix hours: -0.172 (weak)
2. Social media hours: -0.167 (weak)
3. Age: -0.009 (negligible)

### Recommendations:
1. **Study time is the dominant success factor** - interventions should prioritize effective study strategies
2. **Mental health support is crucial** - it's the second-strongest predictor
3. **Screen time management matters** - both social media and streaming show negative associations
4. **Lifestyle factors help moderately** - exercise and sleep show positive but weaker effects
5. **Demographics matter less** - age and attendance show minimal impact

---

## Practical Implications

**For Students:**
- Prioritize study time - it matters more than anything else
- Take care of mental health - it significantly impacts performance
- Limit recreational screen time
- Maintain exercise and sleep routines

**For Educators:**
- Focus interventions on study skills and time management
- Provide mental health resources and support
- Consider impact of entertainment technology on study habits
- Recognize that attendance alone doesn't guarantee success

**For Researchers:**
- Study hours explains 68% of exam score variance (r² = 0.825²)
- Strong correlations suggest potential for predictive modeling
- Multiple factors contribute, suggesting multivariate approaches
- Non-parametric methods should be considered for most variables

---

## Conclusion

This comprehensive variable analysis reveals that **study habits, particularly time spent studying, are overwhelmingly the strongest predictor of academic success** in this dataset. Mental health emerges as a crucial secondary factor. While lifestyle variables (exercise, sleep) and screen time (social media, Netflix) show expected associations, their effects are modest compared to study time. The dataset is high-quality with excellent completeness, making it suitable for further inferential statistical analyses.
