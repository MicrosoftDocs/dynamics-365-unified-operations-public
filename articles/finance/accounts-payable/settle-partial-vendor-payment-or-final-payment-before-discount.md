---
# required metadata

title: Settle a partial vendor payment and the final payment in full before the discount date
description: This article walks you through a scenario where partial payments are made for a vendor invoice, and a cash discount is taken.
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
ms.reviewer: angelading
# ms.tgt_pltfrm: 
ms.assetid: 6b8e3420-b4c9-4e02-9588-598fe6d3df0d
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Settle a partial vendor payment and the final payment in full before the discount date

[!include [banner](../includes/banner.md)]

This article walks you through a scenario where partial payments are made for a vendor invoice, and a cash discount is taken.

Fabrikam buys goods from vendor 3064. The vendor gives Fabrikam a cash discount of 1 percent if the invoice is paid in 14 days. Invoices must be paid in 30 days. The vendor also lets Fabrikam take cash discounts on partial payments. The settlement parameters are located on the **Accounts payable parameters** page. On June 25, April enters an invoice for 1,000.00 for vendor 3064.

## Vendor invoice on June 25
On June 25, April enters and posts an invoice for 1,000.00 for vendor 3064. April can view this transaction on the **Vendor transactions** page.

| Voucher   | Date      | Invoice | Amount in transaction currency debit | Amount in transaction currency credit | Balance   | Currency |
|-----------|-----------|---------|--------------------------------------|---------------------------------------|-----------|----------|
| Inv-10010 | 6/25/2015 | 10010   |                                      | 1,000.00                              | -1,000.00 | USD      |

From the **Vendors** page, April opens the **Settle transactions** page. April can use the **Settle transactions** page to view the dates and amounts of cash discounts. The due date is July 25, and a cash discount of -10.00 is available if the invoice is paid by July 9.

| Mark | Use cash discount | Voucher   | Account | Date      | Due date  | Invoice | Amount in transaction currency | Currency | Amount to settle |
|------|-------------------|-----------|---------|-----------|-----------|---------|--------------------------------|----------|------------------|
|      | Normal            | Inv-10010 | 3064    | 6/25/2015 | 7/25/2015 | 10010   | 1,000.00                       | USD      | 990.00           |

Discount information appears at the bottom of the **Settle open transactions** page.

|       &nbsp;                 | &nbsp;    |
|------------------------------|-----------|
| Cash discount date           | 7/09/2015 |
| Cash discount amount         | -10.00    |
| Use cash discount            | Normal    |
| Cash discount taken          | 0.00      |
| Cash discount amount to take | -10.00    |

April clicks the **Cash discount** tab to view the discount amount.

| Cash discount date | Cash discount amount | Amount in transaction currency |
|--------------------|----------------------|--------------------------------|
| 7/9/2015           | 10.00                | 990.00                         |
| 7/25/2015          | 0.00                 | 1,000.00                       |

## Partial payment on July 1 by using the Settle transactions page
April can create a payment journal for this payment by opening the **Payment journal** page in Accounts payable. April creates a new journal and enters a line for vendor 3064. April then opens the **Settle transactions** page to mark the invoice for settlement. April marks the invoice and changes the value in the **Amount to settle** field to **-500.00**. The value in the **Cash discount amount** field is **-10.00** for the full invoice, and that the value in the **Cash discount amount to take** field is **-5.05**. Therefore, April is settling -505.05 of this invoice.

| Mark     | Use cash discount | Voucher   | Account | Date      | Due date  | Invoice | Amount in transaction currency | Currency | Amount to settle |
|----------|-------------------|-----------|---------|-----------|-----------|---------|--------------------------------|----------|------------------|
| Selected | Normal            | FTI-10010 | 4028    | 6/25/2015 | 7/25/2015 | 10010   | 1,000.00                       | USD      | -500.00          |

Discount information appears at the bottom of the **Settle open transactions** page.

|  &nbsp;                      |  &nbsp;   |
|------------------------------|-----------|
| Cash discount date           | 7/09/2015 |
| Cash discount amount         | -10.00    |
| Use cash discount            | Normal    |
| Cash discount taken          | 0.00      |
| Cash discount amount to take | -5.05     |

