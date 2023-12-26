---
# required metadata

title: Settle a partial vendor payment that has multiple discount periods
description: This article walks you through a scenario where multiple partial payments are made to a vendor that offers multiple cash discounts. 
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
ms.assetid: af95c48a-afd1-476c-978d-e34995100be4
ms.search.region: Global
# ms.search.industry: 
ms.author: angelading
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Settle a partial vendor payment that has multiple discount periods

[!include [banner](../includes/banner.md)]

This article walks you through a scenario where multiple partial payments are made to a vendor that offers multiple cash discounts. 

Vendor 3054 offers Fabrikam a cash discount of 2 percent if an invoice is paid in five days and a cash discount of 1 percent if the invoice is paid in 14 days.

## Invoice
On June 28, April creates an invoice for 1,000.00 for vendor 3054. April can view this transaction on the **Vendor transactions** page.

| Voucher   | Date      | Invoice | Amount in transaction currency debit | Amount in transaction currency credit | Balance   | Currency |
|-----------|-----------|---------|--------------------------------------|---------------------------------------|-----------|----------|
| Inv-10060 | 6/28/2020 | 10060   |                                      | 1,000.00                              | -1,000.00 | USD      |

The following cash discount dates and amounts are available for this invoice.

| Cash discount date | Cash discount amount | Amount in transaction currency |
|--------------------|----------------------|--------------------------------|
| 7/3/2020           | 20.00                | 980.00                         |
| 7/12/2020          | 10.00                | 990.00                         |
| 7/25/2020          | 0.00                 | 1,000.00                       |

## Payment on July 2
On July 2, April wants to pay 300.00 against this invoice, and creates a one-off payment by using the **Payment journal** page in Accounts payable. April adds a line for vendor 3054 and enters a payment amount of **300.00**. April then opens the **Settle transactions** page, to mark the invoice that will be settled. April updates the value in the **Amount to settle** field to **300.00** and notices that the value in the **Cash discount amount to take** field is changed to **6.12**. Because this payment is made in the first discount period, a discount of 2 percent is taken.

| Mark | Use cash discount | Voucher   | Account | Date      | Due date  | Invoice | Amount in transaction currency | Currency | Amount to settle |
|------|-------------------|-----------|---------|-----------|-----------|---------|--------------------------------|----------|------------------|
|      | Normal            | Inv-10060 | 3054    | 6/28/2020 | 7/28/2020 | 10060   | 1,000.00                       | USD      | 300.00           |

Discount information appears at the bottom of the **Settle open transactions** page.

| Field                        | Value     |
|------------------------------|-----------|
| Cash discount date           | 7/02/2020 |
| Cash discount amount         | -20.00    |
| Use cash discount            | Normal    |
| Cash discount taken          | 0.00      |
| Cash discount amount to take | -6.12     |

Because a cash discount is available, April wants to change the payment amount so that the total settled amount is 300.00 for both the payment and the cash discount. April changes the value in the **Amount to settle** field to **294.00** and notices that the value in the **Cash discount amount to take** field is changed to **6.00**.

| Mark | Use cash discount | Voucher   | Account | Date      | Due date  | Invoice | Amount in transaction currency | Currency | Amount to settle |
|------|-------------------|-----------|---------|-----------|-----------|---------|--------------------------------|----------|------------------|
|      | Normal            | Inv-10060 | 3054    | 6/28/2020 | 7/28/2020 | 10060   | 1,000.00                       | USD      | 294.00           |

Discount information appears at the bottom of the **Settle open transactions** page.

| Field                        | Value     |
|------------------------------|-----------|
| Cash discount date           | 7/02/2020 |
| Cash discount amount         | -20.00    |
| Use cash discount            | Normal    |
| Cash discount taken          | 0.00      |
| Cash discount amount to take | -6.00     |

April posts the payment. On the **Vendor transactions** page, April sees that 300.00 has been applied to the invoice. This amount includes a discount of 6.00. Therefore, the remaining balance is 700.00.

