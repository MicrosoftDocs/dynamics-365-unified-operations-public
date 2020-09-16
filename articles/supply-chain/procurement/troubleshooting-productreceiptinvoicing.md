---
# required metadata

title: Troubleshoot product receipt and invoicing
description: This topic describes how to fix issues that you might encounter while working with Product Receipts and Invoicing.
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
# Troubleshoot product receipt and invoicing

This topic describes how to fix common issues that you might encounter while working with product receipt and invoicing.

## Unable to post more than one invoice for a purchase order line with category based items

Quantity is mandatory for posting invoices. Therefore, if the full quantity of a line has been invoiced for only a partial amount, you won't be able to invoice the remaining amount in another invoice.

## "Object reference not set" error seen during purchase order confirmation, or "Exception has been thrown by the target of an invocation", exception thrown during vendor invoice posting

This issue may occur due to inconsistency in purchase order distributions.

To unblock this issue and reset the purchase order to a *Draft* state, go to **Procurement and sourcing > Periodic tasks > Clean up > Purchase order distribution reset**. For more information, see the blog post [Resolve PO distribution errors in Dynamics 365 Supply Chain Management](https://cloudblogs.microsoft.com/dynamics365/it/2020/08/12/resolve-po-distribution-errors-in-dynamics-365-supply-chain-management/).

## Can't consolidate multiple product receipts into a single purchase order

You can't consolidate multiple product receipts into a single purchase order when the different product receipt lines have different accounting dates.

This was permitted in earlier versions of Supply Chain Management, but this practice is prone to error. The accounting date on the created purchase order lines (which is the same as the accounting date on the header of the purchase order) shouldn't be different from the accounting date on the product receipts line from which the purchase order line was created. Therefore, the consolidation of multiple product receipts into a single purchase orders is no longer allowed.

The accounting date is used, for example, for budget reservations and encumbrance, so this should be kept when transitioning from product receipt to purchase order.

## Cancelling product receipts allows transactions to be posted to a suspended ledger account

### Issue description

The system allows transactions to be posted to suspended ledger accounts on cancelling a product receipt even though the main accounts are "suspended".

### Reproduce the issue

One way to reproduce this issue is do the following:

1. Ensure that the **Post product receipt in ledger** option is enabled on the **Accounts payable parameters** page **General** tab.
1. Create a purchase order and add an order line with quantity of 1000 for a product. Confirm the purchase order.
1. Post the product receipt and check the vouchers.
1. Suspend the relevant main accounts 200140 and 140200.
1. Cancel the posted product receipt.
1. Note that this allows posting transactions to the suspended leger accounts.

### Issue resolution

This is allowed because it enables correct postings.

## Product receipt voucher number is consumed even if no financial voucher is generated during product receipt

When the **Accrue liability on product receipt** is set to *OFF* on the item model group, no postings to the general ledger will occur. However, there is a physical event that is recorded for the purpose of accounting in a subledger, and that needs a voucher number. This is what is referenced in the inventory transactions.

In the following blog post, we recommend setting **Accrue liability on product receipt** to *Yes*: [Post Misc. charges at time of product receipt](https://cloudblogs.microsoft.com/dynamics365/no-audience/2014/11/11/post-misc-charges-at-time-of-product-receipt/)

## The "Post to charge account in ledger" setting isn't active

### Issue description

This issue occurs upon invoicing a purchase order, when **Post to charge account in ledger** is set to *Yes* on the **Accounts payable parameters** page **Invoice** tab.

### Reproduce the issue

One way to reproduce this issue is do the following:

1. Go to **Accounts payable > Setup >Accounts payable parameters**. Open the **Invoice** tab and set **Post to charge account in ledger** to *Yes*.
1. Go to **Inventory Management > Setup > Posting > Posting** and open the **Purchase Order** tab.
1. Make sure you have deleted all of the lines in purchase expenditure for product.
1. Go to **Accounts payable > Purchase orders > All purchase orders** and create a new purchase order. For the **Vendor account**, select *1001 Acme Office Supplies*.
1. Add a purchase order line with the following settings:
    - **Item number** - *D0011 Laser Projector*
    - **Site** - *1*
    - **Warehouse** - *11*
    - **Quantity** - *4*
1. On the Action Pane, open the **Purchase** tab and, from the **Action** group, select **Confirm**.
1. On the Action Pane, open the **Receive** tab and, from the **Generate** group, select **Product receipt**.
1. On the **Posting product receipt** dialog box, enter an arbitrary number for **Product receipt** and select **OK**.
1. On the Action Pane, open the **Invoice** tab and, from the **Generate** group, select **Invoice**.
1. Enter an arbitrary number for the invoice **Number**.
1. Update the match status and post.
1. Note that the error "Account number for transaction type Purchase expenditure for product does not exist" is now shown when we generate an invoice form a purchase order.

### Issue fix

This is dependent on the parameter settings for invoices and invoice groups. See this blog bost ofr rull details: [Accounting for Purchase charge and Stock variation](https://cloudblogs.microsoft.com/dynamics365/no-audience/2014/12/15/accounting-for-purchase-charge-and-stock-variation/).

## Additional resources

[Product receipts against purchase orders](product-receipt-against-purchase-orders.md)  
[Vendor Invoicing](vendor-invoices-overview.md)
