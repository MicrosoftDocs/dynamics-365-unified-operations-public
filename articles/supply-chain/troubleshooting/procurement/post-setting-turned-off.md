---
title: The Post to charge account in ledger setting isn't turned on
description: This issue occurs when a purchase order is invoiced, if the "Post to charge account in ledger" option is enabled on the "Invoice" tab of the "Accounts payable parameters" page
author: kamaybac
ms.date: 05/31/2021
ms.topic: troubleshooting
ms.search.form: PurchTable, PurchTablePart
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yanansong
ms.search.validFrom: 2021-05-31
ms.dyn365.ops.version: 10.0.13
---

# The Post to charge account in ledger setting isn't turned on

## Symptoms

This issue occurs when a purchase order is invoiced, if the **Post to charge account in ledger** option is set to *Yes* on the **Invoice** tab of the **Accounts payable parameters** page.

## Reproduce the issue

The following procedure shows one way to reproduce the issue.

1. Go to **Accounts payable \> Setup \> Accounts payable parameters**.
1. On the **Invoice** tab, set the **Post to charge account in ledger** option to *Yes*.
1. Go to **Inventory management \> Setup \> Posting \> Posting**.
1. On the **Purchase order** tab, make sure that you've deleted all the lines in the purchase expenditure for the product.
1. Go to **Accounts payable \> Purchase orders \> All purchase orders**.
1. Create a purchase order. In the **Vendor account** field, select *1001 Acme Office Supplies*.
1. Add a purchase order line that has the following settings:

    - **Item number:** *D0011 Laser Projector*
    - **Site:** *1*
    - **Warehouse:** *11*
    - **Quantity:** *4*

1. On the Action Pane, on the **Purchase** tab, in the **Action** group, select **Confirm**.
1. On the Action Pane, on the **Receive** tab, in the **Generate** group, select **Product receipt**.
1. In the **Posting product receipt** dialog box, in the **Product receipt** field, enter an arbitrary number, and then select **OK**.
1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
1. In the **Number** field, enter an arbitrary number as the invoice number.
1. Update the match status, and post.
1. Notice that you now receive the following error when you generate an invoice from a purchase order: "Account number for transaction type Purchase expenditure for product does not exist."

## Resolution

This depends on the parameter settings for invoices and invoice groups. For more information, see the following blog post: [Accounting for Purchase charge and Stock variation](https://cloudblogs.microsoft.com/dynamics365/no-audience/2014/12/15/accounting-for-purchase-charge-and-stock-variation/).
