### ACL-Rehab-Plateau-Prediction
## Early quadriceps strength as an indicator of stagnation of rehabilitation after ACL reconstruction

### **Project Overview** 
This practicum project investigates whether early-stage quadriceps strength metrics can help identify athletes at risk of a rehabilitation "plateau" following ACL reconstruction.
While return-to-play decisions often rely heavily on Limb Symmetry Index (LSI), this analysis demonstrates whether quadriceps torque normalized to body weight (Nm/kg) provides stronger early signal of of long-term success.

This study is exploratory and hypothesis-generating in nature.

Dataset
    •    Participants: 18 post-ACL reconstruction athletes
    •    Design: Longitudinal repeated-measures dataset
    •    Observations: 350+ total rehabilitation visits
    •    Prediction Window: Early rehabilitation (0–60 days post-op)
    •    Minimum inclusion: ≥14 days post-operative
Each athlete contributed multiple testing sessions over time. For modeling purposes:
    •    testing was looked at by athlete's not rows
Defining “Rehabilitation Plateau”
An athlete was classified as reaching a plateau if either:
    1    Peak quadriceps LSI never reached ≥ 90% 
OR
    2    The final three testing visits demonstrated < 5% improvement in LSI
This definition captures both:
    •    Failure to reach clinically accepted symmetry benchmarks
    •    Stalled longitudinal progression
Final cohort distribution:
    •    Plateau: 3 athletes
    •    Progressing: 15 athletes


### **The "LSI Trap"**

Through Exploratory Data Analysis (EDA), we identified a critical clinical gap. Many athletes achieve 90% symmetry (LSI) by the end of rehab not because the surgical leg is strong, but because the healthy leg has detrained. This creates a scenario of being “symmetric but weak.” Absolute torque (Nm/kg) captures true strength capacity and may better reflect meaningful recovery. This project utilizes a Multivariate Logistic Regression to catch these "symmetric but weak" athletes in the early-rehab window (0–60 days).

## **Analytical Approach**
A logistic regression model was used to examine whether early strength metrics were associated with later plateau classification.
Predictors
    •    Quadriceps LSI (early window average)
    •    Absolute Quadriceps Torque (Nm/kg, early window average)
Outcome
    •    Plateau (binary: yes/no)
Evaluation
    •    In-sample ROC-AUC
Because of the small sample size (n = 18; 3 plateau cases), results should be interpreted as exploratory relationships rather than validated predictive performance.


### **Key Findings**

* **Model Improvement:** Moving from an LSI-only baseline to a Multivariate model (LSI + Torque) increased predictive accuracy from 0.59 AUC to 0.71 AUC.
* **Clinical Threshold:** Athletes falling below 6.79 Nm/kg of torque/BW in the first 60 days are significantly more likely to plateau.
* **Feature Importance:** Torque was found to be the dominant predictor, with a coefficient of -0.212 compared to LSI's near-zero impact in the combined model.

These findings suggest that early absolute strength may provide more clinically useful signal than symmetry metrics alone.


## **Important Limitations**
    •    Small sample size (n = 18)
    •    Only 3 plateau cases (class imbalance)
    •    Performance metrics reflect in-sample fit
    •    No external validation cohort
Because of the limited number of athletes, this project should be used as a pilot longitudinal analysis intended to generate hypotheses for future, larger-scale studies.

## **Clinical Implications**
This analysis supports the concept that:
    •    Symmetry alone may mask inadequate strength
    •    Absolute torque should be monitored early post-operatively
    •    Early weakness may identify athletes at risk for stagnation
These findings warrant further investigation in larger groups.

### **Repository Structure**

1. **`01_Data_Cleaning.py`**: Data processing, date handling, and $\ge 14$-day post-op filtering.
2. **`02_EDA_Visuals.py`**: Exploratory visualizations and correlation analysis, generates the "LSI vs. Torque" scatter plot and correlation heatmaps.
3. **`03_Machine_Learning.py`**: The core logistic regression models and threshold calculations
4. **`Model_Template_SHELL.py`**: A functional script using *mock data to demonstrate code logic while protecting athlete privacy.

### **How to Use**

To verify the machine learning logic without access to the private master dataset, please run:

```bash
python Model_Template_SHELL.py

```

This will execute the Logistic Regression pipeline and output a logic-check AUC score.


