# Lesson 11: Predicting Player Performance with Regression in Azure ML Designer

## Lesson Description:

Students act as junior sports analysts for a South Carolina basketball program. Their goal: predict which players are likely to score the most points using a regression model built in Azure ML Designer. Students use player stats to train and evaluate both a Linear Regression and a Boosted Decision Tree Regression model. They explore how feature selection affects accuracy, compare model performance, and make scouting decisions based on predicted outcomes. 

## Main Learning Goal:

Students will learn to build, compare, and evaluate regression models to predict a numeric outcome using Azure ML Designer.

### Essential Question:

How can regression models help us make accurate predictions about player performance using sports data?

**Standards:**
  - AP6.2 - Describe and use the types of algorithms used for regression

## Objectives:

By the end of this lesson, students will be able to: 
- Describe what regression is and how it differs from classification 

- Use Azure ML Designer to train and score a regression model 

- Manually select features and evaluate their effect on accuracy 

- Interpret RMSE and R² values to assess model quality 

- Compare Linear Regression and Boosted Decision Tree Regression 

- Use predictions to make a justified scouting recommendation

**Who Should We Scout Next?**

The South Carolina high school basketball team is preparing for an important game, but one of their starting players is out due to injury. As student analysts, your job is to help the 
coach decide who should start in their place.The coach shares a data sheet that includes each player’s stats — things like minutes played, assists, field goal percentage (FG%), rebounds, and more — but scoring averages are not available. The coach asks, “Based on this data, who do you think will score the most points in the next game?”


 - Before jumping into modeling, take a few minutes to discuss the following with a partner:
    
    - Which player stats do you think might be strong predictors of scoring performance?
    
    - If you had to guess who would score the most next game, how would you decide?

**What Is Regression?**

- Regression is a type of machine learning used when the outcome you want to predict is a number. In this unit, we want to predict PTS — the number of points a player is likely to score based on other stats like MP (minutes played), AST (assists), FG% (field goal percentage), and TRB (total rebounds).

- A regression model learns patterns between known features and the target (label) to make 
predictions

## Common Types of Regression in Machine Learning

### Linear Regression

**What it does:**

Fits a straight line between features and the target. It assumes a direct, linear relationship: if one value increases, the target increases or decreases by a fixed amount.

**Example in basketball:**
You find that every extra 2 minutes on the court leads to 1 extra point scored. So if Player A plays 20 minutes and scores 10 points, then Player B who plays 30 minutes would be 
expected to score 15 points. The model learns this slope and intercept from the training data.

**Why it’s useful:**
- Simple to build
- Easy to interpret
- Good first model to understand relationships
- Fast and works well on clean, linear data

**Limitation:**

Can **underfit** if relationships are more complex or nonlinear.

### Polynomial Regression

**What it does:**
Fits a curved line (e.g., quadratic, cubic) between features and the target. This helps capture data where increases in input don’t produce constant output changes.

**Example in basketball:**
Suppose performance improves with more minutes up to a point — but then starts to fall due to fatigue. A player playing 25 minutes scores 20 points, but at 35 minutes, they drop 
to 15 points. A curve models this better than a straight line.

**Why it’s useful:**

- Models more complex, non-linear trends
- Still relatively interpretable

**Limitation:**
- Sensitive to overfitting if the degree of the polynomial is too high


### Ridge and Lasso Regression (Regularized Linear Models)

**What they do:**

Add penalties to the linear regression equation to reduce the impact of weak or noisy features.

- Ridge Regression: Shrinks all coefficients slightly
- Lasso Regression: Shrinks some coefficients to zero — effectively removing them

**Example in basketball:**
You include 20 features in your model (minutes, assists, height, age, shoe size…). Ridge/Lasso help prevent overfitting by penalizing irrelevant stats like shoe size.

**Why it’s useful:**
- Improves generalization
- Handles multicollinearity (features that overlap in meaning)
- Encourages simpler models

**Limitation:**
- Slightly harder to interpret
- You must tune the penalty amount

### Boosted Decision Tree Regression (You Will Use This Model)

**What it does:**
Builds a series of small decision trees, each one improving upon the last by focusing on past errors. It doesn’t assume a linear relationship and can capture complex interactions 
between variables.

**Example in basketball:**
A basic tree might say:
- If MP > 25 and FG% > 50%, then predict 18 points
- If AST < 3 and MP < 15, then predict 6 points

The model refines itself layer by layer, focusing on cases it got wrong earlier.

**Why it’s useful:**
 - Highly accurate, even with messy or non-linear data
 - Captures interactions between features
 - Frequently used in real-world ML competitions

