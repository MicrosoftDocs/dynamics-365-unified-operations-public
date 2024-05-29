---
title: General ledger statement by main account
description: Learn how to generate general ledger statements by main account in Microsoft Excel format, including a table that defines various column names.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: article
ms.date: 06/02/2022
ms.reviewer: kfend
audience: Application User
ms.search.validFrom: 2022-06-01
---

# General ledger statement by main account

[!include [banner](../includes/banner.md)]

This article explains how to use [Electronic Reporting (ER)](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md) to generate the **General ledger statement by main account** report in Microsoft Excel format.

The **General ledger statement by main account** report in Excel format is available in Dynamics 365 Finance as of version 10.0.27.

In addition to the [ledger reports](view-journal-entries-transactions.md#ledger-reports), you can use the **General ledger statement by main account** report in Excel format to view general ledger transactions. For each transaction, the report shows the following details.

| Column name | Data source description |
|---|---|
| Transaction posting date | The posting date of the general journal entry: `GeneralJournalEntry.AccountingDate`. |
| Transaction number | The voucher number of the general journal entry: `GeneralJournalEntry.SubledgerVoucher`. |
| Main account | The main account of the general journal account entry: `GeneralJournalAccountEntry.MainAccount`. |
| Main account name | The translation of the main account name into the user's preferred language for the main account from the general journal account entry: `MainAccountTranslation.Name` related to `MainAccount.Name`. If no translation is specified for the user's preferred language, `MainAccount.Name` is reported. |
| Counterparty number | When the posting type of the general journal account entry is **Customer balance**, **Vendor balance**, **Customer collection letter fee**, or **Penny difference in accounting currency**, this column shows the customer or vendor account ID from the related customer or vendor transaction that is found based on the voucher number and transaction date from the general journal entry: `CustTrans.AccountNum` or `VendTrans.AccountNum` found by `GeneralJournalEntry.SubledgerVoucher` and `GeneralJournalEntry.AccountingDate`. |
| Counterparty name | The name of the customer or vendor from the Global address book that is related to the customer or vendor account ID that is reported in the **Counterparty number** column: `DirPartyTable.Name`. |
| Ledger account | The ledger account, including dimensions from the general journal account entry: `GeneralJournalAccountEntry.LedgerAccount`. |
| Description | The description from the general journal account entry: `GeneralJournalAccountEntry.Text`. |
| Transaction currency | The currency of the general journal account entry: `GeneralJournalAccountEntry.TransactionCurrencyCode`. |
| Debit in transaction currency | The amount in the source document currency from the general journal account entry where the **IsCredit** property is **false**: `GeneralJournalAccountEntry.TransactionCurrencyAmount` when `IsCredit = false`. |
| Credit in transaction currency | The amount in the source document currency from the general journal account entry where the **IsCredit** property is **true**: `GeneralJournalAccountEntry.TransactionCurrencyAmount` when `IsCredit = true`. |
| Debit | The amount in the accounting or reporting currency from the general journal account entry where the **IsCredit** property is **false**: `GeneralJournalAccountEntry. AccountingCurrencyAmount` or `GeneralJournalAccountEntry. ReportingCurrencyAmount` when `IsCredit = false`. |
| Credit | The amount in the accounting or reporting currency from the general journal account entry where the **IsCredit** property is **true**: `GeneralJournalAccountEntry.AccountingCurrencyAmount` or `GeneralJournalAccountEntry.ReportingCurrencyAmount` when `IsCredit = true`. |
| Accumulated balance | The accumulated balance is calculated based on the opening balance at the beginning of the reporting period and the turnover by main account from the beginning of the reporting period until the current general ledger entry. |
| Sales tax code | <p>If a general journal account entry has a related **Profit and loss** sales tax entry, this column represents the sales tax codes from the related sales tax entries: `TaxTrans.TaxCode` found by `TaxTransGeneralJournalAccountEntry.TaxTrans` and `TaxTransGeneralJournalAccountEntry.SubledgerJournaalAccountEntry` where `TaxTransGeneralJournalAccountEntry.TaxTransRelationship` = `TaxTransRelationshipType.TransactionLineAccount`.</p><p>If multiple sales tax entries are related to the general journal account entry, a comma (,) is used as the delimiter between sales tax codes.</p> |
| Sales tax amount | If a general journal account entry has a related **Profit and loss** sales tax entry, this column represents the aggregated sales tax amount from the related sales tax entries: `TaxTrans.TaxAmount` or `TaxTrans.TaxAmountRep` found by `TaxTransGeneralJournalAccountEntry.TaxTrans` and `TaxTransGeneralJournalAccountEntry.SubledgerJournaalAccountEntry` where `TaxTransGeneralJournalAccountEntry.TaxTransRelationship = TaxTransRelationshipType.TransactionLineAccount`. |

General journal account entries on the report are presented in groups by main account. For each main account, an opening balance is reported that represents the amount in either the accounting currency or the reporting currency at the beginning of the reporting period. Each main account group of general journal account entries is finalized by using a line that presents the total amount of debit and credit turnover at the end of reporting period, and also the accumulated balance by main account at the end of the reporting period.

The format of the report uses the language that has been selected as the user's preferred language in Finance user options.

> [!NOTE]
> Use of the [One voucher](one-voucher.md) functionality introduces a reporting limitation of the counterpart number and name for some scenarios. We recommend that you set the **Allow multiple transactions within one voucher** option to **No** on the **General ledger parameters** page in your legal entity to ensure that the counterpart number and name are correctly defined on the **General ledger statement by main account** report.

## Prepare your environment to generate a General ledger statement by main account report

To start to work with the **General ledger statement by main account** report, complete the following tasks:

1. [Import Electronic reporting (ER) configurations](#import).
2. [Select the ER configuration in General ledger parameters](#gl-param).
3. [Enable features in Feature management](#features).

### <a name="import"></a>Import ER configurations

Before you can generate a **General ledger statement by main account** report, you must import the latest versions of the following ER configurations.

| ER configuration name | Type | Description |
|-----------------------|------|--------------------|
| Standard Audit File (SAF-T) | Model | The common data model for different audit reports. |
| SAF-T General model mapping | Model mapping | The model mapping that provides general data source mapping. |
| General ledger statement by main account (Excel) | Format | The general ledger statement by main account in Excel format. |

For more information about how to download ER configurations, see [Download ER configurations from the Global repository](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

Import the most recent versions of the configurations. The version description usually includes the number of the Microsoft Knowledge Base (KB) article that explains the changes that were introduced in the configuration version. Use the **Issue search** section of the [LCS](https://lcs.dynamics.com/v2) portal to find and read information about specific version of ER configuration.

> [!IMPORTANT]
> After all the ER configurations are imported, set the **Default for model mapping** option to **Yes** for the **SAF-T General model mapping** configuration.

### <a name="gl-param"></a>Select the ER configuration in General ledger parameters

1. Go to **General ledger** \> **Setup** \> **General ledger parameters**.
2. On the **Ledger** tab, on the **Electronic reporting** FastTab, in the **General ledger statement by main account** field, select the **General ledger statement by main account (Excel)** format.

### <a name="features"></a>Enable features in Feature management

To optimize the timing and memory consumption of report generation, we recommend that you enable some features in the **Feature management** workspace.

1. Open the **Feature management** workspace.
2. On the **All** tab, in the feature list, find and select the following features:
 
    - Optimization of query data source creation time during execution of ER reports
    - Optimize datasets memory consumption at ER reports runtime

3. Select **Enable now**.

## Generate a General ledger statement by main account report

To generate a **General ledger statement by main account** report, follow these steps.

1. Go to **General ledger** \> **Inquiries and reports** \> **Ledger reports** \> **General ledger statement by main account**.
2. In the report dialog box, set the following fields.

    | Field name | Description |
    | ---------- | ----------- |
    | From date, To date | Select dates to specify the date interval for the report. You can select dates within one fiscal year. |
    | Currency | Select **Accounting currency** to report amounts in the **Debit**, **Credit**, and **Accumulated balance** columns of the report in the accounting currency. Select **Reporting currency** to report those amounts in the reporting currency. |
    | Main financial dimension set | Select the standard financial dimension set, including the main account that the report uses to calculate the opening balance by main account at the beginning of the reporting period. For more information about financial dimension sets, see [Financial dimension sets](financial-dimension-sets.md). |
    | Group by main account | Select this checkbox to group general ledger account entries by main account on the report. When this checkbox is selected, the **Ledger account** column is hidden, and the amounts of the general ledger account entries that are reported for each main account are represented as aggregated amounts in the **Transaction posting date** and **Transaction number** columns. |
    | Include reversed | Select this checkbox if reversed transaction must be reported. |
    | Posting layer(s) | Select one or more posting layer transactions to include on the report. If you leave this field blank, all the posting layers are reported. |
    | Sales tax specification | Select this checkbox to include information about the sales tax codes and amounts for each general ledger account entry. This option is available only if the **Group by main account** checkbox is cleared. |
    | Settlement period | Select a settlement period to filter sales tax transactions on the report. If you leave this field blank, sales tax transactions from all settlement periods are included on the report. |
    | Split file by main accounts | Select this checkbox to split the report data into multiple files by main account. |

3. You can use the **Records to include** option to filter the data on the report by one or more main accounts.
4. On the **Run in the background** FastTab, you can specify parameters of the batch job and run the report in batch mode. When an electronic report is generated in batch mode, you can find related batch information and the generated output file as an attachment by going to **Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**. For more information about how to configure a destination for each ER format configuration and its output component, see [Electronic reporting (ER) destinations](../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).

## Generate a General ledger statements by main account report for a large volume of data

The maximum reporting period for the **General ledger statement by main account** report is one fiscal year.

When you generate the **General ledger statement by main account** report for a reporting period that has more than one million general journal account entries, we recommend that you select the **Split file by main accounts** report option. Then, if the number of general journal account entries for a main account exceeds one million in the reporting period, the first million general journal account entries are reported on the first sheet of the Excel output file when the report is generated. The next million general journal account entries are then reported on the second sheet of the same Excel output file, and so on.

If the **Split file by main accounts** option isn't selected, and the number of general journal account entries in the reporting period exceeds one million, no output file is generated, and you receive the following message:

> File cannot be generated. Number of lines in the report data set exceeds max number of lines on one sheet in Excel file. Use options of the report to reduce the data in the report or "Split file by main accounts" parameter.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
