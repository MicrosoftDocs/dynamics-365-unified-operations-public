---
title: Storno accounting
description: Storno accounting is the practice of using negative numbers to reverse original journal account entries, including an example.
author: kfend
ms.author: kfend
ms.topic: article
ms.date: 06/20/2017
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Czech Republic, Germany, Hungary, Latvia, Lithuania, Poland, Russia
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Storno accounting

[!include [banner](../../includes/banner.md)]

Storno accounting is the practice of using negative numbers to reverse original journal account entries.

*Storno accounting* is a practice of using negative debit or credit amounts to reverse original journal account entries. Because bookkeepers typically write Storno entries in red ink, this accounting practice is also known as *Red Storno*. Using Storno accounting you can cancel a document with incorrect amounts, however you should always enter the correct document amount after the cancellation.

## Example
A bookkeeper posts an invoice from a vendor for 120 USD. During the payment process, it's discovered that the bookkeeper mistakenly entered 120 USD instead of 102 USD. Now, the bookkeeper needs to create Storno for the original document, and then create the correct invoice for 102 USD. For more information, see [Vendor invoices overview](../../accounts-payable/vendor-invoices-overview.md). The following table shows the general entry for Storno.

| **Document ID** | **Account** | **Debit** | **Credit** | **Comment**                  |
|-----------------|-------------|-----------|------------|------------------------------|
| Invoice0001     | Purch acc   | 120       |            | Original Invoice (incorrect) |
| Invoice0001     | Vendor acc  |           | 120        | Original Invoice (incorrect) |
|                 |             |           |            |                              |
| Storno0001      | Purch acc   | -120     |            | Storno                       |
| Storno0001      | Vendor acc  |           | -120      | Storno                       |
|                 |             |           |            |                              |
| Invoice0002     | Purch acc   | 102       |            | Correct Invoice              |
| Invoice0002     | Vendor acc  |           | 102        | Correct Invoice              |

In this example, the balance statement shows the following.

| Account    | Debit | Credit | Balance |
|------------|-------|--------|---------|
| Purch acc  | 102   | 0      | 102     |
| Vendor acc | 0     | 102    | -102    |

## Differences between Storno and reverse entries
There are two ways in which to correct posting entries – reverse and storno. If you use a reverse entry, a copy of the original general entry is created with reverse debit and credit accounts, and the amounts remain with the same sign. If you use Storno, the system creates a copy of the original general entry, but the amounts are recorded with a negative sign. The following table shows the general entry for Storno.

| **Document ID** | **Account** | **Debit** | **Credit** | **Comment**                  |
|-----------------|-------------|-----------|------------|------------------------------|
| Invoice0001     | Purch acc   | 120       |            | Original Invoice (incorrect) |
| Invoice0001     | Vendor acc  |           | 120        | Original Invoice (incorrect) |
|                 |             |           |            |                              |
| Reverse0001     | Purch acc   |           | 120        | Reverse                      |
| Reverse0001     | Vendor acc  | 120       |            | Reverse                      |
|                 |             |           |            |                              |
| Invoice0002     | Purch acc   | 102       |            | Correct Invoice              |
| Invoice0002     | Vendor acc  |           | 102        | Correct Invoice              |

In this example, the balance statement shows the following.

| Account    | Debit | Credit | Balance |
|------------|-------|--------|---------|
| Purch acc  | 222   | 120    | 102     |
| Vendor acc | 120   | 222    | -102    |

Note that the balances are equal for the reverse and the storno. There is a difference between debit turnover and credit turnover, because the reverse entry makes redundant debit and credit turnover. The reverse entry is used in countries/regions where turnover is rarely use. Other countries/regions use Storno accounting.

## Partial Storno
*Partial Storno* is an accounting practice of using negative debit or credit amounts to reverse part of the original journal account entries. Some countries/regions allow the use the partial Storno. For example, a bookkeeper posts an invoice from a vendor for 120 USD. During the payment process, it's discovered that the bookkeeper mistakenly entered an incorrect number sequence. The original invoice for 102 USD had a mistake in the number sequence. Using partial Storno, the bookkeeper should create Storno for 18 USD. The following table shows the general entry for partial Storno.

| **Document ID** | **Account** | **Debit** | **Credit** | **Comment**                  |
|-----------------|-------------|-----------|------------|------------------------------|
| Invoice0001     | Purch acc   | 120       |            | Original Invoice (incorrect) |
| Invoice0001     | Vendor acc  |           | 120        | Original Invoice (incorrect) |
|                 |             |           |            |                              |
| Storno0001      | Purch acc   | \-18      |            | Partial Storno               |
| Storno0001      | Vendor acc  |           | \-18       | Partial Storno               |

