# Lesson 16: Final Model Refinement and Presentation

## Lesson Description

In this lesson, students will refine their machine learning models, validate improvements, and present their findings using professional tools. They will redesign their pipelines in **Azure ML Designer** based on prior evaluation results and justify their modeling decisions in a **white paper** and **presentation**. This is the final product of a multi-lesson project.

---

## Main Learning Goal

Students will refine, test, and communicate a machine learning pipeline that predicts a defined target from real sports data using Azure ML Designer.

---

## Essential Question

**How can I refine my predictive model to make better decisions — and how can I justify those decisions clearly?**

---

## Standards

- **AP6.2** – Use and refine machine learning models to improve predictions and classifications  
- **DA3.4** – Justify the choice of data collection method, data analysis tool, and representation format

---

## Objectives

- Refine an existing machine learning pipeline using Azure ML Designer  
- Evaluate and compare classification and regression model performance  
- Justify modeling decisions in a **white paper**  
- Present findings using a **professional slide presentation**

---

## Model Reboot – What Would We Change?

We’re moving from simply building a model to improving it — just like real data scientists. Today, we’ll:

- Evaluate what worked and what didn’t
- Make a smart change
- Justify that decision
- Re-run our pipeline and check results

---

## Warm-Up Discussion

**Prompt:**  
“If we were hired by a sports team to improve our player prediction model — what would we do first, and why?”

Machine learning is about smart iteration. This is our chance to improve and prepare for presentation.

---

## Datasets Available

You may choose from any dataset used in earlier lessons:

- **Batting Dataset (CSV)**  
- **Pitching Dataset (CSV)**  
- **Clemson Football Dataset (CSV)**

---

## Reflection Prompt: What Will We Change?

Before going into Azure, write down **one specific change** you plan to make in one of these areas:

### a. Feature Set
- Remove weak features?
- Add stronger features?
- Combine or transform features?

### b. Label
- Is the label too easy or noisy?
- Could a more meaningful label help?

### c. Model Type
- Try a different algorithm?
- Ex: Swap Linear Regression → Boosted Regression

### d. Preprocessing Strategy
- Different handling of missing data?
- Change train/test split?
- Normalize or scale features?

---

## Justify the Change

Write a short explanation for your change.

**Examples:**

- "We’re removing `Games_Played` because it doesn’t reflect skill — just opportunity."
- "We’re switching to Logistic Regression for more interpretable results."

---

## Pipeline Redesign and Testing

### Goals:
- Make **at least one meaningful change**
- Re-run the updated pipeline
- Record new evaluation metrics
- Compare to Lesson 15’s results
- Choose a model version for your final presentation

---

## What We Can Change in Azure ML Designer

### 1. Feature Refinement
Add, remove, or replace features.

**Example:**
> “We added `OBP_2023` and `BB_2023` to better capture plate discipline.”

### 2. Label Redefinition
Refine or swap your label.

**Example:**
> “We changed our label from `slugger` to one based on `OPS + RBI`.”

### 3. Algorithm Swap
Try a new model type.

**Example:**
> “Switched from Linear Regression to Boosted Regression. R² improved from 0.45 to 0.71.”

### 4. Preprocessing Tuning
Adjust how data is cleaned and split.

**Examples:**
- Fill missing values instead of dropping rows
- Change split ratio to 70/30
- Normalize numeric features for SVM or Logistic Regression

---

## Steps to Follow

1. **Duplicate** your Lesson 15 pipeline  
2. Apply your planned redesign  
3. **Re-run** the pipeline  
4. Record metrics:  
   - For regression: `RMSE`, `R²`  
   - For classification: `Accuracy`, `AUC`, `Confusion Matrix`  
5. Compare with old metrics  
6. Decide which version to present

---

## Example – Football Dataset

**Original:**
- Model: Decision Forest Classifier
- Label: `is_qb1`
- Accuracy: 0.86  
- AUC: 0.79  
- Feature importance: heavily on `GAMES_PLAYED`

**Redesign:**
- Removed `GAMES_PLAYED`
- Added `INT` and `Rush_Yds`
- New Accuracy: 0.89  
- AUC: 0.84  

**Conclusion:**
> The model is now more balanced and fair. It considers rushing and passing.

---

## By the End of This Phase, You Should Have:

✅ A refined pipeline  
✅ A clear record of changes and results  
✅ A finalized model for your white paper and presentation

---

## Write Your White Paper

Your 1-page white paper should clearly explain:

- The dataset and problem you chose  
- Your pipeline design  
- The changes you made  
- Evaluation results  
- Final prediction (if applicable)

### Sections to Include

#### **Goal and Label**
- What did you predict?
- Why did you choose this label?

> *Example:*  
> We aimed to identify the next starting quarterback. We used the `is_qb1` label to reflect real team decisions.

#### **Features and Rationale**
- What features did you use and why?
- Did you remove any?

> *Example:*  
> We removed `GAMES_PLAYED` due to over-reliance.

#### **Model Type and Refinement**
- Which model(s) did you try?
- What worked best?

> *Example:*  
> Tried Logistic Regression, but Decision Forests worked better after feature changes.

#### **Evaluation Metrics**
- Final metrics (include at least two):
    - RMSE / R² (regression)  
    - Accuracy / AUC / Confusion Matrix (classification)

> *Example:*  
> AUC = 0.89, Accuracy = 91%, 1 false negative.

#### **Final Prediction and Justification**
- Who did the model identify?
- Does it make sense?

> *Example:*  
> Player A stood out. Despite fewer games, he was most efficient.

### Formatting Tips
- Use headings and bullet points  
- One page max  
- Include a chart or screenshot (confusion matrix, feature importance)

---

## Final Presentation + Peer Review

Now you’ll present your model in a **4–6 slide presentation**, just like professionals do.

---

## Slide Guide

| Slide | Content |
|-------|---------|
| 1     | Project Overview (dataset, problem, label, features) |
| 2     | Azure Pipeline Screenshot + explanation |
| 3     | Model Changes from Lesson 16 + rationale |
| 4     | Evaluation Results + 1 surprising insight |
| 5     | *(Optional)* Final Prediction – who and why |
| 6     | *(Optional)* Reflection – what you’d change or learned |

---

## Peer Review – Glow & Grow

You’ll give feedback using these categories:

| Category               | Glow – What worked well?           | Grow – What could be stronger?      |
|------------------------|------------------------------------|-------------------------------------|
| Model Clarity          |                                    |                                     |
| Evidence-Based Reasoning |                                  |                                     |
| Communication & Visuals |                                   |                                     |

> Feedback should be supportive, specific, and focused on model quality and communication.

---
