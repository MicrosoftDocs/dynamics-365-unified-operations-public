---
title: Brazil Reformed Tax setup
description: Learn about the steps to support Brazilian tax reform within scope of 2026
author: yanansong
ms.author: yanansong
ms.topic: how-to
ms.date: 09/30/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2025-10-01
ms.custom: 
  - bap-template
---

# Brazil reformed tax setup

[!include [banner](../../includes/banner.md)]

This article outlines the general steps to support Brazilian tax reform for 2026.

The reformed tax solution uses the Advanced Tax Calculation engine. To set up and configure the feature, follow these steps.

The following diagram shows the feature setup and enablement process.
:::image type="content" source="https://github.com/user-attachments/assets/df125501-4368-4907-b9ee-b564bd68ddc6" alt-text="Screenshot of a diagram showing the Brazil reformed tax setup enablement process.":::

## Enable the feature in feature management
The feature is visible but disabled by default during public preview and general availability. Enable the Brazil tax reform feature in the **Feature management** workspace.

Follow these steps to enable the feature.

1. Go to **Workspace > Feature management**.
1. Search for **Meet requirements of tax reform in Brazil in 2026**.
1. Select **Enable** to activate the feature.

> [!NOTE]
> If the feature isn't in the list, select **Check for updates** in the **Feature management** workspace. 

## Create and activate a configuration provider
Follow the instructions in [Create configuration providers and mark them as active](/dynamics365/fin-ops-core/dev-itpro/analytics/tasks/er-configuration-provider-mark-it-active-2016-11?context=%2Fdynamics365%2Fcontext%2Ffinance).

## Download the configuration files
Find configuration files for tax calculation and e-invoicing in two locations. Based on your environment, select where to download them.

- Dataverse
  
  See [Import electronic reporting (ER) configurations from Dataverse](/dynamics365/finance/localizations/global/workspace/gsw-import-er-config-dataverse).

- Lifecycle Services

  See [Import electronic reporting (ER) configurations](/dynamics365/fin-ops-core/dev-itpro/analytics/electronic-reporting-import-ger-configurations?context=%2Fdynamics365%2Fcontext%2Fcommerce).

### Download list
Configuration files for tax calculation
- Tax data model
- Tax calculation data model
- Finance and operations model mapping
- Tax calculation configuration
- Tax calculation data model (Brazil)
- FNO model mapping (Brazil)
- Tax calculation configuration (Brazil)  

Configuration files for e-invoicing
- Fiscal documents
- Fiscal documents mapping
- NF-e submit export format

## Import the configuration files for tax calculation and e-invoicing

### For tax calculation
To import tax calculation configuration files, follow these steps:

1. Go to **Workspaces** > **Electronic reporting**.
1. Select the **Tax configurations** tile.
1. On **Configurations**, select **Exchange**.
1. Select the **Load from XML file** option.
1. Select a file using the **Browse** button.
1. Upload all files in sequence, and then go to step 7.
1. Return to the **Configurations** page. Select **FNO Model Mapping** under **Tax Calculation Data Model**. Set **Default for model mapping** to **YES**.
1. Return to the **Configurations** page. Select **FNO Model Mapping(Brazil)** under **FNO Model Mapping**. Set **Default for model mapping** to **YES**.
 
> [!NOTE]
> Upload the tax calculation configuration files in this sequence:
> 1. Tax Data Model
> 1. Tax Calculation Data Model
> 1. FNO Model Mapping
> 1. Tax Calculation Configuration
> 1. Tax Calculation Data Model (Brazil)
> 1. FNO Model Mapping (Brazil)
> 1. Tax Calculation Configuration (Brazil)

> [!NOTE]
> If importing the file **Tax Calculation Configuration (Brazil)** fails, synchronize the tax measure type:
> 1. Go to **Workspaces** > **Electronic reporting**.
> 1. Select the **Tax configurations** tile.
> 1. On the **Configurations** page, select **Configurations**.
> 1. Under the **Advanced settings** group, select **Tax measure types**.
> 1. Select **Synchronize**.
> 1. Return to the previous steps to continue.
    
### For e-invoicing
To import e-invoicing configuration files, follow these steps:

