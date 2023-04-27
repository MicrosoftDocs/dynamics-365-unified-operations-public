---
# required metadata

title: Settle partial payment before discount date and final payment after discount date
description: This article walks you through a scenario where multiple partial payments are made, some within the cash discount period and others outside the cash discount period.
author: angelad116
ms.date: 10/24/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LedgerJournalTransVendPaym, VendOpenTrans
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 14411
ms.assetid: 302ad6ae-28ee-4899-9f6b-f74424a5f50c
ms.search.region: Global
# ms.search.industry: 
ms.author: angelading
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Settle partial payment before discount date and final payment after discount date

[!include [banner](../includes/banner.md)]

This article walks you through a scenario where multiple partial payments are made, some within the cash discount period and others outside the cash discount period.

Fabrikam purchases goods from vendor 3057. Fabrikam receives a cash discount of 1 percent if the invoice is paid in 14 days. Invoices must be paid in 30 days. The vendor also lets Fabrikam take cash discounts on partial payments. The settlement parameters are located on the **Accounts payable parameters** page.

## Invoice on June 25
On June 25, April enters and posts an invoice for 1,000.00 for vendor 3057. April can view this transaction on the **Vendor transactions** page.

| Voucher   | Transaction type | Date      | Invoice | Amount in transaction currency debit | Amount in transaction currency credit | Balance   | Currency |
|-----------|------------------|-----------|---------|--------------------------------------|---------------------------------------|-----------|----------|
| Inv-10020 | Invoice          | 6/25/2020 | 10020   |                                      | 1,000.00                              | -1,000.00 | USD      |

## Partial payment on July 2
On July 2, April wants to settle 300.00 of this invoice. The payment is eligible for a discount, because Fabrikam takes discounts on partial payments. Therefore, April pays 297.00 and takes a 3.00 discount. April creates a payment journal and enters a line for vendor 3057, and then opens the **Settle transactions** page, to mark the invoice for settlement.

| Mark     | Use cash discount | Voucher   | Account | Date      | Due date  | Invoice | Amount in transaction currency | Currency | Amount to settle |
|----------|-------------------|-----------|---------|-----------|-----------|---------|--------------------------------|----------|------------------|
| Selected | Normal            | Inv-10020 | 3057    | 6/25/2020 | 7/25/2020 | 10020   | -1,000.00                      | USD      | -297.00          |

Discount information appears at the bottom of the **Settle open transactions** page.

| Field                        | Value     |
|------------------------------|-----------|
| Cash discount date           | 7/09/2020 |
| Cash discount amount         | -10.00    |
| Use cash discount            | Normal    |
| Cash discount taken          | 0.00      |
| Cash discount amount to take | -3.00     |

April then posts the payment. The invoice now has a balance of 700.00. April can view this transaction on the **Vendor transactions** page.

| Voucher    | Transaction type | Date      | Invoice | Amount in transaction currency debit | Amount in transaction currency credit | Balance | Currency |
|------------|------------------|-----------|---------|--------------------------------------|---------------------------------------|---------|----------|
| Inv-10020  | Invoice          | 6/25/2020 | 10020   |                                      | 1,000.00                              | -700.00 | USD      |
| APP-10020  | Payment          | 7/1/2020  |         | 297.00                               |                                       | 0.00    | USD      |
| DISC-10020 | Cash discount    | 7/1/2020  |         | 3.00                                 |                                       | 0.00    | USD      |

## Remaining payment on July 15, Use cash discount = Normal
April pays the rest of the invoice on July 15, which is after the discount period. On the **Settle open transactions** page, no discount amount is displayed in the **Estimated cash discount** field, and the value in the **Cash discount amount** field is **0.00**. When April pays the remaining 700.00, no additional discount will be taken.

| Mark     | Use cash discount | Voucher   | Account | Date      | Due date  | Invoice | Amount in transaction currency | Currency | Amount to settle |
|----------|-------------------|-----------|---------|-----------|-----------|---------|--------------------------------|----------|------------------|
| Selected | Normal            | Inv-10020 | 3057    | 6/25/2020 | 7/25/2020 | 10020   | -700.00                        | USD      | -700.00          |

Discount information appears at the bottom of the **Settle transactions** page. April can see that a 3.00 discount has already been taken.

| Field                        | Value     |
|------------------------------|-----------|
| Cash discount date           | 7/09/2020 |
| Cash discount amount         | 0.00      |
| Use cash discount            | Normal    |
| Cash discount taken          | -3.00     |
| Cash discount amount to take | 0.00      |

April then posts the payment. On opening the **Vendor transactions** page, April sees that the invoice has a balance of 0.00. April also sees that there are two payments. One payment is for 297.00 and has a 3.00 discount, and the other payment is for 700.00.

| Voucher    | Transaction type | Date      | Invoice | Amount in transaction currency debit | Amount in transaction currency credit | Balance | Currency |
|------------|------------------|-----------|---------|--------------------------------------|---------------------------------------|---------|----------|
| Inv-10020  | Invoice          | 6/25/2020 | 10020   |                                      | 1,000.00                              | 0.00    | USD      |
| APP-10020  | Payment          | 7/1/2020  |         | 297.00                               |                                       | 0.00    | USD      |
| DISC-10020 | Cash discount    | 7/1/2020  |         | 3.00                                 |                                       | 0.00    | USD      |
| APP-10021  | Payment          | 7/15/2020 |         | 700.00                               |                                       | 0.00    | USD      |

## Remaining payment on July 15, Use cash discount = Always
If the vendor lets April take a discount even though the payment is made after the discount date, April can change the value in the **Use cash discount** field to **Always**. The **Calculate cash discounts for partial payments** setting is overridden, and the discount is taken. The payment amount is 693.00, and the discount is the remaining 7.00.

| Mark     | Use cash discount | Voucher   | Account | Date      | Due date  | Invoice | Amount in transaction currency debit | Amount in transaction currency credit | Currency | Amount to settle |
|----------|----------|------|------|-----------|-----------|---------|-----------------------|---------------------------------------|----------|------------------|
| Selected | Always            | Inv-10020 | 3057    | 6/25/2020 | 7/25/2020 | 10020   | 700.00                   |                   | USD      | -693.00          |

Discount information appears at the bottom of the **Settle transactions** page.

| Field                        | Value     |
|------------------------------|-----------|
| Cash discount date           | 7/09/2020 |
| Cash discount amount         | 7.00      |
| Use cash discount            | Always    |
| Cash discount taken          | -3.00     |
| Cash discount amount to take | -7.00     |

April then posts the payment. On opening the **Vendor transactions** page, April sees that the invoice has a balance of 0.00. April also sees that there are two payments. One payment is for 297.00 and has a 3.00 discount, and the other payment is for 693.00 and has a 7.00 discount.

| Voucher    | Transaction type | Date      | Invoice | Amount in transaction currency debit | Amount in transaction currency credit | Balance | Currency |
|------------|------------------|-----------|---------|--------------------------------------|---------------------------------------|---------|----------|
| Inv-10020  | Invoice          | 6/25/2020 | 10020   |                                      | 1,000.00                              | 0.00    | USD      |
| APP-10020  | Payment          | 7/1/2020  |         | 297.00                               |                                       | 0.00    | USD      |
| DISC-10020 | Cash discount    | 7/1/2020  |         | 3.00                                 |                                       | 0.00    | USD      |
| APP-10021  | Payment          | 7/15/2020 |         | 693.00                               |                                       | 0.00    | USD      |
| DISC-10021 | Cash discount    | 7/15/2020 |         | 7.00                                 |                                       | 0.00    | USD      |







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
