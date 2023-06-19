---
# required metadata

title: Use one payment to settle invoices that span multiple discount periods
description: This article shows how multiple invoices are paid when each invoice qualifies for a cash discount. The scenarios in this article highlight how the cash discounts that are taken vary, depending on when the payment is made.
author: ShivamPandey-msft
ms.date: 11/15/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CustOpenTrans, LedgerJournalTransCustPaym
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: 3e42ccb5-b9d7-4a70-8db9-4206d10fd433
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Use one payment to settle invoices that span multiple discount periods

[!include [banner](../includes/banner.md)]

This article shows how multiple invoices are paid when each invoice qualifies for a cash discount. The scenarios in this article highlight how the cash discounts that are taken vary, depending on when the payment is made.

Fabrikam sells goods to customer 4032. Fabrikam offers a cash discount of 1 percent if the invoice is paid in 14 days. Fabrikam also offers cash discounts on partial payments. The settlement parameters are located on the **Accounts receivable parameters** page.

## Invoices
Customer 4032 has three invoices that total 3,000.00:

-   Invoice FTI-10040, for 1,000.00, was entered on May 15. This invoice is eligible for a cash discount of 1 percent if it's paid in 14 days.
-   Invoice FTI-10041, for 1,000.00, was entered on June 25. This invoice is eligible for a cash discount of 1 percent if it's paid in 14 days.
-   Invoice FTI-10042, for 1,000.00, was entered on June 25. This invoice is eligible for a cash discount of 2 percent if it's paid in five days and a discount of 1 percent if it's paid in 14 days.

## Settle all invoices on June 29
If Arnie creates a payment journal to fully settle these invoices on June 29, the payment is 2,970.00. The total of all discount amounts is 30.00. Arnie creates a payment for customer 4032 and then opens the **Settle transactions** page. On the **Settle transactions** page, Arnie marks all three invoice lines for settlement:

-   The payment for invoice FTI-10040 is 1,000.00. No cash discount is taken.
-   The payment for invoice FTI-10041 is 990.00. A cash discount of 1 percent, or 10.00, is taken.
-   The payment for invoice FTI-10042 is 980.00. A cash discount of 2 percent, or 20.00, is taken.

| Mark | Use cash discount | Voucher   | Account | Date   | Due date  | Invoice | Amount in transaction currency debit | Amount in transaction currency credit | Currency | Amount to settle |
|------|----------|-----------|---------|-----------|-----------|---------|---------------------|---------------------|----------|------------------|
| Selected     | Normal      | FTI-10040 | 4032    | 5/15/2020 | 6/15/2020 | 10040   | 1,000.00  |                    | USD      | 1,000.00         |
| Selected     | Normal      | FTI-10041 | 4032    | 6/25/2020 | 7/25/2020 | 10041   | 1,000.00  |                    | USD      | 990.00           |
| Selected and highlighted | Normal      | FTI-10042 | 4032    | 6/25/2020 | 7/25/2020 | 10042   | 1,000.00    |              | USD      | 980.00           |

After the payment is posted, the customer balance is 0.00.

## Settle all invoices on July 1
If Arnie creates a payment journal to fully settle these invoices on July 1, the payment is 2,980.00. Arnie creates a payment for customer 4032 and then opens the **Settle transactions** page. On the **Settle transactions** page, Arnie marks all three invoice lines for settlement:

-   The payment for invoice FTI-10040 is 1,000.00. No cash discount is taken.
-   The payment for invoice FTI-10041 is 990.00. A cash discount of 1 percent, or 10.00, is taken.
-   The payment for invoice FTI-10042 is 990.00. A cash discount of 1 percent, or 10.00 is taken. Although July 1 is after the period that qualifies for the 2-percent discount, it's still in the period that qualifies for the 1-percent discount.

| Mark                     | Use cash discount | Voucher   | Account | Date      | Due date  | Invoice | Amount in transaction currency debit | Amount in transaction currency credit | Currency | Amount to settle |
|----------|---------|-----------|---------|-----------|-----------|---------|--------------------|------------------|----------|------------------|
| Selected         | Normal            | FTI-10040 | 4032    | 5/15/2020 | 6/15/2020 | 10040   | 1,000.00         |                | USD      | 1,000.00         |
| Selected                 | Normal            | FTI-10041 | 4032    | 6/25/2020 | 7/25/2020 | 10041   | 1,000.00  |               | USD      | 990.00           |
| Selected and highlighted | Normal            | FTI-10042 | 4032    | 6/25/2020 | 7/25/2020 | 10042   | 1,000.00  |             | USD      | 990.00           |

