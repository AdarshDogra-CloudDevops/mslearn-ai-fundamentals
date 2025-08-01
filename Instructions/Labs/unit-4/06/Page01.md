# Lesson 6: Analyzing Manufacturing Feedback with Text Data

## Lesson Description:
In this lesson, students will explore how manufacturers use customer feedback from 
surveys, warranty claims, and product reviews to identify issues and improve product 
quality. Students will process and analyze real-world textual feedback using a machine 
learning pipeline to predict customer satisfaction and discover patterns such as common 
defects or complaints. 

## Main Learning Goal:
Students will explore how manufacturers use customer feedback from surveys or forms to 
identify improvement areas. They will process and analyze real-world textual data using a 
machine learning pipeline in Azure ML Designer to predict customer satisfaction and 
discover patterns.

## Essential Question:
How can manufacturers use customer feedback data to improve products, services, and 
customer satisfaction? 

## Standards:

- 4.4: Evaluate the use of a large data set to explore a real-world scenario. 
- 3.4: Justify the choice of data collection method, data analysis tool, and data 
representation tool.

## Objectives:
By the end of this lesson, students will be able to:

- Explain how manufacturers collect and use text-based feedback. 
- Clean and process customer feedback using Text Preprocessing in Azure ML 
Designer. 
- Convert text into numerical form using Extract N-Gram Features from Text. 
- Train a classification model to predict satisfaction levels. 
- Evaluate model results using accuracy, precision, recall, and a confusion matrix. 
- Reflect on the business value of analyzing large volumes of feedback.


### What’s in a Review?

Let’s begin by looking at a couple of real customer reviews from a car service company -one positive and one negative.

**Positive Review Example:** 

“I brought my vehicle in for a routine oil change and everything went smoothly. The staff was friendly, and the service was completed faster than expected. Very satisfied.” 

**Negative Review Example:** 

“It took three days longer than they promised. No updates, poor communication, and when I finally got the car back, the problem still wasn’t fixed. I won’t be returning.”

Take a moment to read both comments. Then discuss the following with your class:

1. If you were in charge of this company, what would you want to fix?

2. What types of problems or strengths do these comments highlight?
 
3. Why do you think companies ask customers to fill out feedback forms?

Reading one or two reviews is easy. But imagine being the operations manager at a car company where 10,000 service forms are submitted every month. You can’t possibly read all of them—and even if you did, you might miss patterns. That’s where machine learning can help.

But here’s the catch: machines don’t read like humans do. They don’t understand tone, 
sarcasm, or frustration—not unless we teach them how to look for clues in the words 
people write.

**So how do we help a machine "read" feedback?** We turn the text into something it can understand: numbers and patterns.
Let’s walk through the key steps that make that possible.

1. **Text Preprocessing:** Before machines can work with text, it must be cleaned. This includes removing punctuation, changing all letters to lowercase, and deleting common “filler” words that don’t carry meaning (like “the” or “and”).

    - a. Example: “Very satisfied!” becomes “very satisfied”

2. **Tokenization:** Breaking a sentence into smaller pieces—usually individual words—so the computer can analyze them separately.

    - a. Example: “poor communication” becomes [“poor”, “communication”]


3. **Stop Words Removal:** Removing common words that don’t help the model 
understand meaning.

    - a. Example: “I am very happy” becomes “happy”

4. **Looking at N-Grams:** Some words only make sense together. We keep them that 
way to keep the meaning clear. These groups are called N-Grams.

    - a. Example: “not satisfied” is more meaningful together than just the word 
“not”

5. **Vectorizing the Words**: Converting words into numbers that reflect how often they appear and how important they are.

    - a. Example: The word “delay” might get a higher score in negative reviews.

6. **Teaching the Model – Classification:** Once we’ve done all the above, we train the 
machine to spot patterns and sort reviews into groups like satisfied or unsatisfied.

    - a. Example: If the review contains words like “delay,” “problem,” or “won’t return,” the model may classify it as unsatisfied.

### Sentiment Classification Using Azure ML Designer

Now that you’ve explored how manufacturers collect feedback and why it matters, it’s 
time to take on the role of a data analyst for a customer support team. 

#### Your goal: 

Use Microsoft Azure ML Designer to build a model that predicts whether a customer was 
satisfied or unsatisfied based on their written feedback. You will clean and process feedback text, convert it into numerical features, and train a classification model to identify patterns in the language of satisfied vs.unsatisfied customers.

### Understanding the Dataset

We’ll work with a real dataset (.CSV file) called `Manufacturing_Customer_Feedback`, 
including actual customer comments along with additional information, including:

-  Customer ID
- Vehicle 
- Service Date 
- Feedback Text 
- Satisfaction Score


Using Azure Machine Learning Studio, you will go through the process of turning raw text into useful insights, or a Sentiment Classification. To do this, you must: 

1. Preprocess the text – Remove punctuation, filler words, and anything else that does not add any meaning to the text. 

2. Convert text into numeric data – Use tools like TF-IDF to convert the feedback into numbers a model can understand and interpret. 

3. Train a binary classification model – Teach your model to classify each review as 
either “Satisfied” or “Unsatisfied.” 

4. Evaluate results using accuracy, precision, and confusion matrix.

    





