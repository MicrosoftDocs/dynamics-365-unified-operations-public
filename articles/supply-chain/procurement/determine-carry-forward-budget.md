---
title: Define what happens with purchase order carry-forward budget
description: This topic describes what happens with purchase order carry-forward budget when purchase orders are canceled or reduced. You can configure the system so that the associated budget is moved to the new year when carrying forward purchase orders from one year to another.
author: Henrikan
ms.date: 02/11/2022
ms.topic: article
ms.search.form: LedgerFund
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: henrikan
ms.dyn365.ops.version: Version 1611
ms.search.validFrom: 2022-02-01
---

# Define how unused carry-forward budget is reduced to reflect changes in purchase orders

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

<!-- KFM: Add intro that this is about reducing cary forward budget, ... -->

## Reduce carry-forward budget when an purchase order is reduced

This topic describes what happens with the purchase order carry-forward budget when purchase orders are canceled or reduced. You can configure the system so that the associated budget is moved to the new year when carrying forward purchase orders from one year to another. This process creates a budget register entry in the new year that represents the remaining balance of the purchase order. There are two ways to handle the carry-forward budget when a purchase order is canceled or reduced: the carry-forward budget can remain as created or it can be automatically adjusted to remove the canceled or reduced amount. The automatic budget adjustment is controlled by settings found on the fund records in the general ledger. Only purchase order lines with distributions that include a fund are available for automatic budget adjustment. The automatic budget adjustment takes place when the purchase order is finalized.

The following setup must be completed for all funds where you want to define this behavior.

1. Go to **General ledger \> Chart of accounts \> Funds \> Funds**.
1. Under **Purchase order year-end process**, **Override selected year-end option** must be set to *Yes*.
1. Under **Carry-forward budget status**, set **Reinstate the budget when a carry-forward purchase order is canceled or reduced** to one of the following values.
   - *No* – Creates a budget register entry for the remaining balance of purchase orders that have been canceled or reduced.
   - *Yes* – Allows purchase orders to be canceled or reduced without creating a budget register entry. This results in the carry-forward budget remaining available for consumption by other documents.

## Reduce carry-forward budget when an invoice is reduced

When a carry-forward purchase order is reduced during invoicing, a variance is created. Posting the invoice will reduce the purchase order encumbrance by the amount of the price variance. By default, the carry-forward budget isn't reduced in this scenario. That leaves the remaining carry-forward budget behind for the amount of the variance. Reductions include price variances, charge variances, and tax variances. This feature can be set up to create a budget register entry to remove excess carry-forward budget. <!-- KFM: Where is this feature? Do we need to enable it in feature management? I couldn't find it there. -->

### Enable this functionality

<!-- KFM: (I'll write this...) You can automatically remove remaining carry-forward budget in this scenario using the feature *Reduce carry-forward budget when an invoice is reduced*. If you need to be able to cary forward budget when an invoice is reduced, then xxxxx
 -->

### Cary forward budget after reducing an invoice

Once the feature is enabled, the same fund setup that was defined earlier will be used. This setup is defined below and must be completed for any funds that you want to allow to reduce carry-forward budget when an invoice price is reduced.

1. Open **General ledger \> Chart of accounts \> Funds \> Funds**.
1. Under **Purchase order year-end process**, set **Override selected year-end option** to *Yes*.
1. Under **Carry-forward budget status**, set **Reinstate the budget when a carry-forward purchase order is canceled or reduced** to one of the following values.
   - *No* – Creates a budget register entry against the purchase order for the variance reduction amount.
   - *Yes* – Allows the invoice reduction without the creation of a budget register entry. This results in the carry-forward budget remaining available for consumption by other documents.

<!-- KFM: This seems to repeat the previous section. What is going on? -->