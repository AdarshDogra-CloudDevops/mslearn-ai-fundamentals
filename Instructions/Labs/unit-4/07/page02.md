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

### Task 3: Preprocessing Our Data

In this task you will prepare your dataset for modeling by cleaning missing values. You will add and configure the Clean Missing Data component to handle incomplete or missing sensor readings, ensuring the dataset is reliable for training your anomaly detection model.

1. Switch to the **Component** tab and search for **Clean Missing Data** by Microsoft.  
    
   ![](../images/lab01-image20.png) 

1. Click on the **Clean Missing Data** data component, then drag it from the left panel and drop it below the **Dataset card** in the pipeline canvas on the right.

    ![](../images/lab07-image12.png)
   
1. Now connect the Dataset to the Cleaning Component, hover over the small **circle at the bottom** of the dataset block labeled **Data output**. Click and **drag a line** to the **left circle** of the Clean Missing Data component labeled **Dataset**. **Save** your progress by clicking **Save** at the top right of the canvas.

    ![](../images/lab07-image13.png) 

1. Now you will Configure the Clean Missing Data component. Double-click the **Clean Missing Data** block on the canvas. Then click the blue **Edit column** link next to **Columns to be cleaned**. This will open a pop-up window.  

    ![](../images/lab07-image14.png) 

1. Select only **Days Planned ETA Days and Distance_Miles** - Do **not** include columns like  Actual ETA, Shipment_ID, Delay_Flag, Material  Click **Save** in the pop-up,

    ![](../images/lab07-image15.png) 

1. On the **Clean Missing Data** window under **Cleaning mode**, make sure to select **Replace with mean**. Click **Save** again on the main screen.  

    ![](../images/lab07-image17.png) 

1. In the **Component tab**, search for **Split Data**, Confirm that it says: "Partitions the rows of a dataset into two distinct sets.... Drag the component into your canvas, placing it below the Clean Missing Data block.

   ![](../images/lab07-image19.png) 
    
1. Hover over the Cleaned data output port at the bottom of the Clean Missing Data component. Click and drag a line from this port to the input port of the Split Data block
    (This tells Azure to split the cleaned dataset).

    ![](../images/lab07-image20.png)

### Task 4: Configure the Split Data Component

1. Double-click the Split Data block on your canvas. The settings panel will appear on the right-hand side specify the below settings

    - Set the Splitting Mode

       • Under Splitting mode, make sure **Split Rows** is selected (This means the data will be divided by rows, not by columns)
    
    - Set the Split Ratio

       • In the field labeled Fraction of rows in the first output dataset, type: **0.7** (This means 70% of your data will be used for training, and the remaining 30% for testing).
    
    - Turn On Randomization

       • Ensure Randomized split is set to: **True** (This ensures a random and fair mix of rows in each set)
    
    - Set a Random Seed

       • In the Random seed field, type: **42** (This ensures that every time you run the pipeline, the data is split the same way. This is useful for consistency across student runs).
    
    - Leave Stratified Split as False

       • Confirm Stratified split is set to: **False** (Stratified splits are more useful in imbalanced datasets like medical diagnosis— not necessary here) Refer to Figure 29 below.

   -  Click **Save** at the top of the page to lock in your configuration

       ![](../images/lab07-image21.png)

1. Why This Step Matters - Splitting data ensures the model is tested on unseen examples, just like a final exam tests what you've really learned—not just what you memorized. A 70/30 split is a common practice in machine learning to keep both the training and testing sets balanced and informative.

   - Add the Two-Class Decision Forest Model

      **Goal:** You will add the Two-Class Decision Forest component to your pipeline. This model will be trained to predict whether a shipment will be delayed or on time based on historical shipping data.

1. In the Component tab, search for **Two-Class Decision Forest**. Drag the component into your canvas, placing it below the **Split Data** component. Find the result titled: Two-Class Decision Forest Description: **“Creates a two-class classification model using the decision forest algorithm…”**

     ![](../images/lab07-image22.png)

1. Click the **Save** button in the top right corner of the interface

     ![](../images/lab07-image23.png)

