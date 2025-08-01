# Lesson 9: Training Makes It Smarter

## Lesson Description:

In this lesson, students will collect and use real sensor data from their Arduino-based robot to train a machine learning model in Azure. They will analyze how different data conditions—such as low volume or corrupted readings—affect model performance. The lesson emphasizes workflow design, data preparation, and accuracy evaluation in a 
project-based capstone experience.

## Main Learning Goal:

Students will evaluate how the quality and quantity of training data influence the accuracy and reliability of a machine learning model.

## Essential Question:

How does the training data I collect and prepare affect the accuracy and safety of my 
model?

## Standards:

- 4.4: Describe the role of training data in determining the accuracy and margin of 
error of the model

## Objectives:

- Students will collect and label real sensor data from their robot.
- Students will sketch and plan a machine learning workflow before building in Azure.
- Students will train and test a binary classification model to predict robot shutdown behavior.
- Students will evaluate model performance using accuracy, precision, and confusion matrix, and reflect on how training data impacts results

### Shutdown Signals – Can You Trust the Robot?

Is This Robot Safe?

You’ve just been hired as a machine learning engineer for a smart robotics company. The robot you helped build has three sensors: motion, light, and temperature. It shuts down automatically when any of those conditions become unsafe. Your job now is to train a model to recognize when that shutdown should happen — and when it shouldn’t.

Consider Figure 1, which shows short logs of robot behavior below.
