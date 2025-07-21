# Optimizing Inventory with Logistics Data: A Supply 
Chain Simulation

### Task 1: Create Azure ML Workspace

In this task you will set up an Azure Machine Learning workspace where all your machine learning assets and experiments will be organized and run. You will learn how to create a workspace in the Azure ML Studio, select the appropriate region and resource group, and navigate to the Designer interface to start building your pipeline.


1. **Log in** to [Azure Machine Learning Studio](https://ml.azure.com/) when prompted provide below credentials.

    - **Email/Username:** <inject key="AzureAdUserEmail"></inject>

    - **Password:** <inject key="AzureAdUserPassword"></inject>
   
1. On the **Create a new workspace to get started with Azure ML** fill in the following fields:

   - **Name**: `Logistics_Prediction`  
   - **Friendly Name**: *(Optional)*  
      Azure will auto-fill this based on the name.
   - **Hub (Optional)**: Leave this as “None” unless instructed otherwise.
   - **Advanced Settings**:
   - **Subscription**: Select the appropriate Azure subscription from the dropdown. 
   - **Resource Group**: Choose an existing one 
   - **Region**: Select **East US 2** for better performance.
   - After filling out all the required fields, click the **“Create”** button.

        ![](../images/lab07-image2.png) 

    >**Note**: If you **did not** see the page like Figure 1, simply click **“Create Workspace”** on your dashboard and fill out the fields as described in Step 2.

1. Now navigate to your newly created workspace. On the **left-hand menu**, click **“Workspaces”**. Locate the workspace you just created `PCA Anomaly Model`.

     ![](../images/lab02-image2.png) 
   
1. Click on its name to open it. This will take you inside the workspace where you can build and run machine learning experiments.

    ![](../images/lab07-image3.png) 

1. Once you are inside your workspace PCA Anomaly Model, look at the left hand side menu to find the **Designer** tab under the Authoring section. Click on 
this tab.

    ![](../images/lab01-image5.png) 

   >**Note**:  This will open the Azure Machine Learning Designer interface where you can  begin creating your machine learning pipeline by dragging and dropping 
components.

1. Once the **Designer** page is loaded, make sure that you’re on the Classic prebuilt tab under the “New pipeline” section. From here, click on the box with a plus sign 
that says, **Create a new pipeline using classic prebuilt components**.

    ![](../images/lab01-image6.png) 

1. Once you click it, you’ll be taken to a blank canvas where you can start building your machine learning pipeline using components such as:
    • Dataset input
    • Data cleaning
    • Model training 
    • Custom script execution
    • Scoring and evaluation

### Task 2: Add a dataset to your Azure ML pipeline in the Designer:

In this task you will upload the manufacturing sensor data to your Azure ML workspace. You will create a tabular dataset from a local CSV file, configure the data source, and add it to your pipeline canvas for further processing.

1. On the **left panel**, under the **Data (1)** tab, click the **➕ (plus icon) (2)** to upload a dataset.  

    ![](../images/lab01-image7.png) 

1. On **Create a new workspace to get started with Azure ML** page enter the following data.

   - Name the dataset: **`logistics_dataset_manufacturing`**  
   - Select type: **Tabular**  
   - Click **Next**  

    ![](../images/lab07-image4.png) 

1. On the **Choose a source for your data asset** page, choose **From local files** the click on **Next**. 

    ![](../images/lab01-image9.png) 

1. On the **Select a datastore** page select the following option:  
   - Under **Datastore type**, select **Azure Blob Storage**  
   - Choose the datastore named: **`workspaceblobstore`**  
   - Click **Next**  

    ![](../images/lab07-image5.png) 

1. On the **Choose a file or folder** page, select **Upload files or folder (1)** from the dropdown, then select **Upload files (2)**.

    ![](../images/lab01-image11.png) 

1. **File or Folder Selection**  
   - In the file browser, select the file: `US_Manufacturing_Logistics_Dataset`  
   - Wait for the file to appear under “Upload list”  
   - Click **Next**  

    ![](../images/lab07-image6.png) 

1. On the **Settings** page, review the fields and ensure they match the expected format then click **Next**  

    ![](../images/lab07-image7.png) 

1. On the **Schema** page, ensure the schema fields are correctly recognized then click **Next**  

    ![](../images/lab07-image8.png) 

1. On the **Review** page, click **Create** to finalize the dataset upload

    ![](../images/lab07-image9.png) 

1. Under the **Data** tab, locate the uploaded dataset named **`logistics_dataset_manufacturing`**.  

    ![](../images/lab07-image10.png) 

1. Click on the dataset card then select **Use data** to **drop it onto the pipeline canvas** on the right. Verify the data placed in the canvas, and click 'Save' to avoid losing progress.

     ![](../images/lab07-image11.png) 
