# Azure Web Apps & Container Registry

## Web App for Containers

We are going to host our container in an Azure App Service Plan. 

### Deploy resources

1. Navigate to the Azure Portal, and go to the Azure resource group containing your Container Registry. 

1. Click on **Create** and search for **Web App for Containers**.  Click **Create**.

    <img src="imgs/addresource.PNG">

    <img src="imgs/create.PNG">

1. On the next screen, leave the subscription and resource on default (if they aren't selected, choose the subscription and resource group you have been using in this lab). Leave everything else on default, apart from:

    * Name: Choose a unique name for your web app - I suggest using the same name as your resource group to make sure it is unique - e.g. GitHubWorkshop12345678
    * Region: Choose the same region as you used earlier

    <br><img src="imgs/options1.PNG">

1. Click **Docker**

    * Change **Image Source** to **Azure Container Registry** and select your registry from the dropdown.  
    * Select the image **eshop** from the dropdown. 

    <img src="imgs/options2.PNG">

1. Click **Review + create**. Once validated, click **create** and wait for your web app to deploy.

    <img src="imgs/createfinal.PNG">

### Configuration

There is one configuration change we need to make.  

1. Navigate to your newly created web app, and click on **Configuration**.

1. Add a new Application Setting called **ASPNETCORE_ENVIRONMENT** and give it a value of **DEVELOPMENT**. Click **OK** and then **Save**.

    <img src="imgs/config.PNG">

    You can now browse to your website by clicking on **Browse** on the overview page - you should see the front end for our eShop:

    <img src="imgs/browse.PNG">
    <img src="imgs/website.PNG">

So what have we actually got working so far? 

We have a pipeline which takes triggers on changes to the main branch. It builds and tests the .NET Core application to make sure we haven't broken anything. The workflow then builds a Docker image using the Dockerfile we specified, and pushes that image into our private container registry hosted in Azure.

In the next lab, we will:

1. Update the workflow to deploy new container images to the web app
1. Create environments to reflect staging and production, with approvals

[Begin Lab 4!](../lab.4/lab.4.md)
