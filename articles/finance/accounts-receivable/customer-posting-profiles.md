---
# required metadata

title: Customer posting profiles
description: This article describes customer posting profiles, which control the posting of customer transactions to the general ledger.
author: JodiChristiansen
ms.date: 11/21/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CustPosting, CustVendExternalItem
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: cb82245e-8c02-429c-b36e-8db0e3e6f7e5
ms.search.region: Global
# ms.search.industry: 
ms.author: abruer
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Customer posting profiles

[!include [banner](../includes/banner.md)]

This article describes customer posting profiles, which control the posting of customer transactions to the general ledger.

## Customer posting profiles

Customer posting profiles let you assign general ledger accounts and document settings to all customers, a group of customers, or a single customer. These settings will be used when you create sales orders invoices, free text invoices, project invoices, payment journals, collection letters, and interest notes. 

The default posting profile is defined on the **Ledger and Sales Tax** tab of the **Accounts receivable parameters** page. It's then automatically included on the header of new documents. You can change it there if a different posting profile is required. 

Organizations that accept prepayments from customers often configure a second posting profile for prepayments and link it in the parameters as the default posting profile for prepayments. For more information, see [Customer prepayments](customer-prepayments.md).

You can also associate posting definitions with transaction posting types on the **Transaction posting definitions** page. Posting definitions are used instead of posting profiles to control the posting of customer transactions to the general ledger. For more information, see [Posting definitions](../general-ledger/posting-definitions.md).

## Creating a posting profile
Specify the ledger accounts that are used in the posting of transactions that use the selected posting profile. Select an account code and, whenever possible, an account or group number for the selected posting profile. In the posting process, the most appropriate posting profile for each transaction is located by searching for the most specific account code, account number, or group and number combination in the following priority:

| Account code field value | Account/Group number field value                | Search priority |
|--------------------------|-------------------------------------------------|-----------------|
| Table                    | Specific customer account                       | 1               |
| Group                    | Customer group that is assigned to the customer | 2               |
| All                      | Blank                                           | 3               |

If you want all customer transactions to have the same posting profile, set up only one posting profile, where **All** is entered in the **Account code** field. Specify the following values to set up your posting profile.

<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Posting profile</strong></td>
<td>Enter a code for the posting profile. For example, you could create two posting profiles to obtain one account for customer balances in the national currency and another for customer balances in a foreign currency. You could call one account National and the other Foreign.</td>
</tr>
<tr>
<td><strong>Description</strong></td>
<td>Enter a description of the posting profile. This is only used to better identify the posting profile when you view it in this page.</td>
</tr>
<tr>
<td><strong>Account code</strong></td>
<td>Specify whether the posting profile applies to a single customer, a group of customers, or all customers:
<ul>
<li><b>Table</b> – The posting profile applies to a single customer. Select the customer account in the <b>Account/Group number</b> field.</li>
<li><b>Group</b> – The posting profile applies to a customer group. Select the customer group in the <b>Account/Group number</b> field.</li>
<li><b>All</b> – The posting profile applies to all customers. Leave the <b>Account/Group number</b> field blank.</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Account/Group number</strong></td>
<td>If <b>Table</b> is selected in the <b>Account code</b> field, select the account number of the customer who is associated with the posting profile. If <b>Group</b> is selected, select the customer group. If <b>All</b> is selected, leave this field blank.</td>
</tr>
<tr>
<td><strong>Summary account</strong></td>
<td>Select the main account that will be used as the Accounts receivable trade account for the customers who are associated with the posting profile. This account is the account for the <b>Customer balance</b> posting type.</td>
</tr>
<tr>
<td><strong>Liquidity account for payments</strong></td>
<td>Select the <strong>Liquidity ledger account</strong> that is used for cash flow forecasts. This field will appear only if cash flow forecasts are enabled.</td>
</tr>
<tr>
<td><strong>Sales tax prepayments</strong></td>
<td><p>Select the account for sales tax for payments that are received in advance.</p>
<p><strong>Note:</strong> Use the <b>Accounts receivable parameters</b> page to specify the posting profile that is used when a payment is marked as a prepayment.</p>
</td>
</tr>
<tr>
<td><strong>Liabilities for discount account</strong></td>
<td>Select the ledger account for liabilities of discount.</td>
</tr>
<tr>
<td><strong>Collection letter sequence</strong></td>
<td>Select the identifier of the collection letter sequence to use for customers to whom the posting profile is assigned.</td>
</tr>
<tr>
<td><strong>Interest code</strong></td>
<td>Select the interest code to use for the calculation of interest for customers to whom the posting profile is assigned.</td>
</tr>
</tbody>
</table>

## Posting examples

The following table shows examples of the default posting types with sample main accounts and descriptions. The **Debit/Credit** column indicates if the transaction typically Debits or Credits or in some cases can post either. The **Clearing account** column indicates of the posting type is a clearing account. This means the amount posted in this account is automatically reversed when a later transaction is posted. 

| Posting type | Main account example | Main account name example | Account type | Debit/Credit | Clearing account | Description |
|--------------|----------------------|---------------------------|--------------|--------------|------------------|-------------|
| Customer balance | 130100 | Accounts Receivable Trade | Asset | Both | No | Specify the account in the **Summary account** field.|
| None | 110110 | Bank account | Asset | Both | No | Specify the main account in the **Liquidity account for payments** field. This account isn't used for posting. It's used only for cash flow forecasting. |
| Sales tax prepayments | 202900 | Sales tax clearing | Liability | Both | Yes | Select the account for sales tax for payments that are received in advance. |
| Liabilities for discount account | 250600 | Deferred Revenue and Discounts | Liability | Both | Yes | Select the ledger account for liabilities of discounts.|     

### Table restrictions

For transactions that have the selected posting profile, specify whether transactions will be settled automatically, interest will be calculated, and collection letters will be issued. You can also select the account that is used when transactions that have the selected posting profile are closed.

Specify the following values to set up your posting profile:

| Field                 | Description                                           |
|-----------------------|-------------------------------------------------------|
| Settlement        | Select this toggle to enable automatic settlement of transactions that have this posting profile. If this toggle is cleared, you must manually settle transactions by using the **Settle open transactions** page or the **Enter customer payments** page. |
| Interest          | Select this toggle if interest should be calculated on outstanding balances for customer accounts that use this profile. If this toggle is cleared, interest will not be calculated for these customers.                                           |
| Collection letter | Select this toggle if collection letters should be generated for customer accounts that use this profile. If this toggle is cleared, collection letters will not be generated for these customers.                                                 |
| Close             | Select a posting profile to change to when transactions that have this posting profile are closed. A transaction is regarded as closed when it has been settled in full.             |



For more information, see [Customer payment overview](../cash-bank-management/tasks/customer-payment-overview.md).



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