In this example, the balance statement shows the following.

| Account    | Debit | Credit | Balance |
|------------|-------|--------|---------|
| Purch acc  | 102   | 0      | 102     |
| Vendor acc | 0     | 102    | -102    |

Partial Storno can create an issue on the Original Print form. If there is a difference between the date of the original document and the date of Storno, it can make it difficult to get an accurate currency amount. As a result, partial Storno is only allowed for certain documents. Dynamics 365 Finance provides partial Storno functionality for documents and countries/regions where it is allowed.

## How to enter Storno on journal lines
Enter the debit or credit amount with a negative sign on the journal line to make a Storno entry. The **Correction** field is set during the posting process. 

## How Storno is displayed
Finance handles negative journal amounts in a special way. The general journal entry, customer transaction, vendor transaction, and other transactions provide a Storno function, as shown below.

<table>
<thead>
<tr class="row-1">
<th class="column-1" rowspan="2">User input at journal line</th>
<th class="column-2" colspan="2">Storage principle</th>
<th class="column-4" colspan="2">Display principle</th>
<th class="column-6" colspan="3">Impact to the Statement report</th>
</tr>
<tr class="row-1">
<th class="column-2">Correction field</th>
<th class="column-3">Amount field</th>
<th class="column-4">Amount in transaction currency</th>
<th class="column-5">Amount</th>
<th class="column-6">Debit column</th>
<th class="column-7">Credit column</th>
<th class="column-8">Balance column</th>
</tr>
</thead>
<tbody>
<tr class="row-2">
<td class="column-1"> Debit</td>
<td class="column-2">No</td>
<td class="column-3">&gt;0</td>
<td class="column-4" align="right">Amount</td>
<td class="column-5" align="right">Amount</td>
<td class="column-6">Increases</td>
<td class="column-7"></td>
<td class="column-8">Increases</td>
</tr>
<tr class="row-3">
<td class="column-1"> Credit</td>
<td class="column-2">No</td>
<td class="column-3">&lt;0</td>
<td class="column-4" align="right">-Amount</td>
<td class="column-5" align="right">Amount</td>
<td class="column-6"></td>
<td class="column-7">Increases</td>
<td class="column-8">Decreases</td>
</tr>
<tr class="row-4">
<td class="column-1">-Debit</td>
<td class="column-2">Yes</td>
<td class="column-3">&gt;0</td>
<td class="column-4" align="right">+Amount</td>
<td class="column-5" align="right">-Amount</td>
<td class="column-6">Decreases</td>
<td class="column-7"></td>
<td class="column-8">Increases</td>
</tr>
<tr class="row-5">
<td class="column-1">-Credit</td>
<td class="column-2">Yes</td>
<td class="column-3">&lt;0</td>
<td class="column-4" align="right">-Amount</td>
<td class="column-5" align="right">-Amount</td>
<td class="column-6"></td>
<td class="column-7">Decreases</td>
<td class="column-8">Decreases</td>
</tr>
</tbody>
</table>

You can customize the display of Storno in forms, grids, columns, and fields. For example, you can turn off sign display or change padding for negative amounts. You can also use the **Correction** field with all display settings, if the **Correction** field has ‘Yes’, then it is a Storno entry.

![Journal Entry Storno amounts.](../media/journal-storno.png)

## How documents create Storno
Certain documents create cancellation transactions. For example, the foreign currency revaluation for general ledger, accounts payable, and accounts receivable documents cancel unrealized gain and loss. For more details, see [Foreign currency revaluation for General ledger](../../general-ledger/foreign-currency-revaluation-general-ledger.md) or [Foreign currency revaluation for Accounts payable and Accounts receivable](../../cash-bank-management/foreign-currency-revaluation-accounts-payable-accounts-receivable.md). After a cancellation transaction is created, new transactions will be created with unrealized gain and loss. Cancellation transactions are also created for inventory. For more information, see [Inventory close](../../../supply-chain/cost-management/inventory-close.md). 
There are documents that allow you to cancel the previously posted document. For example, the User can create a Credit Note to cancel a previously created Invoice. Documents use specific parameters to create reverse or Storno transactions. For example, the foreign currency revaluation creates reverse or Storno transactions based on the general ledger correction parameter. The customer credit note creates reverse or Storno transactions based on the accounts receivable credit note correction parameter.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
