# Lesson 10: Troubleshooting in Azure ML Designer
## Lesson Description:

In this lesson, students will take on the role of junior data scientists working for a South 
Carolina sports analytics team. They will investigate a faulty Azure ML pipeline filled with 
common configuration errors. Through a hands-on lab, students will identify problems, 
interpret error messages, and fix them step-by-step to restore functionality and continue 
model development.

## Main Learning Goal:

Students will learn to identify and fix common Azure ML Designer pipeline errors through 
error message interpretation and structured troubleshooting steps.
Essential Question:
How can you identify and fix problems in a machine learning pipeline when things go 
wrong?

## Standards:

- CS1.1 – Utilize a common troubleshooting process to identify software problems 
that involve the interpretation of error messages and common system malfunctions

## Objectives:

By the end of this lesson, students will be able to: 

- Recognize a variety of Azure ML Designer pipeline errors.
- Interpret error messages and connect them to specific modules or data steps. 
- Apply a structured troubleshooting process to fix broken or misconfigured 
pipelines. 
- Explain how error resolution improves the reliability of AI-based workflows.


## Fix the Pipeline Before the Deadline (15 Minutes)
## Real-World Scenario 
You are back in your role as a junior analyst for a South Carolina scouting board. You have just been handed a predictive model in Azure ML Designer that is supposed to estimate how many points a player will score—but the pipeline is broken. It will not run. You need to 
fix it before the scout meeting later today.

Now answer these questions: 

- **Q1: If you saw an error while running a machine learning pipeline, what would 
you do first?**

- **Q2: Have you ever seen an error message in Azure before?**

In today’s lesson, you will become a real ML troubleshooter—someone who can read error messages, figure out where things went wrong, and fix them. These skills are essential in real AI careers and future projects


### Real Azure Error 
Below in Figure 1 you can see a pipeline with a red triangle on the Train Model module and an error panel message.

![](../images/g35.png)  


This error is showing up because Azure does not know what target the model is supposed 
to learn. We have forgotten to select the label column, which is the column the model 
should try to predict—in our case, that’s usually PTS.

Point out the visual cues:

- The red warning triangle on the Train Model module
- The validation panel on the left showing the error message
- The “Submit anyway” button indicating that the pipeline will not run correctly

Now, answer the following questions:

- Q1: What is Azure trying to tell us through this message?
- Q2: If you were fixing this, where would you click first?

Let’s clarify the following:

In a working model, we need to tell Azure which column we want to predict. That is called the `label column`. If we leave it blank, the model cannot be trained.

Keep in mind that you will encounter and fix this exact error during the Explore section

## The Goal

Machine learning pipelines do not always work the first time—and that is okay. Every 
professional ML engineer needs to know how to fix failures. Today, you will explore the most common Azure ML Designer errors and learn how to fix each one with confidence.


### Quick Troubleshooting Framework

Consider this short mindset tool you will use throughout the lesson:

When you see an error in Azure ML Designer, here’s a simple way to figure it out:

- Read the error message carefully
  Look for key words like label, input, or disconnected
- Find the module that is causing the issue
  Use the red X in the canvas or look at the message panel
- Try one fix at a time
  Do not guess—test a solution, re-run, and see what changes
  
You’ll use this same process to solve each of the errors we work on today.

### “Decode the Error” Quick Lab
Look at the short error message below:

`Score Model: Input port disconnected. Please connect a dataset and trained model.`

Please, complete the steps below.

- Underline the key parts of the message (e.g., “disconnected”, “dataset”)
- Write a short explanation in your own words: “Q1: What does this mean?”
- On a mini pipeline diagram, circle the module you think the error refers to

You have just completed your first debugging task. Now we will move into full 
troubleshooting mode—fixing seven real pipeline issues one at a time inside Azure ML Designer.


