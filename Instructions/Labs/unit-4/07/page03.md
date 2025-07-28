# Understanding the Score Bin Table (Model Evaluation)

This table helps us understand how confident the model was in its predictions and how those confidence levels relate to actual performance.

Each row in this table represents a score bin, which is a range of model confidence values. These bins help us see how well the model performs at different confidence levels.

## Column-by-Column Explanation

**Score bin**
This shows the range of confidence scores (probability values) for predictions. For example:
- (0.900, 1.000] means the model predicted with 90% to 100% confidence.

**Positive examples**
- The number of actual positive cases that the model predicted within this score range.

**Negative examples**
- The number of actual negative cases that fell in this score range.

**Fraction above threshold**
- The percentage of predictions in this bin that are above the classification threshold (default is 0.5).
- This helps us understand how many predictions are confidently classified.

**Accuracy**
- Shows how many predictions in this bin were correct. A value of 1.0 means 100% accurate.

**F1 Score**
- This combines precision and recall into a single number. Closer to 1 means better performance.

**Precision**
- Out of all predicted positives in this bin, how many were correct?
- A value of 1.0 means there were no false positives.

**Recall**
- Out of all actual positives in this bin, how many did the model catch?
- A value of 1.0 means no false negatives.


### Negative precision / Negative recall
These are the same as precision and recall, but focused on the negative class — how well the model predicted and captured actual "no" labels.

### Cumulative AUC
This helps track how well the model is ranking examples overall. It builds over all score bins and should increase as we include more confident predictions.

## How to Interpret This Table
1. Most positive examples (154 + 21 + 2 = 177) fall in the top 3 bins (confidence > 0.7): This means the model is making highly confident predictions for most positive 
cases — and they’re correct.

2. No negative examples were classified in these top bins, showing excellent separation between classes.

3. In the lowest bin (0.000, 0.100], we see 94 negative examples, which is good — this means the model was confident these were negative, and it was right.

4. F1 Score, Precision, and Recall are all perfect (1.0) in the high-score bins and slightly lower in low-score bins, which is expected.

5. The fact that the model doesn’t place any positive examples in the low-score bins also confirms that it’s not confused or uncertain when identifying the positive class


### Final Insight

This table gives strong evidence that:

- The model is confident when it makes positive predictions.
- It rarely misclassifies negative examples.
- Most predictions are made at high confidence with high precision and recall.

>**Note**: It’s another confirmation that this model is performing extremely well — but always keep in mind that real-world data may not behave this cleanly.

### Make a Delay Prediction
You will reflect on how each step in your pipeline contributed to building a working prediction model, and apply what you have learned to a real-world scenario. 

### Instructions 
Now that you have built your full pipeline using Azure ML Designer, step back and think about what your model is doing and how it could support real decisions on the factory 
floor. 

Answer the questions below individually or with a partner.

### Part 1: Scenario-Based Prediction 
Imagine you are reviewing a new shipment record before it arrives: 

- Material: Engine Mount 
- Distance_Miles: 500 
- ETA_Days: 3 

Analize the following questions:

- Q1: Based on the data and patterns you have seen so far, would you predict this shipment to be on time or delayed? 

- Q2: What factors in the record influenced your decision?

### Part 2: Understanding the Pipeline 
Match each Azure component to what it does. You can draw lines or write the letter that 
fits. 

Think about this question:

- Q3: Which step would be most important if your dataset had blank entries in ETA or Distance?


**Part 3: Quick Reflection**

Consider the following questions:
  - **Q4: What was the most surprising thing you learned while building the model?** 
  - **Q5: How could a factory use your model to make smarter inventory decisions?** 

>**Note**: This activity will give you a chance to consolidate your understanding and prepares you for the Explain section, where you will evaluate the impact and performance of their model.



