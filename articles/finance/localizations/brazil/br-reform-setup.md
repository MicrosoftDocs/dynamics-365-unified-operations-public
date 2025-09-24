---
title: Brazil Reformed Tax setup
description: Learn about the steps to support Brazilian tax reform within scope of 2026
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

# Brazil reformed tax setup

[!include [banner](../../includes/banner.md)]

This article outlines the general steps to support the Brazilian tax reform for 2026.

The reformed tax solution uses the Advanced Tax Calculation engine. Follow these steps 
To set up and configure the feature, follow these steps.

The following diagram shows the feature setup and enablement process.
:::image type="content" source="https://github.com/user-attachments/assets/df125501-4368-4907-b9ee-b564bd68ddc6" alt-text="Screenshot of diagram that shows the Brazil reformed tax setup enablement process.":::


## Enable the feature in Feature management
During public preview and general availability, the feature is visible but disabled by default. Enable the Brazil tax reform feature in the **Feature management** workspace.

Follow these steps to enable the feature.

1. Go to **Workspace->Feature management**.
1. Search for **Meet requirements of Tax reform in Brazil in 2026**.
1. Select **Enable** to activate the feature.

> [!NOTE]
> If the feature isn't in the list, select **Check for updates** in **Feature management**. 

## Create and activate a configuration provider
Follow the instructions in [Create configuration providers and mark them as active](/dynamics365/fin-ops-core/dev-itpro/analytics/tasks/er-configuration-provider-mark-it-active-2016-11?context=%2Fdynamics365%2Fcontext%2Ffinance).

## Download the configuration files
Configuration files for tax calculation and e-invoicing are available in two locations. Based on your environment, select where to download them.

- Dataverse
  
  See [Import Electronic reporting (ER) Configurations from Dataverse](/dynamics365/finance/localizations/global/workspace/gsw-import-er-config-dataverse).

- Lifecycle Services

  See [Import Electronic reporting (ER) Configurations](/dynamics365/fin-ops-core/dev-itpro/analytics/electronic-reporting-import-ger-configurations?context=%2Fdynamics365%2Fcontext%2Fcommerce).

### Download list
Configuration files for Tax Calculation:
- Tax Data Model 
- Tax Calculation Data Model 
- FNO Model Mapping 
- Tax Calculation Configuration  
- Tax Calculation Data Model (Brazil) 
- FNO Model Mapping (Brazil) 
- Tax Calculation Configuration (Brazil)  

Configuration files for e-invoicing:
- Fiscal documents
- Fiscal documents mapping
- NF-e submit export format

## Import the configuration files for tax calculation and e-invoicing

### For tax calculation
The steps for importing tax calculation configuration files are as follows.

1. Go to **Workspaces->Electronic reporting**.
1. Select the **Tax configurations** tile.
1. On the **Configurations** page, select **Exchange**.
1. Select the **Load from XML file** option.
1. Select a file by selecting the **Browse** button.
1. Upload all files in sequence. Then go to step 7.
1. Go back to the **Configurations** page. Select **FNO Model Mapping** under **Tax Calculation Data Model**. Switch **Default for model mapping** to **YES**.
1. Go back to the **Configurations** page. Select **FNO Model Mapping(Brazil)** under **FNO Model Mapping**. Switch **Default for model mapping** to **YES**.
 
> [!NOTE]
> Upload the tax calculation configuration-related files in this sequence:
> 1. Tax Data Model
> 1. Tax Calculation Data Model
> 1. FNO Model Mapping
> 1. Tax Calculation Configuration
> 1. Tax Calculation Data Model (Brazil)
> 1. FNO Model Mapping (Brazil)
> 1. Tax Calculation Configuration (Brazil)

> [!NOTE]
> If importing the file **Tax Calculation Configuration (Brazil)** fails, sync the tax measure type:
> 1. Go to **Workspaces->Electronic reporting**.
> 1. Select the **Tax configurations** tile.
> 1. On the **Configurations** page, select **Configurations**.
> 1. Under the **Advanced settings** group, select **Tax measure types**.
> 1. Select **Synchronize**.
> 1. Return to the previous steps to continue.
    


### For e-invoicing
The steps for importing e-invoicing configuration files are as follows.

