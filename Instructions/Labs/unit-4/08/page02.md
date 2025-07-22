# Hands-On-Lab: Spot the Flaw - Detecting Defective Products with Image Classification

In this hands-on lab, you will explore how artificial intelligence can support quality control in manufacturing by detecting defective parts. You will work with real product images, train a machine learning model using Azure Custom Vision, and evaluate its accuracy and performance. Through guided activities, you will also reflect on when to trust a model’s predictions and how combining multiple data sources can enhance reliability and safety in automated systems.


### Task 1: Create a Custom Vision resource

1. On the **Azure portal**, search for **Azure AI Services (1)** and selct **Azure AI Foundry (2)**.

     ![](../images/n48c1.png) 

1. Expand **More Services (1)**, select **Custom vision (2)** and then click on **+ Create (3)**.

     ![](../images/n48c2.png) 

1. On the **Create Custom Vision** page, provide the following details and then **Review+Create (7)**.

    - Subscription: Leave the deafult one **(1)**
    - Resource group: Select **ODL-SREB-U4L08 (2)**
    - Region: **<inject key="Region" enableCopy="false"/>** **East US (3)**
    - Name: Enter **customvision-casting (4)**
    - Training pricing tier: Select **Free F0** (2 Transactions per second, 2 Projects) **(5)**
    - Prediction pricing tier: Select **Free F0 (6)** 

      ![](../images/n48c3.png)

1. Click on **Create**.

     ![](../images/n48c4.png) 

1. Wait for the deployment to complete.

     ![](../images/n48c5.png) 


### Task 2: Creating a New Project in Custom Vision

