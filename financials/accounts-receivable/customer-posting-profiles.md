---
# required metadata

title: Customer posting profiles
description: Customer posting profiles control the posting of customer transactions to the general ledger.
author: twheeloc
manager: AnnBe
ms date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: CustPosting
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 24651
ms.assetid: cb82245e-8c02-429c-b36e-8db0e3e6f7e5
ms.search.region: Global
# ms.search.industry: 
ms.author: mfalkner
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Customer posting profiles

Customer posting profiles control the posting of customer transactions to the general ledger.

Customer posting profiles
-------------------------

Customer posting profiles enable you to assign general ledger accounts and document settings to all customers, a group of customers or a single customer. These settings will be used when you create sales orders, free text invoices, cash payments, collection letters, and interest notes. For some transactions, you can select a posting profile that differs from and takes precedence over the posting profiles that are set up for transactions in this page. 

The default posting profile is defined in the Ledger and Sales Tax fasttab on the Accounts receivable parameters page. The default posting profile is then included automatically on the header of new documents where you can change it to a different posting profile if needed.

You can also associate posting definitions with transaction posting types in the Transaction posting definitions page. Posting definitions control the posting of customer transactions to the general ledger instead of posting profiles.

## Creating a posting profile
Specify the ledger accounts that are used in the posting of transactions that use the selected posting profile. Select an account code and, whenever possible, an account or group number for the selected posting profile. In the posting process, the most appropriate posting profile for each transaction is located by searching for the most specific account code, account number, or group and number combination in the following priority:

| **Account code** field value | **Account/Group number** field value            | Search priority |
|------------------------------|-------------------------------------------------|-----------------|
| **Table**                    | Specific customer account                       | 1               |
| **Group**                    | Customer group that is assigned to the customer | 2               |
| **All**                      | Blank                                           | 3               |

If you want all customer transactions to have the same posting profile, set up only one posting profile with All in the Account code field. Specify the following values to set up your posting profile:

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
<td>Enter a code for the posting profile. For example, you could create two posting profiles to obtain one account for customer balances in the national currency and another for customer balances in a foreign currency. You could call one account National and the other Foreign.</td>
</tr>
<tr class="even">
<td><strong>Description</strong></td>
<td>Enter a description of the posting profile. This is only used to better identify the posting profile when you view it in this page.</td>
</tr>
<tr class="odd">
<td><strong>Account code</strong></td>
<td>Specify whether the posting profile applies to a single customer, a group of customers, or all customers:
<ul>
<li><strong>Table</strong> – The posting profile applies to a single customer. Select the customer account in the Account/Group number field.</li>
<li><strong>Group</strong> – The posting profile applies to a customer group. Select the customer group in the Account/Group number field.</li>
<li><strong>All</strong> – The posting profile applies to all customers. Leave the Account/Group number field blank.</li>
</ul></td>
</tr>
<tr class="even">
<td><strong>Account/Group number</strong></td>
<td>If Table is selected in the Account code field, select the account number of the customer who is associated with the posting profile. If Group is selected, select the customer group. If All is selected, leave this field blank.</td>
</tr>
<tr class="odd">
<td><strong>Summary account</strong></td>
<td>Select the ledger account that will be used as the customer summary account for the customers who are associated with the posting profile.</td>
</tr>
<tr class="even">
<td><strong>Settle account</strong></td>
<td>Select the liquidity ledger account that is used for cash flow forecasts. This field will only appear if cash flow forecasts are enabled.</td>
</tr>
<tr class="odd">
<td><strong>Sales tax prepayments</strong></td>
<td>Select the account for sales tax for payments that are received in advance.
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="https://i-technet.sec.s-msft.com/areas/global/content/clear.gif" title="Note" alt="Note" id="alert_note" class="cl_IC101471" /><strong>Note</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Use the Accounts receivable parameters page to specify the posting profile to use when a payment is marked as a prepayment.</td>
</tr>
</tbody>
</table>
</div></td>
</tr>
<tr class="even">
<td><strong>Liabilities for discount account</strong></td>
<td>Select the ledger account for liabilities of discount.</td>
</tr>
<tr class="odd">
<td><strong>Collection letter sequence</strong></td>
<td>Select the identifier of the collection letter sequence to use for customers to whom the posting profile is assigned.</td>
</tr>
<tr class="even">
<td><strong>Interest code</strong></td>
<td>Select the interest code to use for the calculation of interest for customers to whom the posting profile is assigned.</td>
</tr>
</tbody>
</table>

### 

### **Table restrictions**

For transactions that have the selected posting profile, specify whether transactions will be settled automatically, interest will be calculated, and collection letters will be issued. You can also select the account that is used when transactions that have the selected posting profile are closed.

Specify the following values to set up your posting profile:

| Field                 | Description                                                                                                                                                                                                                                        |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Settlement**        | Select this toggle to enable automatic settlement of transactions that have this posting profile. If this toggle is cleared, you must manually settle transactions by using the Settle open transactions page or the Enter customer payments page. |
| **Interest**          | Select this toggle if interest should be calculated on outstanding balances for customer accounts that use this profile. If this toggle is cleared, interest will not be calculated for these customers.                                           |
| **Collection letter** | Select this toggle if collection letters should be generated for customer accounts that use this profile. If this toggle is cleared, collection letters will not be generated for these customers.                                                 |
| **Close**             | Select a posting profile to change to when transactions that have this posting profile are closed. A transaction is regarded as closed when it has been settled in full.                                                                           |



