# Hands-On-Lab: Sports Data

In this hands-on lab, you will learn how to prepare sports-related data for analysis by using Azure tools. You will clean and transform raw data, organize it for efficient access, and store it in a structured format. Finally, you'll visualize the data to uncover insights and trends that can support predictive analytics in sports.

### Task 1: Creating Your Workspace

1. **Log in** to [Azure Machine Learning Studio](https://ml.azure.com/) when prompted provide below credentials.

    - **Email/Username:** <inject key="AzureAdUserEmail"></inject>

    - **Password:** <inject key="AzureAdUserPassword"></inject>
   
1. On the **Create a new workspace to get started with Azure ML** fill in the following fields:

    - **Name**: Enter `PCA_Anomaly_Model`  **(1)**
    - **Friendly Name**: *(Optional)*  
      Azure will auto-fill this based on the name.
    - **Hub (Optional)**: Leave this as **None** unless instructed otherwise **(2)**
    - **Advanced Settings**:
    - **Subscription**: Select the appropriate Azure subscription from the dropdown **(3)**
    - **Resource Group**: Choose an existing one **(4)**
    - **Region**: Select **East US 2 (5)** for better performance.
    - After filling out all the required fields, click the **Create (6)** button.

      ![](/images/nc1.png) 

       >**Note**: If you **did not** see the page like Figure 1, simply click **“Create Workspace”** on your dashboard and fill out the fields as described in Step 2.

1. Now navigate to your newly created workspace. On the **left-hand menu**, click **Workspaces (1)**. Select the workspace you just created `PCA Anomaly Model` **(2)**.

     ![](../images/lab01-image3.png) 
   
1. This will take you inside the workspace where you can build and run machine learning experiments.

    ![](../images/lab01-image4.png) 