---
title: Advance payments that are settled during invoice posting
description: Learn about the tax that is posted on a customer advance payment when the payment is settled and the customer invoice is posted.
author: EricWangChen
ms.author: wangchen
ms.topic: concept-article
ms.date: 04/30/2026
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak 
audience: Application User 
ms.search.region: India
ms.search.validFrom: 2019-06-01
ms.search.form:
ms.dyn365.ops.version: 10.0.4
---

# Advance payments that you settle during invoice posting

[!include [banner](../../includes/banner.md)]

The following table shows the tax entries that the system generates for the invoice when you settle an advance payment in various scenarios.

| Transaction details | Example | Tax entries that the system generates during settlement |
|---|---|---|
| Invoice = Payment | Invoice amount: 12,000.00<br>Payment amount: 12,000.00 | The system posts tax on the invoice.<br>The system reverses tax on the payment to prevent a double entry in the related voucher.<br>IGST payable account Cr. 2,000.00.<br><br>**Related voucher:**<br>IGST interim payable account Cr. 2,000.00<br>IGST payable account Dr. 2,000.00 |
| Invoice < Payment | Invoice amount: 6,000.00<br>Payment amount: 12,000.00 | The system posts tax on the invoice.<br>The system reverses tax on the payment to the extent of the invoice amount in the related voucher.<br>IGST payable account Cr. 1,000.00.<br><br>**Related voucher:**<br>IGST interim payable account Cr. 1,000.00<br>IGST payable account Dr. 1,000.00 |
| Invoice > Payment | Invoice amount: 24,000.00<br>Payment amount: 12,000.00 | The system posts tax on the invoice.<br>The system reverses tax on the payment to the extent of the payment amount in the related voucher.<br>IGST payable account Cr. 4,000.00<br><br>**Related voucher:**<br>IGST interim payable account Cr. 2,000.00<br>IGST payable account Dr. 2,000.00 |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