April wants to settle exactly half the invoice. Therefore, the value in the **Amount to settle** field is changed to **-495.00**. The total amount that is settled is now 500.00. This amount includes the -5.00 cash discount.

| Mark     | Use cash discount | Voucher   | Account | Date      | Due date  | Invoice | Amount in transaction currency | Currency | Amount to settle |
|----------|-------------------|-----------|---------|-----------|-----------|---------|--------------------------------|----------|------------------|
| Selected | Normal            | FTI-10010 | 4028    | 6/25/2015 | 7/25/2015 | 10010   | 1,000.00                       | USD      | -495.00          |

Discount information appears at the bottom of the **Settle open transactions** page.

|  &nbsp;                      |  &nbsp;   |
|------------------------------|-----------|
| Cash discount date           | 7/09/2015 |
| Cash discount amount         | -10.00    |
| Use cash discount            | Normal    |
| Cash discount taken          | 0.00      |
| Cash discount amount to take | -5.00     |

April closes the **Settle transactions** page. A payment line for 495.00 is created in the journal, and April then posts the journal. April can review the vendor transactions on the **Vendor transactions** pagen and sees that the invoice has a balance of -500.00. April also sees a payment of 495.00 and a cash discount of 5.00.

| Voucher    | Transaction type | Date      | Invoice | Amount in transaction currency debit | Amount in transaction currency credit | Balance | Currency |
|------------|------------------|-----------|---------|--------------------------------------|---------------------------------------|---------|----------|
| Inv-10010  | Invoice          | 6/25/2015 | 10010   |                                      | 1,000.00                              | -500.00 | USD      |
| APP-10010  | Payment          | 7/1/2015  |         | 495.00                               |                                       | 0.00    | USD      |
| DISC-10010 | Cash discount    | 7/1/2015  |         | 5.00                                 |                                       | 0.00    | USD      |

## Remaining amount paid on July 8
April pays the rest of the invoice for vendor 3064 on July 8, which is in the cash discount period. April creates the payment journal on July 8 and marks the transaction for settlement. April sees that the amount that must be settled is 495.00. The value in the **Estimated cash discount** field is **-5.00**, because the 5.00 discount was previously taken.

|  &nbsp;                 |  &nbsp; |
|-------------------------|--------|
| Marked total            | 495.00 |
| Estimated cash discount | -5.00  |

Information about the marked transaction appears in the grid on the **Settle open transactions** page.

| Mark     | Use cash discount | Voucher   | Account | Date      | Due date  | Invoice | Amount in transaction currency | Currency | Amount to settle |
|----------|-------------------|-----------|---------|-----------|-----------|---------|--------------------------------|----------|------------------|
| Selected | Normal            | FTI-10010 | 4028    | 6/25/2015 | 7/25/2015 | 10010   | 1,000.00                       | USD      | 495.00           |

Discount information appears at the bottom of the **Settle open transactions** page.

|  &nbsp;                      | &nbsp;    |
|------------------------------|-----------|
| Cash discount date           | 7/09/2015 |
| Cash discount amount         | 10.00     |
| Use cash discount            | Normal    |
| Cash discount taken          | 5.00      |
| Cash discount amount to take | 5.00      |

April posts the payment journal and reviews the vendor transactions on the **Vendor transactions** page. The balance for the invoice is now 0.00, and April sees the two payments and the two cash discounts.

| Voucher    | Transaction type | Date      | Invoice | Amount in transaction currency debit | Amount in transaction currency credit | Balance | Currency |
|------------|------------------|-----------|---------|--------------------------------------|---------------------------------------|---------|----------|
| Inv-10010  | Invoice          | 6/25/2015 | 10010   |                                      | 1,000.00                              | 0.00    | USD      |
| APP-10010  |  Payment         | 7/1/2015  |         | 495.00                               |                                       | 0.00    | USD      |
| DISC-10010 | Cash discount    | 7/1/2015  |         | 5.00                                 |                                       | 0.00    | USD      |
| APP-10011  | Payment          | 7/8/2015  |         | 495.00                               |                                       | 0.00    | USD      |
| DISC-10011 | Cash discount    | 7/8/2015  |         | 5.00                                 |                                       | 0.00    | USD      |







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
