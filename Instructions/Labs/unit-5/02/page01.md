# Lesson 2: Sports Data
## Lesson Description:
In this lesson, students will explore the types of data needed for sports and predictive 
analytics. They will learn the importance of preprocessing raw data to make it usable for 
analysis. Students will then apply these skills by working with a dataset in Azure, using 
Azure tools to clean, organize, store, and visualize their data.

## Main Learning Goal:
Students will understand how to preprocess and organize data using tools like Azure to 
prepare it for predictive analytics in sports. 

## Essential Question:
How do we transform raw data, using tools like Azure, to make data useable for sports 
analytics?

## Standards:

- DA 3.3 - Select methods of data organization and storage, local, portable, cloud 
storage. 
- DA 3.3 - Explain how different collection methods and tools influence the amount 
and quality of the data this is observed and recorded. 
- DA 3.3 - Analyze Utilize and visually represent static data.

## Objectives:
- Explain the basics of data cleaning, sorting, and storage methods. 
- Upload and manage a dataset in Azure Machine Learning. 
- Apply Azure tools to clean, organize, store, and visualize data


## NASCAR Numbers
Many different types of data are used in sports analytics, ranging from race winners to lap 
speeds. To begin today’s lesson, we will take a closer look at the dataset we will be working 
with: [NASCAR Season History 1949-Present](https://www.kaggle.com/datasets/thedevastator/nascar-champions-season-history-1949-present). The CSV file is located here.

You will have few minutes to explore the dataset. Then, answer the following questions on 
your SREB_U5_L2_Handout:

- Q1: What types of data are included in this dataset? (e.g., numerical, 
categorical, descriptive)
- Q2: What kinds of data could NASCAR teams use to build a more accurate 
machine learning model?
- Q3: Are there any variables that are difficult to predict or account for (such as 
mechanical failures, weather conditions, or driver injuries)?

You will discuss the answers as a class. Once you share your observations, answer the 
fourth question both aloud and in writing.

- Q4: What would we need to do to make this raw data usable for machine 
learning?

Before most data can be analyzed, it must be preprocessed and stored. Preprocessing 
fixes errors, fills in missing information, and organizes it into a usable format. Storing the 
data properly ensures that it can be safely accessed, managed, and used efficiently 
through the machine learning process.


## Preprocessing Data 
There are three key steps in preparing data for use: cleaning, sorting, and storing.

## Data Cleaning

Data cleaning is the process of fixing or removing incorrect, corrupted, incorrectly 
formatted, duplicate, or incomplete data within a dataset. For more information, refer to 
the following source [Guide To Data Cleaning: Definition, Benefits, Components, And How 
To Clean Your Data](https://www.tableau.com/learn/articles/what-is-data-cleaning)

Basic cleaning tasks include:

- Removing missing or poorly formatted data
- Dropping duplicate entries
- Eliminating unnecessary features – Removing columns that do not add value
- Normalizing data – Scaling values to a consistent range
- Encoding categorical data – Turning text labels into numerical form

Without proper cleaning, data can be misleading, inconsistent, or incomplete, leading to 
inaccurate analysis and unreliable machine learning models.


## Sorting Data
Sorting is the process of arranging data into meaningful order so that you can analyze it 
more effectively. Please consult the following source for further information [Oracle® 
Business Intelligence Discoverer Plus User's Guide](https://docs.oracle.com/html/B13915_02/sorting.htm)

Basic types of sorting include:

- Ascending or descending order
- Filtered sorting - Sorting based on a condition
- Chronological sorting – Ordering by time or date

Organizing data through sorting helps reveal patterns, highlight important trends, and 
prepare the dataset for more effective modeling and visualization.

## Data Storage
In earlier lessons, we explored the importance of external storage. Data storage is 
preserving digital information in a medium for subsequent retrieval. To learn more, refer to 
the following source [What Is Data Storage?](https://www.paloaltonetworks.com/cyberpedia/data-storage). There are several types of storage, each 
serving different purposes depending on how and where the data needs to be accessed.

Common methods of data storage include:

- Local storage – Saving on a computer or local storage
- Portable storage – Saving on removable media like USB drives
- Cloud storage – Saving remotely on platforms like Azure, Google Cloud, or AWS

Proper storage ensures that data remains organized, secure, and accessible when needed, 
which is critical for ongoing analysis, sharing, and building machine learning projects.

Now, let us explore how we can prepare and manage our data using Azure