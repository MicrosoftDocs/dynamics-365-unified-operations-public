---
title: Resolve sales tax differences
description: Learn how to resolve sales tax differences between purchase orders and invoices, which you must verify are correct for vendor invoices.
author: kailiang
ms.author: kailiang
ms.topic: how-to
ms.date: 07/31/2026
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: 
ms.search.validFrom: 2022-09-02
ms.search.form: 
ms.dyn365.ops.version:
---

# Resolve sales tax differences

[!include [banner](../includes/banner.md)]

Sometimes, the sales tax for a purchase order and the sales tax for the corresponding vendor invoice differ. In this case, you must verify that the sales tax codes and sales tax amounts are correct for the vendor invoice.

> [!NOTE]
> If you need to make changes, make them on the invoice lines before you change the sales tax information on the **Sales tax transactions** page. These changes include changes that might affect the sales tax calculations, such as changes to unit prices and quantities. It's especially important that you make any required changes to tax groups for invoice lines first. If you change tax groups for invoice lines, the system might recalculate previous changes that you made on the **Sales tax transactions** page.

## Sales tax total amounts differ on the purchase order and vendor invoice

The sales tax total amounts for the purchase order and for the vendor invoice that you receive from the vendor might differ. If **Invoice totals invoice matching** is enabled, these differences can cause a matching discrepancy. If the **Post invoice with discrepancies** field on the **Accounts payable parameters** page is set to **Require approval**, and you're authorized, you can approve the matching variance. As required, you can change a tax group for the invoice or correct the tax amounts for the invoice.

1. Go to **Accounts payable** > **Vendor invoices** > **Pending vendor invoices**.
1. Select and open an invoice.
1. On the **Vendor invoice** page, on the Action Pane, on the **Financials** tab, select **Sales tax**.
1. Compare the sales tax codes on the **Sales tax transactions** page with the sales tax codes on the invoice that you received from the vendor. If the invoice from the vendor includes sales tax codes that differ from the sales tax codes for the purchase order, determine whether the purchase order or the invoice is correct.

    - If the purchase order is correct, you can put the invoice on hold until the vendor provides a new invoice. You can then post the invoice. For information about how to put an invoice on hold, see Key tasks: Vendor invoices.
    - If the invoice from the vendor is correct, follow these steps:

        1. Close the **Sales tax transactions** page.
        1. On the **Vendor invoice** page, select different tax groups for one or more invoice lines.
        1. On the Action Pane, on the **Financials** tab, select **Sales tax**.

1. Compare the sales tax amounts on the **Sales tax transactions** page with the sales tax amounts on the invoice that you received from your vendor. If the invoice from the vendor includes sales tax amounts that differ from the sales tax amounts for the purchase order, determine whether the purchase order or the invoice is correct.

    - If the purchase order is correct, you can put the invoice on hold until the vendor provides a new invoice. Then move on to step 6.
    - If the invoice from the vendor is correct, follow these steps:

        1. On the **Adjustment** tab, in the **Total calculated sales tax amount** field, enter the correct sales tax amount.

            - If there's a difference for a special line, set the **Adjust sales tax** field to **Detail**.
            - If an adjustment is required for a negative line, update a corresponding tax code amount with a negative amount.

        1. Select the **Override calculated sales tax** checkbox.
        1. Optional: If the tax rate for the sales tax code is incorrect, the calculated sales tax amount might be incorrect. Verify the tax rate on the **Sales tax codes** page by going to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax codes**.

1. Close the **Sales tax transactions** page.
1. On the **Vendor invoice** page, save or post the invoice.

## Sales tax codes differ on the purchase order and vendor invoice

The sales tax codes for the purchase order and the vendor invoice might differ. You can change a tax group for the invoice, delete any sales tax codes that aren't derived from the tax groups for the invoice, or reset the actual sales tax amount to the calculated amount.

1. Go to **Accounts payable** > **Vendor invoices** > **Pending vendor invoices**.
1. Select and open an invoice.
1. On the **Vendor invoice** page, on the Action Pane, on the **Financials** tab, select **Sales tax**.
1. Compare the sales tax codes on the **Sales tax transactions** page with the sales tax information on the invoice that you received from the vendor. If the invoice from the vendor includes sales tax codes that differ from the sales tax codes for the purchase order, determine whether the purchase order or the invoice is correct.

    - If the purchase order is correct, put the invoice on hold until the vendor provides a new invoice. When you receive the new invoice, verify the invoice matching information, and then save or post the invoice.
    - If the invoice from the vendor is correct, complete one or more of the following procedures.

      ### Change tax groups for the invoice

        1. Close the **Sales tax transactions** page.
        1. On the **Vendor invoice** page, select different tax groups for one or more invoice lines.
        1. On the Action Pane, on the **Financials** tab, select **Sales tax**.

      ### Delete non-derived sales tax codes

        - On the **Sales tax transactions** page, delete any sales tax code lines that aren't included in the tax groups for the invoice lines. Sales tax code lines might not be included if, for example, the invoice was created by a service. If the **Keep sales tax adjustments for PO invoices** option is selected on the **Accounts payable parameters** page, you can't post transactions if they include sales tax code lines that aren't derived from the intersection of the tax groups. Therefore, only sales tax code lines that are included in both the sales tax group and the item tax group for the invoice line can be posted.

      ### Reset actual amounts to the calculated amounts

        1. On the **Sales tax transactions** page, on the **Adjustment** tab, select **Reset actuals to calculated**.
        1. Review the sales tax code lines. As required, change the amount in the **Actual sales tax amount** field, and then select the **Override calculated sales tax** checkbox.
