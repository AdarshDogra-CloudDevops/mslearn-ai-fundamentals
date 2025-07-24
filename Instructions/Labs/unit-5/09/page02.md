# Hands-On-Lab: Algorithms in Action

In this hands-on lab, you will work with core control structures such as sequencing, selection, iteration, and recursion—building blocks of computer and machine learning programs. Through guided exercises and interactive examples, you will observe how each control structure functions within an algorithm. You will then apply these concepts to create simple logic flows, helping you build a strong foundation for developing your own machine learning or programming projects.

### Task 1: Set Up the Azure ML Workspace

1. **Log in** to [Azure Machine Learning Studio](https://ml.azure.com/) when prompted provide below credentials.

    - **Email/Username:** <inject key="AzureAdUserEmail"></inject>

    - **Password:** <inject key="AzureAdUserPassword"></inject>
   
1. On the **Create a new workspace to get started with Azure ML** fill in the following fields:

    - **Name**: Enter `Class_Workspace`  **(1)**
    - **Friendly Name**: Leave default
    - **Hub (Optional)**: Leave this as **None** unless instructed otherwise **(2)**
    - **Advanced Settings**:
    - **Subscription**: Select the appropriate Azure subscription from the dropdown **(3)**
    - **Resource Group**: Select **ODL-SREB-U5L09** **(4)**
    - **Region**: Select **East US 2 (5)** for better performance.
    - After filling out all the required fields, click the **Create (6)** button.

      ![](../images/n59c1.png) 

       >**Note**: If you **did not** see the page like Figure 1, simply click **“Create Workspace”** on your dashboard and fill out the fields as described in Step 2.

1. Wait for the workspace to create, it may take around 2-3 minutes.

1. Now navigate to your newly created workspace. On the **left-hand menu**, click **Workspaces (1)**. Select the workspace you just created `Class_Workspac` **(2)**.

     ![](../images/n59c2.png) 

1. This will take you inside the workspace where you can build and run machine learning experiments.

### Task 2: Setting Up Your Notebook

We will be using a notebook in Azure today to execute all our technical examples. We will be examining 2024 season statistics from the South Carolina Gamecocks football team.

1. Navigate to **Notebooks (1)** from the left menu and then **Close (2)** the pop up.

     ![](../images/n59c3.png) 

1. Select **Add files (1) > Upload files (2)**. 

     ![](../images/n59c4.png) 

1. Click **+** to upload the Notebook.

     ![](../images/n59c5.png) 

1. Select the **L9_Notebook.ipynb**.

1. Once the notebook is uploaded, check the **I trust contents of this file** box **(1)** and then **Upload (2)**.

     ![](../images/n59c6.png) 

1. Select **Add files (1) > Upload files (2)**. 

     ![](../images/n59c7.png)

1. Click **+** to upload the Notebook.

     ![](../images/n59c5.png)

1. Select **Gamecocks_Running_Stats.csv**.

1. Once the notebook is uploaded, check the **I trust contents of this file** box **(1)** and then **Upload (2)**.

     ![](../images/n59c8.png) 

1. Click on **L9_Notebook** to open it. 

     ![](../images/n59c9.png)

1. On the top of the notebook, select **“Select compute”**  dropdown **(1)** and then select the available compute 
instance **(2)**.

     ![](../images/n59c10.png)

1. Click on **Confirm** to **Confirm switch compute**.

     ![](../images/n59c11.png)

1. Copy the path of your dataset by clicking the three dots to the right of it **(1)** and selecting **“Copy file path” (2)**.

     ![](../images/n59c12.png)

1. Paste the file path in the first code block in the notebook where it says `[INSERT FILE PATH HERE]` as shown below. 

     ![](../images/n59c15.png)

1. Press the **play** button to the left of the first code block. This will start the session, which may take `3-5 minute`s, of which you can move ahead with the lesson while it loads.     

     ![](../images/n59c16.png)

1. This will show the top 5 rows of the dataset you just imported and cleaned.

     ![](../images/n59c14.png)



