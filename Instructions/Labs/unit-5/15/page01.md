# Lesson 15: Build and Evaluate Your Predictive Model

## Lesson Description

In this lesson, students will implement the modeling plan they created in Lesson 14 by building and evaluating two machine learning models using **Azure ML Designer**: one **linear regression model** and one **decision tree model**.

Students will analyze how well each model fits their data, interpret outputs such as **accuracy** and **error**, identify **outliers**, and explain what the models reveal about player performance. This phase is essential for their final project and prepares them to refine their models in Lesson 16.

---

## Main Learning Goal

Students will run both a **linear regression** and a **decision tree** model on their dataset, interpret the results, identify outliers, and explain how the models make predictions.

---

## Essential Question

**How can we use regression and decision trees to make accurate predictions and uncover meaningful patterns in sports data?**

---

## Standards

- **AP6.2** – Design, build, and test level-appropriate algorithms that use linear regression and describe existing outliers in the context of the programming solution.
- **AP6.2** – Use decision trees and linear regressions to make predictions and classifications.

---

## Objectives

By the end of this lesson, students will:

- Build both a linear regression and a decision tree model using Azure ML Designer  
- Visualize and interpret key model outputs (R², RMSE, AUC, confusion matrix)  
- Identify and describe outliers or misclassifications  
- Compare model results and reflect on effectiveness  

---

## What Makes a Model Work? Why Did the Model Get It Wrong?

**Scenario:** You built a model to identify sluggers. One player has:

- Batting AVG: `.310`  
- SLG%: `.500`  
- Home Runs: `6`  
- Model says: **Not a slugger**

That feels off. Why?

### Think-Pair-Share Activity:

- **Think (30 seconds)**: Why did the model make this mistake?
- **Discuss with a partner**: Share possible reasons

### Possibilities to Consider:

- 6 HR might be below the model’s internal slugger threshold  
- Player had low game count (sample size too small)  
- Model may not have used the best features  
- Dataset may be imbalanced (too few sluggers)

---

## Let’s Dig Deeper: How Models Think

### Class Discussion Questions:

- What might cause a model to misclassify?
- What happens if the player barely missed the cutoff (e.g., 6 HR vs. 7 HR)?
- What does **class imbalance** do to model behavior?
- How would a **regression model** handle this differently than a **decision tree**?

> A regression model might say “48% chance of being a slugger”  
> A decision tree might hard classify: “If HR ≥ 7 → slugger = yes”

---

## Pre-Azure Activity: Sketch Your Two Model Pipelines

### Your Task

Sketch **two pipelines** — one for each model type.

### Include these steps:

1. Import Data  
2. Clean Missing Data  
3. Select Columns in Dataset  
4. Split Data  
5. Train Model  
   - Linear Regression or Decision Forest Classifier  
6. Score Model  
7. Evaluate Model

Label your sketches:

- “**Regression Model – Predicting [your label]**”  
- “**Classification Model – Predicting [your label]**”

---

## Build Your Two Azure ML Pipelines

You're now creating the models in Azure ML Designer.

### You will build:

- A **Linear Regression** model → Predicts a number (e.g., OPS, ERA)
- A **Decision Tree Classifier** → Predicts a category (e.g., slugger = yes/no)

> These are **supervised learning** models.

---

## Pipeline 1 – Linear Regression Model

### Goal: Predict a numeric label  
**Examples**:
- `OPS_2024`, `ERA_2024`, `Total_Points`

### Model Component:
- **Train Model → Linear Regression**

### Key Metrics:
- **RMSE** (Root Mean Squared Error)
- **R²** (Explained variance)

---

## Pipeline 2 – Decision Tree Model

### Goal: Classify a player as yes/no  
**Examples**:
- `slugger` (1/0)
- `ace_pitcher`, `is_qb1`

### Model Component:
- **Train Model → Decision Forest Classifier**

> *Optional: Use Decision Forest Regression for numeric labels*

### Key Metrics:
- **Confusion Matrix**, **Accuracy**, **AUC**

---

## Comparison Table

| Concept            | Linear Regression            | Decision Tree Classification     |
|--------------------|------------------------------|----------------------------------|
| Prediction Type    | Numeric (e.g., OPS = 0.532)   | Binary (e.g., slugger = yes/no) |
| Evaluation Metrics | RMSE, R²                     | Accuracy, AUC, Confusion Matrix |
| Learning Style     | Fits a line                  | Builds tree of rules/splits      |
| Pitfalls           | Outliers skew results        | Misclassifies near thresholds   |
| Explanation Style  | Feature weights              | Feature importance, split logic |

---

## Ready to Build? Check Your Plan

✅ Do you know your label?  
✅ Are your features **from past years only**?  
✅ Did you remove text columns like player names?  
✅ Are your features all **numeric**?

---

## Azure ML Designer – Pipeline Structure

| Step | Azure Component           | Purpose                         |
|------|---------------------------|----------------------------------|
| 1    | Import Data               | Load your dataset                |
| 2    | Clean Missing Data        | Handle blanks/missing values     |
| 3    | Select Columns            | Choose label + input features    |
| 4    | Split Data                | Train/test split (80/20)         |
| 5    | Train Model               | Choose algorithm                 |
| 6    | Score Model               | Predict label for test set       |
| 7    | Evaluate Model            | Check RMSE, R², AUC, etc.        |

---

## Troubleshooting Tips

- Did you select the **correct label** in Train Model?
- Are **all features numeric** and relevant?
- Did you connect **Split Data** correctly?
  - One path to Train Model  
  - Other path to Score Model  

---

## What to Look For in Azure Outputs

### For Linear Regression:
- **RMSE**: Lower is better. Compare to label range.
- **R²**: Closer to 1 = model explains more variation
- **Prediction vs. Actual**: Are they aligned?

### For Classification:
- **Confusion Matrix**: Who was misclassified?
- **AUC**: Model’s ability to separate classes
- **Accuracy / Precision / Recall**: Know the difference

---

## Example – Regression Model

- **Label**: `OPS_2024`
- **Features**: `HR_2023`, `SLG%_2023`, `OBP_2023`
- **Results**:
  - RMSE = 0.032  
  - R² = 0.81  

🟢 *Strong model that explains most variation*

---

## Example – Classification Model

- **Label**: `slugger`
- **Results**:
  - True Positives: 12  
  - False Negatives: 3  
  - AUC = 0.87  

🟢 *Model is strong, but missed some true sluggers*

---

## Analyze Your Results

Answer these questions using your **actual model outputs**:

1. **What did your models predict?**
   - Label and model type (regression or classification)
   - How does it connect to Lesson 14’s plan?

2. **How well did each model perform?**
   - Report metrics (RMSE, R², AUC, etc.)
   - Was performance strong? Any surprises?

3. **What features were most important?**
   - Use Azure’s Feature Importance chart
   - Which stats mattered most? Any surprises?

4. **Any outliers or misclassifications?**
   - Regression: Players with large prediction errors
   - Classification: Incorrectly labeled players

5. **What might explain the results?**
   - Missing data? Poor features? Class imbalance?
   - What would you change next time?

---

## Optional Peer Discussion

- Which model worked better — and why?
- Surprising outlier or mistake?
- What one modeling choice would you change in Lesson 16?

---

## Final Reflection

Answer these prompts in writing:

- What label did your models try to predict, and why?
- Which features seemed most important?
- What did your best model do well — and where did it struggle?
- Describe one specific outlier or misclassification.
- If you rebuilt this pipeline, what would you improve?

---
