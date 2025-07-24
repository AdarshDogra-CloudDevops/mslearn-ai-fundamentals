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

        >**Note**: This step will generate metrics like **accuracy, precision, recall, F1 score,** and **AUC**. 
  

### Task 6: Run the Supervised Pipeline
      
1. Make sure your pipeline is saved, then click **Configure & Submit** at the top of the screen. 

    ![](../images/n57c37.png)

1. You will now walk through a few configuration steps, then click **Next (3)**:
  
   - Experiment name: **Create new (1)**
   - New experiment name: **Clemson-Supervised-Pipeline(2)**

     ![](../images/n57c38.png)  

1. Leave Inputs & Outputs as is, there is nothing to configure for this step. Click **Next.**      

    ![](../images/n52c24.png)     

1. Now we’re on the **Runtime settings** step of the pipeline submission process. This is where you choose the **computer (called a compute cluster)** that Azure will use to run your 
pipeline.

    - Select Compute Type: From the dropdown, select **Compute cluster (1)**.

    - Click on **Create Azure ML compute cluster (2)**

      ![](../images/nc14.png)  

1. You are now in the **Virtual Machine** tab for setting up a compute cluster. This step helps Azure decide which kind of machine to use for running your pipeline.

    - **Location**: Confirm that the selected region is the same as your workspace (**East US 2**) **(1)**
    - **Virtual Machine Tier**: Leave as default. (do not select "Dedicated" or "Low priority" unless specified otherwise for cost-saving purposes) **(2)**
    - **Virtual Machine Type**: Keep this as **CPU (3)** 
    - **Virtual Machine Size**: Choose **Standard_DS3_v2 (4)**
    - Click **Next (5)**  

      ![](../images/n57c39.png)   

1. **Advanced Settings**: Give a Compute Name as **Test (1)** and leave everything default. Then click **Create (2)**.

     ![](../images/n57c41.png)  

1. Select the Compute Created **Test (1)** and click **Next (2)**.   

     ![](../images/n56c30.png)

     >**Note**: It may take a few attempts to get selected. Please keep trying — you'll be able to proceed once the **Test** status turns **green**.

1. Once on the **final** page, click **Submit**.     

     ![](../images/n57c42.png)  

1. Once submitted, a success notification appears at the top of the page. Click on **'View details'** to monitor the pipeline. It may take some time for the pipeline to complete.

     ![](../images/n57c43.png) 

1. Pipeline may take around `10-15 mins` to complete meanwhile we will move on to setting up our **unsupervised learning pipeline**, which you will build using the previous steps as a guide.      

### Task 7: Clustering in Azure (Unsupervised)

Now you will build an unsupervised machine learning pipeline on your own, following the same general structure as the supervised model we just completed. The goal is to use K-Means Clustering to separate the seasons into three groups that you can later interpret and label as “Elite,” “Average,” and “Poor” based on performance metrics.

Tips that you need to understand in order to successfully build your unsupervised pipeline:

- K-Means clustering only works with numerical and non-null values.
- Search for “clustering” components specifically. Some of the components we 
used before may not be applicable to unsupervised models.
- Unsupervised learning does not use labeled outcomes, so “label column” settings will not be relevant.
- There is a “Validate” button in Azure to check for incomplete or incorrectly 
connected pipeline components.
- If an error occurs during runtime, reviewing the error message can often provide clear direction on what to fix

1. Make another clone of the **Preprocessing Pipeline**.

1. Navigate to **Pipeline (1)** from the left navigation pane and then Select **Pipeline drafts (2)** tab and then click on **Preprocessing_Pipeline (3)**.

    ![](../images/n57c44.png)

1. Click the **Clone** button at the top. This will create a copy of the pipeline and open it in a new tab.

    ![](../images/n57c45.png)

1. Select the **Pencil (1)** icon to rename the Pipeline.    

     - Rename your cloned pipeline to **Clemson – Unsupervised Pipeline** and then **Save (2)**. 

       ![](../images/n57c46.png)

1. Navigate to the **Data (1)** tab on the left, drag your **Clemson dataset** onto the pipeline canvas **(2)** and connect it to the existing **preprocessing pipeline (3)**.

    ![](../images/n57c47.png)

1. Double click on the **Clean Missing Data (1)** component. Select **Edit Column** under “Columns to be cleaned”.
    
    ![](../images/n57c48.png)

1. Select **Column names (1)** and then type or select all these columns `Overall Wins, Overall Losses, Overall Ties, Overall Win-Loss Percentage, Conference Wins, Conference Losses, Conference Win-Loss Percentage, Simple Rating System, Strength of Schedule, AP Pre Rank, AP Highest Rank, CFP Highest Rank,CFP Final Rank` **(2)** and then **Save (3)**.

    ![](../images/n57c49.png)

1. Set the **Cleaning mode** to **Replace with mean (1)** and then **Save (2)**.    

    ![](../images/n57c50.png)

1. These are the components that are replaced in the Unsupervised pipeline compared to the Supervised pipeline:

     - Swap out “Two-Classification Regression” with **“K-Means Clustering”** for the model type.
     - Swap out “Train Model” with **“Train Clustering Model”** and connect it to your dataset and clustering model.
     - Swap out “Score Model” with **“Assign Data to Clusters”** and remove **“Evaluate Model.”** This will label each row in the dataset with a cluster ID

1. Switch to the **Component** tab in the left panel and search for **“K-Means Clustering (1).** Drag that component onto the canvas **(2)** beside the `Split Data` component. 

    ![](../images/n57c51.png)

1. Switch to the **Component** tab in the left panel and search for **Train Clustering Model (1).** Drag that component into the canvas **(2)**.

    ![](../images/n57c52.png)

1. Connect:

     - Connect **output** of **K-Means Clustering** to **left input of Train Clustering Model (1)**

     - Connect **left output of **Split Data** to **Right input of Train Clustering Model (2)**

       ![](../images/n57c53.png)

1. Switch to the **Component** tab in the left panel and search for **Assign Data to Clusters (1).** Drag that component into the canvas **(2)**.

     - Connect **left output of Train Clustering Model** to **left input of Assign Data to Clusters (3)**

     - Connect **Right output of Split Data** to **Right input of Assign Data to Clusters (4)**

     - Then **Save (5)**

       ![](../images/n57c54.png)

1. Double-click **“K-Means Clustering” (1)** and set “Number of centroids” to `3` **(2)** and then **Save (3)**.     

    ![](../images/n57c55.png)

     >**Note**: We want to have 3 centroids, so we can group the seasons into “Elite”, “Average”, and “Poor”.

1. Double-click **“Train Clustering Model” (1)**. Select **Edit Column (2)** under `Column Set`.

    ![](../images/n57c56.png)

1. Select **Column names (1)** and enter the following numeric columns you want the model to use:

     - `Overall Wins, Overall Losses, Overall Ties, Overall Win-Loss Percentage, Conference Wins, Conference Losses, Conference Win-Loss Percentage, Simple Rating System, Strength of Schedule, AP Pre Rank, AP Highest Rank, CFP Highest Rank,CFP Final Rank` **(2)**

     - Then **Save (3)**

       ![](../images/n57c57.png)

1. 


