# Hands-On-Lab: Classification Two Ways - Supervised vs Unsupervised Categorization

In this hands-on lab, you will build and experiment with machine learning models for both classification and clustering tasks. You will apply supervised learning techniques to train models that can predict outcomes based on labeled data, and use unsupervised learning methods to group data based on underlying patterns without predefined labels. By comparing the performance and results of these different algorithms, you will gain insights into how each approach can be used to categorize and understand data in unique ways.

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
    - **Resource Group**: Select **ODL-SREB-U5L07** **(4)**
    - **Region**: Select **East US 2 (5)** for better performance.
    - After filling out all the required fields, click the **Create (6)** button.

      ![](../images/n57c1.png) 

       >**Note**: If you **did not** see the page like Figure 1, simply click **“Create Workspace”** on your dashboard and fill out the fields as described in Step 2.

1. Wait for the workspace to create, it may take around 2-3 minutes.

1. Now navigate to your newly created workspace. On the **left-hand menu**, click **Workspaces (1)**. Select the workspace you just created `Class_Workspace` **(2)**.

     ![](../images/n57c2.png) 

1. This will take you inside the workspace where you can build and run machine learning experiments.
  

1. In the side menu of your workspace, select **Designer (1)**. Click **Create a new pipeline using classic prebuilt components (2)**.     

     ![](../images/n57c4.png)

### Task 2: Create a Preprocessing Pipeline     

1. Switch to the **Component** tab in the left panel **(1)** and search for **Clean Missing Data (2).** Drag that component onto the canvas **(3)**.   

     ![](../images/n57c5.png)

1. Double click on **Clean Missing Data (1)** and then select **Edit Column (2)** under `Columns to be cleaned`.

     ![](../images/n57c6.png)

1. Select **All Columns (1)** and then **Save (2)**.

     ![](../images/n57c7.png)

1. Select **Save**.

1. Switch to the **Component** tab in the left panel **(1)** and search for **Remove Duplicate Rows (2).** Drag that component onto the canvas **(3)**.

    - Connect **left output** of **Clean Missing Data** to **Dataset** of **Remove Duplicate Rows** **(4)**

      ![](../images/n57c8.png)

1. Double click on **Remove Duplicate Rows (1)** and then select **Edit Columns (2)**.

     ![](../images/n57c9.png)

1. Select **All Columns (1)** and then **Save (2)**.

     ![](../images/n57c10.png)

1. Select **Save**.

     ![](../images/n57c11.png)

1. Switch to the **Component** tab in the left panel **(1)** and search for **Split Data (2).** Drag that component onto the canvas **(3)**.

    - Connect **Output** of **Remove Duplicate Rows** to **Dataset** input of  **Split Data** **(4)**

      ![](../images/n57c12.png)

1. Select the **Edit** icon to rename the Pipeline. 

     ![](../images/n57c13.png)

1. Name the pipeline as **Preprocessing_Pipeline (1)** and then **Save (2)**.   

     ![](../images/n57c14.png)

### Task 3: Add the Dataset to Your Pipeline Canvas     

1. Navigate to **Data (1)** from the left navigation and then select **+ Create (2)**.

     ![](../images/n57c3.png)

1. On **Create data asset** page enter the following data.

    - Name: Enter **`Clemson-Tigers-School-History` (1)**  
    - Description: **Contains Clemson University’s Tigers football team season stats. (2)**
    - Select type: **Tabular (3)**  
    - Click **Next (4)**  

      ![](../images/n57c15.png)     

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

    - In the file browser, select the file: `Clemson Tigers School History.csv` **(1)** 
    - Wait for the file to appear under “Upload list”  
    - Click **Next (2)**  

      ![](../images/n57c16.png) 

1. On the **Settings** page, review the fields and ensure they match the expected format then click **Next**  

    ![](../images/n57c17.png) 

1. On the **Schema** page, ensure the schema fields are correctly recognized then click **Next**  

    ![](../images/n57c18.png) 

