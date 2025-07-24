# Hands-On-Lab: Troubleshooting in Azure Machine Learning Designer

In this hands-on lab, you will step into the role of a junior data scientist tasked with diagnosing and fixing issues in a malfunctioning Azure Machine Learning pipeline. You will explore a pre-built pipeline containing common configuration errors, interpret system-generated error messages, and troubleshoot each problem step-by-step. By the end of the lab, you will have hands-on experience identifying and resolving real-world issues that can occur during model development, helping to reinforce your understanding of pipeline workflows and debugging techniques in Azure ML.

### Task 1: Set Up the Azure ML Workspace

1. **Log in** to [Azure Machine Learning Studio](https://ml.azure.com/) when prompted provide below credentials.

    - **Email/Username:** <inject key="AzureAdUserEmail"></inject>

    - **Password:** <inject key="AzureAdUserPassword"></inject>
   
1. On the **Create a new workspace to get started with Azure ML** fill in the following fields:

    - **Name**: Enter `Sports_Analytics`  **(1)**
    - **Friendly Name**: Leave default
    - **Hub (Optional)**: Leave this as **None** unless instructed otherwise **(2)**
    - **Advanced Settings**:
    - **Subscription**: Select the appropriate Azure subscription from the dropdown **(3)**
    - **Resource Group**: Select **ODL-SREB-U5L10** **(4)**
    - **Region**: Select **East US 2 (5)** for better performance.
    - After filling out all the required fields, click the **Create (6)** button.

      ![](../images/N10c1.png) 

       >**Note**: If you **did not** see the page like Figure 1, simply click **“Create Workspace”** on your dashboard and fill out the fields as described in Step 2.

1. Wait for the workspace to create, it may take around 2-3 minutes.

1. Now navigate to your newly created workspace. On the **left-hand menu**, click **Workspaces (1)**. Select the workspace you just created `Sports_Analytics` **(2)**.

     ![](../images/N10c2.png) 

1. This will take you inside the workspace where you can build and run machine learning experiments.

     ![](../images/N10c3.png)  

1. In the side menu of your workspace, select **Designer (1)**. Click **Create a new pipeline using classic prebuilt components (2)**.     

     ![](../images/N10c4.png) 

### Task 2: Add a dataset to your Azure ML pipeline in the Designer:

1. On the **left panel**, under the **Data (1)** tab, click the **➕ (plus icon) (2)** to upload a dataset.  

     ![](../images/N10c5.png)

1. On **Create data asset** page enter the following data.

    - Name: Enter **`Train_Test_Validation_dataset` (1)**  
    - Select type: **Tabular (2)**  
    - Click **Next (3)**  

      ![](../images/N10c6.png)   

1. On the **Choose a source for your data asset** page, choose **From local files (1)** the click on **Next (2)**. 

    ![](../images/lab01-image9.png) 

1. On the **Select a datastore** page select the following option:  
    
    - Under **Datastore type**, select **Azure Blob Storage (1)**  
    - Choose the datastore named: **`workspaceblobstore` (2)**  
    - Click **Next (3)**  

      ![](../images/lab01-image10.png) 

1. On the **Choose a file or folder** page, select **Upload files or folder (1)** from the dropdown, then select **Upload files (2)**.

    ![](../images/lab01-image11.png)  

1. **File or Folder Selection**  

    - In the file browser, select the file: `SC_Basketball_Enhanced.csv` **(1)** 
    - Wait for the file to appear under “Upload list”  
    - Click **Next (2)**  

      ![](../images/N10c7.png)

1. On the **Settings** page, review the fields and ensure they match the expected format then click **Next**  

     ![](../images/N10c8.png)

1. On the **Schema** page, ensure the schema fields are correctly recognized then click **Next**  

     ![](../images/N10c9.png) 

1. On the **Review** page, click **Create** to finalize the dataset upload

     ![](../images/N10c10.png)   