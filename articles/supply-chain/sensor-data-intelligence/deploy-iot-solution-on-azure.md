---
title: Deploy an IoT solution on Azure
description: Sensor Data Intelligence uses data from sensors that are connected to Azure. This article describes how to deploy an IoT solution to your own Azure subscription. 
author: johanhoffmann
ms.date: 09/02/2022
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: johanho
ms.search.validFrom: 2022-09-02
ms.dyn365.ops.version: 10.0.30
---

# Deploy an IoT solution on Azure

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

Sensor Data Intelligence uses data from sensors that are connected to Azure. In the deployment step, you will deploy an IoT solution to your own Azure subscription. The following architectural diagram provides an overview of the solution and its components.

![Sensor Data Intelligence architectural diagram](media/sdi-architecture.png "Sensor Data Intelligence architectural diagram")

Follow these steps to deploy the required resources on Azure:

1. Sign in to Supply Chain Management as an admin.
1. Go to **Production control \> Setup \> Sensor Data Intelligence \> Deploy and connect Azure resources** to open the deployment wizard. (The path is going to change to **System administration \> Setup \> Sensor Data Intelligence \> Deploy and connect Azure resources** in the 10.0.29 release).
1. Read the information on the **Welcome** page and select **Next**.
1. Read the information on the **Deploy the sample IoT solution to Azure** page and then, in the **Instructions** section, select **Deploy**.
1. You are now forwarded to Azure Portal for deploying the Azure resources, which opens in a new browser tab. If asked, sign in using your credentials for your Azure subscription.
1. The **Custom deployment** page opens. Select your subscription in the **Subscription** field.
1. Under the **Resource group** field, select **Create new** to create a new resource group for the Azure components you are going to deploy.
1. A drop-down dialog opens. Enter a **Name** (for example, *IoT-demo*) and then select**OK**.
1. Make the following settings:
    - **Resource group** – Select the resource group that you just created.
    - **Region** – Select a region, ideally the region where your Supply Chain Management environment is deployed. Keep in mind that Azure regions have different pricing. You can see estimated costs for your region by using the [Sensor Data Intelligence price calculator](https://azure.com/e/c36c4947ebff4215b2e62590c2a24c68).
    - **Supply Chain Management environment** **URL** – Enter the URL for your Supply Chain Management environment.
    - **Reuse existing Azure IoT Hub** – Leave unchecked.

1. Select **Next: Review + Create**.
1. The **Custom deployment** page opens. Verify that the validation has passed and then select **Create**.
1. The **Deployment is in progress** page opens, which tracks the progress of your deployment. The deployment process can take up to 30 minutes to complete.
1. When the **Deployment is in progress** page indicates that the deployment is complete, select the link for the **Resource group** name to open a page that shows resources deployed in the group.
1. In the list of resources, find the record with **Type** *Manage Identity* and select its name in the**Name** column to open the details page for that resource.
1. On the details page for the resource, copy the identification number in the field **Client ID** (for example, by selecting the **Copy to clipboard** button).
1. Go back to the browser tab where Supply Chain Management is running with the **Deploy the sample IoT solution to Azure** page still open. Be sure to keep the Azure tab open.
1. Select **Next** to open the **Connect Azure resources** page.
1. In the field **Azure AD Application client ID,** paste the **Client ID** value that you copied.
1. Go back to the browser tab where Azure is open, showing the resource details you were looking at previously (but keep your Supply Chain Management tab open). Then select the **Back** button in your browser to return to the list of resources in your new resource group.
1. In the list of resources, find the record with **Type** *Azure Cache for Redis* and select its name in the**Name** column to open the details page for that resource.
1. On the left navigation pane, select **Access keys** to open the **Access keys** page.
1. Copy the value shown for **Primary connection string (StackExchange.Redis)** (for example, by selecting the **Copy to clipboard** button).
1. Go back to the browser tab where Supply Chain Management is running with the **Connect Azure resources** page still open.
1. Paste the **Primary connection string (StackExchange.Redis)** value that you copied into the **Redis metric store connection string** field.
1. Select **Finish**.

Azure resources for Sensor Data Intelligence are now deployed on your Azure subscription.
