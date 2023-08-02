---
title: Accounting basis (Regnskab Basis) electronic report for Denmark
description: This article explains how to set up and generate the Accounting basis (Regnskab Basis) electronic report for legal entities that have a primary address in Denmark.
author: liza-golub
ms.date: 08/02/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Denmark
ms.author: egolub
ms.search.validFrom: 
ms.dyn365.ops.version: 
---

# Accounting basis (Regnskab Basis) electronic report for Denmark

This article describes how to prepare Microsoft Dynamics 365 Finance to work with the **Accounting basis** (**Regnskab Basis**) electronic report, and how to generate the file in comma-separated values (CSV) format for legal entities that have a primary address in Denmark.

## Setup

To start to work with the **Accounting basis** electronic report for Denmark, follow these steps.

1. [Turn on features in Feature management](#features).
2. [Import Electronic reporting (ER) configurations](#import).
3. [Select the Accounting electronic report format in General ledger parameters](#satt).
4. [Configure a standard chart of accounts](#coa).

### <a name="features"></a>Turn on features in Feature management

1. In the **Feature management** workspace, on the **All** tab, find and select the **Optimize datasets memory consumption at ER reports runtime** feature.
2. Select **Enable now**.

### <a name="import"></a>Import ER configurations

In Finance, import the following versions or later of these ER configurations from the Global repository. For more information about how to download ER configurations, see [Download ER configurations from the Global repository](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

| ER configuration name | Type | Version | Description |
|-----------------------|------|---------|-------------|
| Standard Audit File (SAF-T) | Model | 173 | The common data model for different audit reports. |
| SAF-T General model mapping | Model mapping | 173.373 | The model mapping that provides general data source mapping. |
| Accounting Basis (Regnskab Basis) CSV (DK) | Format | 173.9 | The CSV format that represents the **Accounting basis** electronic report in accordance with the requirements for Denmark. |

Import the most recent versions of the configurations. The version description usually includes the number of the Microsoft Knowledge Base (KB) article that explains the changes that were introduced in the configuration version.

> [!IMPORTANT]
> After all the ER configurations from the previous table are imported, set the **Default for model mapping** option to **Yes** for the **SAF-T General model mapping** configuration.
>
> ![Default for model mapping option set to Yes for the SAF-T General model mapping configuration.](media/dk-saf-t-default-model-mapping.png)

### <a name="satt"></a>Select the Accounting electronic report format in General ledger parameters

1. Go to **General ledger** \> **Setup** \> **General ledger parameters**.
2. On the **Ledger** tab, on the **Electronic reporting** FastTab, in the **Accounting electronic report** field, select **Accounting Basis (Regnskab Basis) CSV (DK)**.

### <a name="coa"></a>Configure a standard chart of accounts (Standardkontoplan)

In the Danish **Accounting basis** electronic report, main accounts that are used in Finance must be associated with Danish standard accounts. Use the [consolidation account groups and additional consolidation accounts](../budgeting/consolidation-account-groups-consolidation-accounts.md) functionality to create this association.

1. Create a [consolidation account group](../general-ledger/tasks/create-consolidation-groups.md#create-a-consolidation-account-group). For example, create a group that's named **Standardkontoplan**.
2. [Add accounts to the consolidation account group](../general-ledger/tasks/create-consolidation-groups.md#add-accounts-to-consolidation-account-group). In the **Consolidation account** field, specify a standard account. This value is reported in the **StandardAccountID** element of SAF-T, under the **Master data** \> **GeneralLedgerAccounts** \> **Account** node. In the **Consolidation account name** field, optionally specify the standard account name or description. This value isn't used in SAF-T.

## Generate the Accounting basis electronic report

1. Go to **General ledger** \> **Inquiries and reports** \> **Accounting electronic report**.
2. In the **Electronic report parameters** dialog box, set the following fields.

    | Field name | Description |
    |------------|-------------|
    | Date | Specify the date to report the **Accounting basis** electronic report for. |
    | Print zero balance | This checkbox affects the data that's reported in the **MasterFiles** \> **GeneralLedgerAccounts** node of SAF-T. Select the checkbox to include all the main accounts of your company, including main accounts that have a zero balance during the specified period. Clear the checkbox to include only main accounts that have a non-zero balance or transactions during the specified period. |
    | Consolidation account group | Select the consolidation account group that you [set up earlier](#coa) to configure the standard chart of accounts (Standardkontoplan). |
    | Currency | Select **Accounting currency** to report amounts in the **Debit**, **Credit**, and **Accumulated balance** columns of the report in the accounting currency. Select **Reporting currency** to report those amounts in the reporting currency. |
    | Main financial dimension set | Select the standard financial dimension set, including the main account that the report uses to calculate the opening balance by main account at the beginning of the reporting period. For more information about financial dimension sets, see [Financial dimension sets](financial-dimension-sets.md). |
    | Posting layer(s) | Select one or more posting layer transactions to include on the report. If you leave this field blank, all posting layers are reported. |

3. On the **Run in the background** FastTab, you can specify parameters of the batch job and run the report in batch mode.

    When an electronic report is generated in batch mode, you can find related batch information and the generated output file as an attachment by going to **Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**. For more information about how to configure a destination for each ER format configuration and its output component, see [Electronic reporting (ER) destinations](../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).

4. Select **OK** to generate the report.

### Special symbols in the value of text fields

A semicolon (;) is a special symbol on the **Accounting basis** electronic report. If it's used in the value of a text field on the report, it's replaced with a space.
