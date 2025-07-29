# Lesson 13: Classifying Players Using Decision Trees

## Lesson Description:
In this lesson, students will act as basketball scouting analysts and use real-world South Carolina sports data to classify players as starters or non-starters. They will build a decision tree classification model using Azure ML Designer and learn how the model “splits” data to make predictions. Students will select features, build a model using the Two-Class Decision Forest module, and interpret the model’s accuracy and decision process using Azure’s built-in evaluation tools.

## Main Learning Goal:
Students will use Azure ML Designer to train and evaluate a decision tree classifier and 
analyze how the model splits input features to predict player categories.

### Essential Question:
How can a decision tree help us recognize patterns in sports data and make accurate 
classification decisions?

### Standards:
- AP6.2 – Use decision trees and linear regression to make predictions and classifications. (Note: Linear regression is addressed in Lesson 11; this lesson focuses on decision 
tree classification)

### Objectives:

- Select relevant features from a dataset to train a classification model
- Use Azure ML Designer to build a decision tree pipeline
- Predict player classifications (starter vs. non-starter) using model output
- Evaluate model performance using Azure's scoring and evaluation tools
- Reflect on how the model splits input data and makes decisions

### Scouting with Data – Who Starts?

**Pick Your Starters**

**Imagine this scenario:**

You’ve been hired as the head analyst for a South Carolina high school basketball team preparing for the playoffs. Your job? Help the coach choose the best starting three players 
— using data, not gut instinct.

Refer to Figure 1 below for more information.

[](../images/U5lab013-image38.png)

**Answer the following questions:**
   
   - Q1: Which of these players would you start — and why?
   
   - Q2: What patterns do you see that might suggest who’s a strong starter?
   
   - Q3: Could we create a rule based on minutes or assists to make this decision?

**Let’s brainstorm:**

- If you had to write a rule like: “Start the player if…,” Q1: what would it be?

    - There are many perspectives — you may value points, assists, FG%, or time played.

Now we understand that humans use pattern logic to classify — and that this logic can be learned by machines.

**What Is a Decision Tree?**

Let’s explore how a machine might learn to classify players like we just did — using something called a Decision Tree.

  [](../images/U5lab013-image39.png)

**Key points:**

- A decision tree is like a flowchart.
- It learns splits in the data — like “Is minutes per game greater than 25?” — to separate players into groups.
- Each branch leads to a prediction: Starter (1) or Non-Starter (0).
- The tree keeps splitting until it’s confident about its decisions.

**Real example:**
A decision tree might learn that:

- Players with MP > 25 and AST > 3 are often starters.
- Players with low minutes and low assists are usually not.

**Be the Algorithm**

**Imagine the following scenario:**

The coach is choosing a new starter and gives you stats for 5 players. Your job is to predict if a player should start or not using just two features: Field Goal Percentage (FG%) and 
Assists per game.

**Step 1: Review the Data**

  - Analyze Figure 3 below.

      [](../images/U5lab013-image40.png)

**Step 2: Build Your Decision Tree**
  
  - Start with all 5 players.
  - Ask yourself: Q1: What is the best first split? (e.g., “FG% > 45?” or “Assists > 3?”)
  - Create two branches based on that condition.
  - Repeat the process until each leaf ends with only “Yes” or “No.”

**Step 3: Draw and Explain**
**On a blank sheet:**

   1. Draw your tree structure
   2. Label your conditions at each split
   3. Write a 2–3 sentence explanation:

       • Q1: Why did you choose those splits?

       • Q2: Which feature seemed more important?