1. Login to **Custom Vision portal** by copy and paste the following link [Custom Vision portal](https://customvision.ai/) in the new tab of the LabVM browser.

1. Click on **Sign in**.

     ![](../images/n48c6.png) 

1. If prompted, login with the below credentials:

    - **Email/Username:** <inject key="AzureAdUserEmail"></inject>

    - **Password:** <inject key="AzureAdUserPassword"></inject>

1. Select the Terms of Service checkbox **(1)**  and then click on **I Agree (2)**.

     ![](../images/n48c7.png) 

1. Click on **NEW PROJECT**.

     ![](../images/n48c8.png) 

1. On the **Create New Project** page, provide the following details:

    - Name: Enter **Casting Defect Detection (1)**
    - Description: **Classifying casting images as ok or defective (2)**
    - Resource: **customvisioncasting<inject key="DeploymentID" enableCopy="false"/> [F0] (3)**
    - Project Types: Ensure **Classification** is selected (not Object Detection), as 
you're identifying overall labels for entire images **(4)**
    - Classification Types: Choose **Multiclass** (Single tag per image) because each image belongs to only one category: either Defect or Non-Defective **(5)**

   - Domains: Choose **General (compact) (6)**
    - Export Capabilities: Leave **Basic platforms (Tensorflow, CoreML, ONNX, 
…)** selected **(7)**

    - Then select **CREATE PROJECT (8)**

      ![](../images/n48c9.png) 

### Task 3: Upload and Tag Images

Once your project has been created, you'll land on the Training Images tab of your Custom Vision workspace. This is where you'll upload and tag the images your model will learn from. The main panel is empty because no images have been uploaded yet, which is where we’ll start off at in this part!

#### Task 1.1: Adding Training Images for Non-Defective Parts

1. Click on the **Add Images** button.

     ![](../images/n48c10.png) 

1. Navigate to the respective folder,  search for the dataset folder named **ok_front**. Click on one image and press **Ctrl+A** to select all the images **(1)** and then **Open (2)**.   

     ![](../images/n48c11.png)

1. On the **Image Upload** screen, enter **Non Defective (1)** as **My Tags** and then select **Upload 519 files (2)**.

     ![](../images/n48c12.png)

1. Once uploaded, select **Done**.

     ![](../images/n48c13.png)

1. Briefly wait for the images to be uploaded. Once it’s complete, you’ll see a screen like the one below. Navigate to **Tagged (1)** there you can see the **Non Defective (2)** tag.

     ![](../images/n48c14.png)

#### Task 1.2: Adding Training Images for Defective Parts

Now that all the Non Defective images have been uploaded and tagged, it's time to upload the Defect class images.

1. Click on the **Add Images** button.

     ![](../images/n48c15.png)

1. Search for the **def_front** folder and select all the images within this folder **(1)** and Click **Open (2)** to upload these images.     

     ![](../images/n48c16.png)

1. On the **Image Upload** screen, enter **“Defect (1)** as **My Tags** and then select **Upload files (2)**.

     ![](../images/n48c17.png)  

1. Once uploaded, select **Done**.

     ![](../images/n48c18.png) 

1. Under **Tagged (1)**, now you can see both `Defect` and `Non Defective` tagged images **(2)**.

     ![](../images/n48c19.png) 

### Task 4: Training the Model

Now that we’ve uploaded both sets of images, we're ready to train the image classification model.

1. To get started, click the green **Train** button at the top of screen.

     ![](../images/n48c20.png)

1. On the Choose Training Type page, select **Quick Training (1)** and then **Train (2)**.

     ![](../images/n48c21.png)

1. You will be redirected to the **Performance (1)** tab, where we see the training in action.

     ![](../images/n48c22.png)

     - `Iteration [Number]`: This indicates the current training run
     - `Probability Threshold`: A slider where we can set the cutoff confidence level the model uses when classifying images. It’s set at 50%, which means the model must be at least 50% confident in its classification. 

1. Once your training finishes, you’ll automatically see the Performance tab update.

     ![](../images/n48c23.png)

     We can understand the overall model scores as follows:

    - Precision: Out of all the times the model predicted a specific class (Defect or NonDefective), how many were actually correct?
    - Recall: Out of all actual images of a specific class, how many did the model 
correctly identify?
    - AP (Average Precision): A comprehensive score that combines both precision and 
recall over different thresholds.
    - False Negative: When the model predicts “non-defective” but the item is defective.

Performance Per Tag shows separate precision and recall values for the Defect and NonDefective tags respectively.

The high numbers seen in the figure above suggest that the model is performing very well on the training dataset!  

### Task 5: Test the Model with New Images


#### Task 5.1 Testing the Model with New Defective Images

1. Click on the **Quick Test** button located in the top right corner of the screen.

     ![](../images/n48c24.png)

1. In the Quick Test Panel that opens, click on **Browse Local Files (1)**. Within the file explorer that opens, search for the **def_front** folder under the test
folder. Select any **one image** to perform a quick test **(3)** and then **Open (4)**.

     ![](../images/n48c25.png)

1. Once uploaded, you’ll see prediction results as shown in the figure below. The 
percentages next to the tags **Defect and Non Defective** let us know the model’s selection 
between the two. With a `99.9%` confidence rating, this tells us that the model is highly confident that the image is a `Defective` part.    

     ![](../images/n48c26.png)


#### Task 5.2: Testing the Model with New Non-Defective Images

Now you’ll take the same steps over to test the model’s capabilities with new images. 
However, instead of picking from the def_front folder, you’ll pick one image from the ok_front folder under test.

1. In the Quick Test Panel that opens, click on **Browse Local Files (1)**. Within the file explorer that opens, search for the **ok_front (2)** folder under the test
folder. Select any **one image** to perform a quick test **(3)** and then **Open (4)**.

     ![](../images/n48c27.png) 

### Task 6: Exporting Capabilities

1. Once everything is done with testing the model with new images, let’s take a look at the export functionality. To do so, we’ll click on the **Export** button seen below.

     ![](../images/n48c30.png) 

1. A list of available platforms will be shown. **You do not need to proceed with using these options**, we’re simply just exploring!

     ![](../images/n48c31.png)
     



     




















