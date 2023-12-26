---
# required metadata

title: Settle partial payment before discount date with final payment after discount date
description: This article discusses the effect of settling payments to invoices for customers. The scenario focuses on the effects in the subledger, not in General ledger.
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
ms.assetid: e54936f5-053b-4ed3-b778-42c7e9aeb7cf
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Settle partial payment before discount date with final payment after discount date

[!include [banner](../includes/banner.md)]

This article discusses the effect of settling payments to invoices for customers. The scenario focuses on the effects in the subledger, not in General ledger.

Fabrikam sells goods to customer 4027. Fabrikam offers a cash discount of 1 percent if the invoice is paid in 14 days. Invoices must be paid in 30 days. Fabrikam also offers cash discounts on partial payments. The settlement parameters are located on the **Accounts receivable parameters** page.

## Invoice
On June 25, Arnie enters and posts an invoice for 1,000.00 for customer 4027. Arnie can view this invoice by using the **Transactions** button on the **Customers** page.

| Voucher   | Transaction type | Date      | Invoice | Amount in transaction currency debit | Amount in transaction currency credit | Balance  | Currency |
|-----------|------------------|-----------|---------|--------------------------------------|---------------------------------------|----------|----------|
| FTI-10020 | Invoice          | 6/25/2020 | 10020   | 1,000.00                             |                                       | 1,000.00 | USD      |

## Partial payment before the cash discount date
On July 2, customer 4027 makes a partial payment of 297.00 for the invoice. The payment is eligible for a cash discount, because Fabrikam offers cash discounts on partial payments, and the partial payment is made before the cash discount date. Therefore, customer 4027 takes a 3.00 cash discount. Arnie records the payment for customer 4027 by using the Payment journal. Arnie then opens the **Settle transactions** page, so that Arnie can mark the invoice for settlement.

| Mark     | Use cash discount | Voucher   | Account | Date      | Due date  | Invoice | Amount in transaction currency debit | Currency | Amount to settle |
|----------|-------------------|-----------|---------|-----------|-----------|---------|--------------------------------------|----------|------------------|
| Selected | Normal            | FTI-10020 | 4027    | 6/25/2020 | 7/25/2020 | 10020   | 1,000.00                             | USD      | 297.00           |

Discount information appears at the bottom of the **Settle open transactions** page. If you don't change the **Amount to settle** value to 297.00, the **Cash discount amount** values that appear will differ. However, 3.00 will be taken as the cash discount when the payment is posted, because settlement automatically adjusts the **Amount to settle **value for you.

| Field                        | Value     |
|------------------------------|-----------|
| Cash discount date           | 7/09/2020 |
| Cash discount amount         | 10.00     |
| Use cash discount            | Normal    |
| Cash discount taken          | 0.00      |
| Cash discount amount to take | 3.00      |

Arnie posts this payment. The invoice now has a balance of 700.00. The following transactions can be seen for the customer.

| Voucher    | Transaction type | Date      | Invoice | Amount in transaction currency debit | Amount in transaction currency credit | Balance | Currency |
|------------|------------------|-----------|---------|--------------------------------------|---------------------------------------|---------|----------|
| FTI-10020  | Invoice          | 6/25/2020 | 10020   | 1,000.00                             |                                       | 700.00  | USD      |
| ARP-10020  |  Payment         | 7/1/2020  |         |                                      | 297.00                                | 0.00    | USD      |
| DISC-10020 |  Cash discount   | 7/1/2020  |         |                                      | 3.00                                  | 0.00    | USD      |

## Remaining payment after the cash discount date
On July 11, which is after the discount period, customer 4027 pays the rest of this invoice. On the **Settle transactions** page, a discount amount doesn't appear in the **Estimated cash discount** field, and the value in the **Cash discount amount** field is **0.00**. When customer 4027 pays the remaining 700.00, no additional discount is taken.

| Mark     | Use cash discount | Voucher   | Account | Date      | Due date  | Invoice | Amount in transaction currency debit | Currency | Amount to settle |
|----------|-------------------|-----------|---------|-----------|-----------|---------|--------------------------------------|----------|------------------|
| Selected | Normal            | FTI-10020 | 4027    | 6/25/2020 | 7/25/2020 | 10020   | 700.00                               | USD      | 700.00           |

Discount information appears at the bottom of the **Settle open transactions** page.

| Field                        | Value     |
|------------------------------|-----------|
| Cash discount date           | 7/09/2020 |
| Cash discount amount         | 0.00      |
| Use cash discount            | Normal    |
| Cash discount taken          | 3.00      |
| Cash discount amount to take | 0.00      |

If Arnie changes the value in the **Use cash discount** field to **Always**, the **Calculate cash discounts for partial payments** setting is overridden, and the cash discount is taken. The payment amount changes to 693.00, and the cash discount is the remaining 7.00.

| Mark     | Use cash discount | Voucher   | Account | Date      | Due date  | Invoice | Amount in transaction currency debit | Amount in transaction currency credit | Currency | Amount to settle |
|----------|-------------------|-----------|---------|-----------|-----------|---------|---------------|---------------------|----------|------------------|
| Selected | Always            | FTI-10020 | 4027    | 6/25/2020 | 7/25/2020 | 10020   | 700.00        |                        | USD      | 693.00           |

Discount information appears at the bottom of the **Settle open transactions** page.

| Field                        | Value     |
|------------------------------|-----------|
| Cash discount date           | 7/09/2020 |
| Cash discount amount         | 7.00      |
| Use cash discount            | Always    |
| Cash discount taken          | 3.00      |
| Cash discount amount to take | 7.00      |

Arnie changes the value in the **Use cash discount** field back to **Normal**, because Arnie is not letting this customer take the remaining cash discount of 7.00. Arnie then posts the payment. When Arnie opens the **Customer transactions** page, the invoice has a balance of 0.00. There are two payments. One payment is for 297.00 and has a 3.00 cash discount, and the other payment is for 700.00.

| Voucher    | Transaction type | Date      | Invoice | Amount in transaction currency debit | Amount in transaction currency credit | Balance | Currency |
|------------|------------------|-----------|---------|--------------------------------------|---------------------------------------|---------|----------|
| FTI-10020  | Invoice          | 6/25/2020 | 10020   | 1,000.00                             |                                       | 0.00    | USD      |
| ARP-10020  |                  | 7/1/2020  |         |                                      | 297.00                                | 0.00    | USD      |
| DISC-10020 |                  | 7/1/2020  |         |                                      | 3.00                                  | 0.00    | USD      |
| ARP-10021  |                  | 7/11/2020 |         |                                      | 700.00                                | 0.00    | USD      |







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
