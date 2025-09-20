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
### Create
1. Go to **Workspace -> Globalization Studio**
2. Select **Tax calculation**
3. On the **Tax calculation feature** form, click **Add** button
4. Select **New feature** , input **Name** and **Description**, then select **Default** under **Type**
5. Click **Create feature**

### Configure
6. After the creation, then go to the right-hand of the page, under **Versions** tab
7. Highlight the version record with status **Draft**, then click **Edit** option to configure the selected feature.
   **Note** If you can't find **Edit**, then try to click **the three dots** depending on screen resolution.
9. Select the **Tax Calculation Configuration (Brazil)** with the version corresponding to your F&O version. Please find the mapping in the article Overview.

## Enable lookups in applicability rules
10. Turn on the **Enable lookups in applicability rules** option
11. Then select the **Source Legal Entity** (for example, BRMF)
12. Click **Select** button.

### Setup Tax codes for new tax types (CBS/IBS)
13. Go to **Tax codes and groups** FastTab, under **Tax codes** tab click **Add** button 
14. Input values in **Tax code** (For example, CBS, IBS-City12 etc)
15. Select **By Net Amount Brazil** in **Calculation origin** field
16. Click **Save** button.
17. Go to the right page **General** fasttab, fill in the values for all related fields ( for example, **Calculaiton Method**, **cClassTrib code** and **Tax type**  etc )
18. Go to **Rate** fasttab, fill in the values for all related fields (for example, **Tax Rate** etc)

> [!Note]
> Tax codes created here in advanced tax engine could be synchronized in Tax->Indirect tax-> Sales tax -> Sales tax codes form.

> **Settlement period** and **Leger posting group** in tax codes haven't been specified. You will be prompted to define them when enabling the feature in Advanced tax calculation engine in the tax parameter.   

### Setup Tax group and assign tax codes
19. Go to **Tax codes and groups** FastTab, on the **Tax group** tab click **Manage columns**
20. Select the relevant columns to define the elements of the tax groups defination .(For example,Transactiondate from header and line etc)
21. Move them using the right arrow and confirm with **OK** 
22. Click **Add** button, then input values in **Lines.Tax group** and other selected fields through **Manage columns**.
23. Highlight the tax group record, and select the values in **Tax codes** to define the relationship between the tax group and the tax codes.

> [!Note]
> Since the new tax reform takes effect in 2026, customers who configure the **Tax group** in advance (for example, in 2025) should add **Header.FromTransitionDate** and **Line.FromTransitionDat**, and set both to **January 1, 2026**, to prevent unexpected errors.

### Setup Item Tax group and assign tax codes
24.  Go to **Tax codes and groups** FastTab, on the **Item Tax group** tab click **Manage columns**
25.  Select the relevant columns to define the elements of the item tax groups defination.(For example,TransactionDate on header and line etc)
26.  Move them using the right arrow and confirm with **OK**. 
27.  Click **Add** button and input values in **Lines.Item Tax group**and other selected fields through **Manage columns**.
28.  Highlight the tax group record, and select the values in **Tax codes** to define the relationship between the item tax group and the tax codes.

> [!Note]
> Since the new tax reform takes effect in 2026, customers who configure the **Item Tax group** in advance (for example, in 2025) should add **Header.FromTransitionDate** and **Line.FromTransitionDat**, and set both to **January 1, 2026**, to prevent unexpected errors.
  

### Define applicability rules for Tax group

29. Go to **Applicability rules** FastTab, under **Tax group applicability** tab, click **Manage columns**
30. Select relevant columns to define the elements of the applicability rules used to determine the **tax group** （for example Business process,CFOP code, Ship to City, Fiscal establishment, Fiscal classification code, etc)
31. Move them using the right arrow and confirm with **OK**
32. Input the values in the selected fields.

> [!Note]
> Since the new tax reform takes effect in 2026, customers who configure the **Tax group applicability** in advance (for example, in 2025) should add **Header.FromTransitionDate** and **Line.FromTransitionDat**, and set both to **January 1, 2026**, to prevent unexpected errors.


### Define applicability rules for Item tax group

33. Go to **Applicability rules** FastTab, under **Item tax group applicability** tab, click **Manage columns**
34. Select relevant columns to define the elements of the applicability rules used to determine the **item tax group** （for example Business process,CFOP code, Ship to City, Fiscal establishment, Fiscal classification code, etc)
35. Move them using the right arrow and confirm with **OK**
36. Input the values in the selected fields.

> [!Note]
> Since the new tax reform takes effect in 2026, customers who configure the **Item tax group applicability** in advance (for example, in 2025) should add **Header.FromTransitionDate** and **Line.FromTransitionDat**, and set both to **January 1, 2026**, to prevent unexpected errors.

### Complete and change status
After completing all onfiguration steps, such as tax codes, tax groups, item tax groups and rules, change the status of current version from **Draft** to **Completed**.
37. Go to **Workspace -> Globalization Studio ->Tax calculation**
38. On the **Tax calculation feature** form highlight the current version
39. Click **Change status** button, then select **Complete** option

## Enable Advanced Tax Calculation
With all the configuration and setup completing, enable the created feature in Advanced tax calculation engine. 

The steps for enablement are as follows.

1. Go to Module **Tax -> Setup -> Tax configuration -> Tax calculation parameters**
2. Select **General** Page,then click **Advanced tax clauclation** fasttab
3. Set **Enable advanced tax calculation** option to be **YES**
4. In the **Feature** group click **Name**, and then select the previously created feature with the completed version.
5. You will be prompted to maintain the attributes for the new tax code created:
   - **Settlement period**
   - **Ledger posting group**
   - **Currency**
6. The **Business process** field will be inactive.

## Hint

- Reformed tax codes must be created and maintained exclusively within the tax feature of the Advanced Tax Calculation engine. (For example CBS, IBS)

- Do not attempt to add legacy tax codes from the legacy engine into the Advanced Tax Calculation tax feature in Globalization Studio. Legacy tax codes must continue to be maintained using the established procedures in the legacy engine, while reformed tax codes are managed only in the Advanced Tax Calculation engine.

- Any changes that affect reformed tax calculation—such as adjustments to tax rates, modifications of tax types, or the inclusion of sales tax codes in sales tax groups or item sales tax groups—made in the legacy engine forms (Sales tax codes, Sales tax groups, Item sales tax groups) will not be applied during tax calculation.