1. Go to **Workspaces->Electronic reporting**
1. Select the **Reporting configurations** tile.
1. On the **Configurations** page, select **Exchange**.
1. Select **Load from XML file** option
1. Select a file by Clicking **Browse** button
1. Upload all configuration files in sequence. Then go to step 7.
1. Go to **Organization administration -> Setup -> Brazilian parameters**.
1. Select the **Electronic reporting** tab.
1. Select **NF-e** in the **Type** field and **Fiscal documents mapping** in the **Model Mapping** field.
1. Go to **Organization administration -> Organizations -> Fiscal establishments -> Fiscal document types**.
1. Select **NF-e submit export format** in the **Export format mapping** field.

> [!NOTE]
> Upload the e-invoicing configuration files in this sequence:
> 1. Fiscal documents
> 1. Fiscal documents mapping
> 1. NF-e submit export format

## Create tax calculation feature 

Follow these steps to create the tax calculation feature.
### Create
1. Go to **Workspace -> Globalization Studio**.
1. Select **Tax calculation**.
1. On the **Tax calculation feature** form, select **Add**.
1. Select **New feature**, enter **Name, and **Description**, then select **Default** under **Type**.
1. Select **Create feature**.

### Configure
1. After you create the feature, go to the right side of the page and select the **Versions** tab.
1. Select the version with status **Draft**, then select **Edit** to configure the feature.

> [!NOTE]
> If you don't see **Edit**, select **the three dots**. Screen resolution can hide the option.
  
1. Go to the **General** FastTab.
1. Select **Tax Calculation Configuration (Brazil)** with the version that matches your Finance and Operations version.

> [!NOTE]
> See **Brazil tax reform overview** for version mapping.

## Enable lookups in applicability rules
1. Turn on the **Enable lookups in applicability rules** option
1. Then select the **Source Legal Entity** (for example, BRMF)
1. Select **Select** button.

### Set up Tax codes for new tax types (CBS/IBS)
1. Go to **Tax codes and groups** FastTab, under **Tax codes** tab select **Add** button 
1. Input values in **Tax code** (For example, CBS, IBS-City12 etc.)
1. Select **By Net Amount Brazil** in **Calculation origin** field
1. Select **Save** button.
1. Go to the right page **General** FastTab. Fill in the values for all related fields (for example, **Calculation Method**, **cClassTrib code** and **Tax type**  etc.)
1. Go to **Rate** FastTab. Fill in the values for all related fields (for example, **Tax Rate** etc.)

> [!NOTE]
> Tax codes created here in advanced tax engine could be synchronized in **Tax->Indirect tax-> Sales tax -> Sales tax codes** form once the feature is enabled in the parameter.
> 
> **Settlement period** and **Leger posting group** in tax codes haven't been specified. You'll be prompted to define them when enabling the feature in Advanced tax calculation engine in the tax parameter.
> 
> For the synchronization between advanced tax engine and legacy system, follow this link for reference.
>
> [Sync the tax setup from the Tax Calculation feature to Dynamics 365 Finance | Dynamics 365 | Microsoft Learn](/dynamics365/finance/localizations/global/global-master-data-sync-tax-calculation-service-finance)

 

### Set up the Tax group and assign tax codes
1. Go to **Tax codes and groups** FastTab, on the **Tax group** tab select **Manage columns**
1. Select the relevant columns to define the elements of the tax groups definition. (For example, Transaction date from header and line etc.)
1. Move them using the right arrow and confirm with **OK** 
1. Select **Add** button, then input values in **Lines.Tax group** and other selected fields through **Manage columns**.
1. Highlight the tax group record, and select the values in **Tax codes** to define the relationship between the tax group and the tax codes.

> [!NOTE]
> Since the new tax reform takes effect in 2026, customers who configure the **Tax group** in advance (for example, in 2025) should add **Header.FromTransitionDate** and **Line.FromTransitionDat**, and set both to **January 1, 2026**, to prevent unexpected errors.

### Set up the Item Tax group and assign tax codes
1.  Go to **Tax codes and groups** FastTab, on the **Item Tax group** tab select **Manage columns**
1.  Select the relevant columns to define the elements of the item tax groups definition. (For example, TransactionDate on header and line etc.)
1.  Move them using the right arrow and confirm with **OK**. 
1.  Select **Add** button and input values in **Lines. Item Tax group and other selected fields through **Manage columns**.
1.  Highlight the tax group record, and select the values in **Tax codes** to define the relationship between the item tax group and the tax codes.