**Limitation:**
 - Harder to interpret (can’t be reduced to a line or single formula)
 - Slightly slower than linear models

You’ll use this in Azure ML Designer as a comparison model to test whether accuracy improves over linear regression.

### Decision Forest Regression
**What it does:**

Creates a large number of randomized decision trees and averages their predictions. It works by reducing overfitting and capturing a wide variety of patterns.

**Example in basketball:**
Different trees in the forest might focus on minutes, others on assists, others on FG%. The average of their predictions gives a stable output.

**Why it’s useful:**
- Robust to noisy data
- Generally improves accuracy over single-tree models
- Less sensitive to specific feature splits

**Limitation:**
- Not easily explainable (black-box)
- Can be slower on large datasets

### Neural Network Regression
**What it does:**
Uses layers of math-based neurons to learn patterns in complex or high-dimensional data. These models are extremely flexible and powerful, especially when large amounts of training data are available.

**Example in basketball:**
A neural network might use 20+ stats — plus unstructured inputs like text or images — to predict season performance trends.

**Why it’s useful:**
- Powerful with large, unstructured datasets
- Can model patterns that no other model type can

**Limitation:**
- Requires lots of data
- Very hard to interpret
- Overkill for your current dataset of ~80 rows

Not used in this lesson, but it is important to know it exists in the broader ML ecosystem.


### Quantile Regression

**What it does:**
Instead of predicting just an average value, it predicts a range or percentile — like the 10th, 50th, or 90th percentile of scoring.

**Example in basketball:**
The model could tell you:“Player A is likely to score between 10 and 18 points in 80% of cases.”

**Why it’s useful:**
- Helps estimate uncertainty
- Good for risk-sensitive decisions

**Limitation:**
- Less intuitive for beginners
- Not available in Azure ML Designer by default

### Poisson Regression
**What it does:**

Used for predicting count-based events, not continuous values. It assumes the target is a non-negative integer.

**Example in basketball:**

Predicting number of fouls, rebounds, or 3-point attempts — where outcomes are whole numbers, not decimals.

**Why it’s useful:**
- Models event frequency
- Often used in sports stats modeling

**Limitation:**
- Not suited for predicting continuous values like PTS
- Deprecated in Azure ML Designer

### Focus for his Lesson

Today you’ll use and compare:

- Linear Regression – A simple, interpretable baseline

- Boosted Decision Tree Regression – A more powerful, layered model

You’ll build both in Azure, compare the results, and then make a data-driven recommendation to your coach.

**Summary**

Today, you learned that regression is a machine learning method used to predict numbers, like how many points a basketball player might score, using other known stats such as minutes played or assists.

You explored different types of regression models, including:

- Linear Regression, which fits a straight line between stats and outcomes
- Boosted Decision Tree Regression, which builds if-then rules to model more complex patterns
- And others like Polynomial, Ridge/Lasso, and Decision Forest Regression, each used in different real-world scenarios

You also learned that the model you choose depends on your data and the type of relationship you're trying to capture. Some models are easier to explain; others are more 
powerful but harder to interpret.

In this lesson, you’ll build both a Linear Regression and a Boosted Decision Tree Regression model using Azure ML Designer. You’ll test how well they predict player performance and make a recommendation to your coach based on your model’s results.

This work sets the foundation for understanding how data can drive sports decisions — not just with guesswork, but with machine learning.


### Understanding the Dataset

Before you build your regression model, take a moment to understand the data you'll be working with. You’ll be using a realistic, synthetic dataset built for sports analytics.

**What’s in the dataset?**
This dataset includes stats for 120 basketball players, each with:
- MP: Minutes Played
- AST: Assists
- FG%: Field Goal %
- TRB: Total Rebounds
- PTS: Points Scored (target column)
- Plus: 3P%, FT%, TOV, STL, BLK, G, GS, and Tier

These stats were selected because they are often used by real coaches and analysts to evaluate player performance.

**Why use synthetic data?**

Synthetic means the data is not from real players, but was generated to follow real-world patterns. This gives us:

- A clean, complete dataset (no missing values)
- A wide range of player styles and roles
- Control over quality for learning and testing

In the real world, data is often messy, private, or hard to access. Synthetic data lets us focus on learning how models work, without distractions.

**Why 120 players?**
We expanded the original dataset to 120 rows to:

- Train more accurate models
- Improve Boosted Decision Tree performance
- Give more variety for testing predictions

**What are we trying to predict?**

Your task is to predict a player’s PTS (points scored) using other stats. You’ll use:

- Linear Regression (a basic model)
- Boosted Decision Tree Regression (a more powerful model)

You’ll compare how well each model performs and decide which player the coach should start