1. On the **Review** page, click **Create** to finalize the dataset upload

    ![](../images/n57c19.png)


### Task 4: Cloning our Preprocessing Pipeline

1. Navigate to **Pipeline (1)** from the left navigation pane and then Select **Pipeline drafts (2)** tab and then click on **Preprocessing_Pipeline (3)**.

    ![](../images/n57c-20.png)

1. Click the **Clone** button at the top. This will create a copy of the pipeline and open it in a new tab.

    ![](../images/n57c21.png)

1. Select the **Pencil** icon to rename the Pipeline.    

    ![](../images/n57c22.png)

1. Rename your cloned pipeline to **Clemson – Supervised Pipeline (1)** and then **Save (2)**.    

    ![](../images/n57c23.png)


### Task 5: Classification in Azure (Supervised)

We will be using logistic regression, a common supervised learning model, to predict whether Clemson will win or lose a bowl game based on the season’s performance data.

1. Navigate to the **Data** tab on the left, drag your **Clemson dataset** onto the pipeline canvas **(1)** and connect it to the existing **preprocessing pipeline (2)** and then **Save (3)**.

    ![](../images/n57c24.png)

1. Double click on the **Clean Missing Data (1)** component. Select **Edit Column** under “Columns to be cleaned” to include the **Bowl** column, either “With rules” or “By name”.     
    
    ![](../images/n57c25.png) 

1. Select **Column names (1)** and then choose **Bowl (2)** and then **Save (2)**.

    ![](../images/n57c26.png)

1. Set **Cleaning mode** to **Remove entire row (1)** to filter out seasons that do 
not include a bowl game and then **Save (2)**.

    ![](../images/n57c27.png)

     >**Note**: This ensures our model only trains on seasons with a **win/loss** outcome in a bowl.

1. The **Split Data** component already handles splitting our data into training and test sets, so now we need to train our model.     

1. Switch to the **Component** tab in the left panel **(1)** and search for **Train Model (2).** Drag that component onto the canvas **(3)** below the `Split Data` component.

    - **LEFT (training data) output** from the **“Split Data”** component into 
the **Right** **“Dataset”** input of the **“Train Model”** component **(4)**

      ![](../images/n57c28.png)

1. We will be using **logistic regression** for our model, because it classifies outcomes into one of two groups, in our case, win or loss.     

1. Switch to the **Component** tab in the left panel **(1)** and search for **“Two-Class Logistic Regression (2).** Drag that component onto the canvas **(3)** beside the `Split Data` component. 

    ![](../images/n57c29.png)

1. Connect it to the left **“Untrained model”** input on the **“Train Model”** component **(1)**.   

     - Connect the **left output of Split Data** component to **Right input of Train Model** **(2)**

       ![](../images/n57c30.png)

1. Double click the **“Train Model”** component **(1)**. Under Label column, select **Edit Column (2)**. 

    ![](../images/n57c31.png)

1. Under Label column, select **“Win/Loss” (1)**  and then **Save (2)**.     

    ![](../images/n57c32.png) 

1. Select **Save**.

    ![](../images/n57c33.png) 

1. Switch to the **Component** tab in the left panel **(1)** and search for **“Score Mode (2).** Drag that component onto the canvas **(3)** below the `Train Model` component. 

    ![](../images/n57c34.png) 

1. Connect:

     - Connect the **output** of the **“Train Model”** to the **left input of “Score Model.” (1)**

     - Connect the **RIGHT (test data) output from “Split Data”** into the **right input of “Score Model.” (2)**

     - Then **Save (3)**

       ![](../images/n57c35.png) 

        >**Note**: This will compare the 
model’s predictions against the actual win/loss outcomes.     

1. Switch to the **Component** tab in the left panel **(1)** and search for **Evaluate Model (2).** Drag that component onto the canvas **(3)** below the `Score Model` component. 

     - Connect the **output from “Score Model”** to the **left input for “Evaluate Model.” (4)**

     - Then **Save (5)**

       ![](../images/n57c36.png) 

1.        

