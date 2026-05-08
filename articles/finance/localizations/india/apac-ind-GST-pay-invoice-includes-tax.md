---
title: Payment of invoices that include tax
description: Learn about payment of an invoice that includes tax, including a step-by-step process and outline on validating financial entries.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/30/2026
ms.reviewer: johnmichalak 
ms.search.region: India
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4
---

# Payment of invoices that include tax

[!include [banner](../../includes/banner.md)]

To post an invoice that includes sales tax, follow these steps:

1. Go to **Accounts receivable \> Payments \> Payment journal**.
1. Create a record.
1. In the **Name** field, select a value.
1. On the **Setup** tab, select the **Amounts include sales tax** check box.
1. Select **Lines**.
1. Create a customer advance payment journal.
1. Select **Functions \> Settlement**.
1. In the **Invoice** field, select a value.
1. Close the page.
1. Save the record.
1. Select **Post \> Post**.
1. Close the message that you receive.

### Validate financial entries

Validate the financial entries by selecting **Inquiries \> Voucher**.

The following table shows the tax entries that are generated when an invoice payment is made in various scenarios.

| Transaction details | Example | Tax entries that are generated during settlement |
|---|---|---|
| Invoice = Payment | Invoice amount: 12,000.00 Payment amount: 12,000.00 | No tax entries are generated. |
| Invoice < Payment | Invoice amount: 6,000.00 Payment amount: 12,000.00 Note that if either a Harmonized System of Nomenclature (HSN) code or a Services Accounting Code (SAC) is defined for the journal, tax is calculated and posted on the journal amount. | Tax is calculated and posted on the payment amount. Tax on the payment is reversed to the extent of the invoice amount in the related voucher. IGST interim payable account Dr. 2,000.00. IGST payable account Cr. 2,000.00. **Related voucher** IGST interim payable account Cr. 1,000.00 IGST payable account Dr. 1,000.00 |
| Invoice > Payment | Invoice amount: 24,000.00 Payment amount: 12,000.00 without tax | No tax entries are generated. |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
