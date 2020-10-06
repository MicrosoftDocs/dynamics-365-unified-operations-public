---
# required metadata

title: Troubleshoot product receipts and invoicing
description: This topic describes how to fix issues that you might encounter while you work with product receipts and invoicing.
author: SmithaNataraj
manager: tfehr
ms.date: 09/16/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: PurchTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: smnatara
ms.search.validFrom: 2020-9-16
ms.dyn365.ops.version: Release 10.0.14

---
# Troubleshoot product receipts and invoicing

This topic describes how to fix issues that you might encounter while you work with product receipts and invoicing.

## I can't post more than one invoice for a purchase order line that has category-based items.

A quantity is mandatory if you want to post invoices. Therefore, if the full quantity of a line has been invoiced for only a partial amount, you won't be able to invoice the remaining amount on another invoice.

## I receive an "Object reference not set" error during purchase order confirmation, or an "Exception has been thrown by the target of an invocation" exception occurs during vendor invoice posting.

This issue can occur because of inconsistency in purchase order distributions.

To unblock this issue and reset the purchase order to a *Draft* state, go to **Procurement and sourcing \> Periodic tasks \> Clean up \> Purchase order distribution reset**. For more information, see the following blog post: [Resolve PO distribution errors in Dynamics 365 Supply Chain Management](https://cloudblogs.microsoft.com/dynamics365/it/2020/08/12/resolve-po-distribution-errors-in-dynamics-365-supply-chain-management/).

## I can't consolidate multiple product receipts into a single purchase order.

You can't consolidate multiple product receipts into a single purchase order if the different product receipt lines have different accounting dates.

In earlier versions of Microsoft Dynamics 365 Supply Chain Management, consolidation was allowed in this situation. However, the practice is prone to error. The accounting date on the purchase order lines that are created should not differ from the accounting date on the product receipt lines that those purchase order lines were created from. (The accounting date on the purchase order lines matches the accounting date on the purchase order header.) Therefore, the consolidation of multiple product receipts into a single purchase orders is no longer allowed.

The accounting date is used, for example, for budget reservations and encumbrance. Therefore, it should be kept during the transition from product receipt to purchase order.

## When product receipts are canceled, transactions can be posted to a suspended ledger account.

### Issue description

If a product receipt is canceled, the system allows transactions to be posted to suspended ledger accounts, even though the main accounts are suspended.

### Reproduce the issue

The following procedure shows one way to reproduce the issue.

1. On the **Accounts payable parameters** page, on the **General** tab, make sure that the **Post product receipt in ledger** option is set to *Yes*.
1. Create a purchase order, and add an order line that has a quantity of *1,000* for a product.
1. Confirm the purchase order.
1. Post the product receipt, and check the vouchers.
1. Suspend the relevant main accounts, *200140* and *140200*.
1. Cancel the posted product receipt.
1. Notice that transactions can be posted to the suspended leger accounts.

### Issue resolution

Transactions can be posted to the suspended leger accounts when product receipts are canceled, because this behavior allows for correct postings.

## A product receipt voucher number is consumed even if no financial voucher is generated during product receipt.

If the **Accrue liability on product receipt** option is set to *No* for the item model group, no postings to the general ledger will occur. However, a physical event will be recorded for the purpose of accounting in a subledger, and that event requires a voucher number. This voucher number is the voucher number that is referenced in the inventory transactions.

We recommend that you set the **Accrue liability on product receipt** option to *Yes*, as described in the following blog post: [Post Misc. charges at time of product receipt](https://cloudblogs.microsoft.com/dynamics365/no-audience/2014/11/11/post-misc-charges-at-time-of-product-receipt/).

## The Post to charge account in ledger setting isn't turned on.

### Issue description

This issue occurs when a purchase order is invoiced, if the **Post to charge account in ledger** option is set to *Yes* on the **Invoice** tab of the **Accounts payable parameters** page.

### Reproduce the issue

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

### Issue resolution

This depends on the parameter settings for invoices and invoice groups. For more information, see the following blog post: [Accounting for Purchase charge and Stock variation](https://cloudblogs.microsoft.com/dynamics365/no-audience/2014/12/15/accounting-for-purchase-charge-and-stock-variation/).
