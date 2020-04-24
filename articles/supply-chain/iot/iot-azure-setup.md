---
# required metadata

title: Azure setup for IoT Intelligence core insights
description: This topic describes how to create and configure the Azure resources you need for IoT Intelligence core insights.
author: robinarh
manager: AnnBe
ms.date: 08/16/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: 
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: 
ms.search.validFrom: 2020-04-04
ms.dyn365.ops.version: 10.0.5

---

# Azure setup for IoT Intelligence core insights

[!include [banner](../../includes/banner.md)]

This topic describes how to create and configure the Azure resources you need for IoT Intelligence core insights.

## Create Azure resources

Follow these steps to create an IoT Hub, a Redis cache, and a key vault that is accessible by Microsoft Dynamics 365 Supply Chain Management:

1. Verify that **Microsoft Dynamics ERP Microservices** first-party app Id is inside your tenant.
    1. Sign in to the Azure portal at https://portal.azure.com.
    1. Navigate to **Azure Active Directory**.
    2. Navigate to **Enterprise applications**.
    3. In the **Application type** dropdown, select **Microsoft applications**.
    4. In the search box, search for **Microsoft Dynamics ERP Microservices**.
    5. Verify that **Microsoft Dynamics ERP Microservices** is in the list. There are other applications with similar names, make sure you find the right one. The application Id is **0cdb527f-a8d1-4bf8-9436-b352c68682b2**.
    6. If the application is not in the list, you must add it to your tenant. To add it, follow these steps:
        1. In the Azure portal, click the tool bar icon to open the Cloud Shell.
        3. Run the command `Install-Module AzureAD`. Enter `Y` to install the module.
        4. To verify that the module is installed, run the command `Get-InstalledModule -Name "AzureAD"`.
        5. Run the command `Connect-AzureAD -Confirm` to run the authentication.
        6. Run the command `New-AzureADServicePrincipal -AppId 0cdb527f-a8d1-4bf8-9436-b352c68682b2`.
        7. Now you can rerun steps 1 through 5 to verify that the app Id is inside your tenant.

2. Create a key vault resource.
    1. In the Azure portal, create or navigate to a resource group.
    2. Click **Add**.
    3. On the **New** page, in the search box, enter **Key vault**. Click **Create**.
    4. On the **Create key vault page**, enter a name in the **Key vault name** textbox.
    5. Leave the rest of default values, and click **Review + create**.
    6. Click **Create**. The key vault is created in the background.

3. Create an IoT Hub resource.  We recommendation that you create only one IoT Hub resource per environment.
    1. Create or navigate to a resource group.
    2. Click **Add**.
    3. On the **New** page, in the search box, enter **Iot Hub**. Click **Create**.
    4. Enter a name in the **IoT hub name** textbox.
    5. Leave the rest of the default values, and click **Review + create**.
    6. Click **Create**. The IoT hub is created in the background.

4. Create a Redis cache resource. We recommendation that you create only one Redis cache per environment.
    1. Create or navigate to a resource group.
    2. Click **Add**.
    3. On the **New** page, in the search box, enter **Azure Cache for Redis**. Click **Create**.
    4. Enter a name in the **DNS name** textbox.
    5. Leave the rest of the default values, and click **Create**. The Redis cache is created in the background.

The resources are all created now.

## Configure the Azure resources

To configure the key vault, Redis cache, and Iot hub, follow these steps:

1. Configure the IoT hub.
    1. In your resources, click on the IoT hub resource.

2. Configure the key vault to give the **Microsoft Dynamics ERP Microservices** first-part app Id access to the key vault.
    1. In your resources, click on the key vault resource.
    2. In the left navigation, click **Access policies**.
    3. Click **Add an access policy**.
    4. On the **Add access policy** page, select **Get** and **List** from the **Secret permissions** dropdown.
    5. Click in the **Select principal** dropdown. In the **Principal** dialog, search for and select **Microsoft Dynamics ERP Microservices**. Click the **Select** button.
    6. Click **Add**.
    7. Click **Save**. Now the app has access to the secrets in the key vault.

3. Configure the secrets.
    1. In the left navigation, click **Secrets**.
    2. Click on the IoT hub resource.
    3. In the left navigation, click **Built-in endpoints**.
    4. Under **Consumer groups**, paste in the consumer groups. These correspond to the out-of-box scenarios.
        + **microsoft.dynamics.iotintelligence-1**
        + **microsoft.dynamics.iotintelligence-2**
        + **microsoft.dynamics.iotintelligence-3**
    5. Copy the value from the **Event Hub-compatible endpoint** textbox.
    6. Navigate back to the resource group.
    7. Click on the key vault resource.
    8. In the left navigation, click on **Secrets**.
    9. Click on **Generate/Import**.
    10. Enter a name in the **Name** text box.
    11. Paste the endpoint into the **Value** textbox.
    12. Click **Create**.
    13. Navigate back to the resource group, and wait for the Redis cache to be provisioned. You can click the **Refresh** button to refresh the status.

    > [!NOTE]
    > Whenever you update one of the connection strings, you must also update the secret values.

4. Configure the Redis cache.
    1. Click on the Redis cache resource.
    2. Click **Access keys**.
    3. Copy the value from the **Primary connection string** textbox.
    4. Navigate back to the resource group.
    5. Click on the key vault resource.
    6. In the left navigation, click on **Secrets**.
    7. Click on **Generate/Import**.
    8. Enter a name in the **Name** text box.
    9. Paste the connection string into the **Value** textbox.
    10. Click **Create**.

You are now done provisioning Azure. The next step is to [setup LCS](iot-lcs-setup.md).
