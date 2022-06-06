---
# required metadata

title: General ledger statement by main account
description: This article explains how to generate General ledger statements by main account in Microsoft Excel format.
author: liza-golub
ms.author: elgolu
ms.date: 06/02/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.search.industry: 
ms.search.validFrom: 2022-06-01

---

# General ledger statement by main account

[!include [banner](../includes/banner.md)]

This article explains how to generate the **General ledger statement by main account** report in Microsoft Excel format using [Electronic Reporting (ER)](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md).

The **General ledger statement by main account** report in Excel format is available in Dynamics 365 Finance starting in version 10.0.27.

In addition to the [ledger reports](view-journal-entries-transactions#ledger-reports.md), you can use the **General ledger statement by main account** report in Excel format to view general ledger transactions that are represented with the following details:

| Column name | Data source description |
|----|----|
| Transaction posting date | The date of posting of the general journal entry: `GeneralJournalEntry.AccountingDate`. |
| Transaction number       | The voucher number of the general journal entry: `GeneralJournalEntry.SubledgerVoucher`. |
| Main account             | The main account of the general journal account entry: `GeneralJournalAccountEntry.MainAccount`. |
| Main account name        | The translation of the main account name into the user preference language of main account from general journal account entry: `MainAccountTranslation.Name` related to `MainAccount.Name`. If no translation is specified for the user preference language, the `MainAccount.Name` is reported. |
| Counterparty number      | When the posting type of the general journal account entry is one of the following: *Customer balance, Vendor balance, Customer collection letter fee, Penny difference in accounting currency*, the **Counterparty number** column represents Customer or Vendor account ID from related customer or vendor transaction found by Voucher number and transaction date from general journal entry: `CustTrans.AccountNum` or `VendTrans.AccountNum` found by `GeneralJournalEntry.SubledgerVoucher` and `GeneralJournalEntry.AccountingDate`.|
| Counterparty name        | The name of the customer or vendor from the Global address book related to the Customer or Vendor account ID reported in **Counterparty number** column: `DirPartyTable.Name`.|
| Ledger account           | The ledger account, including dimensions from the general journal account entry: `GeneralJournalAccountEntry.LedgerAccount`.|
| Description              | The description from the general journal account entry: `GeneralJournalAccountEntry.Text`.|
| Transaction currency     | The currency of general journal account entry: `GeneralJournalAccountEntry.TransactionCurrencyCode`.|
| Debit in transaction currency   | The amount in the source document currency from the general journal account entry where the **IsCredit** property is false: `GeneralJournalAccountEntry.TransactionCurrencyAmount` when `IsCredit = false`.|
| Credit in transaction currency  | The amount in the source document currency from the general journal account entry where the **IsCredit** property is true: `GeneralJournalAccountEntry.TransactionCurrencyAmount` when `IsCredit = true`.|
| Debit                    | The amount in the accounting or reporting currency from the general journal account entry where the **IsCredit** property is false: `GeneralJournalAccountEntry. AccountingCurrencyAmount` or `GeneralJournalAccountEntry. ReportingCurrencyAmount` when `IsCredit = false`.|
| Credit                   | The amount in the accounting or reporting currency from the general journal account entry where the **IsCredit** property is true: `GeneralJournalAccountEntry.AccountingCurrencyAmount` or `GeneralJournalAccountEntry.ReportingCurrencyAmount` when `IsCredit = true`.|
| Accumulated balance      | The accumulated balance is calculated as the opening balance on the beginning of the reporting period and turnover by main account from the beginning of the reporting period until the current general ledger entry. |
| Sales tax code           | If a general journal account entry has related sales tax entry of **Profit and loss**, the **Sales tax code** column represents the sales tax codes from the related sales tax entries: `TaxTrans.TaxCode` found by `TaxTransGeneralJournalAccountEntry.TaxTrans` and `TaxTransGeneralJournalAccountEntry.SubledgerJournaalAccountEntry` where `TaxTransGeneralJournalAccountEntry.TaxTransRelationship` = `TaxTransRelationshipType.TransactionLineAccount`.<br>If there are several sales tax entries related to general journal account entry, the sales tax codes will be represented using \“,\” delimiter.|
| Sales tax amount         | If a general journal account entry has a related sales tax entry of **Profit and loss**, the **Sales tax amount** column represents the aggregated sales tax amount from the related sales tax entries: `TaxTrans.TaxAmount` or `TaxTrans.TaxAmountRep` found by `TaxTransGeneralJournalAccountEntry.TaxTrans` and `TaxTransGeneralJournalAccountEntry.SubledgerJournaalAccountEntry` where `TaxTransGeneralJournalAccountEntry.TaxTransRelationship = TaxTransRelationshipType.TransactionLineAccount`.|

General journal account entries in the report are represented in groups by main accounts. For each main account there is an opening balance reported representing the amount in either accounting or reporting currency at the beginning of the reporting period. Each main account group of general journal account entries is finalized with a line representing the total amount of debit and credit turnover at the end of reporting period as well as the accumulated balance by main account at the end of the reporting period.

The format of the report uses the language selected as user preference in user options of Dynamics 365 Finance.

> [!NOTE]
> Using the [One voucher](one-voucher.md) functionality introduces a reporting limitation of the counterpart number and name for some scenarios. We recommend that you set the **Allow multiple transactions within one voucher** parameter on the **General ledger parameters** page to **No** in your legal entity to get counterpart number and name properly defined in **General ledger statement by main account** report.

## Prepare your environment to generate General ledger statement by main account report

To start to work with the **General ledger statement by main account** report, complete the following steps:

1. [Import Electronic reporting configurations.](#import)
2. [Select the Electronic reporting configuration in General ledger parameters.](#gl-param)
3. [Enable features in Feature management.](#features)

### <a name="import"></a> Import Electronic reporting configurations

Before you can generate a **General ledger statement by main account** report, you must import the latest versions of the following Electronic reporting (ER) configurations.

| ER configuration name       | Type          | Description |
|-----------------------------|---------------|--------------------|
| Standard Audit File (SAF-T) |   Model       |  The common data model for different audit reports.  |
| SAF-T General model mapping | Model mapping |  The model mapping that provides general data source mapping. |
| General ledger statement by main account (Excel)  | Format        |  The General ledger statement by main account in Microsoft Excel format. |

For more information about how to download ER configurations, see [Download ER configurations from the Global repository](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

Import the most recent versions of the configurations. The version description usually includes the number of the Microsoft Knowledge Base (KB) article that explains the changes that were introduced in the configuration version. Use the **Issue search** section of the [LCS](https://lcs.dynamics.com/v2) portal to find and read information about specific version of ER configuration.

> [!IMPORTANT]
> After all the ER configurations  are imported, set the **Default for model mapping** option to **Yes** for the **SAF-T General model mapping** configuration.

### <a name="gl-param"></a> Select the Electronic reporting configuration in General ledger parameters

1. Go to **General ledger** > **Setup** > **General ledger parameters**.
2. On the **Electronic reporting** FastTab of the **Ledger** tab, in the **General ledger statement by main account** field, select the **General ledger statement by main account (Excel)** format.

### <a name="features"></a> Enable features in Feature management

To optimize timing and memory consumption of the report generation, we recommend enabling features in the **Feature management** workspace.

1. Go to **Feature management**, and select the **All** tab.
2. In the feature list, find and select the following features:
 
   - **Optimization of query data source creation time during execution of ER reports**
   - **Optimize datasets memory consumption at ER reports runtime**

3. Select **Enable now**.

## Generate General ledger statement by main account report

To generate the **General ledger statement by main account** report, go to **General ledger** > **Inquiries and reports** > **Ledger reports** > **General ledger statement by main account**.

The following table describes the fields in the report dialog box.

| Parameter | Description |
| --------- | ----------- |
| **From date** <br> **To date** | Select dates to specify the date interval for the report. You can select dates within one fiscal year. |
| **Currency** | Select the **Accounting currency** to report amounts in the **Debit**, **Credit**, and **Accumulated balance** columns of the report in the accounting currency.<br> Select **Reporting currency** to report amounts in the **Debit**, **Credit** and **Accumulated balance** columns of the report in the reporting currency. |
| **Main financial dimension set** | Select the standard financial dimension set including the **Main account** which is used by the report to calculate the opening balance by main accounts at the beginning of the reporting period. For more information about Financial dimension sets, see [Financial dimension sets](financial-dimension-sets.md). |
| **Group by main account** | Select this checkbox to report general ledger account entries that are grouped by main account. When this checkbox is marked, the **Ledger account** column is hidden and the amounts of the general ledger account entries reported for each main account are represented as aggregated amounts in the **Transaction posting date** and **Transaction number** columns. |
| **Include reversed** | Mark this checkbox if reversed transaction must be reported. |
| **Posting layer(s)** | Select one or more posting layer transactions to include in the report. When no posting layers are selected for the report, all the posting layers are reported. |
| **Sales tax specification** | Mark this checkbox to include information about the sales tax codes and amounts for each general ledger account entry. This option is available when the option **Group by main account** option isn't selected. |
| **Settlement period** | Select one settlement period to filter sales tax transactions in the report or leave the field empty. When no settlement period is selected, sales tax transactions from all the settlement periods are included in the report. |
| **Split file by main accounts** | Mark this checkbox to split the report data into multiple files by main account. |

In addition to the described fields in the report dialog box, use the **Records to include** option to filter data in the report by one or more main accounts.

Use the **Run in the background** FastTab of the report dialog box to specify parameters of the batch job and run the report in batch. When an electronic report is generated in batch, you can find related batch information and generated output file as an attachment by going to **Organization administration** > **Electronic reporting** > **Electronic reporting jobs**. For more information about how to configure a destination for each ER format configuration and its output component, see [Electronic reporting (ER) destinations](../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).

## Generate the General ledger statements by main account report for big volume of data

The maximum reporting period for **General ledger statement by main account** report is one fiscal year.

When you generate the **General ledger statement by main account** report for a reporting period with more than one million general journal account entries, we recommend using the report option, **Split file by main accounts**. If you generate the report without selecting the **Split file by main accounts** option and the number of general journal account entries in the reporting period is more then one million, the output file isn't generated and the following message occurs: **File cannot be generated. Number of lines in the report data set exceeds max number of lines on one sheet in Excel file. Use options of the report to reduce the data in the report or \”Split file by main accounts\” parameter.**

When you generate the **General ledger statement by main account** report using the **Split file by main accounts** option and the number of general journal account entries for a main account is more then one million in the reporting period, one million of general journal account entries are reported on the first sheet of the Excel output file. The other general journal account entries are be reported on the second sheet of the same Excel output file. The number of general journal account entries that can be reported on the second sheet of Excel output file is also limited to one million general journal account entries.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
