---
title: Vendor invoice payment holds in the public sector in France
description: The standard processes related to vendor invoice payment holds in Microsoft Dynamics 365 Finance are augmented for French entities in the public sector. This article describes the vendor invoice payment holds functionality used by the public sector in France.
author: AdamTrukawka
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: France
ms.author: atrukawk
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.search.industry: Public sector
ms.search.form: PaymTerm
---

# Vendor invoice payment holds in the public sector in France

[!include [banner](../includes/banner.md)]

The standard processes related to vendor invoice payment holds in Dynamics 365 Finance are augmented for French entities in the public sector. This article describes the vendor invoice payment holds functionality used by the public sector in France.

## Set up rules for vendor invoice payment holds

Rules for vendor invoice payment holds are set up on the **Hold** FastTab on the **Terms of payment** page. Each rule has three parts:

-   A user role, such as accountant, accounting manager, or controller. Only users who are assigned the specified role can hold or release a payment under the specified terms of payment.
-   The minimum number of days that will be added to the invoice payment due date when a user with the selected role releases the hold.
-   The maximum number of times that a user with the selected role can hold a payment on each invoice. **Tip**: To allow unlimited holds, enter a large number, such as 9999.

For example, on the Net 30 term of payment, you might create two rules, one for accountants and one for directors. The rule for accountants adds a minimum of 30 days to the invoice payment due date when the hold is released, and allows a maximum of 3 holds on an invoice. The rule for directors adds a minimum of 15 days to the invoice payment due date, with a maximum of 10 holds on an invoice.

## When can I place and release vendor invoice payment holds?
Holds can be placed and released in the following circumstances:

-   Payment terms must be set up for a vendor invoice, or for all vendor invoices for a specific vendor, before you can place a hold.
-   To place or release a hold, you must be assigned to a user role where rules have been set up for payment holds.
-   If a hold is active for a vendor, you cannot release a hold for an invoice for that same vendor. You must first release the hold for the vendor.
-   You cannot release a hold unless you are the user who placed the hold, or you are assigned to the same user role as the user who placed the hold.
-   You cannot post a vendor invoice if it has a payment hold. The hold must first be released.

## Where do I place and release vendor invoice payment holds?
### For a vendor
Place or release a payment hold for all invoices for a selected vendor on the **Vendor transactions** page or the **Settle transactions** page. If you place a payment hold for a vendor, this hold includes all existing invoices for that vendor. If you release a payment hold for a vendor, this releases the payment hold only for those vendor invoices that do not have individual payment holds. For example, you place individual payment holds on two different vendor invoices for the same vendor. You later place a payment hold for that vendor. If you later release the payment hold for that vendor, it will not release the individual holds for the two vendor invoices.

### For a vendor invoice

Place or release a payment hold for a single invoice on the **Vendor invoice** page or the **Settle transactions** page.

### For a posted vendor invoice

Place or release a payment hold for a posted vendor invoice on the **Invoice journal** page.

### For all vendor invoices associated with a purchase order

Place or release a payment hold for all vendor invoices that are associated with a purchase order on the **Settle transactions** page.

## Can I settle an invoice that is on hold?
If you are assigned to the same user role as the user who placed the hold, you can clear the hold from the **Settle transactions** page and settle the vendor invoice. When you place a payment hold, the **Invoice payment hold** option is automatically selected on the **Payment** tab of the **Settle transactions** page. This prevents a vendor invoice from being settled until the hold is released.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
