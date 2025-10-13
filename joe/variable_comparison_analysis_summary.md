# Group Comparison Analysis Summary
## T-Tests and ANOVA for Student Habits vs Exam Performance

**Notebook:** `variable_comparison_analysis.ipynb`
**Purpose:** Compare exam scores across different groups using independent samples t-tests and one-way ANOVA to determine if study habits and mental health significantly impact academic performance.

---

## Overview

This analysis answers four key research questions:
1. Do students with high study hours score higher on exams than students with low study hours?
2. Do students with good mental health score higher on exams than students with poor mental health?
3. Does exam performance differ across multiple study hour categories?
4. Does exam performance differ across multiple mental health categories?

---

## 1. Data Loading and Preparation

**What was done:** Loaded the dataset with 1,000 students and verified key variables.

**Practical interpretation:**
- **1,000 students** with complete data on study hours, mental health, and exam scores
- Study hours: Mean = 3.6 hours/day (SD = 1.5), Range = 0-8.3 hours
- Mental health rating: Mean = 5.4 out of 10 (SD = 2.8), Range = 1-10
- Exam scores: Mean = 69.6 points (SD = 16.9), Range = 18.4-100 points

---

## 2. Creating Group Categories

**What was done:** Created groups based on median splits (for t-tests) and tertile splits (for ANOVA).

**Practical interpretation:**

### Study Hours Groups (2-level for t-test):
- **Low Study Hours:** 471 students (47.1%) - studying less than 3.5 hours/day
- **High Study Hours:** 529 students (52.9%) - studying 3.5+ hours/day

### Study Hours Groups (3-level for ANOVA):
- **Low:** 314 students (31.4%) - studying less than 2.8 hours/day
- **Medium:** 347 students (34.7%) - studying 2.8-4.4 hours/day
- **High:** 339 students (33.9%) - studying 4.4+ hours/day

### Mental Health Groups (2-level for t-test):
- **Lower Mental Health:** 411 students (41.1%) - rating below 5
- **Higher Mental Health:** 589 students (58.9%) - rating 5 or above

### Mental Health Groups (3-level for ANOVA):
- **Low:** 301 students (30.1%) - rating 1-3
- **Medium:** 317 students (31.7%) - rating 4-6
- **High:** 382 students (38.2%) - rating 7-10

---

## 3. T-Test Analysis: Study Hours Groups

**Research Question:** Do students with high study hours score higher on exams?

### Descriptive Statistics:
- **Low Study Hours (n=471):**
  - Mean: **57.81 points**
  - SD: 13.28
  - Median: 58.40

- **High Study Hours (n=529):**
  - Mean: **80.10 points**
  - SD: 12.17
  - Median: 79.60

- **Mean Difference: 22.30 points** (high study hours group scores higher)

