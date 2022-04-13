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
ms.author: v-kiarnd
ms.search.validFrom: 2019-10-24
ms.dyn365.ops.version: 10.0.13

---

# Trial balance with transactional detail report

[!include [banner](../includes/banner.md)]

This topic describes the default report for trial balances. The **Trial balance with transactional detail** report generates a trial balance and includes the detailed transactions that were posted to each ledger account. By selecting to include specific unposted transactions, you can use the report to generate a provisional trial balance together with detailed transactions.

Electronic reporting (ER) was used to create the **Trial balance with transactional detail** report. Therefore, an organization can either use the version of the report that is included in the Global repository or create their own version of the report.

## ER setup

If you haven't configured the Global repository, you must configure it for the updated version of the **Trial balance with transactional detail** report. 
For more information, see [Configure the Global repository](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

1. Go to **Electronic reporting**.
2. Select **Repositories** for the **Microsoft** provider.
3. Select **Open**.
4. Scroll down, or add a filter for the configuration name that begins with **Trial**.
5. Select **Trial balance with transactional detail (excel)**, and then select **Import**. 

You can now run the updated report, and the results will be available in Microsoft Excel.

## Feature management

The **Trial balance with transactional detail** report is automatically enabled when the **Generate the trial balance with transactional detail** report feature is enabled in **Feature management**. To include unposted transactions on the report, enable the **Generate trial balance with pending type transactions** feature. To view summary data from the general journal account entry, enable the **Amount details from the General journal account entry are displayed on the Trial balance with transactional detail report** feature.

## Report options

When you generate the report, you can include the following detailed general ledger transactions on it:

- Posted transactions
- Pending transactions
- All transactions

Inclusion of posted transactions on the report can cause a large set of data.

All detailed general ledger transactions in the report's date range will be printed on the report. Therefore, the report can be generated only for 31 days or less.

If you include pending transactions on the report, you must select the type of unposted transaction types to include. Only the unposted transaction types that are listed in the report parameters can be included on the provisional report. Here are some of the unposted transaction types:

- Advanced ledger entries
- Allocation journals
- Budget journals
- Budget register entries
- Customer payment journals
- Daily journals
- Free text invoices
- Project invoices
- Purchase orders
- Purchase requisitions
- Vendor invoices
- Vendor invoice journals
- Vendor invoice register journals

Unposted intercompany transactions that are entered in the general journal (daily journal) or vendor invoice journals aren't shown on the report. The appropriate "due to" and "due from" entries can't be generated before posting. If those account entries aren't generated, the report will show an unbalanced accounting entry, because the report includes the account entries only for the active legal entity.

The **Primary financial dimension set** option defines how transactions are grouped together for combinations of main accounts and financial dimensions. For example, if you select a dimension set that includes the **Main account** and **Department** dimensions, the report will show the opening balance, detailed transactions, and the ending balance for each combination of a main account value and a department value. Regardless of the financial dimension set that is selected, the full ledger account is shown in the **Ledger dimension** account column.

Use the **From date** and **To date** fields to define a date range. This date range must be 31 days or less. This restriction is in place because of the large number of transactions that are included on a detailed transaction report.

In the **Posting layer** field, select the posting layer that you want to view the detailed transactions for. Only one posting layer can be selected.

Use the **Include opening transaction amount in detail** option to add the details of the opening balance to the report.

Use the **Closing transaction** option to include closing transactions on the report. If the **Create closing transactions during transfer** General ledger parameter is set to **Yes**, closing transactions are created when a year-end close is run. Closing transactions are posted on the last day of the fiscal year and are shown only when the last day of the fiscal year is included in the date range.

## Report details

The **Trial balance with transactional detail** report includes the following information in the rows:

- Opening balance
- Debit or credit amount
- Ending balance

For transaction details, the report includes the following information in the columns:

- Date
- Voucher
- Document
- Account number
- Description
- Ledger dimension account
- Ledger dimension name
- Debit
- Credit
- Balance

## Transaction information on the report

The information that is shown in the **Document** and **Description** columns varies, depending on the type of transaction. The following table provides some examples of information that is shown in those columns.

| Transaction type | Document | Description |
|------------------|----------|-------------|
| General journal – Ledger accounts only | Journal batch number | Ledger account or Offset ledger account |
| General journal – Vendor/Ledger account | **Pay number**: XXX **Pay date**: xx/xx/xxxx | Main account name |
| Free text invoice or Free text credit memo | **Posting type**: Customer balance or **Posting type**: Customer revenue | Journal number: XXXXXX Line description |
| Vendor invoice | **Posting type:** Vendor balance or **Pay number**: XXX **Pay date**: xx/xx/xxxx | Vendor name |
| Vendor payment journal or Customer payment journal | **Pay number**: XXX **Pay date**: xx/xx/xxxx | Vendor name or Customer name |

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