## Partial settlement on June 29
Customer 4032 can pay a partial amount, such as half of each invoice. Arnie creates a payment for customer 4032 and then opens the **Settle transactions** page. On the **Settle transactions** page, Arnie marks all three invoice lines for settlement. On each line, Arnie enters the amount to settle, based on the instructions that the customer provided. When Arnie selects a line, Arnie sees the discount amount for that line and the cash discount amount that is taken. Because the customer is paying half the invoice, Arnie sees that the value in the **Cash discount amount** field for FTI-10042 is **20.00**, but the value in the **Cash discount taken** field is **10.00**. The payment amount is 1,485.00.

| Mark   | Use cash discount | Voucher   | Account | Date      | Due date  | Invoice | Amount in transaction currency debit | Amount in transaction currency credit | Currency | Amount to settle |
|-------------|-------------------|-----------|---------|-----------|-----------|---------|-----------|------------------|----------|------------------|
| Selected   | Normal       | FTI-10040 | 4032    | 5/15/2020 | 6/15/2020 | 10040   | 1,000.00        |               | USD      | 500.00           |
| Selected                 | Normal            | FTI-10041 | 4032    | 6/25/2020 | 7/25/2020 | 10041   | 1,000.00     |     | USD      | 495.00           |
| Selected and highlighted | Normal            | FTI-10042 | 4032    | 6/25/2020 | 7/25/2020 | 10042   | 1,000.00     |         | USD      | 490.00           |

Arnie can also manually enter the payment amount of 1,485.00 before opening the **Settle transactions** page. If Arnie manually enters the payment amount and then marks all three transactions, but doesn't adjust the value in the **Amount to settle** field for each transaction, Arnie receives the following message when the page closes:

> The total amount of marked transactions is different from the journal amount. Change journal amount?

If Arnie wants the payment amount to be only 1,485.00, Arnie clicks **No** and then posts the journal. The transactions are settled as follows:

1.  Invoice FTI-10040 is fully settled for 1,000.00, because it was entered on May 15 and is the oldest invoice. No cash discount is taken. The remaining amount on the payment transaction is 485.00.
2.  Invoice FTI-10041 isn't settled at all. Invoices FTI-10041 and FTI-10042 were entered on the same date. However, a 1-percent discount is available to invoice FTI-10041, and a 2-percent discount is available to invoice FTI-10042. Because a better discount is available to invoice FTI-10042, the remaining 485.00 is settled with invoice FTI-10042.
3.  Invoice FTI-10042 is settled with the remaining 485.00. Fabrikam offers partial discounts. In this case, the discount is 9.90 (= 485.00 ÷ 0.98 × 0.02). The amount (485.00) is divided by 0.98, because there is a 2-percent discount (therefore, the customer pays 98 percent of the invoice). The result is then multiplied by the discount percentage, or 2 percent. The payment of 485.00 plus the discount of 9.90 equals 494.90. The amount of the original invoice was 1,000.00. Therefore, the transaction has a balance of 505.10 (= 1,000.00 – 494.90).

Arnie views the information on the **Customer transactions** page.

| Voucher    | Transaction type | Date      | Invoice | Amount in transaction currency debit | Amount in transaction currency credit | Balance  | Currency |
|------------|------------------|-----------|---------|--------------------------------------|---------------------------------------|----------|----------|
| FTI-10040  | Invoice          | 5/15/2020 | 10040   | 1,000.00                             |                                       | 0.00     | USD      |
| FTI-10041  | Invoice          | 6/25/2020 | 10041   | 1,000.00                             |                                       | 1,000.00 | USD      |
| FTI-10042  | Invoice          | 6/25/2020 | 10042   | 1,000.00                             |                                       | 505.10   | USD      |
| ARP-10040  | Payment          | 6/29/2020 |         |                                      | 1,485.00                              | 0.00     | USD      |
| DISC-10040 | Cash discount    | 6/29/2020 |         |                                      | 9.90                                  | 0.00     | USD      |







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