**Your Model**
**What Did Your Model Actually Do?**
You just built a machine learning model that can predict whether a shipment will be on time or delayed, using structured data about past deliveries. In a real manufacturing environment, even a single delayed shipment can cause a chain reaction: 
  i. Missed deadlines on the assembly floor.
  ii. Unplanned downtime for machines and workers.
  iii. Extra costs from rush orders or emergency sourcing.

Your model helps prevent those problems by making data-driven predictions in advance. Rather than reacting to shipment delays as they happen, this system enables your team to make proactive decisions—like ordering early, choosing alternate vendors, or adjusting production schedules based on predicted risk. 

### What Did You Teach the Model? 

The model learned from historical data such as: 
  i. Distance traveled 
  ii. Estimated and actual delivery times 
  iii. Material type 
  iv. Vehicle used 
  v. Shipment quantity 

These inputs helped the model recognize patterns that usually lead to delays. For example: 
  i. Longer distances might mean more delays.
  ii. Certain materials may arrive late more often.
  iii. Some carriers may be more reliable than others.

When a new shipment record is entered into the pipeline, the model uses what it has learned to classify that shipment as: 
- On Time (0) 
- Delayed (1) 

This is a binary classification model—it decides between two possible outcomes. Unlike guessing or manual guesswork, the model uses patterns backed by data to make its 
prediction. 

### How Did You Check If It Worked? 
After training the model, you evaluated its performance using built-in tools in Azure ML Designer. These tools help determine whether your model is ready to support real-world 
decisions: 
  i. Confusion Matrix: Tells you how many predictions were correct vs. incorrect. 
  ii. Accuracy: Shows the percentage of correct predictions across the whole test dataset. 
  iii. Precision: Out of all predicted “delayed” shipments, how many actually were delayed? 
  iv. Recall: Out of all actual delayed shipments, how many did the model catch? 
  v. F1 Score: Combines precision and recall into one performance number. 
  vi. ROC Curve: Measures how well the model separates “delayed” from “on time” examples at different thresholds. 

#### By analyzing these results, you can decide whether your model is: 
- Good enough for use in production 
- Too inaccurate or biased to be trusted 
- In need of additional data or another model type


#### Real-World Scenario: Manufacturing Floor Delivery Challenge 
Let’s say you work for a company that assembles electric motors used in vehicles. Every day, your warehouse receives key parts like aluminum casings, rotors, copper windings, 
and bearings. 

**Your production manager explains:** 
“Even one late delivery causes a ripple across the line. We lose hours of build time, 
reschedule labor, and sometimes even miss our own shipping deadlines. I need a way to 
spot these risks earlier.” 
Your job is to build a system that uses past delivery records to predict risk. 
With the machine learning pipeline you just created, your team could: 
i. Flag risky shipments ahead of time.
ii. Reorder vulnerable materials sooner.
iii. Adjust production shifts based on updated timelines.
iv. Even auto-notify supervisors when a predicted delay crosses a certain confidence 
threshold.
This kind of system can prevent thousands of dollars in downtime and allow the factory 
to respond proactively instead of reactively. 
Think Like a Factory Analyst 
Your model has real impact—but its usefulness goes beyond shipping. Predictive analytics 
like this are being used all across modern factories. Think about these situations: 
i. Q1: Could we build a similar model to predict machine failures using sensor 
data from manufacturing equipment? 
ii. Q2: What if we used this same idea to forecast inventory shortages, based on 
production speed and order volume? 
iii. Q3: Could we train a model to detect which suppliers are most likely to deliver 
damaged or incomplete shipments? 
Each of these ideas represents a way that machine learning transforms operations—not by 
replacing human judgment, but by amplifying awareness and accelerating smart 
decisions. 
Scenario:
Imagine you’re presenting your recommendation to the Inventory Planning Manager at a 
manufacturing plant. Write a short email or memo explaining:
• What your model predicts
• How confident you are in it (based on R² and MAE)
• One suggestion to improve inventory planning decisions

