1. Why This Step Matters - This is the model that will learn patterns in your data. It builds multiple decision trees and combines them into one strong prediction tool. It's especially effective for your logistics dataset because it can handle both numerical and categorical features like ETA, distance, and material type.

   - Add and Connect the Train Model Component

     **Goal:** You will connect the Two-Class Decision Forest model and the training dataset to the Train Model component. This enables Azure ML Designer to train your model on       historical shipment data.

1. In the Component tab, search for **Train Model**. Drag the component into your canvas, placing it below the **Two-Class Decision Forest** component. Find the result titled: **“Trains a classification or regression model in a supervised manner…”**

     ![](../images/lab07-image24.png)
   
1. Before proceeding with the next step, please drag the Two-Class Decision Forest component toward the left to align it properly

1. Connect the Model and the Data

    • From the Two-Class Decision Forest, drag a line from the output port to the left input of the Train Model component (This provides the model to be trained)
    • From the Split Data component, drag a line from the left output port (Results dataset 1 / 70%) to the right input of the Train Model block (This provides the training dataset)

      ![](../images/lab07-image25.png)

1. Confirm the Train Model Block
    • The block should now display:

          Left input = Untrained model
          Right input = Dataset
          Output = Trained model

    • This confirms it’s correctly wired to perform training. 

1. Save your pipeline by clicking the **Save** button at the top right of your screen.

1. Why This Step Matters- Training is where the machine learning actually happens. The model uses the training dataset to recognize patterns (like how distance and material relate to delay). After this, the model will be ready to make predictions on unseen data.

1. Set the Label Column in Train Model **Goal:** You will specify that the column Delay_Flag is the label—the value your model is trying to predict. This tells Azure ML which column contains the correct answer during training.

1. Double-click the Train Model block on your canvas. The settings panel will open on the right-hand side. In the settings panel, find the option labeled Label column. Click the blue Edit column link next to it.

    ![](../images/lab07-image26.png)

1. Choose the Correct Label:

    • In the pop-up that appears, scroll through the list of columns
    • Select: Delay_Flag
    • Click **Save** in the pop-up window.

   This is the binary column where 1 = delayed and 0 = on time.

   ![](../images/lab07-image27.png)

    **Why This Step Matters**- Choosing the correct label is like telling your model what question it’s supposed to answer. In this case, you’re asking:
    “Given the shipment details, can you predict if the shipment will be delayed?”.

1. Confirm that **Delay_Flag** now appears as the selected label in the settings panelSave Your Pipeline. Click **Save** at the top right corner of Azure ML Designer.

      ![](../images/lab07-image28.png)

    **Add and Connect the Score Model Component**

     **Goal:** You will use the Score Model component to apply your trained Decision Forest  model to the test dataset (30% of your original data). This generates predicted outcomes   for evaluation.

1. In the Component tab, search for **Score Model**. Drag the component into your canvas, placing it below the **Train Model** component.

    ![](../images/lab07-image29.png)

1. Connect the Components

   • Connect the output of Train Model to the left input port of the Score Model (This is the trained model)

   • From the Split Data component, connect the right output port (30% test data) to the right input port of the Score Model. 

1. Confirm the Setup. The Score Model component should now be connected like this:

    • Left input = Trained model

    • Right input = Test dataset

    • Click **Save** at the top right of the scree

      ![](../images/lab07-image30.png)

1. Why This Step Matters - This step answers: “How would the model perform on new shipments we haven’t seen before?” It produces predictions and probabilities for each test case based on the patterns the model learned during training. Add and Configure the Evaluate Model Component

1. This will let you measure how well your model performed using standard metrics like:
    • Accuracy
    • Precision
    • Recall
    • AUC (Area Under Curve)

1. Add and Connect the Evaluate Model Component 
    **Goal:** Use the Evaluate Model component to analyze how well your trained model performed on the test data.

1. In the Component tab, search for Evaluate Model. Drag the component into your canvas, placing it below the Score Model block.

1. Connect the Component. From the Score Model output, drag a connection to the left input port of the Evaluate Model block.

1. Click **Save** at the top right.
   
   ![](../images/lab07-image31.png)

