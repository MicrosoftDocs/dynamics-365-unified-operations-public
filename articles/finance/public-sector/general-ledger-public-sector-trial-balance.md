---
# required metadata

title: Trial balance with transactional detail report
description: This topic describes the default report for trial balances. It also describes the building blocks that are associated with this report and how you can modify the report to fit your business requirements.
author: v-kiarnd
manager: AnnBe
ms.date: 10/24/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations, Core 
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

This topic describes the default report for trial balances. It also describes the building blocks that are associated with this report and how you can modify the report to fit your business requirements.

You can use the **Trial balance with transactional detail** report to show the details of each transaction for ledger accounts. The report includes the following information: 

- Opening balances
- Debits and credits 
- The resulting balances for a date range of 31 days or less

For transactions, the report includes the following information: 

- Transaction date
- Voucher number
- Account number
- Document number
- Ledger dimension
- Ledger dimension name
- Transaction description
- Debits or credits
- A running balance for the year to date, based on the current fiscal year

You can use the trial balance to identify errors for account balances. All accounts that have debit balances should equal all accounts that have credit balances. The report includes information from the general journal accounting entries.

You can filter the data by any of the following items:

- Posted transactions
- Pending transactions (These transactions include all transactions that aren't posted.) 
- All transactions 

If the transactions include financial dimensions, the report shows that information under a ledger account. Otherwise, information for financial dimensions is grouped at the top of the page. 

Currently, the report is exported directly to Microsoft Excel. 

## Transaction information on the report

Depending on the type of transaction, such as an advanced ledger entry (ALE) or purchase order, the following additional information appears on the report.

<table> 
<thead>
<tr>
<th>Transaction type</th>
<th>Additional document information</th>
<th>Additional description information</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<ul>
<li>ALE voucher</li>
<li>Allocation rule</li>
<li>General journal transfer</li>
<li>Journal</li>
</ul>
</td>
<td>ALE number or general journal number</td>
<td>Line item description</td>
</tr>
<tr>
<td></td>
<td>No data</td>
<td>ALE or general journal header description</td>
</tr>
<tr>
<td>
<ul>
<li>Invoice voucher</li>
<li>Credit note voucher</li>
</ul>
</td>
<td>Invoice number</td>
<td>Vendor number and Vendor name</td>
</tr>
<tr>
<td></td>
<td>Invoice date</td>
<td>Line item description</td>
</tr>
<tr>
<td></td>
<td>No data</td>
<td>Purchase order number and/or PA number</td>
</tr>
<tr>
<td>Accounts payable (AP) payment voucher</td>
<td>Check number or electronic funds transfer (EFT) number</td>
<td>Vendor number – Vendor name for the "pay to" or invoice account</td>
</tr>
<tr>
<td></td>
<td>Check date, EFT date, or settlement date</td>
<td>Vendor number and Vendor name for the original order account</td>
</tr>
<tr>
<td>
<ul>
<li>Free text credit note</li>
<li>Free text invoice voucher</li>
</ul>
</td>
<td>Free text invoice number</td>
<td>Customer number and Customer name</td>
</tr>
<tr>
<td></td>
<td>Billing code</td>
<td>Free text invoice line item description<br>
(<strong>Description</strong> field on the <strong>Invoice lines</strong> FastTab of the <strong>Free text invoices</strong> page)</td>
</tr>
<tr>
<td>Accounts receivable (AR) payment voucher</td>
<td>Journal batch number<br>
(<strong>Journal batch number</strong> field on the <strong>Overview</strong> tab of the <strong>Payment journal</strong> page)</td>
<td>Customer number – Customer name<br>
(<strong>Account</strong> and <strong>Account name</strong> fields on the <strong>Overview</strong> tab of the <strong>Journal voucher</strong> page)</td>
</tr>
<tr>
<td></td>
<td>Payment reference</td>
<td>Line description<br>
(<strong>Description</strong> field on the <strong>Overview</strong> tab of the <strong>Journal voucher</strong> page)</td>
</tr>
<tr>
<td>Budget register entries</td>
<td>Budget register entry number</td>
<td>Budget register entry description</td>
</tr>
<tr>
<td></td>
<td>Budget code</td>
<td>Reason code – Budget register entry header description<br>
(<strong>Comment</strong> field on the <strong>Budget account entry details</strong> FastTab on the <strong>Budget entry</strong> page or the <strong>Budget register entry</strong> page)</td>
</tr>
<tr>
<td>
<ul>
<li>Purchase order confirmation</li>
<li>Purchase order confirmation voucher</li>
</ul>
</td>
<td>Purchase order number</td>
<td>Line item description<br>
(<strong>Text</strong> field on the <strong>Line details</strong> FastTab of the <strong>Purchase order</strong> page)</td>
</tr>
<tr>
<td></td>
<td>Purchase order line number</td>
<td>Procurement category</td>
</tr>
<tr>
<td>Purchase requisition voucher</td>
<td>Purchase requisition number</td>
<td>Purchase requisition name</td>
</tr>
<tr>
<td></td>
<td>Purchase requisition line number</td>
<td>Purchase requisition line description<br>
(<strong>Product name</strong> field on the <strong>Purchase requisition lines</strong> FastTab of the <strong>Purchase requisition</strong> page)</td>
</tr>
<tr>
<td>
<ul>
<li>Project invoice voucher</li>
<li>Project invoice</li>
</ul>
</td>
<td>Project invoice number</td>
<td>Invoice account and Account name</td>
</tr>
<tr>
<td></td>
<td>Funding source</td>
<td>Project ID and Project name</td>
</tr>
</tbody>
</table>
