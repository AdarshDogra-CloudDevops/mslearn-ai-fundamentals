### Task 1: Create Azure ML Workspace

In this task you will set up an Azure Machine Learning workspace where all your machine learning assets and experiments will be organized and run. You will learn how to create a workspace in the Azure ML Studio, select the appropriate region and resource group, and navigate to the Designer interface to start building your pipeline.


1. **Log in** to [Azure Machine Learning Studio](https://ml.azure.com/) when prompted provide below credentials.

    - **Email/Username:** <inject key="AzureAdUserEmail"></inject>

    - **Password:** <inject key="AzureAdUserPassword"></inject>
   
1. On the **Create a new workspace to get started with Azure ML** fill in the following fields:

   - **Name**: `ClemsonWinPredictor`  
   - **Friendly Name**: *(Optional)*  
      Azure will auto-fill this based on the name.
   - **Hub (Optional)**: Leave this as “None” unless instructed otherwise.
   - **Advanced Settings**:
   - **Subscription**: Select the appropriate Azure subscription from the dropdown. 
   - **Resource Group**: Choose an existing one 
   - **Region**: Select **East US 2** for better performance.
   - After filling out all the required fields, click the **“Create”** button.

        ![](../images/U5lab08-image1.png) 

    >**Note**: If you **did not** see the page like Figure 1, simply click **“Create Workspace”** on your dashboard and fill out the fields as described in Step 2.

1. Now navigate to your newly created workspace. On the **left-hand menu**, click **“Workspaces”**. Locate the workspace you just created `PCA Anomaly Model`.

     ![](../images/U5lab08-image2.png) 
   
1. Click on its name to open it. This will take you inside the workspace where you can build and run machine learning experiments.

    ![](../images/U5lab08-image3.png) 

### Task 2: Add a dataset to your Azure ML pipeline in the Designer:

In this task you will upload the manufacturing sensor data to your Azure ML workspace. You will create a tabular dataset from a local CSV file, configure the data source, and add it to your pipeline canvas for further processing.

1. Once you are inside your workspace PCA Anomaly Model, look at the left hand side menu to find the **Designer** tab under the Authoring section. Click on 
this tab.

    ![](../images/lab01-image5.png) 

   >**Note**:  This will open the Azure Machine Learning Designer interface where you can  begin creating your machine learning pipeline by dragging and dropping 
components.

1. Once the **Designer** page is loaded, make sure that you’re on the Classic prebuilt tab under the “New pipeline” section. From here, click on the box with a plus sign 
that says, **Create a new pipeline using classic prebuilt components**.

    ![](../images/lab01-image6.png) 

1. On the **left panel**, under the **Data (1)** tab, click the **➕ (plus icon) (2)** to upload a dataset.  

    ![](../images/lab01-image7.png) 

1. On **Create a new workspace to get started with Azure ML** page enter the following data then click on **Next**.

   - Name the dataset: **`Clemson_Dataset`**  
  
    ![](../images/U5lab08-image3.png) 

1. On the **Choose a source for your data asset** page, choose **From local files** the click on **Next**. 

    ![](../images/lab01-image9.png) 

1. **File or Folder Selection**  
   - In the file browser, select the file: `US_Manufacturing_Logistics_Dataset`  
   - Wait for the file to appear under “Upload list”  
   - Click **Next**  

    ![](../images/lab07-image6.png)

1. In Next page, Click on **Next** Button **Twice** and then click on **Create** Button

   ![](../images/U5lab08-image9.png) 

1. Under the **Data** tab, locate the uploaded dataset named **Clemson_Dataset**.

   ![](../images/U5lab08-image10.png)

1. Drag **Clemson_Dataset** onto the canvas

    ![](../images/U5lab08-image6.png)

1. Switch to the **Component** tab and search for **Select Columns in Dataset**. Then drag the component into your canvas, placing it below the **Clemson_Dataset**.

    ![](../images/U5lab08-image7.png)

1. Connect the output circle of the dataset module to the input of this module

    ![](../images/U5lab08-image8.png)

1. Double click on the **Select Columns in Dataset** module. In the right panel, click **Edit column** selection.

     ![](../images/U5lab08-image11.png)

1. Choose the following input features then click **Save**
    a. Rk, Year, W, L, T, Conf_W, Conf_L, Conf_T, Conf_Pct, SRS, SOS, AP_Pre, 
    AP_High, AP_Post, CFP_High, CFP_Final

    ![](../images/U5lab08-image12.png)
     
1. Click on **Save**.

    ![](../images/U5lab08-image13.png)

1. Switch to the **Component** tab and search for **Split Data**. Then drag the component into your canvas.

    ![](../images/U5lab08-image14.png)

1. Connect it to the output of **Select Columns in Dataset** to **Split Data**.

     ![](../images/U5lab08-image15.png)

1. Double click on the **Split Data module** and configure the following then click on **Save**.

   a. Fraction of rows in the first output dataset: 0.8 (80% training)

   b. Leave Stratified split as default. 

      ![](../images/U5lab08-image16.png)

1. Switch to the **Component** tab and search for **Linear Regression**. Then drag the component into your canvas.
   
1. Drag the Linear Regression module onto the canvas as shown in the below image.

    ![](../images/U5lab08-image17.png)

1. Search for **Train Model**. Then drag the component into your canvas. Drag the Train Model module onto the canvas as shown in the below image.

    ![](../images/U5lab08-image18.png)

1. Connect:

   - Left input → output of Linear Regression
   - Right input → first output of Split Data

      ![](../images/U5lab08-image19.png)
