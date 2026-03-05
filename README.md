# ACL-Rehab-Plateau-Modeling
## Early quadriceps strength as an indicator of stagnation of rehabilitation after ACL reconstruction

### **Project Overview** 
This practicum project investigates whether early-stage quadriceps strength metrics can help identify athletes at risk of a rehabilitation "plateau" following ACL reconstruction.
While return-to-play decisions often rely heavily on Limb Symmetry Index (LSI), this analysis demonstrates whether quadriceps torque normalized to body weight (Nm/kg) provides stronger early signal of of long-term success.

This study is exploratory and hypothesis-generating in nature.

Dataset

* Participants: 18 post-ACL reconstruction athletes

* Design: Longitudinal repeated-measures dataset
* Observations: 350+ total rehabilitation visits
* Evaluation Window: Early rehabilitation (0–60 days post-op)
* Minimum inclusion: ≥14 days post-operative
Each athlete contributed multiple testing sessions over time. For modeling purposes:
* Testing was looked at by athlete's not rows
Defining “Rehabilitation Plateau”
An athlete was classified as reaching a plateau if either:
1. Peak quadriceps LSI never reached ≥ 90% 
OR
2. The final three testing visits demonstrated < 5% improvement in LSI
This definition captures both:
* Failure to reach clinically accepted symmetry benchmarks
* Stalled longitudinal progression
Final cohort distribution:
* Plateau: 3 athletes
* Progressing: 15 athletes


### **The "LSI Trap"**

Through Exploratory Data Analysis (EDA), we identified a critical clinical gap. Many athletes achieve 90% symmetry (LSI) by the end of rehab not because the surgical leg is strong, but because the healthy leg has detrained. This creates a scenario of being “symmetric but weak.” Absolute torque (Nm/kg) captures true strength capacity and may better reflect meaningful recovery. This project utilizes a Multivariate Logistic Regression to catch these "symmetric but weak" athletes in the early-rehab window (0–60 days).

## **Analytical Approach**
A logistic regression model was used to examine whether early strength metrics were associated with later plateau classification.
Features
* Quadriceps LSI (early window average)
* Absolute Quadriceps Torque (Nm/kg, early window average)
Outcome
* Plateau (binary: yes/no)
Evaluation
* In-sample ROC-AUC
Due to small sample size (n = 18; 3 plateau cases), results should be interpreted as exploratory relationships rather than validated predictive performance.


### **Key Findings**

* **Model Improvement:** Moving from an LSI-only baseline to a Multivariate model (LSI + Torque) within the sample AUC increased from 0.59 to 0.71.
* **Clinical Threshold:** Athletes falling below 6.79 Nm/kg of torque/BW in the first 60 days are significantly more likely to plateau.
* **Feature Importance:** Torque was found to be the most influencial feature, with a coefficient of -0.212 compared to LSI's near-zero impact in the combined model.

These findings suggest that early absolute strength may provide more clinically useful signal than symmetry metrics alone.


## **Important Limitations**
* Small sample size (n = 18)
* Only 3 plateau cases (class imbalance)
* Performance metrics reflect in-sample fit
* No external validation cohort
Because of the limited number of athletes, this project should be used as a pilot longitudinal analysis intended to generate hypotheses for future, larger-scale studies.

## **Clinical Implications**
This analysis supports the concept that:
* Symmetry alone may mask inadequate strength
* Absolute torque should be monitored early post-operatively
* Early weakness may identify athletes at risk for stagnation
These findings warrant further investigation in larger groups.

### **Repository Structure**

1.**`Code/`** Python scripts that replicate the full workflow of the project:
   - **`Practicum Cleaning-Final-Copy1-2.py`** – Data preprocessing, date handling, and filtering of early post-operative testing windows.
   - **`Practicum EDA-Final-Copy1.py`** – Exploratory data analysis including summary statistics, correlation analysis, and visualization generation (e.g., LSI vs. Torque scatterplots).
   - **`Practicum AUC Log Model-Final-Copy1-2.py`** – Logistic regression models used to analyze rehabilitation plateaus and calculate risk thresholds.

2.  **`Data/`**   Contains a small synthetic dataset (`ACL Master Longitudinal.csv`) used to demonstrate the analysis pipeline while protecting athlete privacy.
   
4. **`Figures/`**  
   Visual outputs generated during exploratory analysis

5. **`docs/`**  
   Project documentation, including the full practicum report.

---

### How to Use

To verify the analysis pipeline without access to the private master dataset, run the scripts in the following order:

```bash
python Practicum Cleaning-Final-Copy1-2.py
python Practicum EDA-Final-Copy1.py
python Practicum AUC Log Model-Final-Copy1-2.py
```

The scripts will load the example dataset in the **Data/** folder and reproduce the core workflow used in the project, including the exploratory analysis and machine learning model.

---

### Full Report

For full methodology, background research, and discussion of results, see:

```
docs/Practicum_paper.pdf
```
