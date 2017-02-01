---
# required metadata

title: Take a cash discount outside the cash discount period | Microsoft Docs
description: This article provides two scenarios that show how a cash discount can be taken even if the payment is made outside the cash discount period.
author: twheeloc
manager: AnnBe
ms.date: 2015-12-02 23:21:36
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

keywords: LedgerJournalTransVendPaym, VendOpenTrans
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 14301
ms.assetid: 46dae2fc-f0ed-4613-b834-b6bb95974f69
ms.region: Global
# ms.industry: 
ms.author: kweekley

---

# Take a cash discount outside the cash discount period

This article provides two scenarios that show how a cash discount can be taken even if the payment is made outside the cash discount period.

On June 28, April creates an invoice for 2,000.00 for vendor 3052. The invoice has a cash discount of 1 percent if the invoice is paid in 14 days.

## Use cash discount option = Always
April creates a payment on July 1, which is after the discount date. April opens the **Settle transactions** page to view the transactions that can be settled. April marks the invoice for payment. No cash discount is taken, because the payment is after the discount date. However, the vendor has given April approval to take the cash discount anyway. Therefore, April changes the value in the **Use cash discount** field to **Always**.

| Mark     | Use cash discount | Voucher   | Account | Cash discount date | Due date  | Invoice | Amount in transaction currency | Currency | Amount to settle |
|----------|-------------------|-----------|---------|--------------------|-----------|---------|--------------------------------|----------|------------------|
| Selected | Always            | Inv-10030 | 3052    | 6/28/2015          | 7/12/2015 | 10030   | -2,000.00                      | USD      | -1,980.00        |

Discount information appears at the bottom of the **Settle transactions** page.

|                              |           |
|------------------------------|-----------|
| Cash discount date           | 7/12/2015 |
| Cash discount amount         | -20.00    |
| Use cash discount            | Always    |
| Cash discount taken          | 0.00      |
| Cash discount amount to take | -20.00    |

## Date to use for calculating discounts = Selected date
If both the invoice and the payment have been posted, the cash discount can still be taken when the transactions are settled on the **Settle transactions** page. April changes the value in the **Date to use for calculating discounts** field to **Selected date**. She then enters a date of June 28, which is in the cash discount period for the invoice. That date is used to calculate a cash discount for the transaction. On the **Settle open transactions** page, April sees that, by default, the full discount of 20.00 appears. The invoice line shows that the amount to settle is 1,980.00.

| Mark                     | Use cash discount | Voucher   | Account | Cash discount date | Due date  | Invoice | Amount in transaction currency | Currency | Amount to settle |
|--------------------------|-------------------|-----------|---------|--------------------|-----------|---------|--------------------------------|----------|------------------|
| Selected and highlighted | Normal            | Inv-10030 | 3052    | 6/28/2015          | 7/12/2015 | 10030   | -2,000.00                      | USD      | -1,980.00        |
| Selected                 | Normal            | APP-10030 | 3052    | 7/15/2015          | 7/15/2015 |         | 500.00                         | USD      | 500.00           |

Discount information appears at the bottom of the **Settle open transactions** page. The discount amount that is taken is 20.00, because the amount to settle for the invoice is the default amount, 1,980.00.

|                              |           |
|------------------------------|-----------|
| Cash discount date           | 7/12/2015 |
| Cash discount amount         | -20.00    |
| Use cash discount            | Normal    |
| Cash discount taken          | 0.00      |
| Cash discount amount to take | -20.00    |

April updates the value in the **Amount to settle** field to **500.00**. The value in the **Cash discount amount to take** field is calculated as **5.05**.

| Mark                     | Use cash discount | Voucher   | Account | Date      | Due date  | Invoice | Amount in transaction currency | Currency | Amount to settle |
|--------------------------|-------------------|-----------|---------|-----------|-----------|---------|--------------------------------|----------|------------------|
| Selected and highlighted | Normal            | Inv-10030 | 3052    | 6/28/2015 | 7/12/2015 | 10030   | 2,000.00                       | USD      | -500.00          |
| Selected                 | Normal            | APP-10030 | 3052    | 7/15/2015 | 7/15/2015 |         | 500.00                         | USD      | 500.00           |

Discount information appears at the bottom of the **Settle open transactions** page. The value in the **Cash discount amount to take** field is **5.05**, because the amount to settle for the invoice was changed to the payment amount, 500.00.

|                              |           |
|------------------------------|-----------|
| Cash discount date           | 7/12/2015 |
| Cash discount amount         | -20.00    |
| Use cash discount            | Normal    |
| Cash discount taken          | 0.00      |
| Cash discount amount to take | -5.05     |



