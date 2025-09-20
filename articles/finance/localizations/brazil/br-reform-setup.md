---
title: Brazil Reformed Tax setup
description: The article outlines the general steps to support Brazilian tax reform within scope of 2026
author: yanansong
ms.author: yanansong
ms.topic: how-to
ms.date: 09/13/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2025-10-01
ms.custom: 
  - bap-template
---

# Brazil Reformed tax setup 

[!include [banner](../../includes/banner.md)]

The article outlines the general steps needed to support the Brazilian tax reform in scope for 2026.

The Reformed Tax solution leverages the Advanced Tax Calculation engine. The following steps explain how to set up the feature and perform the necessary configuration.

The following diagrams presents the feature setup and enablment process.
<img width="1065" height="145" alt="image" src="https://github.com/user-attachments/assets/df125501-4368-4907-b9ee-b564bd68ddc6" />





## Enable feature in Feature Management
During both the public preview and general availability phases, the feature will be visible but disabled by default. Therefore, to utilize the Brazil reform feature offered by Microsoft, it must be enabled through the **Feature management** workspace. 

The steps for enabling the feature are as follows.

1. Go to **Workspace->Feature management**

2. Search feature name **Meet requirements of Tax reform in Brazil in 2026**.

3. Click **Enable** button to activite the feature.

**Note**: If the feature is not showing in the list, please click the **Check for updates** button in **Feature management**. 

## Create and activate configuration provider 
Please follow the instructions: [Create configuration providers and mark them as active - Finance & Operations | Dynamics 365 | Microsoft Learn](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/tasks/er-configuration-provider-mark-it-active-2016-11?context=%2Fdynamics365%2Fcontext%2Ffinance)

## Download the configuration-related files
The configuration-related files for tax calculation and e-invocing have been updated in two different locations. Based on your environment, select the appropriate option below to download.
- Dataverse

- LCS/Appsource

The configuration-related files for Tax Calculation
- Tax Data Model 
- Tax Calculation Data Model 
- FNO Model Mapping 
- Tax Calculation Configuration  
- Tax Calculation Data Model (Brazil) 
- FNO Model Mapping (Brazil) 
- Tax Calculation Configuration (Brazil)  

The configuration-related files for e-invoicing
- Fiscal documents
- Fiscal documents mapping
- NF-e submit export format

## Import the Configuration-related files for tax calculation and e-invoicing

### For tax calculation
The steps for importing tax calculation configuration files are as follows.

1. Go to **Workspaces->Electronic reporting**
2. Click **Tax configurations** tile
3. On the **Configurations** page, click **Exchange** button on top
4. Select **Load from XML file** option
5. Select a file by Clicking **Browse** button
6. Upload all the files in sequence, then go to step7.
7. Go bcak to **Configurations** page, select **FNO Model Mapping** under **Tax Calculation Data Model**, switch **Default for model mapping** to **YES**.
8. Go bcak to **Configurations** page, select **FNO Model Mapping(Brazil)** under **FNO Model Mapping**, switch **Default for model mapping** to **YES**.
 
> [!Note]
> The configuration-related files for tax calculation are required to be uploaded in the following sequence.
> 1. Tax Data Model 
> 2. Tax Calculation Data Model 
> 3. FNO Model Mapping 
> 4. Tax Calculation Configuration  
> 5. Tax Calculation Data Model (Brazil) 
> 6. FNO Model Mapping (Brazil) 
> 7. Tax Calculation Configuration (Brazil)  

> [!Note]
> If you encounter issue with importing the file **Tax Calculation Configuration (Brazil)**,you need to perform below operation to sync the tax measure type. 
> 1. Go to **Workspaces->Electronic reporting**
> 2. Click **Tax configurations** tile
> 3. On the **Configurations** page, click **Configurations** button on top
> 4. Under **Advanced settings** group, Select **Tax measure types**
> 5. Click **Synchronize** button on top
> 6. Go to the previous steps to continue.
    


### For e-invoicing
The steps for importing e-invoicing configuration files are as follows.

1. Go to **Workspaces->Electronic reporting**
2. Click **Reporting configurations** tile
3. On the **Configurations** page, click **Exchange** button on top.
4. Select **Load from XML file** option
5. Select a file by Clicking **Browse** button
6. Upload all the configuration files in sequence, then go to Step7
7. Go to **Organization administration -> Setup -> Brazilian parameters**
8. Click **Electronic reporting** tab
9. Select **NF-e** in **Type** filed and **Fiscal documents mapping** in the **Model Mapping** filed
10.Go to **Organization administration -> Organizations -> Fiscal establishments -> Fiscal document types**
11.Select **NF-e submit export format** in the **Export format mapping** field 

> [!Note]
> The configuration-related files for e-invoicing are required to be uploaded in the following sequence.
> 1. Fiscal documents
> 2. Fiscal documents mapping
> 3. NF-e submit export format

## Create Tax Calculation Feature 

The steps for generally creating tax calculation feature are as follows.

1. Go to **Workspace -> Globalization Studio**
2. Select **Tax calculation**
3. On the **Tax calculation feature** form, click **Add** button
4. Select **New feature** , input **Name** and **Description**, then select **Default** under **Type**
5. Click **Create feature**
6. After the creation, then go to the right-hand of the page, under **Versions** tab, click **Edit** option to configure the selected feature.
   **Note** If you can't find **Edit**, then try to click **the three dots** depending on screen resolution.
7. Select the **Tax Calculation Configuration (Brazil)** with the version corresponding to your F&O version. Please find the mapping in the article Overview.
8. To enable lookups for the fields, turn on the **Enable lookups in applicability rules** option, and then select the **Source Legal Entity** (for example, BRMF)