1. Now that your pipeline is fully built with all the components connected—from data ingestion to anomaly scoring—you’re ready to run it.

1. Click the **Configure & Submit** button in the top-right corner.

    ![](../images/lab07-image32.png)



1. On the **Basics** page, perform the steps as mentioned below:

   - In the Experiment name select **Create new**
   - In **New experiment name** filed provide **`Test_Logistics_Manufacturing`**
   - Click the blue **Next** button at the bottom-right corner of the screen

      ![](../images/lab07-image33.png)

1. On the **Inputs & outputs** page, click on **Next** to skip.

1. On the Runtime Settings page, from the dropdown of the **Select Compute Type** section, click on Compute Cluster. Since no cluster is currently available, we’ll need to create one. Click on **Create Azure ML Compute Cluster**.

1. On the **Select virtual machine** page, specify the following then click on **Next** :
  
    - Location: Confirm that the selected region is the same as your workspace.
    
    - Virtual Machine Tier: Leave as default. 
    
    - Virtual Machine Type: Keep this as **CPU** (sufficient for our anomaly detection task).

    - Virtual Machine Size: Choose **Standard_DS11_v2**.
  
        ![](../images/lab01-image38.png)

1. On the **Configure Settings** page, provide Compute name Compute-cluster-<inject key="DeploymentID" enableCopy="false"/> then click on **Create**

    ![](../images/lab07-image34.png)

1. Back on the **Runtime Settings** page, select the newly created Azure ML compute cluster from the dropdown in the **Select Azure ML compute cluster** field, then click on **Review + Submit**.

     ![](../images/lab07-image35.png)

1. On **Review + Submit** page, click on **Submit**. 

     ![](../images/lab07-image36.png)

1. Once submitted, a success notification appears at the top of the page. Click on **View details** to monitor the pipeline. It may take some time for the pipeline to complete.

      ![](../images/lab07-image37.png)

1. Once the Pipeline is run, you can see the similar result.

     ![](../images/lab07-image38.png)

1. Right-click on the **Evaluate Model** component, hover over **Preview data** to click on **Evaluation results**.

     ![](../images/lab07-image39.png)

1. This will open the evaluation window where you can view:
    • Confusion matrix
    • ROC curve
    • Precision-Recall curve
    • Lift curve
    • Key metrics such as Accuracy, Precision, Recall, F1 score, and AUC
    Model Evaluation Results (Azure ML Designer)

1. This screenshot shows the evaluation results of a machine learning model trained to predict a logistics-related outcome.

      ![](../images/lab07-image41.png)

   >**Note**: Click on **Maximize panel** icon to review result in full screen.

      ![](../images/lab07-image40.png)
      
1. After training a model, it’s important to evaluate how well it performs. The evaluation results include charts and metrics that show how accurately the model made predictions 
on test data. 


1. ROC Curve - The ROC (Receiver Operating Characteristic) curve helps us see how well the model separates positive and negative cases.

    ![](../images/lab07-image42.png)
    
    • The horizontal axis shows the false positive rate (wrongly predicting "yes").
    • The vertical axis shows the true positive rate (correctly predicting "yes").

   A perfect model would have a curve that reaches the top-left corner — which this model does. That means the model never confused a negative example for a positive one.

1. Precision-Recall Curve - This chart explains how well the model identifies positive cases.

   ![](../images/lab07-image43.png)

    • Precision is how many of the model’s positive predictions were correct.
    • Recall is how many of the actual positive cases the model found.

   A curve that reaches the top-right corner means the model found all positives without making any mistakes — which is exactly what we see here.

1. Lift Curve- The lift curve shows whether the model ranks the most important predictions (true positives) higher than others.

    ![](../images/lab07-image44.png)
   
   • A steep curve means the model successfully puts the most important cases at the top.

   In this case, the curve rises sharply, showing that the model ranks positive examples very effectively.

1. Threshold Slider- The threshold is the cutoff point the model uses to decide between predicting "yes" or "no."**For example**, if a prediction score is above 0.5, the model predicts "yes."Here, the model is still performing perfectly at the 0.5 threshold, meaning it’s confident and accurate in its decisions.

    ![](../images/lab07-image45.png)