> [!NOTE]
> Since the new tax reform takes effect in 2026, customers who configure the **Item Tax group** in advance (for example, in 2025) should add **Header.FromTransitionDate** and **Line.FromTransitionDat**, and set both to **January 1, 2026**, to prevent unexpected errors.

> [!NOTE]
> To prevent unexpected errors, specify the FromDate for either the tax group or the item tax group. Optionally, you can configure both.

### Define applicability rules for Tax group

1. Go to **Applicability rules** FastTab, under **Tax group applicability** tab, select **Manage columns**
1. Select relevant columns to define the elements of the applicability rules used to determine the **tax group** （for example Business process, CFOP code, Ship to City, Fiscal establishment, Fiscal classification code, etc.)
1. Move them using the right arrow and confirm with **OK**
1. Input the values in the selected fields.



### Define applicability rules for Item tax group

1. Go to **Applicability rules** FastTab, under **Item tax group applicability** tab, select **Manage columns**
1. Select relevant columns to define the elements of the applicability rules used to determine the **item tax group** （for example Business process, CFOP code, Ship to City, Fiscal establishment, Fiscal classification code, etc.)
1. Move them using the right arrow and confirm with **OK**
1. Input the values in the selected fields.

> [!NOTE]
> Since the new tax reform takes effect in 2026, customers who configure the **Item tax group applicability** in advance (for example, in 2025) should add **Header.FromTransitionDate** and **Line.FromTransitionDat**, and set both to **January 1, 2026**, to prevent unexpected errors.
> 
> For determination logic, please refer to [Sales tax applicability and sales tax group determination logic - Finance](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/global/global-sales-tax-group-determination?context=%2Fdynamics365%2Fcontext%2Ffinance).

### Complete and change status
After completing all configuration steps, such as tax codes, tax groups, item tax groups, and rules, change the status of current version from **Draft** to **Completed**.
1. Go to **Workspace -> Globalization Studio ->Tax calculation**
1. On the Tax calculation feature form, highlight the current version
1. Select **Change status** button, then select **Complete** option

## Enable Advanced Tax Calculation
With all the configuration and setup completing, enable the created feature in Advanced tax calculation engine. 

The steps for enablement are as follows.

1. Go to Module **Tax -> Setup -> Tax configuration -> Tax calculation parameters**
1. Select **General** Page, then select **Advanced tax calculation** FastTab
1. Set **Enable advanced tax calculation** option to be **YES**
1. In the **Feature** group select **Name**, and then select the previously created feature with the completed version.
1. You are prompted to maintain the attributes for the new tax code created:
   - **Settlement period**
   - **Ledger posting group**
   - **Currency**
6. The **Business process** field is inactive.

## Hint

* Reformed tax codes must be created and maintained exclusively within the tax feature of the Advanced Tax Calculation engine. (For example CBS, IBS)

* Don't attempt to add legacy tax codes from the legacy engine into the Advanced Tax Calculation tax feature in Globalization Studio. Legacy tax codes must continue to be maintained using the established procedures in the legacy engine, while reformed tax codes are managed only in the Advanced Tax Calculation engine.

* Any changes that affect reformed tax calculation—such as adjustments to tax rates, modifications of tax types, or the inclusion of sales tax codes in sales tax groups or item sales tax groups—made in the legacy engine forms (Sales tax codes, Sales tax groups, Item sales tax groups) won't be applied during tax calculation.

* **Settlement period** and **Leger posting group** needs to be modified in legacy tax module **Tax->Indirect tax-> Sales tax -> Sales tax codes**.

## Related setup
> **Sales tax authorities**, please find the details in the below link.
>
>  [Set up sales tax authorities - Finance | Dynamics 365 | Microsoft Learn](https://learn.microsoft.com/en-us/dynamics365/finance/general-ledger/tasks/set-up-sales-tax-authorities)
>
> **Leger posting groups**, please find the details in the below link.
> 
> [Set up Ledger posting groups for sales tax - Finance | Dynamics 365 | Microsoft Learn](https://learn.microsoft.com/en-us/dynamics365/finance/general-ledger/tasks/set-up-ledger-posting-groups-sales-tax)
> 
> **Settlement periods**,please find the details in the below link.
> 
> [Set up sales tax settlement periods - Finance | Dynamics 365 | Microsoft Learn](https://learn.microsoft.com/en-us/dynamics365/finance/general-ledger/tasks/set-up-sales-tax-settlement-periods)
