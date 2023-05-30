---
title: Settle partial and final payments in full before the discount date
description: This article provides scenarios that show how to record partial payments for a customer and take cash discounts within the cash discount period.
author: angelad116
ms.date: 10/24/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: angelading
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 0f07d3ce-a439-43ed-a22e-957ccd36a37b
ms.search.form: CustOpenTrans, LedgerJournalTransCustPaym
---

# Settle partial and final payments in full before the discount date

[!include [banner](../includes/banner.md)]

This article provides scenarios that show how to record partial payments for a customer and take cash discounts within the cash discount period.

Fabrikam sells goods to customer 4028. Fabrikam offers a cash discount of 1 percent if the invoice is paid in 14 days. Invoices must be paid in 30 days. Fabrikam also offers cash discounts on partial payments. The settlement parameters are located on the **Accounts receivable parameters** page.

## Customer invoice
On June 25, Arnie enters and posts an invoice for 1,000.00 for customer 4028. Arnie can view this transaction on the **Customer transactions** page.

| Voucher   | Transaction type | Date      | Invoice | Amount in transaction currency debit | Amount in transaction currency credit | Balance  | Currency |
|-----------|------------------|-----------|---------|--------------------------------------|---------------------------------------|----------|----------|
| FTI-10010 | Invoice          | 6/25/2020 | 10010   | 1,000.00                             |                                       | 1,000.00 | USD      |

From the **Customer** or **Customer transactions** page, Arnie can open the **Settle transactions** page to view the dates and amounts of cash discounts that are available for the invoice. The due date is July 25, and a cash discount of 10.00 is available if the invoice is paid by July 9.

| Mark     | Use cash discount | Voucher   | Account | Date      | Due date  | Invoice | Amount in transaction currency | Currency | Amount to settle |
|----------|-------------------|-----------|---------|-----------|-----------|---------|--------------------------------|----------|------------------|
| Selected | Normal            | FTI-10010 | 4028    | 6/25/2020 | 7/25/2020 | 10010   | 1,000.00                       | USD      | 990.00           |

Discount information appears at the bottom of the **Settle transactions** page for the marked invoice.

|    &nbsp;                    |  &nbsp;   |
|------------------------------|-----------|
| Cash discount date           | 7/09/2020 |
| Cash discount amount         | 10.00     |
| Use cash discount            | Normal    |
| Cash discount taken          | 0.00      |
| Cash discount amount to take | 10.00     |

Arnie clicks the **Cash discount** tab to view the discount amount.

| Cash discount date | Cash discount amount | Amount in transaction currency |
|--------------------|----------------------|--------------------------------|
| 7/9/2020           | 10.00                | 990.00                         |
| 7/25/2020          | 0.00                 | 1,000.00                       |

## Partial payment by using the Enter customer payments page
Customer 4028 sends a payment for 500.00 on July 1. To enter this payment, Arnie doesn't click **Lines**. Instead, Arnie records the payment by creating a new payment journal and then opening the **Enter customer payments** page. Arnie enters the payment information and marks the invoice that they entered. When Arnie enters **500.00** as the amount, they also enter **500.00** in the **Amount to pay** field in the grid. Because Fabrikam allows a cash discount on partial payments, Arnie sees that a partial cash discount of 5.05 will also be taken. The calculation for this discount is 500.00 ÷ 0.99 × 0.01 = 5.05. (In this calculation, 500.00 is divided by 0.99, because there is a 1-percent discount. Therefore, the customer pays 99 percent of the invoice. The result is then multiplied by the discount percentage, which is 1 percent, or 0.01. If the customer takes the full discount of 10.00, the amount that must be settled will be 990.00.) Discount information appears in the grid at the bottom of the **Enter customer payments** page.

| Cash discount amount to take | Cash discount taken | Amount to pay |
|------------------------------|---------------------|---------------|
| 5.05                         | 0.00                | 500.00        |

## Partial payment by using the journal lines
Instead of opening the **Enter customer payments** page in the payment journal, Arnie can click **Lines** to enter a payment. The payment journal is displayed, where Arnie can enter a line for customer 4028. Arnie then opens the **Settle transactions** page, so that Arnie can mark the invoice for settlement. Arnie marks the invoice and changes the value in the **Amount to settle** field to **500.00**. Again, Arnie sees that the value in the **Cash discount amount** field is **10.00** for the full invoice, and the value in the **Cash discount amount to take** field is **5.05**. Therefore, Arnie is settling 505.05 of this invoice.

| Mark     | Use cash discount | Voucher   | Account | Date      | Due date  | Invoice | Amount in transaction currency | Currency | Amount to settle |
|----------|-------------------|-----------|---------|-----------|-----------|---------|--------------------------------|----------|------------------|
| Selected | Normal            | FTI-10010 | 4028    | 6/25/2020 | 7/25/2020 | 10010   | 1,000.00                       | USD      | 500.00           |

