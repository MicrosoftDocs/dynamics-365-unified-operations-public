---
title: Update the carry-forward budget after reductions in purchase orders and invoices
description: Learn how to control what happens to the carry-forward budget when purchase orders are canceled or reduced, and when invoices are reduced.
author: music727 
ms.author: mibeinar
ms.topic: article
ms.date: 7/23/2024
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2022-02-01
ms.search.form: LedgerFund
ms.dyn365.ops.version: Version 1611
---

# Update the carry-forward budget after reductions in purchase orders and invoices

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article describes how to control what happens to the carry-forward budget when purchase orders are canceled or reduced, and when invoices are reduced.

For information about how purchase orders are processed at year-end, see [Process purchase orders at year-end](/dynamicsax-2012/appuser-itpro/process-purchase-orders-at-year-end).

## Turn carry-forward budget reductions for invoice variances on or off

The carry-forward budget can always be updated when a purchase order is canceled or reduced, and when an invoice is reduced.

## Purchase order reductions and cancellations

The carry-forward budget is updated when a qualifying purchase order is canceled or reduced. You can set each general ledger fund to respond in one of the following ways:

- Preserve the carry-forward budget as it was created.
- Automatically adjust the carry-forward budget to remove the canceled or reduced amount.

Only purchase order lines that have distributions that include a fund are available for automatic budget adjustment. The automatic budget adjustment occurs when the purchase order is finalized or a purchase order reduction is confirmed.

## Invoice reductions

You can specify whether each fund should reduce the carry-forward budget when an invoice is reduced, in addition to when a purchase order is reduced or canceled. The invoice must be for a purchase order that has carry-forward budget. Reductions include price variances, charge variances, and tax variances. When a carry-forward purchase order is reduced during invoicing, a variance is created. When the invoice is posted, the purchase order encumbrance is reduced by the amount of the variance. The automatic budget adjustment is created for the amount of the variance.

## Configure the carry-forward budget options for each fund

For each general ledger fund that reduces the carry-forward budget when a purchase order or invoice is reduced, follow these steps.

1. Go to **General ledger \> Chart of accounts \> Funds \> Funds**.
2. Select the fund that you want to set up.
3. Under **Purchase order year-end process**, select the **Override selected year-end option** option.
4. Under **Carry-forward budget status**, set the **Reinstate the budget when a carry-forward purchase order is canceled or reduced** field as needed.

The option settings work in the following way:

- **No** – For invoice variances, a budget register entry is created against the purchase order for the amount of the variance reduction. For canceled or reduced purchase orders, a budget register entry is created for the remaining balance.
- **Yes** – For invoice variances, the invoice reduction is allowed, but it doesn't create a budget register entry. The carry-forward budget remains available for consumption by other documents. For canceled or reduced purchase orders, the cancellation or reduction is allowed, but it doesn't create a budget register entry. The carry-forward budget remains available for consumption by other documents.

## Additional resources

- [Process purchase orders at year end](/dynamicsax-2012/appuser-itpro/process-purchase-orders-at-year-end)
- [Maintain general budget reservations](general-budget-reservation-tasks.md)
- [Funds in the public sector](funds-public-sector.md)
- [Set up a fund in the public sector](tasks/set-up-fund-public-sector.md)
