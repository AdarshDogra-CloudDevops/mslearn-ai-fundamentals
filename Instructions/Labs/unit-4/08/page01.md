# Lesson 8: Spot the Flaw - Detecting Defective Products with Image Classification

## Lesson Description

In this lesson, students will explore how artificial intelligence can assist with quality control in manufacturing by identifying defective parts. They will examine real product images, train a machine learning model using Azure Custom Vision, and evaluate its performance. Through guided discussion, students will also consider when to trust a model’s prediction and how combining data sources can improve reliability and safety in automated systems.

## Main Learning Goal

Students will explore how computer vision is used in manufacturing to identify defective parts. Using a real dataset of metal casting images, students will train and evaluate a machine learning model that distinguishes between defective and non-defective products.

## Essential Question

**How can AI models trained on product images help factories improve quality control and reduce waste?**

## Standards

* **4.4**: Evaluate the use of a large data set to explore a real-world scenario.

## Objectives

* Understand how computer vision supports manufacturing quality control.
* Load and explore an image dataset in Azure ML or Python.
* Train a binary classification model to detect defective products.
* Evaluate the model’s accuracy and suggest improvements.
* Explain how this model helps manufacturers reduce errors and improve product reliability.

## Would You Ship This Part?

Imagine you're working at a factory that builds car parts. Two parts come down the line. One is decent, the other one has a flaw.

  ![](../images/0408/1.png) 

  ![](../images/0408/2.png) 

Your job: decide if each part should be shipped to a customer.

### Discussion:

* Would you approve both parts for shipping?
* What are the consequences of a defective part going unnoticed?
* Could you make 500 such decisions per hour?
* Could a computer model do it better or more consistently?

AI in high-stakes industries helps reduce risk of:

* Engine failure due to cracks
* Turbine damage from misalignment
* Medical device failure

Today, students will build a visual classifier to support human decision-making in factories.

## Build a Defect Classifier Using Azure ML
### Understanding the Dataset
We will be working with an image dataset containing hundreds of labeled examples of cast 
metal parts. Each image falls into one of two categories: 
  - Non-Defective: The part has passed visual inspection and contains no detectable 
flaws. 
  - Defective: The part has failed inspection due to a crack, dent, chip, or other visible 
anomaly.

The images are consistent in framing, angle, and lighting. Some flaws are subtle, while 
others are more obvious - giving the model a realistic variety of learning conditions.

In large-scale manufacturing, workers often inspect thousands of parts per day. Manual inspection is prone to error from fatigue, lighting conditions, or oversight. It’s also timeconsuming and difficult to scale across shifts and locations.

Using image-based machine learning tools like Azure Custom Vision, companies can standardize visual inspections across plants and catch subtle flaws human inspectors may miss. This overall reduces the number of defective items that reach customers.

We’ll be uploading this dataset to Azure Custom Vision and building a visual classification model. There’s a handful of tasks to complete this, so let’s dive in!



