---
# required metadata

title: Settle a partial customer payment that has discounts on credit notes
description: This article walks you through a scenario where a cash discount is taken on a credit note when the original invoice also had a cash discount. 
author: twheeloc
manager: AnnBe
ms.date: 2015-12-02 23 - 33 - 50
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: CustOpenTrans, LedgerJournalTransCustPaym
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 14564
ms.assetid: d9984cef-ddcf-46bd-816d-c01b8cc5cf48
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Settle a partial customer payment that has discounts on credit notes

This article walks you through a scenario where a cash discount is taken on a credit note when the original invoice also had a cash discount. 

Fabrikam allows customers to take cash discounts on partial payments and also on credit notes (credit memos). A cash discount can be taken on a credit note when the credit note is issued for an invoice that the customer took a cash discount on. Instead of providing a credit for the full amount, you can credit the customer's balance for an amount that excludes the cash discount percent that the customer took. The [settlement parameters](http://ax.help.dynamics.com/en/?p=246884) are located on the **Accounts receivable parameters** page.

## Invoice and credit note
Customer 4035 has an invoice for 1,000.00 and a credit note for 100.00. Each document has a 1 percent discount if it's paid in 14 days. Arnie can view this information on the **Customer transactions** page.

| Voucher    | Transaction type | Date      | Invoice  | Amount in transaction currency debit | Amount in transaction currency credit | Balance  | Currency |
|------------|------------------|-----------|----------|--------------------------------------|---------------------------------------|----------|----------|
| FTI-10050  | Invoice          | 6/28/2015 | 10050    | 1,000.00                             |                                       | 1,000.00 | USD      |
| CCRN-10050 | Credit note      | 6/28/2015 | CR-10050 |                                      | 100.00                                | -100.00  | USD      |

## Settle a credit note with an invoice
From the **Customer transactions** page, Arnie opens the **Settle transactions** page. He can use the **Settle transactions** page to settle the invoice and credit note. As part of the settlement process, he views the cash discount dates and amounts. He marks the two documents and then clicks **Post** to settle the transactions. There is a discount of -1.00 on the credit note, because Fabrikam allows for discounts on credit notes.

| Mark     | Use cash discount | Voucher    | Account | Date      | Due date  | Invoice  | Amount in transaction currency | Currency | Amount to settle |
|----------|-------------------|------------|---------|-----------|-----------|----------|--------------------------------|----------|------------------|
| Selected | Normal            | FTI-10050  | 4035    | 6/28/2015 | 7/28/2015 | 10050    | 1,000.00                       | USD      | 990.00           |
| Selected | Normal            | CCRN-10050 | 4035    | 6/28/2015 | 7/28/2015 | CR-10050 | -100.00                        | USD      | -99.00           |

Discount information appears at the bottom of the **Settle transactions** page.

|                              |           |
|------------------------------|-----------|
| Cash discount date           | 7/12/2015 |
| Cash discount amount         | -1.00     |
| Use cash discount            | Normal    |
| Cash discount taken          | 0.00      |
| Cash discount amount to take | -1.00     |

The settlement will be 100.00, and will include a payment of 99.00 and a discount of 1.00.