Discount information appears at the bottom of the **Settle open transactions** page.

|        &nbsp;                | &nbsp;    |
|------------------------------|-----------|
| Cash discount date           | 7/09/2020 |
| Cash discount amount         | 10.00     |
| Use cash discount            | Normal    |
| Cash discount taken          | 0.00      |
| Cash discount amount to take | 5.05      |

If the customer wants to settle exactly half the invoice, the customer submits a payment of 495.00. In this case, Arnie enters **495.00** in the **Amount to settle** field. The cash discount for 5.00 will also be taken, so that the total settled amount is 500.00.

| Mark     | Use cash discount | Voucher   | Account | Date      | Due date  | Invoice | Amount in transaction currency | Currency | Amount to settle |
|----------|-------------------|-----------|---------|-----------|-----------|---------|--------------------------------|----------|------------------|
| Selected | Normal            | FTI-10010 | 4028    | 6/25/2020 | 7/25/2020 | 10010   | 1,000.00                       | USD      | 495.00           |

Discount information appears at the bottom of the **Settle open transactions** page.

|     &nbsp;                   | &nbsp;    |
|------------------------------|-----------|
| Cash discount date           | 7/09/2020 |
| Cash discount amount         | 10.00     |
| Use cash discount            | Normal    |
| Cash discount taken          | 0.00      |
| Cash discount amount to take | 5.00      |

Arnie closes the **Settle transactions** page. A payment line for 495.00 is created in the journal, and Arnie then posts the journal. Arnie can review the customer transactions on the **Customer transactions** page. On this page, Arnie sees that the invoice has a balance of 500.00. Arnie also sees a payment of 495.00 and a discount of 5.00.

| Voucher    | Transaction type | Date      | Invoice | Amount in transaction currency debit | Amount in transaction currency credit | Balance | Currency |
|------------|------------------|-----------|---------|--------------------------------------|---------------------------------------|---------|----------|
| FTI-10010  | Invoice          | 6/25/2020 | 10010   | 1,000.00                             |                                       | 500.00  | USD      |
| ARP-10010  |  Payment         | 7/1/2020  |         |                                      | 495.00                                | 0.00    | USD      |
| DISC-10010 |  Cash discount   | 7/1/2020  |         |                                      | 5.00                                  | 0.00    | USD      |

## Payment for the remaining amount
Customer 4028 pays the remaining amount of 495.00 on July 8, which is in the cash discount period. Arnie creates the payment journal on July 8 and marks the transaction for settlement. Arnie sees that the amount that must be settled is 495.00. The value in the **Estimated cash discount** field is **5.00**, because the 5.00 discount was previously taken.

|   &nbsp;                | &nbsp; |
|-------------------------|--------|
| Marked total            | 495.00 |
| Estimated cash discount | 5.00   |

Information about the marked transaction appears in the grid on the **Settle open transactions** page.

| Mark     | Use cash discount | Voucher   | Account | Date      | Due date  | Invoice | Amount in transaction currency | Currency | Amount to settle |
|----------|-------------------|-----------|---------|-----------|-----------|---------|--------------------------------|----------|------------------|
| Selected | Normal            | FTI-10010 | 4028    | 6/25/2020 | 7/25/2020 | 10010   | 1,000.00                       | USD      | 495.00           |

Discount information appears at the bottom of the **Settle open transactions** page.

|  &nbsp;                      |  &nbsp;   |
|------------------------------|-----------|
| Cash discount date           | 7/09/2020 |
| Cash discount amount         | 10.00     |
| Use cash discount            | Normal    |
| Cash discount taken          | 5.00      |
| Cash discount amount to take | 5.00      |

Arnie posts this journal and reviews the customer transactions on the **Customer transactions** page. The balance for the invoice is now 0.00, and Arnie sees the two payments and the two cash discounts.

| Voucher    | Transaction type | Date      | Invoice | Amount in transaction currency debit | Amount in transaction currency credit | Balance | Currency |
|------------|------------------|-----------|---------|--------------------------------------|---------------------------------------|---------|----------|
| FTI-10010  | Invoice          | 6/25/2020 | 10010   | 1,000.00                             |                                       | 0.00    | USD      |
| ARP-10010  | Payment          | 7/1/2020  |         |                                      | 495.00                                | 0.00    | USD      |
| DISC-10010 | Cash discount    | 7/1/2020  |         |                                      | 5.00                                  | 0.00    | USD      |
| ARP-10011  | Payment          | 7/8/2020  |         |                                      | 495.00                                | 0.00    | USD      |
| DISC-10011 | Cash discount    | 7/8/2020  |         |                                      | 5.00                                  | 0.00    | USD      |







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
