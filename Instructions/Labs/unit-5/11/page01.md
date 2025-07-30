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

### Common Types of Regression in Machine Learning

**Linear Regression**