1. Go to **Workspaces->Electronic reporting**.
1. Select the **Reporting configurations** tile.
1. On **Configurations**, select **Exchange**.
1. Select **Load from XML file**.
1. Select a file by selecting **Browse**.
1. Upload all configuration files in sequence. Then go to step 7.
1. Go to **Organization administration** > **Setup** > **Brazilian parameters**.
1. Select the **Electronic reporting** tab.
1. Select **NF-e** in the **Type** field, and select **Fiscal documents mapping** in the **Model Mapping** field.
1. Go to **Organization administration** > **Organizations** > **Fiscal establishments** > **Fiscal document types**.
1. Select **NF-e submit export format** in the **Export format mapping** field.

> [!NOTE]
> Upload the e-invoicing configuration files in this order:
> 1. Fiscal documents
> 1. Fiscal documents mapping
> 1. NF-e submit export format

## Create tax calculation feature 

To create the tax calculation feature, follow these steps.
### Create the feature
1. Go to **Workspace** > **Globalization Studio**.
1. Select **Tax calculation**.
1. On the **Tax calculation feature** form, select **Add**.
1. Select **New feature**, enter a **Name** and **Description**, and then select **Default** under **Type**.
1. Select **Create feature**.

### Configure
1. After you create the feature, on the right side of the page, select the **Versions** tab.
1. Select the version with status **Draft**, and then select **Edit** to configure the feature.

> [!NOTE]
> If you don't see **Edit**, select **the three dots** because screen resolution might hide the option.
  
1. On the **General** FastTab, configure the required settings.
1. Select **Tax Calculation Configuration (Brazil)** with the version that matches your Finance and Operations version.

> [!NOTE]
> For version mapping information, see **Brazil tax reform overview**.

## Enable lookups in applicability rules
1. Turn on the **Enable lookups in applicability rules** option.
1. Select the **Source Legal Entity** (for example, BRMF).
1. Select **Select**.

### Set up Tax codes for new tax types (CBS/IBS)
1. Go to the **Tax codes and groups** FastTab. On the **Tax codes** tab, select **Add**.
1. Enter values in **Tax code** (for example, CBS, IBS-City12, etc.).
3. In the **Calculation origin** field, select **By Net Amount Brazil**.
4. Select **Save**.
1. Go to the **General** FastTab. Enter values for all related fields (for example, **Calculation Method**, **cClassTrib code**, and **Tax type**, etc.).
1. Go to the **Rate** FastTab. Enter values for all related fields (for example, **Tax Rate**, etc.).

> [!NOTE]
> Tax codes created here in advanced tax engine can be synchronized in **Tax->Indirect tax-> Sales tax -> Sales tax codes** form once the feature is enabled in the parameter.
> 
> **Settlement period** and **Ledger posting group** in tax codes aren't specified. You are prompted to define them when enabling the feature in Advanced tax calculation engine in the tax parameter.
> 
> For the synchronization between advanced tax engine and legacy system, follow this link for reference.
>
> [Sync the tax setup from the Tax Calculation feature to Dynamics 365 Finance | Dynamics 365 | Microsoft Learn](/dynamics365/finance/localizations/global/global-master-data-sync-tax-calculation-service-finance)

### Set up the Tax group and assign tax codes
1. Go to the **Tax codes and groups** FastTab. On the **Tax group** tab, select **Manage columns**.
2. Select the relevant columns to define the elements of the tax groups definition (for example, Transaction date from header and line).
1. Move them using the right arrow, and confirm with **OK**.
4. Select **Add**, then enter values in **Lines.Tax group** and other selected fields through **Manage columns**.
1. Highlight the tax group record and select values in **Tax codes** to define the relationship between the tax group and the tax codes.

> [!NOTE]
> Since the new tax reform takes effect in 2026, customers who configure the **Tax group** in advance (for example, in 2025) should add **Header.FromTransitionDate** and **Line.FromTransitionDat**, and set both to **January 1, 2026**, to prevent unexpected errors.

### Set up the Item Tax group and assign tax codes
1. Go to the **Tax codes and groups** FastTab. On the **Item Tax group** tab, select **Manage columns**.
1. Select the relevant columns to define the elements of the item tax groups definition (for example, TransactionDate on header and line).
1. Move them by using the right arrow, and confirm with **OK**.
1. Select **Add**, and enter values in **Lines.Item Tax group** and other selected fields through **Manage columns**.
1. Highlight the tax group record, and select the values in **Tax codes** to define the relationship between the item tax group and the tax codes.

