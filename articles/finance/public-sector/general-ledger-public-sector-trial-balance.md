---
# required metadata

title: Trial balance with transactional detail report
description: This topic describes the default report for trial balances. It also describes the building blocks that are associated with this report and how you can modify the report to fit your business requirements.
author: v-kiarnd
ms.date: 10/24/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
ms.search.industry: public sector
ms.author:  v-kiarnd
ms.search.validFrom: 2019-10-24
ms.dyn365.ops.version: 10.0.13

---

# Trial balance with transactional detail report

[!include [banner](../includes/banner.md)]

This topic describes the default report for trial balances. The **Trial balance with transactional detail** generates a trial balance, including the detailed transactions that posted to each ledger account. The report can also be used to generate a provisional trial balance with detailed transactions by choosing to include specific unposted transactions. 

## Set up

The **Trial balance with transactional detail** report was created using **Electronic reporting**, allowing for an organization to use the report included in the global repository or create their own version of the report.


## Electronic Reporting Setup 
If you don't have a global repository configured, you will need to configure one for the updated version of the Trial balance with transactional detail report. 
For more information, see [Configure the Global repository](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md) 
1.	Go to **Electronic reporting**. 
2.	Click **Repositories** of the Microsoft provider. 
3.	Click **Open**. 
4.	Scroll down or add a filter for configuration name begins with **Trial**. 
5.	Select **Trial balance with transactional detail (excel)** and click **Import**.  
 
You can now run the updated report and the results will be available in excel. 

## Feature management
The **Trial balance with transactional detail** report is automatically enabled with feature **Generate the trial balance with transactional detail** report in **Feature management**. Enable the feature **Generate trial balance with pending type transactions** in **Feature management** to include unposted transactions on the report. To view summary data from the general journal account entry, enable the feature **Amount details from the General journal account entry are displayed on the Trial balance with transactional detail report**.

## Report options
When generating the report, you can choose to include the following detailed general ledger transactions on the report: 
•	Posted transactions 
•	Pending transactions
•	All transactions 
 
Including posted transactions on this report can result in a large set of data.  All detailed general ledger transactions within the report date range will print on the report. As a result, the report can only be generated for 31 days or less. 

When including **Pending transactions** on the report, you must select the type of unposted transaction types to include. Only unposted transaction types listed on the report parameters can be included on the provisional report. The unposted transaction types include: 
•	Advanced ledger entries 
•	Allocation journals 
•	Budget journals 
•	Budget register entries 
•	Customer payment journals 
•	Daily journals 
•	Free text invoices 
•	Project invoices 
•	Purchase orders 
•	Purchase requisitions 
•	Vendor invoices 
•	Vendor invoice journals 
•	Vendor invoice register journals 

Unposted, intercompany transactions entered in the general journal (daily journal) or vendor invoice journals are not shown on the report. The appropriate due to/due from entries cannot be generated prior to posting. Without those account entries, the report would show an unbalanced accounting entry because this report only includes the account entries for the active legal entity.  


The **Primary financial dimension set** option defines how to group transactions together for combinations of main accounts and financial dimensions.  For example, if you select a dimension set that includes the **Main account** and **Department** dimension, the report will show the opening balance, detailed transactions and ending balance for each combination of main account and department value. Regardless of the financial dimension set selected, the full ledger account is displayed under the **Ledger dimension** account column. 

A date range must be entered that is 31 days or less using the **From date** and **To date**. The restriction is in place due to the large number of transactions included on a detailed transaction report. 

Select the **Posting layer** for which you would like to view the detailed transactions. Only one posting layer can be selected.

The option **Include opening transaction amount in detail** is used to add the detail of the opening balance to the report. 

The option **Closing transaction** is used to include **Closing transactions** on the report. **Closing transactions** are created when running the year-end close if the General ledger parameter **Create closing transactions during transfer** is set to **Yes**. Closing transactions, posted on the last day of the fiscal year, are only shown when the last day of the fiscal year is included in the date range. 

## Report details
The trial balance with transactional detail report includes the following information on the rows: 
•	Opening balance
•	Debit or credit amount
•	Ending balance
 
For transaction detail, the report includes the following information in the columns: 
•	Date
•	Voucher 
•	Document
•	Account number 
•	Description
•	Ledger dimension account
•	Ledger dimension name 
•	Debit
•	Credit
•	Balance

## Transaction information on the report

The information shown in the **Document** and **Description** columns varies depending on the type of transaction. The following table provides some examples of information shown in those columns. 

| Transaction type| Document| Description|
| :------------- |:-------------|:----------------|
|General journal – Ledger accounts only|	Journal batch number|	Ledger account or Offset ledger account|
|General journal – Vendor/Ledger account|	**Pay number**: XXX  **Pay date:** xx/xx/xxxx	|Main account name|
|Free text invoice or Free text credit memo|	**Posting type**: Customer balance or **Posting type** Customer revenue	|Journal number: XXXXXX  Line description|
|Vendor invoice| **Posting type**: Vendor balance or **Pay number**: XXX  **Pay date**: xx/xx/xxxx	|Vendor name|
|Vendor payment journal or Customer payment journal|	**Pay number**: XXX  **Pay date**: xx/xx/xxxx	|Vendor name or Customer name|



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
