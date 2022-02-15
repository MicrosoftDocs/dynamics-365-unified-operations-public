---
title: Update the carry-forward budget after reductions in purchase orders and invoices
description: This topic describes how to control what happens to the carry-forward budget when purchase orders are canceled or reduced, and when invoices are reduced.
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

# Update the carry-forward budget after reductions in purchase orders and invoices

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes how to control what happens to the carry-forward budget when purchase orders are canceled or reduced, and when invoices are reduced.

For details about how purchase orders are processed at year end, see [Process purchase orders at year end](/dynamicsax-2012/appuser-itpro/process-purchase-orders-at-year-end).

## Turn carry-forward budget reductions for invoice variances on or off

The system is always able to update the cary-forward budget when a purchase order is cancelled or reduced. However, if you would also like the system to update the cary-forward budget when an invoice is reduced, the *Reduce carry-forward budget when an invoice against a purchase order is reduced with a variance* feature must be turned on for your system. Admins can turn this feature on or off by searching for it in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

## Purchase order reductions and cancellations

Regardless of whether the *Reduce carry-forward budget when an invoice against a purchase order is reduced with a variance* feature is turned on for your system, the system can always update the carry-forward budget when a qualifying purchase order is reduced or cancelled. You can set each general ledger fund to respond in either of the following two ways:

- Preserve the carry-forward budget as created.
- Automatically adjust the carry-forward budget to remove the canceled or reduced amount.

Only purchase order lines with distributions that include a fund are available for automatic budget adjustment. The automatic budget adjustment takes place when the purchase order is finalized or when a purchase order reduction is confirmed.

## Invoice reductions

When the *Reduce carry-forward budget when an invoice against a purchase order is reduced with a variance* feature is turned on for your system, you can set whether each fund should also reduce the carry-forward budget when an invoice is reduced in addition to when a purchase order is reduced or cancelled. The invoice must be for a purchase order with carry-forward budget. Reductions include price variances, charge variances, and tax variances. When a carry-forward purchase order is reduced during invoicing, a variance is created. Posting the invoice will reduce the purchase order encumbrance by the amount of the variance. This feature will also create the automatic budget adjustment for the amount of the variance.

When the *Reduce carry-forward budget when an invoice against a purchase order is reduced with a variance* feature is turned off, the carry-forward budget isn't reduced in this scenario. That leaves the remaining carry-forward budget behind for the amount of the variance.

## Configure the cary-forward budget options for each fund

Make the following settings for each general ledger fund that you want to allow to reduce carry-forward budget when a purchase order or invoice is reduced.

1. Go to **General ledger \> Chart of accounts \> Funds \> Funds**.
1. Under **Purchase order year-end process**, **Override selected year-end option** must be set to *Yes*.
1. Under **Carry-forward budget status**, set the **Reinstate the budget when a carry-forward purchase order is canceled or reduced** field as needed. The settings have slightly different effects, depending on whether or not the *Reduce carry-forward budget when an invoice against a purchase order is reduced with a variance* feature is turned on for your system.
   - When the feature is turned off, the system only reacts to cancelled or reduced purchase orders and the options work as follows:
       - *No* – Creates a budget register entry for the remaining balance of purchase orders that have been canceled or reduced.
       - *Yes* – Allows purchase orders to be canceled or reduced without creating a budget register entry. This results in the carry-forward budget remaining available for consumption by other documents.
   - When the feature is turned on, the system reacts both to invoice variances and cancelled or reduced purchase orders. The options work as follows:
       - *No* – For invoice variances, the system creates a budget register entry against the purchase order for the variance reduction amount. For cancelled or reduced purchase orders, this option works the same as when the feature is turned off (as described previously).
       - *Yes* – For invoice variances, the system allows the invoice reduction without the creation of a budget register entry. This results in the carry-forward budget remaining available for consumption by other documents. For cancelled or reduced purchase orders, this option works the same as when the feature is turned off (as described previously).
