---
# required metadata

title: Cash position inquiry
description: This topic provides information about how to determine the corresponding cash positions for financial dimension sets that contain self-balancing dimensions.
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
ms.author: v-alpavk
ms.search.validFrom: 2019-10-24
ms.dyn365.ops.version: 10.0.13

---

# Trial balance with transactional detail

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes the default reports for trial balances. It also describes the building blocks that are associated with these reports and how you can modify the reports to fit your business requirements.

Use the **Trial balance with transactional detail** report to display the details about each transaction for ledger accounts. The report information includes the following items: 

- Opening balances
- Debits and credits 
- The resulting balances for a date range of 31 days or less

For transactions, the report information includes the following: 

- Transaction date
- Voucher number
- Account number
- Document number
- Ledger dimension
- Ledger dimension name
- Transaction description
- Debits or credits
- Arunning balance for the year-to-date based on the current fiscal year

You can use this trial balance to identify errors for account balances. All accounts that have debit balances should equal all accounts that have credit balances. The report includes information from the general journal accounting entries.

The data can run by

- Posted transactions
- Pending transactions (which includes all transactions that are not posted), or 
- All transactions 

If the transaction includes the financial dimensions, the report displays that information under a ledger account. If dimensions aren’t included with transactions, information for financial dimensions will be grouped at the top of the page. 
Currently, the report is exported directly to excel. 

## Transaction information on the report
Based on the type of transaction, such as an Advanced ledger entry (ALE) or purchase order, additional information appears on the report.

<table  border="1" cellspacing="0" cellpadding="0" > 
<tbody>
<tr>
 <td  valign="top" ><p>Transaction type</p></td>
 <td  valign="top" ><p>Additional document information</p></td>
 <td  valign="top" ><p>Additional description information</p></td>
 </tr>

 <tr>
 <td  valign="top" ><p>· Advanced ledger entry (ALE) voucher</p>

<p>· Allocation rule</p>

<p>· General journal transfer</p>

<p>· Journal</p></td>
 <td  valign="top" ><p>ALE number OR General journal number</p></td>
 <td  valign="top" ><p>Line item description</p></td>
 </tr>

 <tr>
 <td  valign="top" ><p> </p></td>
 <td  valign="top" ><p>No data</p></td>
 <td  valign="top" ><p>ALE or general journal header description</p></td>
 </tr>

 <tr>
 <td  valign="top" ><p>· Invoice voucher</p>

<p>· Credit note voucher</p></td>
 <td  valign="top" ><p>Invoice number</p></td>
 <td  valign="top" ><p>Vendor number – Vendor name</p></td>
 </tr>

 <tr>
 <td  valign="top" ><p> </p></td>
 <td  valign="top" ><p>Invoice date</p></td>
 <td  valign="top" ><p>Line item description</p></td>
 </tr>

 <tr>
 <td  valign="top" ><p> </p></td>
 <td  valign="top" ><p>No data</p></td>
 <td  valign="top" ><p>PO number and/or PA number</p></td>
 </tr>

 <tr>
 <td  valign="top" ><p>AP payment voucher</p></td>
 <td  valign="top" ><p>Check number OR EFT number</p></td>
 <td  valign="top" ><p>Vendor number – Vendor name for the 'pay to' or invoice account</p></td>
 </tr>

 <tr>
 <td  valign="top" ><p> </p></td>
 <td  valign="top" ><p>Check date OR EFT date OR Settlement date</p></td>
 <td  valign="top" ><p>Vendor number – Vendor name for the original order account</p></td>
 </tr>

 <tr>
 <td  valign="top" ><p>· Free text credit note</p>

<p>· Free text invoice voucher</p></td>
 <td  valign="top" ><p>Free text invoice number</p></td>
 <td  valign="top" ><p>Customer number – Customer name</p></td>
 </tr>

 <tr>
 <td  valign="top" ><p> </p></td>
 <td  valign="top" ><p>Billing code</p></td>
 <td  valign="top" ><p>Free text invoice line item description</p>

<p>(<strong>Free text invoices</strong> form, <strong>Invoice lines</strong> FastTab, <strong>Description</strong> field)</p></td>
 </tr>

 <tr>
 <td  valign="top" ><p>AR payment voucher</p></td>
 <td  valign="top" ><p>Journal batch number</p>

<p>(<strong>Payment journal</strong> form, <strong>Overview</strong> tab, <strong>Journal batch number</strong> field)</p></td>
 <td  valign="top" ><p>Customer number – customer name</p>

<p>(<strong>Journal voucher</strong> form, <strong>Overview</strong> tab; <strong>Account</strong> and <strong>Account name</strong> fields)</p></td>
 </tr>

 <tr>
 <td  valign="top" ><p> </p></td>
 <td  valign="top" ><p>Payment reference</p></td>
 <td  valign="top" ><p>Line description</p>

<p>(<strong>Journal voucher</strong> form, <strong>Overview</strong> tab, <strong>Description</strong> field)</p></td>
 </tr>

 <tr>
 <td  valign="top" ><p>Budget register entries</p></td>
 <td  valign="top" ><p>Budget register entry number</p></td>
 <td  valign="top" ><p>Budget register entry description</p></td>
 </tr>

 <tr>
 <td  valign="top" ><p> </p></td>
 <td  valign="top" ><p>Budget code</p></td>
 <td  valign="top" ><p>Reason code – Budget register entry header description</p>

<p>(<strong>Budget register entry</strong> form, <strong>Budget entry</strong> form, <strong>Budget account entry details</strong> FastTab, <strong>Comment</strong> field)</p></td>
 </tr>

 <tr>
 <td  valign="top" ><p>· Purchase order confirmation</p>

<p>· Purchase order confirmation voucher</p></td>
 <td  valign="top" ><p>Purchase order number</p></td>
 <td  valign="top" ><p>Line item description</p>

<p>(<strong>Purchase order</strong> form, <strong>Line details</strong> FastTab, <strong>Text</strong> field)</p></td>
 </tr>

 <tr>
 <td  valign="top" ><p> </p></td>
 <td  valign="top" ><p>Purchase order line number</p></td>
 <td  valign="top" ><p>Procurement category</p></td>
 </tr>

 <tr>
 <td  valign="top" ><p>Purchase requisition voucher</p></td>
 <td  valign="top" ><p>Purchase requisition number</p></td>
 <td  valign="top" ><p>Purchase requisition name</p></td>
 </tr>

 <tr>
 <td  valign="top" ><p> </p></td>
 <td  valign="top" ><p>Purchase requisition line number</p></td>
 <td  valign="top" ><p>Purchase requisition line description</p>

<p>(<strong>Purchase requisition</strong> form, <strong>Purchase requisition lines</strong> FastTab, <strong>Product name</strong> field)</p></td>
 </tr>

 <tr>
 <td  valign="top" ><p>· Project invoice voucher</p>

<p>· Project invoice</p></td>
 <td  valign="top" ><p>Project invoice number</p></td>
 <td  valign="top" ><p>Invoice account – Account name</p></td>
 </tr>

 <tr>
 <td  valign="top" ><p> </p></td>
 <td  valign="top" ><p>Funding source</p></td>
 <td  valign="top" ><p>Project ID – Project name</p></td>
 </tr>

 </tbody>
</table>
