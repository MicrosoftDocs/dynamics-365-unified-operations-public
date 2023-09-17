---
# required metadata

title: Settle a partial customer payment that has multiple discount periods
description: This article shows how partial customer payments are settled when there are multiple discount periods.
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
ms.assetid: b633a7c4-c18d-42e7-91cc-adcdc8a3ba98
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Settle a partial customer payment that has multiple discount periods

[!include [banner](../includes/banner.md)]

This article shows how partial customer payments are settled when there are multiple discount periods.

Fabrikam offers customer 4031 two cash discount periods. The customer receives a 2-percent cash discount if the invoice is paid in five days and a 1-percent cash discount if the invoice is paid in 14 days. Fabrikam also offers cash discounts on partial payments. The settlement parameters are located on the **Accounts receivable parameters** page.

## Invoice
On June 25, Arnie enters and posts an invoice for 1,000.00 for customer 4031. When Arnie reviews the cash discounts for this invoice, Arnie sees that customer 4031 receives a 20.00 discount if the invoice is paid by June 30. If the invoice is paid by July 9, the customer receives a 10.00 discount.

| Cash discount date | Cash discount amount | Amount in transaction currency |
|--------------------|----------------------|--------------------------------|
| 6/30/2020          | 20.00                | 980.00                         |
| 7/9/2020           | 10.00                | 990.00                         |
| 7/25/2020          | 0.00                 | 1,000.00                       |

Arnie can view this transaction on the **Customer transactions** page.

| Voucher   | Transaction type | Date      | Invoice | Amount in transaction currency debit | Amount in transaction currency credit | Balance  | Currency |
|-----------|------------------|-----------|---------|--------------------------------------|---------------------------------------|----------|----------|
| FTI-10030 | Invoice          | 6/25/2020 | 10030   | 1,000.00                             |                                       | 1,000.00 | USD      |

## Partial payment before the cash discount date
On June 28, Customer 4031 makes a partial payment of 294.00. Because June 28 is within the first cash discount period, the customer takes a 6.00 discount. On the **Settle transactions** page, the **Cash discount amount** value is 20.00, and the **Cash discount amount to take** value is 6.00.

| Mark     | Use cash discount | Voucher   | Account | Date      | Due date  | Invoice | Amount in transaction currency | Currency | Amount to settle |
|----------|-------------------|-----------|---------|-----------|-----------|---------|--------------------------------|----------|------------------|
| Selected | Normal            | FTI-10030 | 4031    | 6/25/2020 | 7/25/2020 | 10030   | 1,000.00                       | USD      | 294.00           |

Discount information appears at the bottom of the **Settle open transactions** page. If you don't change the **Amount to settle** value to **294.00**, the **Cash discount amount** values that appear will differ. However, 6.00 will be taken as the cash discount when the payment is posted, because settlement automatically adjusts the **Amount to settle** value for you.

| &nbsp;                       | &nbsp;    |
|------------------------------|-----------|
| Cash discount date           | 6/30/2020 |
| Cash discount amount         | 20.00     |
| Use cash discount            | Normal    |
| Cash discount taken          | 0.00      |
| Cash discount amount to take | 6.00      |

After Arnie posts the payment, the invoice balance is 700.00.

## Partial payment before the second cash discount date
On July 8, the customer pays the rest of the invoice amount. A 7.00 discount (1 percent) is taken, because the payment was made within the second cash discount period.

| Mark     | Use cash discount | Voucher   | Account | Date      | Due date  | Invoice | Amount in transaction currency debit | Amount in transaction currency credit | Currency | Amount to settle |
|----------|-------------------|-----------|---------|-----------|-----------|---------|--------------|-----------------------|----------|------------------|
| Selected | Normal            | FTI-10030 | 4031    | 6/25/2020 | 7/25/2020 | 10030   | 700.00       |            | USD      | 693.00           |

Discount information appears at the bottom of the **Settle open transactions** page.

| &nbsp;                       | &nbsp;    |
|------------------------------|-----------|
| Cash discount date           | 7/09/2020 |
| Cash discount amount         | 30.00     |
| Use cash discount            | Normal    |
| Cash discount taken          | 6.00      |
| Cash discount amount to take | 7.00      |

The invoice balance is now 0.00. Arnie views the information on the **Customer transactions** page.

| Voucher    | Transaction type | Date      | Invoice | Amount in transaction currency debit | Amount in transaction currency credit | Balance | Currency |
|------------|------------------|-----------|---------|--------------------------------------|---------------------------------------|---------|----------|
| FTI-10030  | Invoice          | 6/25/2020 | 10030   | 1,000.00                             |                                       | 0.00    | USD      |
| ARP-10030  |  Payment         | 6/28/2020 |         |                                      | 294.00                                | 0.00    | USD      |
| DISC-10030 |  Cash discount   | 6/28/2020 |         |                                      | 6.00                                  | 0.00    | USD      |
| ARP-10031  |  Payment         | 7/8/2020  |         |                                      | 693.00                                | 0.00    | USD      |
| DISC-1031  |  Cash discount   | 7/8/2020  |         |                                      | 7.00                                  | 0.00    | USD      |







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