> [!NOTE]
> Since the new tax reform takes effect in 2026, add **Header.FromTransitionDate** and **Line.FromTransitionDat**, and set both to **January 1, 2026**, if you configure the **Item Tax group** in advance (for example, in 2025) to prevent unexpected errors.

> [!NOTE]
> To prevent unexpected errors, specify the FromDate for either the tax group or the item tax group. You can optionally configure both.

### Define applicability rules for Tax group

1. Go to the **Applicability rules** FastTab. On the **Tax group applicability** tab, select **Manage columns**.
1. Select relevant columns to define the elements of the applicability rules used to determine the **tax group** (for example, Business process, CFOP code, Ship to City, Fiscal establishment, and Fiscal classification code).
1. Move them by using the right arrow, and confirm with **OK**.
1. Enter the values in the selected fields.

### Define applicability rules for item tax group

1. Go to the **Applicability rules** FastTab. On the **Item tax group applicability** tab, select **Manage columns**.
1. Select relevant columns to define the elements of the applicability rules used to determine the **item tax group** (for example, Business process, CFOP code, Ship to City, Fiscal establishment, and Fiscal classification code).
1. Move them by using the right arrow and confirm with **OK**.
1. Input the values in the selected fields.

> [!NOTE]
> Since the new tax reform takes effect in 2026, add **Header.FromTransitionDate** and **Line.FromTransitionDat**, and set both to **January 1, 2026**, to prevent unexpected errors if you configure the **Item tax group applicability** in advance (for example, in 2025).
> 
> For determination logic, see [Sales tax applicability and sales tax group determination logic - Finance](/dynamics365/finance/localizations/global/global-sales-tax-group-determination?context=%2Fdynamics365%2Fcontext%2Ffinance).

### Complete and change status
After completing all configuration steps, such as tax codes, tax groups, item tax groups, and rules, change the status of current version from **Draft** to **Completed**.
1. Go to **Workspace -> Globalization Studio ->Tax calculation**
1. On the Tax calculation feature form, highlight the current version.
1. Select **Change status**, then select **Complete**.

## Enable advanced tax calculation
After you complete all the configuration and setup steps, enable the feature in the Advanced tax calculation engine. 

Follow these steps to enable the feature:

1. Go to **Tax > Setup > Tax configuration > Tax calculation parameters**.
1. Select the **General** page, then select the **Advanced tax calculation** FastTab.
1. Set the **Enable advanced tax calculation** option to **YES**.
1. In the **Feature** group, select **Name**, then select the previously created feature with the completed version.
1. You're prompted to maintain the attributes for the new tax code you created:
   - **Settlement period**.
   - **Ledger posting group**.
   - **Currency**.
1. The **Business process** field is inactive.

## Hint

* Create and maintain reformed tax codes exclusively within the tax feature of the Advanced Tax Calculation engine (for example, CBS and IBS).

* Don't add legacy tax codes from the legacy engine into the Advanced Tax Calculation tax feature in Globalization Studio. Maintain legacy tax codes by using the established procedures in the legacy engine. Manage reformed tax codes only in the Advanced Tax Calculation engine.

* Changes that affect reformed tax calculation, such as adjustments to tax rates, modifications of tax types, or the inclusion of sales tax codes in sales tax groups or item sales tax groups, made in the legacy engine forms (sales tax codes, sales tax groups, item sales tax groups) don't apply during tax calculation.

* Modify **Settlement period** and **Ledger posting group** in the legacy tax module **Tax > Indirect tax > Sales tax > Sales tax codes**.

## Related setup
> **Sales tax authorities**: For more information, see [Set up sales tax authorities - Finance | Dynamics 365 | Microsoft Learn](/dynamics365/finance/general-ledger/tasks/set-up-sales-tax-authorities).
>
> **Ledger posting groups**: For more information, see [Set up Ledger posting groups for sales tax - Finance | Dynamics 365 | Microsoft Learn](/dynamics365/finance/general-ledger/tasks/set-up-ledger-posting-groups-sales-tax).
> 
> **Settlement periods**: For more information, see [Set up sales tax settlement periods - Finance | Dynamics 365 | Microsoft Learn](/dynamics365/finance/general-ledger/tasks/set-up-sales-tax-settlement-periods).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
