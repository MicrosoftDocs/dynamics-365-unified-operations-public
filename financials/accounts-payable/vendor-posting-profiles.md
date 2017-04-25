---
# required metadata

title: Vendor posting profiles
description: Vendor posting profiles control the posting of vendor transactions to the general ledger.
author: twheeloc
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: VendPosting
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 24691
ms.assetid: 18def866-7655-4f0b-b299-eec83098d23a
ms.search.region: Global
# ms.search.industry: 
ms.author: mfalkner
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Vendor posting profiles

[!include[banner](../includes/banner.md)]


Vendor posting profiles control the posting of vendor transactions to the general ledger.

Vendor posting profiles
-----------------------

Vendor posting profiles enable you to assign general ledger accounts and document settings to all vendors, a group of vendors or a single vendor. These settings will be used when you create purchase orders, vendor invoices and cash payments. For some transactions, you can select a posting profile that differs from and takes precedence over the posting profiles that are set up for transactions in this page. The default posting profile is defined in the Ledger and Sales Tax fasttab on the Accounts payable parameters page. The default posting profile is then included automatically on the header of new documents where you can change it to a different posting profile if needed.

You can also associate posting definitions with transaction posting types in the Transaction posting definitions page. Posting definitions control the posting of vendor transactions to the general ledger instead of posting profiles.

## Creating a posting profile
### **Setup**

Specify the ledger accounts that are used in the posting of transactions that use the selected posting profile. Select an account code and, whenever possible, an account or group number for the selected posting profile. In the posting process, the most appropriate posting profile for each transaction is located by searching for the most specific account code, account number, or group and number combination in the following priority:

| **Account code** field value | **Account/Group number** field value        | Search priority |
|------------------------------|---------------------------------------------|-----------------|
| **Table**                    | Specific vendor account                     | 1               |
| **Group**                    | vendor group that is assigned to the vendor | 2               |
| **All**                      | Blank                                       | 3               |

If you want all vendor transactions to have the same posting profile, set up only one posting profile with All in the Account code field. Specify the following values to set up your posting profile:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Posting profile</strong></td>
<td>Enter a code for the posting profile. For example, you could create two posting profiles to obtain one account for vendor balances in the national currency and another for vendor balances in a foreign currency. You could call one account National and the other Foreign.</td>
</tr>
<tr class="even">
<td><strong>Description</strong></td>
<td>Enter a description of the posting profile.</td>
</tr>
<tr class="odd">
<td><strong>Account code</strong></td>
<td>Specify whether the posting profile applies to a specific vendor, a group of vendors, or all vendors:
<ul>
<li><strong>Table</strong> – The posting profile applies to a single vendor. Select the vendor account in the Account/Group number field.</li>
<li><strong>Group</strong> – The posting profile applies to a vendor group. Select the vendor group in the Account/Group number field.</li>
<li><strong>All</strong> – The posting profile applies to all vendors. Leave the Account/Group number field blank.</li>
</ul></td>
</tr>
<tr class="even">
<td><strong>Account/Group number</strong></td>
<td>If Table is selected in the Account code field, select the account number of the vendor that is associated with the posting profile. If Group is selected, select a vendor group. If All is selected, leave this field blank.</td>
</tr>
<tr class="odd">
<td><strong>Summary account</strong></td>
<td>Select the ledger account that will be used as the summary account for the vendors that the posting profile relates to.
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="https://i-technet.sec.s-msft.com/areas/global/content/clear.gif" title="Note" alt="Note" id="alert_note" class="cl_IC101471" /><strong>Note</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>If the Use posting definitions toggle is selected in the General ledger parameters page, the transaction posting definition for vendor invoices is used instead of the summary account.</td>
</tr>
</tbody>
</table>
</div></td>
</tr>
<tr class="even">
<td><strong>Settle account</strong></td>
<td>Select the liquidity ledger account that is used for cash flow forecasts. This fields is only available when cash flow forecasting is enabled.</td>
</tr>
<tr class="odd">
<td><strong>Sales tax prepayments</strong></td>
<td>Select the account for sales tax payments that are received in advance.
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="https://i-technet.sec.s-msft.com/areas/global/content/clear.gif" title="Note" alt="Note" id="alert_note" class="cl_IC101471" /><strong>Note</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>The posting profile that is used when the payment is marked as a prepayment is selected in the Posting profile with prepayment journal voucher field in the Ledger and sales tax area of the Accounts payable parameters page.</td>
</tr>
</tbody>
</table>
</div></td>
</tr>
<tr class="even">
<td><strong>Arrival</strong></td>
<td>Select the ledger account that information about unapproved vendor invoices is posted to. The information is entered in the Invoice register journal. For example, a user enters very basic information about vendor invoices when they are received in the invoice register. When the invoice register is posted, the transactions are posted to the account that is entered here and in the Offset account field. When the invoices are approved, the debt is transferred from the Arrival account to the vendor summary account.</td>
</tr>
<tr class="odd">
<td><strong>Offset account</strong></td>
<td>Select the ledger account that is used for offsetting unapproved vendor invoices that are updated by using the invoice register. The offset account acts as the offset account for transactions that are posted to arrival accounts. Therefore, the account contains vendor purchases that have not yet been approved.</td>
</tr>
</tbody>
</table>
 

### **Table restrictions**

For transactions that have the selected posting profile, specify whether transactions will be settled automatically, interest will be calculated, and collection letters will be issued. You can also select the account that is used when transactions that have the selected posting profile are closed.

Specify the following values to set up your posting profile:

| Field          | Description                                                                                                                                                                                                    |
|----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Settlement** | Select this option to enable automatic settlement of transactions that have this posting profile. If this option is cleared, you must manually settle transactions by using the Settle open transactions page. |
| **Cancel**     | Select this option if you want to be able to cancel transactions that have this posting profile.                                                                                                               |
| **Close**      | Select a posting profile to change to when transactions that have this posting profile are closed. A transaction is regarded as closed when it has been settled in full.                                       |





