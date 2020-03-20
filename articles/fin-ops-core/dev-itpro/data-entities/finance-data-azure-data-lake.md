---
# required metadata

title: Finance and Operations apps data in Azure Data Lake
description: This topic provides information about how to configure your environment for Dynamics 365 Finance and Operations apps with an Azure Data Lake.
author: MilindaV2
manager: AnnBe
ms.date: 03/20/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: NOINDEX, NOFOLLOW
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations

# ms.tgt_pltfrm: 
ms.custom: 96283
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: milindav
ms.search.validFrom: 2020-03-01
ms.dyn365.ops.version: Platform Update 34

---

# Dynamics 365 Finance data in Azure Data Lake

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

You can configure your environment for Dynamics 365 for Finance and Operations apps with an Azure Data Lake using this feature. Tables and Entities from the Finance and Operations apps will be reflected in your Azure Data lake when configuration is successful.

## NOTES

- **This feature may not be available in all regions and/or all environments**. If you do not see this feature in your environment, it will become available in the future.
- To enable Aggregate measurements in an Azure Data Lake, continue to use the feature as described in the topic, [Make entity store available as a Data Lake](entity-store-data-lake.md).


## Overview

There are several steps to complete to enable this service.

1. Create an Azure Storage (Gen2) account in your subscription.
2. Accept the offer and terms to enable Data lake integration.
3. Enable the **Export to Azure Data Lake** feature
5. Choose tables and Entities to be staged in the Azure Data Lake.
6. Monitor the tables in Azure Data Lake.

##  Create an Azure Storage (Gen2) account in your subscription
This storage account will be used to store data. To create a storage account, you need to be a user with administrative rights to your organization's Azure subscription.
Alternatively, the system can create a storage account on your behalf within your own Azure subscription. 

### Manually create a storage account
You can create a storage account in your own subscription and provide that account to the system by using a Key vault. Next, you need to create an AAD application ID that grants access to the root of your storage account. This application will be used by the system to create folder structure and to write data. You will then create a key vault in your own subscription and provide information about your storage account as well as the application to the LCS offer. 

1. To create a storage account, follow the instructions in the section [Create storage accounts](entity-store-data-lake.md#create-storage-accounts). 
2. Provide the AAD tenant ID of your environment. You can find your AAD tenant ID from the Azure portal. Login to Azure portal, Open Azure Active Directory service. Go to properties page and Copy the Directory ID field.
3. Next, follow the instructions to create a Key vault and a secret in the section [Create a key vault and a secret](entity-store-data-lake.md#create-a-key-vault-and-a-secret). You will need to provide the Key vault DNS and the secret name.

### Let the system create a storage account
As opposed to creating storage accounts on your own, you can ask the system to create a storage account in your subscription on your behalf. This option will be enabled in the future.

## Accept offer and terms to enable Azure Data Lake integration
Before you can configure the Azure Data Lake integration, you need to accept the Azure Data Lake offer in Dynamics Life Cycle Services (LCS). To do this, you need to be an environment administrator for the Finance and Operations apps and you must have access to the LCS portal.

1. Login to lcs.dynamics.com and navigate to the **Environment** page.
2. Expand the **Environment add-ins** tab. If the Data Lake add-in is already installed, you should see **Azure Data Lake** in the list. If not, you need to install the Azure Data Lake add-in.

    ![Verify if the Data lake add-in is installed](./media/LCS-EnvironmentPage-with-Addins.png)

3. To install the add-in, select **+ install a new add-in** from the flyout menu.
4. Find **Azure Data Lake** in the list. If you do not see the option, the feature many not yet be available for your environment.

    ![Azure Data lake option in the list of add-ins](./media/LCS-EnvironmentPage-with-DataLake-Flyover.png)

5. Provide the required information. To answer the questions, you should have already created an Azure Storage account. If you have not, create an Azure storage account, or ask your administrator to create one on your behalf.
    
    ![Details for Azure Data Lake add-in](./media/azure-data-lake-addin.png)

6. Accept the terms of the offer by selecting the check box, and then select **Install**.  The system will install and configure the Azure Data Lake for this environment. When installation and configuration is complete, you will see the Azure Data Lake configured for this environment.

## Enable the Export to Azure Data Lake feature
An administrator must enable the Export to Azure Data Lake feature before it can be activated, similar to all new features in Finance and Operations apps. 

- In the **Feature Management** workspace, navigate to the **Export Data to Azure Data lake** feature, select the feature, and then select **Enable**.

After the feature is enabled, under **System administration**, you should be able to see the option, **Export to Azure Data Lake**.

## Choose data 
You can choose the tables and entities to be staged in Azure Data Lake. 

1. In your environment, go to **System Administration** \> **Export to Azure Data Lake**.
2. Select **Configure Data feeds for export to Lake**. 
3. On the **Tables** tab, select the data tables to be staged in Azure Data Lake. You can search for tables using the display name or the system name. You can also see if the table is already being synced.
4. Select one or more tables, and then select **Add tables**. The tables will be added to Azure Data Lake.

![Choose Tables](./media/Export-Tables-toData-lake-unselected.png)

5. If you are not familiar with the specific tables you need, select the tables using entities instead.
Entities are a higher-level abstraction of data that may include multiple tables. By choosing Entities, you are choosing the tables that comprise the Entity. Regardless of how you choose, the tables will be staged in the Azure Data Lake.

![Choose using Entities](./media/Export-Entities-toData-lake-unselected.png)

## Monitor Tables in Azure Data Lake
The system keeps the data updated in Azure Data Lake. You don't need to monitor data exports or schedule data exports because the system keeps the data fresh. However, you can see the status of ongoing data exports using the **Active** tab on the **Configure data feeds to Data lake** page.

![Monitor tables progress](./media/Export-Tables-toData-lake-monitor.png)

