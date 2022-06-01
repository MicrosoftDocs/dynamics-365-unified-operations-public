---
# required metadata

title: General ledger statement by main account
description: This topic explains how to generate General ledger statement by main account in Microsoft Excel format.
author: liza-golub
ms.author: elgolu
ms.date: 06/01/2022
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

This topic explains how to generate **General ledger statement by main account** report in Microsoft Excel format using [Electronic Reporting (ER)](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/general-electronic-reporting?toc=%2Fdynamics365%2Ffinance%2Ftoc.json).

**General ledger statement by main account** in Microsoft Excel format is available in Dynamics 365 Finance starting from 10.0.27 version.

In addition to the [ledger reports](https://docs.microsoft.com/en-us/dynamics365/finance/general-ledger/view-journal-entries-transactions#ledger-reports), you can use **General ledger statement by main account** in Microsoft Excel format to view general ledger transactions represented with following details:

|**Column name**|**Data source description**|
|----|----|
|**Transaction posting date** |Date of posting of general journal entry: `GeneralJournalEntry.AccountingDate`.|
|**Transaction number**|Voucher number of general journal entry: `GeneralJournalEntry.SubledgerVoucher`.|
|**Main account**|Main account of general journal account entry: `GeneralJournalAccountEntry.MainAccount`.|
|**Main account name**|Translation of main account name into the user preference language of main account from general journal account entry: `MainAccountTranslation.Name` related to `MainAccount.Name`. In case, no translation is specified for the user preference language, the `MainAccount.Name` is reported. |
|**Counterparty number**|In case when posting type of general journal account entry is one of the following: *Customer balance, Vendor balance, Customer collection letter fee, Penny difference in accounting currency*, the **Counterparty number** column represents Customer or Vendor account ID from related customer or vendor transaction found by Voucher number and transaction date from general journal entry: `CustTrans.AccountNum` or `VendTrans.AccountNum` found by `GeneralJournalEntry.SubledgerVoucher` and `GeneralJournalEntry.AccountingDate`.|
|**Counterparty name**|Name of the customer or vendor from Global address book related to the Customer or Vendor account ID reported in **Counterparty number** column: `DirPartyTable.Name`.|
|**Ledger account**|Ledger account including dimensions from general journal account entry: `GeneralJournalAccountEntry.LedgerAccount`.|
|**Description**|Description from general journal account entry: `GeneralJournalAccountEntry.Text`.|
|**Transaction currency**|Currency of general journal account entry: `GeneralJournalAccountEntry.TransactionCurrencyCode`.|
|**Debit in transaction currency**|Amount in source document currency from general journal account entry where *IsCredit* property is false: `GeneralJournalAccountEntry.TransactionCurrencyAmount` when `IsCredit = false`.|
|**Credit in transaction currency**|Amount in source document currency from general journal account entry where *IsCredit* property is true: `GeneralJournalAccountEntry.TransactionCurrencyAmount` when `IsCredit = true`.|
|**Debit**|Amount in either accounting or reporting currency from general journal account entry where *IsCredit* property is false: `GeneralJournalAccountEntry. AccountingCurrencyAmount` or `GeneralJournalAccountEntry. ReportingCurrencyAmount` when `IsCredit = false`.|
|**Credit**|Amount in either accounting or reporting currency from general journal account entry where *IsCredit* property is true: `GeneralJournalAccountEntry.AccountingCurrencyAmount` or `GeneralJournalAccountEntry.ReportingCurrencyAmount` when `IsCredit = true`.|
|**Accumulated balance**|Accumulated balance is calculated as opening balance on the beginning of the reporting period and turnover by main account from the beginning of the reporting period until the current general ledger entry. |
|**Sales tax code**|If general journal account entry has related sales tax entry of *Profit and loss* type, **Sales tax code** column represents the sales tax codes from the related sales tax entries: `TaxTrans.TaxCode` found by `TaxTransGeneralJournalAccountEntry.TaxTrans` and `TaxTransGeneralJournalAccountEntry.SubledgerJournaalAccountEntry` where `TaxTransGeneralJournalAccountEntry.TaxTransRelationship` = `TaxTransRelationshipType.TransactionLineAccount`.<br>In case there are several sales tax entries related to general journal account entry, the sales tax codes will be represented using \“,\” delimiter.|
|**Sales tax amount**|If general journal account entry has related sales tax entry of *Profit and loss*, **Sales tax amount** column represents aggregated sales tax amount from the related sales tax entries: `TaxTrans.TaxAmount` or `TaxTrans.TaxAmountRep` found by `TaxTransGeneralJournalAccountEntry.TaxTrans` and `TaxTransGeneralJournalAccountEntry.SubledgerJournaalAccountEntry` where `TaxTransGeneralJournalAccountEntry.TaxTransRelationship = TaxTransRelationshipType.TransactionLineAccount`.|

General journal account entries in the report are represented in groups by main accounts. For each main account there is an opening balance reported representing the amount in either accounting or reporting currency at the beginning of the reporting period. Each main account group of general journal account entries is finalized with a line representing the total amount of debit and credit turnover at the end of reporting period as well as the accumulated balance by main account at the end of the reporting period.

The format of the report uses the language selected as user preference in user options of Dynamics 365 Finance.

> [!NOTE]
> Use of the [One voucher](https://docs.microsoft.com/en-us/dynamics365/finance/general-ledger/one-voucher) functionality introduces a limitation on reporting of counterpart number and name for some scenarios. We recommend that you set the **Allow multiple transactions within one voucher** parameter on the **General ledger parameters** page to **No** in your legal entity to get counterpart number and name properly defined in **General ledger statement by main account** report.

## Prepare your environment to generate General ledger statement by main account report

To start to work with the **General ledger statement by main account** report, complete the following steps:

1. [Import Electronic reporting configurations.](#import)
2. [Select the Electronic reporting configuration in General ledger parameters.](#gl-param)
3. [Enable features in Feature management.](#features)

### <a name="import"></a> Import Electronic reporting configurations

Before you can generate a **General ledger statement by main account** report, you must import the latest versions of the following Electronic reporting (ER) configurations.

| ER configuration name       | Type          | Description |
|-----------------------------|---------------|--------------------|
| **Standard Audit File (SAF-T)**| **Model**         | **The common data model for different audit reports.**|
| SAF-T General model mapping | Model mapping |  The model mapping that provides general data source mapping. |
| General ledger statement by main account (Excel)  | Format        |  General ledger statement by main account in Microsoft Excel format. |

For more information about how to download ER configurations, see [Download ER configurations from the Global repository](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

Import the most recent versions of the configurations. The version description usually includes the number of the Microsoft Knowledge Base (KB) article that explains the changes that were introduced in the configuration version. Use *Issue search* section of [LCS](https://lcs.dynamics.com/v2) portal to find and read information about specific version of ER configuration.

> [!IMPORTANT]
> After all the ER configurations from the previous table are imported, set the **Default for model mapping** option to **Yes** for the **SAF-T General model mapping** configuration.

### <a name="gl-param"></a> Select the Electronic reporting configuration in General ledger parameters

1. Go to **General ledger** \> **Setup** \> **General ledger parameters**.
2. On the **Electronic reporting** FastTab of the **Ledger** tab, in the **General ledger statement by main account** field, select the **General ledger statement by main account (Excel)** format.

### <a name="features"></a> Enable features in Feature management

To optimize timing and memory consumption of the report generation, we recommend enabling features in Feature management.

1.	Go to **Feature management**, and select the **All** tab.
2.	In the feature list, find and select the following features:
  -	**Optimization of query data source creation time during execution of ER reports**
  -	**Optimize datasets memory consumption at ER reports runtime**
3.	Select **Enable now**.

## Generate General ledger statement by main account report

To generate the **General ledger statement by main account** report, go to **General ledger** \> **Inquiries and reports** \> **Ledger reports** \> **General ledger statement by main account**.

The following table describes the fields in the report dialog box.

| **Parameter** | **Description** |
| --- | --- |
| **From date** <br> **To date** | Select dates in **From date** and **To date** to specify interval to generate the report for. You can select dates within one fiscal year. |
| **Currency** | Select **Accounting currency** to report amounts in **Debit** , **Credit** and **Accumulated balance** columns of the report in accounting currency.<br> Select **Reporting currency** to report amounts in **Debit** , **Credit** and **Accumulated balance** columns of the report in reporting currency. |
| **Main financial dimension set** | Select the standard financial dimension set including *Main account* which will be used by the report to calculate opening balance by main accounts at the beginning of the reporting period. For more information about Financial dimension set, see [Financial dimension sets](https://docs.microsoft.com/en-us/dynamics365/finance/general-ledger/financial-dimension-sets). |
| **Group by main account** | Mark this checkbox to report general ledger account entries grouped by main account. When the checkbox is marked, **Ledger account** column will be hidden and amounts of general ledger account entries reported for each main account will be represented as aggregated amounts by **Transaction posting date** and **Transaction number** columns. |
| **Include reversed** | Mark this checkbox if reversed transaction must be reported. |
| **Posting layer(s)** | Select one or more posting layers, transactions with which must be included in report. When no posting layer are selected for report, all the posting layers will be reported. |
| **Sales tax specification** | Mark this checkbox to include information about sales tax codes and amount per general ledger account entry. This option is available when **Group by main account** option of the report is NOT used. |
| **Settlement period** | Select one settlement period to filter sales tax transactions in the report or leave the field empty. When no settlement period is selected for the report, sales tax transaction from all the settlement periods will be included in the report. |
| **Split file by main accounts** | Mark this checkbox to split the report data into multiple files by main accounts. |

In addition to the described fields in the report dialog box, you can use **Records to include** to filter data in the report by one or multiple main accounts.

Use **Run in the background** FastTab of the report dialog box to specify parameters of batch job and run the report in batch. When an electronic report is generated in batch, you can find related batch information and generated output file as au attachment in **Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**. For more information about how to configure a destination for each ER format configuration and its output component, see [Electronic reporting (ER) destinations](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations).

## Generation of General ledger statement by main account report for big volume of data

The maximum reporting period for **General ledger statement by main account** report is one fiscal year.

When you generate **General ledger statement by main account** report for a reporting period containing more than one million general journal account entries, we recommend using **Split file by main accounts** option of the report. If you run the report generation without **Split file by main accounts** option and number of general journal account entries in the reporting period is more then one million, the output file will not be generated with the following message: *File cannot be generated. Number of lines in the report data set exceeds max number of lines on one sheet in Excel file. Use options of the report to reduce the data in the report or \”Split file by main accounts\” parameter.*

When you generate **General ledger statement by main account** report using **Split file by main accounts** option and the number of general journal account entries for a main account is more then one million in the reporting period, one million of general journal account entries will be reported on the first sheet of the Excel output file and the other general journal account entries will be reported on the second sheet of the same Excel output file. The number of general journal account entries that can be reported on the second sheet of Excel output file is also limited to one million general journal account entries.
