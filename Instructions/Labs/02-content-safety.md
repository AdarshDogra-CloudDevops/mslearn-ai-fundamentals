# Lab 02: Explore Azure AI Services

## Lab overview

In this lab, you will create an Azure AI multi-service resource, retrieve its keys and endpoint, and explore its capabilities using the Azure AI Foundry portal. You'll get hands-on experience with services like Face detection, without needing any coding skills.

## Lab Objectives

In this lab, you will perform:

- Task 1: Create an Azure AI services resource in the Azure portal
- Task 2: Check out the keys and endpoint
- Task 3: See Azure AI services in action

### Task 1: Create an Azure AI services resource

In this task, you will learn how to create an **Azure AI Services** resource to access various AI capabilities for your applications.

You can use Azure AI Face service with an **Azure AI services** multi-service resource. If you haven't already done so, create an **Azure AI services** resource in your Azure subscription.

1. In the Azure portal, Click the **＋Create a resource** button.

    ![The image and its captions are displayed.](./media/ai9873.png)

1. Search for **Azure AI services (1)** and select **Azure AI services (2)**.

    ![The image and its captions are displayed.](./media/ai2l1.png)

1. Select **Azure AI services**.

    ![](./media/ai2l2.png)

1. Select **Create**.

    ![The image and its captions are displayed.](./media/ai2l3.png)

1. Configure  the AI Service with the following settings:
   
    - **Subscription (1)**: Use the existing Azure subscription.
    - **Resource group (2)**: **AI-900-Module-02**
    - **Region (3)**: Select **<inject key="location" enableCopy="false"/>**
    - **Name (4)**: Enter **contentsafety<inject key="DeploymentID" enableCopy="false"/>**
    - **Pricing tier (5)**:Select **Standard S0**.
    - **By checking this box, I acknowledge that I have read and understood all the terms below (6)**: *Selected*. 

      ![The image and its captions are displayed.](./media/ai2l4.png)
      ![The image and its captions are displayed.](./media/ai2l5.png)      

1. On the Review + create tab, select **Create** and wait for deployment to complete.

>***Congrats! You've just created or provisioned an Azure AI services resource. The one you provisioned in particular is a multi-service resource.***

1. Once the deployment is complete, select *Go to resource*. 

    ![](./media/ai2l6.png)

1. Select **contentsafety<inject key="DeploymentID" enableCopy="false"/>**.

    ![](./media/ai2l7.png)

### Task 2: Check out the keys and endpoint

In order to incorporate Azure AI services into applications, developers need a service key and endpoint. The keys and endpoint used for application development can be found in the Azure Portal. 

1. In the Azure Portal, select your resource. On the left-hand menu, look under **Resource Management (1)** for *Keys and Endpoints*. Select **Keys (2) and Endpoints (3)** to view the endpoint and keys for your resource. 

    ![](./media/ai2l8.png)

### Task 3: See Azure AI services in action

Let's start by creating an Azure AI Foundry project.

1. In a web browser, open the [Azure AI Foundry portal](https://ai.azure.com) at `https://ai.azure.com`.

1. If prompted, provide the credentials below:

   - **Email/Username:** <inject key="AzureAdUserEmail"></inject>

   - **Password:** <inject key="AzureAdUserPassword"></inject>
 
1. In a new browser window, navigate to the [Azure AI services exploration page](https://ai.azure.com/explore/aiservices).

1. On the *AI Services* page, select the **Vision + Document** tile to try out Azure AI Vision and Document capabilities.

    ![](./media/ai2lai2l9.png)

1. Under *View all Vision capabilities* select the **Face (1)** tab. Select the **Detect faces in an image (2)** demo tile.

    ![](./media/ai2l10.png)

1. Try out the Face service, which is one of many Azure AI services. Click on an image.

    ![](./media/ai2l11.png)

1. Check out the detected attributes. 

    ![](./media/ai2l12.png)

1. Scroll down to the **Run the code** section. Select **View Code (1)**. Scroll down to the section that starts with *import os*. In the sample code provided, you'll see placeholders where you could put a key and endpoint **(2)**.

    ![](./media/ai2l14.png)

1. If you were to build an application that used Azure AI services, you could start with the provided code. By replacing the placeholders with your own service's key and endpoint, your application would be able to send requests and receive responses that utilize Azure AI services. In the case of the Face service, the *request* is for the Face service to analyze the image. The *response* is the detected attributes. 

    >**Note**
    >You do     
  
### Task 3: See Azure AI services in action

In this task, you will explore and interact with Azure AI services through demos in the Azure AI Foundry portal.

1. In a browser tab, navigate to [Azure AI Foundry](https://ai.azure.com?azure-portal=true).

1. Sign in with your account.

1. Close any tips or quick start panes that are opened the first time you sign in, and if necessary, use the Azure AI Foundry logo at the top left to navigate to the home page, which looks similar to the following image (close the Help pane if it's open).

1. In a new browser window, open the [Azure AI services exploration page](https://ai.azure.com/explore/aiservices).

1. Under *AI Services*, select the **View AI Services** tile.
 
    ![Screenshot of the left-hand menu on the project screen with AI Services selected.](./media/view-ai-foundry-outside-project.png)  

1. On the **AI Services** page, select the **Vision + Document** tile to try out Azure AI Vision and Document capabilities.

    ![Screenshot of the Vision and Document tile selected on the AI Services page.](./media/upd-3.2.png)

1. Under *View all Vision capabilities* select the **Face** tab. 

1. Select the **Detect faces in an image** tile. 

   ![](./media/face.png)

1. Try out the Face service, which is one of many Azure AI services. Click on an image and check out the detected attributes. 

    ![Screenshot of the detect faces demo in Azure AI Foundry portal.](./media/detect-faces-demo.png)

1. Scroll down to the **Run the code** section. Select **View Code**. 

    ![Screenshot of the view code screen with a view of the code placeholders for key and endpoint.](./media/view-code-example.png) 

1. Scroll down to the section that starts with *import os*. In the sample code provided, you'll see placeholders where you could put a key and endpoint.

   ![Screenshot of the view code screen with a view of the code placeholders for key and endpoint.](./media/view-code-example1.png)

1. If you were to build an application that used Azure AI services, you could start with the provided code. By replacing the placeholders with your own service's key and endpoint, your application would be able to send requests and receive responses that utilize Azure AI services. In the case of the Face service, the *request* is for the Face service to analyze the image. The *response* is the detected attributes. 

    >**Note**
    >You do not need to know programming to complete any of the exercises in this course. We will continue to take a look at Azure AI services in action through the Azure AI Foundry portal.  

## Validation

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
 
- Hit the Validate button for the corresponding task. You will receive a success message. 
- If not, carefully read the error message and retry the step, following the instructions in the lab guide.
- If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.

  <validation step="5371378e-8511-44ed-9037-3a000338132f" />

## Learn more

This simple search index only some of the capabilities of the Content Safety Studio. To learn more about what you can do with this service, see the [ Explore the Content Safety Studio ](https://learn.microsoft.com/en-us/azure/ai-services/content-safety/overview).

### Review
In this lab, you have completed the following tasks:
- Explored Content Safety Studio
- Associated a resource with the safety studio
- Tried out text moderation in the Content Safety Studio
- Checked out the keys and endpoint

## You have successfully completed this lab.