### Assumption Checks:
- **Normality:** Low group is normal (p = 0.142), High group is not normal (p < 0.001)
- **Equal variances:** Yes, variances are equal (Levene's test p = 0.138)

### T-Test Results:
- **t-statistic: 27.71**
- **p-value: < 0.001** (essentially zero)
- **Result: HIGHLY SIGNIFICANT**
- **Cohen's d: 1.76** (Large effect size)

**Practical interpretation:**
- **Students who study more score 22 points higher on average** - this is a substantial difference
- The difference is **highly statistically significant** (p < 0.001)
- The effect size is **very large** (d = 1.76), meaning this is not just statistically significant but also practically meaningful
- **This represents approximately a full letter grade difference** (e.g., C+ vs. B+)
- The impact of study hours on exam performance is unmistakable and dramatic

---

## 4. T-Test Analysis: Mental Health Groups

**Research Question:** Do students with better mental health score higher on exams?

### Descriptive Statistics:
- **Lower Mental Health (n=411):**
  - Mean: **64.03 points**
  - SD: 16.39
  - Median: 64.20

- **Higher Mental Health (n=589):**
  - Mean: **73.49 points**
  - SD: 16.14
  - Median: 74.00

- **Mean Difference: 9.45 points** (higher mental health group scores better)

### Assumption Checks:
- **Normality:** Lower group is normal (p = 0.083), Higher group is not normal (p < 0.001)
- **Equal variances:** Yes, variances are equal (Levene's test p = 0.907)

### T-Test Results:
- **t-statistic: 9.05**
- **p-value: < 0.001** (7.14 × 10⁻¹⁹)
- **Result: HIGHLY SIGNIFICANT**
- **Cohen's d: 0.58** (Medium effect size)

**Practical interpretation:**
- **Students with better mental health score 9.5 points higher on average**
- The difference is **highly statistically significant** (p < 0.001)
- The effect size is **medium** (d = 0.58), meaning the practical importance is notable though not as dramatic as study hours
- **This represents approximately half a letter grade difference** (e.g., C+ vs. B-)
- Mental health clearly matters for academic performance, though not as much as study time

---

## 5. Visualization of T-Test Results

**What was done:** Created side-by-side boxplots showing exam score distributions for each group comparison.

**Practical interpretation:**
- **Study Hours boxplot:** Clear separation between low and high groups with minimal overlap
- **Mental Health boxplot:** Noticeable separation but more overlap than study hours
- Visual confirmation of statistical findings - both factors matter, but study hours has a more dramatic impact

---

## 6. One-Way ANOVA: Study Hours (3 Groups)

**Research Question:** Does exam performance differ across low, medium, and high study hour groups?

### Descriptive Statistics by Group:
- **Low Study Hours (n=314):** Mean = **53.45 points** (SD = 12.40)
- **Medium Study Hours (n=347):** Mean = **69.64 points** (SD = 10.15)
- **High Study Hours (n=339):** Mean = **84.52 points** (SD = 11.38)

**Progressive improvement:** 53.45 → 69.64 → 84.52 (31-point range across groups)

### Assumption Checks:
- **Normality:** Low is normal (p = 0.668), Medium is normal (p = 0.749), High is not normal (p < 0.001)
- **Equal variances:** No, variances are unequal (Levene's test p < 0.001)

### ANOVA Results:
- **F-statistic: 614.67**
- **p-value: < 0.001** (1.19 × 10⁻¹⁷⁴)
- **Result: HIGHLY SIGNIFICANT**
- **Eta-squared (η²): 0.552** (Large effect size - 55.2% of variance explained)

### Post-Hoc Analysis (Tukey HSD):
All pairwise comparisons are significant (p < 0.001):
- **High vs. Low:** Mean difference = -31.07 points (p < 0.001)
- **High vs. Medium:** Mean difference = -14.88 points (p < 0.001)
- **Medium vs. Low:** Mean difference = +16.19 points (p < 0.001)

**Practical interpretation:**
- **Every increase in study hours category leads to significantly better exam scores**
- The progression is **dramatic and linear**: Low (53) → Medium (70) → High (85)
- **Moving from Low to High study hours is associated with a 31-point increase** - more than two full letter grades
- **Even moving from Medium to High adds 15 points** - a substantial improvement
- Study hours **explains 55% of the variance in exam scores** - this is exceptional in social science research
- **Clear dose-response relationship:** More studying = better performance at every level

---

## 7. One-Way ANOVA: Mental Health (3 Groups)

**Research Question:** Does exam performance differ across low, medium, and high mental health groups?

### Descriptive Statistics by Group:
- **Low Mental Health (n=301):** Mean = **63.43 points** (SD = 15.94)
- **Medium Mental Health (n=317):** Mean = **67.87 points** (SD = 16.85)
- **High Mental Health (n=382):** Mean = **75.90 points** (SD = 15.49)

**Progressive improvement:** 63.43 → 67.87 → 75.90 (12.5-point range across groups)

### Assumption Checks:
- **Normality:** Low is normal (p = 0.085), Medium is not normal (p = 0.011), High is not normal (p < 0.001)
- **Equal variances:** Yes, variances are equal (Levene's test p = 0.268)

### ANOVA Results:
- **F-statistic: 53.43**
- **p-value: < 0.001** (9.08 × 10⁻²³)
- **Result: HIGHLY SIGNIFICANT**
- **Eta-squared (η²): 0.097** (Medium effect size - 9.7% of variance explained)

### Post-Hoc Analysis (Tukey HSD):
All pairwise comparisons are significant:
- **High vs. Low:** Mean difference = -12.47 points (p < 0.001)
- **High vs. Medium:** Mean difference = -8.04 points (p < 0.001)
- **Medium vs. Low:** Mean difference = +4.43 points (p = 0.002)

**Practical interpretation:**
- **Every improvement in mental health category leads to significantly better exam scores**
- The progression is **consistent and meaningful**: Low (63) → Medium (68) → High (76)
- **Moving from Low to High mental health is associated with a 12.5-point increase** - about one full letter grade
- Mental health **explains 10% of the variance in exam scores** - substantial but less than study hours
- **Clear dose-response relationship:** Better mental health = better performance at every level
- The effect is smaller than study hours but still educationally and clinically significant

---

## 8. Visualization of ANOVA Results

**What was done:** Created side-by-side boxplots showing exam score distributions across three groups for both study hours and mental health.

**Practical interpretation:**
- **Study Hours:** Clear, dramatic separation between all three groups with minimal overlap
- **Mental Health:** Noticeable separation with more overlap, especially between Low and Medium
- **Visual confirmation:** Study hours shows a steeper gradient and larger differences than mental health
- Both factors show clear linear trends: more is better

---

## 9. Comprehensive Summary

### T-Test Results (2 Groups):

**Study Hours:**
- Low: M = 57.81 (SD = 13.28)
- High: M = 80.10 (SD = 12.17)
- t = 27.71, p < 0.001
- **Difference: 22.30 points**
- **Result: HIGHLY SIGNIFICANT with LARGE effect**

**Mental Health:**
- Lower: M = 64.03 (SD = 16.39)
- Higher: M = 73.49 (SD = 16.14)
- t = 9.05, p < 0.001
- **Difference: 9.45 points**
- **Result: HIGHLY SIGNIFICANT with MEDIUM effect**

### ANOVA Results (3 Groups):

**Study Hours:**
- Low: M = 53.45
- Medium: M = 69.64
- High: M = 84.52
- F = 614.67, p < 0.001
- η² = 0.552 (55% of variance explained)
- **Result: HIGHLY SIGNIFICANT with LARGE effect**
- **All pairwise comparisons significant**

**Mental Health:**
- Low: M = 63.43
- Medium: M = 67.87
- High: M = 75.90
- F = 53.43, p < 0.001
- η² = 0.097 (10% of variance explained)
- **Result: HIGHLY SIGNIFICANT with MEDIUM effect**
- **All pairwise comparisons significant**

---

## Practical Implications

### For Students:

1. **Study time is the #1 controllable factor for success**
   - Increasing from low to high study hours: +31 points
   - Even moderate increases (medium to high): +15 points
   - Every additional hour of focused study matters

2. **Mental health significantly impacts performance**
   - Improving from low to high mental health: +12.5 points
   - Mental wellness is not a luxury but a necessity for academic success
   - Seeking support can improve both well-being AND grades

3. **Both factors matter, but study time matters more**
   - Study hours: 55% of exam score variance
   - Mental health: 10% of exam score variance
   - Combined, they likely explain ~60% of performance

### For Educators and Counselors:

1. **Prioritize study skills interventions**
   - Effect sizes are exceptionally large (d = 1.76)
   - Teaching effective study strategies should be a top priority
   - Time management training can have dramatic impacts

2. **Invest in mental health support**
   - Medium effect size (d = 0.58) is still educationally significant
   - Mental health services are not just for crisis intervention
   - Preventive mental health support can improve academic outcomes

3. **Recognize dose-response relationships**
   - Both factors show linear trends: more is better
   - Small improvements can lead to meaningful grade changes
   - Support students at all levels, not just those struggling

### For Institutional Policy:

1. **Resource allocation**
   - Study skills workshops and tutoring: High ROI
   - Mental health counseling: Moderate-to-high ROI
   - Both deserve significant investment

2. **Early intervention**
   - Students in "low" or "medium" groups need proactive support
   - Don't wait for failure before providing resources
   - Screening for both study habits and mental health

3. **Holistic approach**
   - Academic success requires addressing multiple factors
   - Study skills alone won't help students in mental distress
   - Mental health support won't substitute for poor study habits
   - Integrated support services are ideal

---

## Statistical Rigor

### Strengths:
- Large sample size (n = 1,000) provides excellent statistical power
- Multiple analysis methods (t-tests and ANOVA) confirm findings
- Effect sizes reported alongside p-values (best practice)
- Assumption checking documented
- Post-hoc tests prevent Type I error inflation
- Results are robust and replicable

### Limitations:
- Some violations of normality (common with large samples)
- Study hours ANOVA shows unequal variances (Levene's test)
- Cross-sectional design prevents causal claims
- Possible confounding variables not controlled

### Recommendations for Future Research:
- Longitudinal studies to establish causality
- Multivariate models controlling for demographics
- Investigation of interaction effects
- Qualitative research on mechanisms
- Intervention studies testing recommendations

---

## Conclusion

This comprehensive group comparison analysis provides **strong, clear evidence** that both **study hours and mental health significantly impact academic performance**.

**Study hours is the dominant factor**, with students in the high study group scoring **22-31 points higher** than those in lower study groups - representing approximately **two full letter grades**. The effect size is **very large** (Cohen's d = 1.76), and study hours **explains 55% of exam score variance**.

**Mental health is the second most important factor**, with students reporting higher mental health scoring **9-12 points higher** - representing approximately **one full letter grade**. The effect size is **medium** (Cohen's d = 0.58), and mental health **explains 10% of exam score variance**.

**All differences are highly statistically significant** (p < 0.001), and **dose-response relationships are clear**: more studying and better mental health consistently associate with better performance at every level.

**The practical implications are clear:** Educational institutions should prioritize both study skills interventions and mental health support to maximize student success. These findings justify significant investment in both academic and wellness services.
