---
title: Audit file (XML Auditfile Financieel, XAF)
description: Learn how to set up and generate the Audit file for legal entities in the Netherlands in Microsoft Dynamics 365 Finance.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 05/13/2026
ms.reviewer: johnmichalak
ms.search.region: Netherlands
ms.search.validFrom: 2016-06-30
ms.search.form: TaxEvatParameters_NL
---

# Audit file (XML Auditfile Financieel, XAF)

[!include [banner](../../includes/banner.md)]

This article explains how to set up and generate the audit file for legal entities in the Netherlands in Microsoft Dynamics 365 Finance.

This functionality is available for legal entities whose primary address is in the Netherlands.

## Set up Audit File Financial XAF for the Netherlands

To set up the Audit File Financial XAF for the Netherlands, follow these steps:

1. [Import Electronic reporting configurations](#import-er-configurations).
1. [Configure RGS (ReferentieGrootboekSchema, standard chart of accounts)](#configure-rgs).
1. [Configure the **Ledger transactions export format** parameter in **General ledger parameters**](#configure-gl-parameters) (available only when the *[Netherlands] Audit File Financial XAF 4.0 - performance improvement* feature is enabled).

### <a name="import-er-configurations"></a>Import Electronic reporting configurations

To prepare Finance to generate the Audit file, first import the following electronic reporting (ER) configurations.

| # | ER configuration name | Type | Description |
|---|---|---|---|
| 1 | Audit file model | Model | A model for the Audit file for the Netherlands. Contains a built-in (old) model mapping used by legacy formats. |
| 2 | Audit file (NL) | Format (exporting) | ER format for XML Auditfile Financieel, XAF 3.2. Used before December 31, 2025. Uses the old model mapping inside the *Audit file model* configuration. |
| 3 | Audit File Financial XAF 4.0 in XML (NL) | Format (exporting) | ER format for XML Auditfile Financieel, XAF 4.0. Used starting January 1, 2026. |
| 4 | Audit file model mapping | Model mapping | New model mapping configuration optimized for XAF 4.0 reporting performance. **Required starting from version 47.8 of the \"Audit File Financial XAF 4.0 in XML (NL)\" format** when the *[Netherlands] Audit File Financial XAF 4.0 - performance improvement* feature is enabled. |

Learn more about how to import ER configurations in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

Import the most recent versions of the configurations. The version description usually includes the number of the Microsoft Knowledge Base (KB) article that explains the changes that the configuration version introduces.

#### ER format and model mapping usage summary

The following table summarizes which ER format and model mapping applies depending on the scenario:

| Scenario | ER format | Model mapping used | Feature required |
|---|---|---|---|
| XAF 3.2 reporting (before December 31, 2025) | Audit file (NL) | Old model mapping (built into *Audit file model*) | None |
| XAF 4.0 reporting (starting January 1, 2026) **before version 47.8** | Audit File Financial XAF 4.0 in XML (NL) | Old model mapping (built into *Audit file model*) | None |
| XAF 4.0 reporting (starting January 1, 2026) **version 47.8 and later** | Audit File Financial XAF 4.0 in XML (NL) | Audit file model mapping (new, separate configuration) | *[Netherlands] Audit File Financial XAF 4.0 - performance improvement* must be enabled |

> [!NOTE]
> When the *[Netherlands] Audit File Financial XAF 4.0 - performance improvement* feature is enabled, the system automatically uses the new *Audit file model mapping* configuration for XAF 4.0 generation. The old model mapping inside the *Audit file model* is no longer used for XAF 4.0 in this scenario.

### <a name="configure-rgs"></a>Configure RGS (ReferentieGrootboekSchema, standard chart of accounts)

In the Audit File Financial XAF 4.0 for Netherlands, you must associate main accounts that you use in Finance with Dutch RGS (ReferentieGrootboekSchema, standard chart of accounts). Use the [consolidation account groups and additional consolidation accounts](../../budgeting/consolidation-account-groups-consolidation-accounts.md) functionality to create this association.

To configure RGS, follow these steps:

1. Create a [consolidation account group](../../general-ledger/tasks/create-consolidation-groups.md#create-a-consolidation-account-group). For example, create a group named **RGS**.
1. [Add accounts to the consolidation account group](../../general-ledger/tasks/create-consolidation-groups.md#add-accounts-to-consolidation-account-group). In the **Consolidation account** field, specify a standard account. This value is reported in the `<RGScode>` element of XAF 4.0 under the `company > generalLedger > ledgerAccount` node. In the **Consolidation account name** field, optionally specify the standard account name or description. This value isn't used in XAF 4.0.

### <a name="configure-gl-parameters"></a>Configure the ER format in General ledger parameters

This setting is only available when the *[Netherlands] Audit File Financial XAF 4.0 - performance improvement* feature is enabled in Feature management.

To set up the ER format, follow these steps:

1. In Finance, go to **General ledger** > **Ledger setup** > **General ledger parameters**.
1. On the **General ledger parameters** page, on the **Ledger** tab, in the **Ledger transactions export format** field, select **Audit File Financial XAF 4.0 in XML (NL)**.

## Performance improvements for Audit File Financial (XAF)

> [!IMPORTANT]
> Available in Dynamics 365 Finance version **10.0.48** and **Audit File Financial XAF 4.0 in XML (NL)** ER configuration version 47.8 and later.

Starting in version 10.0.48, the Audit File Financial (XAF) report benefits from significant performance improvements that reduce processing time and system load when generating audit files, especially for large data volumes. These improvements apply to the **XAF 4.0** format only.

These performance improvements are achieved through two key enhancements:

- **Leveraging general ledger dimension set balance calculation** – The Audit File Financial report takes advantage of the *Performance enhancement for general ledger dimension set balance calculation* feature. When enabled, the system precalculates and continuously updates ledger balances for defined financial dimension sets in the background (through a process automation job that runs every few minutes). The XAF report pulls data from these preaggregated balances instead of computing everything from scratch, enabling the audit file to be produced quickly even for large transactional data volumes.

- **Optimized Electronic Reporting (ER) model mapping** – A new, separate ER model mapping configuration (*Audit file model mapping*) is introduced, specifically optimized for XAF 4.0 generation. This replaces the old model mapping that was built into the *Audit file model* configuration. By using the ER framework's latest best practices for regulatory reporting, the solution improves both maintainability and runtime performance.

### Prerequisites

Before you can use the performance improvements, ensure you meet the following prerequisites:

1. You deploy **Dynamics 365 Finance version 10.0.48 or later**.
1. You enable the **Performance enhancement for general ledger dimension set balance calculation** feature in Feature management.
1. You enable the **[Netherlands] Audit File Financial XAF 4.0 - performance improvement** feature in Feature management.
1. You define financial dimension sets and enable balance tracking for them.
1. You import the latest ER configurations, including the new *Audit file model mapping* configuration (version 47.8 or later).

### Enable the performance improvement

To enable the performance improvements for Audit File Financial (XAF), follow these steps:

#### Step 1: Enable the required features in Feature management

To enable the required features in Feature management, follow these steps:

1. Go to **Feature management** (**System administration** > **Workspaces** > **Feature management**).
1. Search for and enable the **Performance enhancement for general ledger dimension set balance calculation** feature.
1. Search for and enable the **[Netherlands] Audit File Financial XAF 4.0 - performance improvement** feature.

> [!IMPORTANT]
> The **[Netherlands] Audit File Financial XAF 4.0 - performance improvement** feature is the main switch that activates the optimized XAF 4.0 generation. When you enable this feature, the system uses the new *Audit file model mapping* configuration and exposes the **Ledger transactions export format** parameter in General ledger parameters.

> [!IMPORTANT]
> Before enabling the *Performance enhancement for general ledger dimension set balance calculation* feature in a production environment, review any customizations that rely on the previous balance data model. Complete full functional and performance testing in a sandbox or UAT environment to validate expected behavior. For more information, see [New financial dimension sets](../../general-ledger/financial-dimension-set-new.md).

#### Step 2: Configure Ledger transactions export format

When you enable the *[Netherlands] Audit File Financial XAF 4.0 - performance improvement* feature, a new parameter becomes available in General ledger parameters.

To configure Ledger transactions export format, follow these steps:

1. Go to **General ledger** > **Ledger setup** > **General ledger parameters**.
1. On the **Ledger** tab, locate the **Ledger transactions export format** field.
1. Select the **Audit File Financial XAF 4.0 in XML (NL)** ER format for the audit file export.

> [!NOTE]
> You can only see and use this parameter when the *[Netherlands] Audit File Financial XAF 4.0 - performance improvement* feature is enabled.

#### Step 3: Set up financial dimension sets with balance tracking

To set up financial dimension sets with balance tracking, follow these steps:

1. Go to **General ledger** > **Chart of accounts** > **Dimensions** > **Financial dimension sets**.
1. Ensure that you define the dimension set required for Audit File Financial reporting. The *[Netherlands] Audit File Financial XAF 4.0 - performance improvement* feature uses the main account dimension set.
1. Select a relevant dimension set and select **Enable balances** to start tracking balances for it. 
1. Verify the balance status by using the **Balance status** button. The system uses a background process automation job (*General ledger balance process*) that runs every 5 minutes by default to keep balances up to date.

> [!NOTE]
> The initial balance calculation might take several hours for large data volumes. Reports that use dimension sets aren't available until processing finishes. You can monitor the status on the **Dimension set** page.

#### Step 4: Import the latest ER configurations

To import the latest ER configurations, follow these steps:

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. Import the latest versions of the following configurations from Dataverse:
   - **Audit file model**
   - **Audit file model mapping** (new separate configuration)
   - **Audit File Financial XAF 4.0 in XML (NL)** (version 47.8 or later)

Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

## Generate the audit file

To generate the audit file, follow these steps:

1. In Dynamics 365 Finance, go to **General ledger** > **Periodic tasks** > **Audit file**.
1. In the **From date** field, enter a date.
1. In the **To date** field, enter a date.
1. In the **Consolidation account group** field (supported in the "Audit File Financial XAF 4.0 in XML (NL)" ER format), select the name of the consolidation account group that you created and set up for Dutch RGS (ReferentieGrootboekSchema). This parameter is optionally required in Audit File Financial XAF 4.0 as of January 1, 2026.
1 In the **Format mapping** field, select the appropriate format - available only when the *[Netherlands] Audit File Financial XAF 4.0 - performance improvement* feature is **off**:
   - **Audit File Financial XAF 4.0 in XML (NL)** – to report XAF 4.0 starting January 1, 2026.
   - **Audit file (NL)** – to report XAF 3.2 before December 31, 2025 (used only when the *[Netherlands] Audit File Financial XAF 4.0 - performance improvement* feature is **off**).
 <br> When the *[Netherlands] Audit File Financial XAF 4.0 - performance improvement* feature is enabled, the system automatically runs the format selected in the **General ledger parameters**, and the **Format mapping** field isn't shown in the report dialog.
1. Select **OK**.

## Related information

- [New financial dimension sets](../../general-ledger/financial-dimension-set-new.md)
- [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md)
- [Consolidation account groups and additional consolidation accounts](../../budgeting/consolidation-account-groups-consolidation-accounts.md)
