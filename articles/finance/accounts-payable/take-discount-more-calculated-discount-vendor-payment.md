---
# required metadata

title: Take more than the calculated discount for a vendor payment
description: This article walks you through a scenario where a cash discount is taken for an amount that is more than the discount that was originally available on the invoice. This scenario might occur if an organization comes to an agreement with the vendor to pay a smaller amount on the invoice. 
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
ms.custom: 14281
ms.assetid: 7f0a4197-95dd-4969-ade9-154815cf659e
ms.search.region: Global
# ms.search.industry: 
ms.author: angelading
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Take more than the calculated discount for a vendor payment

[!include [banner](../includes/banner.md)]

This article walks you through a scenario where a cash discount is taken for an amount that is more than the discount that was originally available on the invoice. This scenario might occur if an organization comes to an agreement with the vendor to pay a smaller amount on the invoice. 

Vendor 3051 gives Fabrikam a cash discount of 4 percent if an invoice is paid in seven days. On June 29, April enters an invoice for 1,000.00. The vendor lets April take a discount of 60.00 instead of the default discount of 40.00 that is available for the invoice. April records a one-off payment by using the Accounts payable payment journal and enters the vendor for the payment. April then opens the **Settle transactions** page and marks the invoice and changes the value in the **Cash discount amount** field to **60.00**.

| Mark     | Use cash discount | Voucher   | Account | Date      | Due date  | Invoice | Amount in transaction currency | Currency | Amount to settle |
|----------|-------------------|-----------|---------|-----------|-----------|---------|--------------------------------|----------|------------------|
| Selected | Normal            | Inv-10040 | 3051    | 6/29/2020 | 7/29/2020 | 10040   | 1,000.00                       | USD      | 940.00           |

Discount information appears at the bottom of the **Settle transactions** page.

| Field                        | Value     |
|------------------------------|-----------|
| Cash discount date           | 7/12/2020 |
| Cash discount amount         | 60.00     |
| Use cash discount            | Normal    |
| Cash discount taken          | 0.00      |
| Cash discount amount to take | 60.00     |

April posts the payment journal. The invoice is fully settled by using a payment of 940.00 and a discount of 60.00.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