| Voucher    | Date      | Invoice | Amount in transaction currency debit | Amount in transaction currency credit | Balance | Currency |
|------------|-----------|---------|--------------------------------------|---------------------------------------|---------|----------|
| Inv-10060  | 6/28/2020 | 10060   |                                      | 1,000.00                              | -700.00 | USD      |
| APP-10060  | 7/2/2020  |         | 294.00                               |                                       | 0.00    | USD      |
| DISC-10060 | 7/2/2020  |         | 6.00                                 |                                       | 0.00    | USD      |

## Payment on July 8
On July 8, April makes an additional payment against the invoice. To enter the amount, April opens the **Settle transactions** page and then clicks the **Cash discount** tab. April sees the dates and amounts for the two cash discounts that are available. Because this payment is made in the second discount period, a discount of 1 percent, or 5.00, is available. This amount is calculated as half the 1-percent discount on 1,000.00, or half of 10.00.

| Cash discount date | Cash discount amount | Amount in transaction currency |
|--------------------|----------------------|--------------------------------|
| 7/3/2020           | 20.00                | 680.00                         |
| 7/12/2020          | 10.00                | 690.00                         |
| 7/25/2020          | 0.00                 | 700.00                         |

April decides to pay 495.00 and take the 5.00 cash discount. Therefore, the total amount that is settled is 500.00.

| Mark | Use cash discount | Voucher   | Account | Date      | Due date  | Invoice | Amount in transaction currency | Currency | Amount to settle |
|------|-------------------|-----------|---------|-----------|-----------|---------|--------------------------------|----------|------------------|
|      | Normal            | Inv-10060 | 3054    | 6/28/2020 | 7/28/2020 | 10060   | 1,000.00                       | USD      | 495.00           |

Discount information appears at the bottom of the **Settle open transactions** page.

| Field                        | Value     |
|------------------------------|-----------|
| Cash discount date           | 7/12/2020 |
| Cash discount amount         | -10.00    |
| Use cash discount            | Normal    |
| Cash discount taken          | -6.00     |
| Cash discount amount to take | -5.00     |

On the **Vendor transactions** page, April sees that the new balance is 200.00.

| Voucher    | Date      | Invoice | Amount in transaction currency debit | Amount in transaction currency credit | Balance | Currency |
|------------|-----------|---------|--------------------------------------|---------------------------------------|---------|----------|
| Inv-10060  | 6/28/2020 | 10060   |                                      | 1,000.00                              | -200.00 | USD      |
| APP-10060  | 7/2/2020  |         | 294.00                               |                                       | 0.00    | USD      |
| DISC-10060 | 7/2/2020  |         | 6.00                                 |                                       | 0.00    | USD      |
| APP-10061  | 7/12/2020 |         | 495.00                               |                                       | 0.00    | USD      |
| DISC-10061 | 7/12/2020 |         | 5.00                                 |                                       | 0.00    | USD      |

## Payment on July 20
On July 20, April creates a final payment for 200.00. No discount is taken, because the payment is made after both discount periods. The balance for the invoice is 0.00.

| Voucher    | Date      | Invoice | Amount in transaction currency debit | Amount in transaction currency credit | Balance | Currency |
|------------|-----------|---------|--------------------------------------|---------------------------------------|---------|----------|
| Inv-10060  | 6/28/2020 | 10060   |                                      | 1,000.00                              | -200.00 | USD      |
| APP-10060  | 7/2/2020  |         | 294.00                               |                                       | 0.00    | USD      |
| DISC-10060 | 7/2/2020  |         | 6.00                                 |                                       | 0.00    | USD      |
| APP-10061  | 7/12/2020 |         | 495.00                               |                                       | 0.00    | USD      |
| DISC-10061 | 7/12/2020 |         | 5.00                                 |                                       | 0.00    | USD      |
| APP-10062  | 7/20/2020 |         | 200.00                               |                                       | 0.00    | USD      |







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
