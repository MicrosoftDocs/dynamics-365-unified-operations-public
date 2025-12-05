---
title: Storno accounting
description: Storno accounting is the practice of using negative numbers to reverse original journal account entries, including an example.
author: kfend
ms.author: johnmichalak
ms.topic: article
ms.date: 12/05/2025
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Czech Republic, Germany, Hungary, Latvia, Lithuania, Poland, Russia
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Storno accounting

[!include [banner](../../includes/banner.md)]

Storno accounting uses negative numbers to reverse original journal account entries.

*Storno accounting* uses negative debit or credit amounts to reverse original journal account entries. Because bookkeepers typically write Storno entries in red ink, this accounting practice is also known as *Red Storno*. With Storno accounting, you can cancel a document with incorrect amounts. However, you should always enter the correct document amount after the cancellation.

## Example

A bookkeeper posts an invoice from a vendor for 120 USD. During the payment process, the bookkeeper discovers that they mistakenly entered 120 USD instead of 102 USD. Now, the bookkeeper needs to create Storno for the original document, and then creates the correct invoice for 102 USD. For more information, see [Vendor invoices overview](../../accounts-payable/vendor-invoices-overview.md). The following table shows the general entry for Storno.

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

In this example, the balance statement shows the following information.

| Account    | Debit | Credit | Balance |
|------------|-------|--------|---------|
| Purch acc  | 102   | 0      | 102     |
| Vendor acc | 0     | 102    | -102    |

## Differences between Storno and reverse entries

You can correct posting entries in two ways: reverse entries and storno entries. If you use a reverse entry, you create a copy of the original general entry with reversed debit and credit accounts, but the amounts keep the same sign. If you use Storno, the system creates a copy of the original general entry, but it records the amounts with a negative sign. The following table shows the general entry for Storno.

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

In this example, the balance statement shows the following information.

| Account    | Debit | Credit | Balance |
|------------|-------|--------|---------|
| Purch acc  | 222   | 120    | 102     |
| Vendor acc | 120   | 222    | -102    |

The balances are equal for the reverse and the storno. There's a difference between debit turnover and credit turnover because the reverse entry makes redundant debit and credit turnover. Use the reverse entry in countries or regions where turnover is rarely used. Other countries or regions use Storno accounting.

## Partial Storno

*Partial Storno* is an accounting practice that uses negative debit or credit amounts to reverse part of the original journal account entries. Some countries and regions allow the use of partial Storno. For example, a bookkeeper posts an invoice from a vendor for 120 USD. During the payment process, the bookkeeper discovers that they mistakenly entered an incorrect number sequence. The original invoice for 102 USD had a mistake in the number sequence. By using partial Storno, the bookkeeper creates Storno for 18 USD. The following table shows the general entry for partial Storno.

| **Document ID** | **Account** | **Debit** | **Credit** | **Comment**                  |
|-----------------|-------------|-----------|------------|------------------------------|
| Invoice0001     | Purch acc   | 120       |            | Original Invoice (incorrect) |
| Invoice0001     | Vendor acc  |           | 120        | Original Invoice (incorrect) |
|                 |             |           |            |                              |
| Storno0001      | Purch acc   | \-18      |            | Partial Storno               |
| Storno0001      | Vendor acc  |           | \-18       | Partial Storno               |

In this example, the balance statement shows the following information.

| Account    | Debit | Credit | Balance |
|------------|-------|--------|---------|
| Purch acc  | 102   | 0      | 102     |
| Vendor acc | 0     | 102    | -102    |

Partial Storno can create an issue on the Original Print form. If there's a difference between the date of the original document and the date of Storno, it can make it difficult to get an accurate currency amount. As a result, partial Storno is only allowed for certain documents. Dynamics 365 Finance provides partial Storno functionality for documents and countries or regions where it's allowed.

## How to enter Storno on journal lines

Enter the debit or credit amount with a negative sign on the journal line to make a Storno entry. The **Correction** field is set during the posting process.

## How Storno appears

Finance handles negative journal amounts in a special way. The general journal entry, customer transaction, vendor transaction, and other transactions provide a Storno function, as shown in the following table.

| User input at journal line | Correction field | Amount field | Amount in transaction currency | Amount | Debit column | Credit column | Balance column |
|----------------------------|------------------|--------------|--------------------------------|--------|--------------|---------------|----------------|
| Debit | No | >0 | Amount | Amount | Increases | | Increases |
| Credit | No | <0 | -Amount | Amount | | Increases | Decreases |
| -Debit | Yes | >0 | +Amount | -Amount | Decreases | | Increases |
| -Credit | Yes | <0 | -Amount | -Amount | | Decreases | Decreases |

You can customize the display of Storno in forms, grids, columns, and fields. For example, you can turn off sign display or change padding for negative amounts. You can also use the **Correction** field with all display settings. If the **Correction** field has 'Yes', then it is a Storno entry.

:::image type="content" source="../media/journal-storno.png" alt-text="Screenshot of journal entry storno amounts.":::

## How documents create Storno

Certain documents create cancellation transactions. For example, the foreign currency revaluation for general ledger, accounts payable, and accounts receivable documents cancel unrealized gain and loss. For more details, see [Foreign currency revaluation for General ledger](../../general-ledger/foreign-currency-revaluation-general-ledger.md) or [Foreign currency revaluation for Accounts payable and Accounts receivable](../../cash-bank-management/foreign-currency-revaluation-accounts-payable-accounts-receivable.md). After a cancellation transaction is created, new transactions are created with unrealized gain and loss. Cancellation transactions are also created for inventory. For more information, see [Inventory close](../../../supply-chain/cost-management/inventory-close.md). 
Some documents allow you to cancel the previously posted document. For example, you can create a Credit Note to cancel a previously created Invoice. Documents use specific parameters to create reverse or Storno transactions. For example, the foreign currency revaluation creates reverse or Storno transactions based on the general ledger correction parameter. The customer credit note creates reverse or Storno transactions based on the accounts receivable credit note correction parameter.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
