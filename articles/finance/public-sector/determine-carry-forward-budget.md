---
title: Update the carry-forward budget after reductions in purchase orders and invoices
description: This article describes how to control what happens to the carry-forward budget when purchase orders are canceled or reduced, and when invoices are reduced.
author: TaylorVH 
ms.date: 02/11/2022
ms.topic: article
ms.search.form: LedgerFund
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: v-savanh
ms.dyn365.ops.version: Version 1611
ms.search.validFrom: 2022-02-01
---

# Update the carry-forward budget after reductions in purchase orders and invoices

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article describes how to control what happens to the carry-forward budget when purchase orders are canceled or reduced, and when invoices are reduced.

For information about how purchase orders are processed at year end, see [Process purchase orders at year end](/dynamicsax-2012/appuser-itpro/process-purchase-orders-at-year-end).

## Turn carry-forward budget reductions for invoice variances on or off

The system can always update the carry-forward budget when a purchase order is canceled or reduced. However, if you want to update the carry-forward budget when an invoice is reduced, you must turn on the *Reduce carry-forward budget when an invoice against a purchase order is reduced with a variance* feature. Admins can turn this feature on or off by searching for it in the **[Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md)** workspace.

## Purchase order reductions and cancellations

Regardless of whether the *Reduce carry-forward budget when an invoice against a purchase order is reduced with a variance* feature is turned on, the carry-forward budget will be updated when a qualifying purchase order is canceled or reduced. You can set each general ledger fund to respond in one of the following ways:

- Preserve the carry-forward budget as it was created.
- Automatically adjust the carry-forward budget to remove the canceled or reduced amount.

Only purchase order lines that have distributions that include a fund are available for automatic budget adjustment. The automatic budget adjustment occurs when the purchase order is finalized or a purchase order reduction is confirmed.

## Invoice reductions

When the *Reduce carry-forward budget when an invoice against a purchase order is reduced with a variance* feature is turned on, you can specify whether each fund should reduce the carry-forward budget when an invoice is reduced, in addition to when a purchase order is reduced or canceled. The invoice must be for a purchase order that has carry-forward budget. Reductions include price variances, charge variances, and tax variances. When a carry-forward purchase order is reduced during invoicing, a variance is created. When the invoice is posted, the purchase order encumbrance will be reduced by the amount of the variance. The feature will also create the automatic budget adjustment for the amount of the variance.

When the *Reduce carry-forward budget when an invoice against a purchase order is reduced with a variance* feature is turned off, the carry-forward budget isn't reduced in this scenario. Therefore, the remaining carry-forward budget for the amount of the variance is left behind.

## Configure the carry-forward budget options for each fund

Follow these steps for each general ledger fund that should be able to reduce carry-forward budget when a purchase order or invoice is reduced.

1. Go to **General ledger \> Chart of accounts \> Funds \> Funds**.
1. Select the fund that you want to set up.
1. Under **Purchase order year-end process**, make sure that the **Override selected year-end option** option is set to *Yes*.
1. Under **Carry-forward budget status**, set the **Reinstate the budget when a carry-forward purchase order is canceled or reduced** field as you require. The settings have slightly different effects, depending on whether the *Reduce carry-forward budget when an invoice against a purchase order is reduced with a variance* feature is turned on in your system.

    - When the feature is turned off, the system reacts only to canceled or reduced purchase orders. The option settings work in the following way:

        - *No* – The system creates a budget register entry for the remaining balance of purchase orders that have been canceled or reduced.
        - *Yes* – The system allows purchase orders to be canceled or reduced, but doesn't create a budget register entry. The carry-forward budget remains available for consumption by other documents.

    - When the feature is turned on, the system reacts both to invoice variances and to canceled or reduced purchase orders. The option settings work in the following way:

        - *No* – For invoice variances, the system creates a budget register entry against the purchase order for the variance reduction amount. For canceled or reduced purchase orders, this setting has the same effect that it has when the feature is turned off.
        - *Yes* – For invoice variances, the system allows the invoice reduction but doesn't create a budget register entry. The carry-forward budget remains available for consumption by other documents. For canceled or reduced purchase orders, this setting has the same effect that it has when the feature is turned off.

## Additional resources

- [Process purchase orders at year end](/dynamicsax-2012/appuser-itpro/process-purchase-orders-at-year-end)
- [Maintain general budget reservations](general-budget-reservation-tasks.md)
- [Funds in the public sector](funds-public-sector.md)
- [Set up a fund in the public sector](tasks/set-up-fund-public-sector.md)
