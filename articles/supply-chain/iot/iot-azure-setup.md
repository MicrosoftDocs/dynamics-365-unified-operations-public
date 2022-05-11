---
# required metadata

title: Set up Azure resources for IoT Intelligence
description: This topic explains how to create and configure the Microsoft Azure resources that you require for IoT Intelligence.
author: johanhoffmann
ms.date: 08/16/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: johanho
ms.search.validFrom: 2020-04-04
ms.dyn365.ops.version: 10.0.5

---

# Set up Azure resources for IoT Intelligence

[!include [banner](../../includes/banner.md)]

This topic explains how to create and configure the Microsoft Azure resources that you require for IoT Intelligence.

## Create Azure resources

Follow these steps to create an IoT hub, a Redis cache, and a key vault that can be accessed by Microsoft Dynamics 365 Supply Chain Management.

### Verify that the Microsoft Dynamics ERP Microservices first-party app ID is in your tenant

To verify that the app ID for the Microsoft Dynamics ERP Microservices first-party app is in your tenant, follow these steps.

1. Sign in to the Azure portal at <https://portal.azure.com>.
2. Go to **Azure Active Directory**.
3. Go to **Enterprise applications**.
4. In the **Application type** field, select **Microsoft applications**.
5. In the search field, enter **Microsoft Dynamics ERP Microservices**.
6. Verify that **Microsoft Dynamics ERP Microservices** is in the list. Other applications have similar names. Therefore, make sure that you find the correct application. The app ID is **0cdb527f-a8d1-4bf8-9436-b352c68682b2**.

    If the application isn't in the list, you must add it to your tenant:

    1. In the Azure portal, on the toolbar, select the button to open Azure Cloud Shell.
    2. Run the command **Install-Module AzureAD**. Enter **Y** to install the module.
    3. Run the command **Get-InstalledModule -Name "AzureAD"** to verify that the module is installed.
    4. Run the command **Connect-AzureAD -Confirm** to run the authentication.
    5. Run the command **New-AzureADServicePrincipal -AppId 0cdb527f-a8d1-4bf8-9436-b352c68682b2**.

    You can now repeat steps 1 through 6 to verify that the app ID is in your tenant.

### Create a key vault resource

To create a key vault resource, follow these steps.

1. In the Azure portal, create or go to a resource group.
2. Select **Add**.
3. On the **New** page, in the search field, enter **Key vault**. Then select **Create**.
4. On the **Create key vault** page, in the **Key vault name** field, enter a name.
5. Review the default values, and then select **Review + create**.
6. Select **Create**.

The key vault is created in the background.

### Create an IoT hub resource

To create an IoT hub resource, follow these steps.

1. Create or go to a resource group.
2. Select **Add**.
3. On the **New** page, in the search field, enter **Iot Hub**. Then select **Create**.
4. In the **IoT hub name** field, enter a name.
5. Review the default values, and then select **Review + create**.
6. Select **Create**.

The IoT hub is created in the background.

> [!NOTE]
> We recommend that you create only one IoT hub resource per environment.

### Create a Redis cache resource

To create a Redis cache resource, follow these steps.

1. Create or go to a resource group.
2. Select **Add**.
3. On the **New** page, in the search field, enter **Azure Cache for Redis**. Then select **Create**.
4. In the **DNS name** field, enter a name.
5. Review the default values, and then select **Create**.

The Redis cache is created in the background.

> [!NOTE]
> We recommend that you create only one Redis cache per environment.

All the resources have now been created.

## Configure the Azure resources

### Configure the IoT hub

To configure the IoT hub, follow these steps.

1. In your resources, select the IoT hub resource.
2. In the left navigation pane, select **Built-in endpoints**.
3. Under **Consumer groups**, paste the following consumer groups. These consumer groups correspond to the out-of-box scenarios.

    + microsoft.dynamics.iotintelligence-1
    + microsoft.dynamics.iotintelligence-2
    + microsoft.dynamics.iotintelligence-3

### Configure the key vault

To configure the key vault, follow these steps.

1. In your resources, select the key vault resource.
2. In the left navigation pane, select **Access policies**.
3. Select **Add an access policy**.
4. On the **Add access policy** page, in the **Secret permissions** field, select **Get** and **List**.
5. Click in the **Select principal**.
6. In the **Principal** dialog box, search for and select **Microsoft Dynamics ERP Microservices**. Then select **Select**.
7. Select **Add**.
8. Select **Save**.

The app now has access to the secrets in the key vault.

### Save the IoT hub connection string secret

To save the secret for the IoT hub connection string, follow these steps.

1. In your resources, select the IoT hub resource.
2. In the left navigation pane, select **Built-in endpoints**.
3. Copy the value in the **Event Hub-compatible endpoint** field.
4. Go to the key vault resource.
5. In the left navigation pane, select **Secrets**.
6. Select **Generate/Import**.
7. In the **Name** field, enter a name.
8. In the **Value** field, paste the endpoint value that you copied earlier.
9. Select **Create**.

### Save the Redis cache connection string secret

To save the secret for the Redis cache connection string, follow these steps.

1. In your resources, select the Redis cache resource.
2. Select **Access keys**.
3. Copy the value in the **Primary connection string** field.
4. Go to the key vault resource.
5. In the left navigation pane, select **Secrets**.
6. Select **Generate/Import**.
7. In the **Name** field, enter a name.
8. In the **Value** field, paste the connection string that you copied earlier.
9. Select **Create**.

> [!NOTE]
> Whenever you update one of the connection strings, you must also update the secret values.

You've now finished provisioning the required Azure resources. The next step is to [install the IoT Intelligence add-in in Microsoft Dynamics Lifecycle Services (LCS)](iot-lcs-setup.md).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
