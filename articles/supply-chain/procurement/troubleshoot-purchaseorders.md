---
# required metadata

title: Troubleshoot purchase orders
description: This topic describes how to fix issues that you might encounter while you work with purchase orders.
author: SmithaNataraj
manager: tfehr
ms.date: 09/16/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: PurchTable, PurchTablePart
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
# Troubleshoot purchase orders

This topic describes how to fix issues that you might encounter while you work with purchase orders.

## An action can be completed only after the line number is fully distributed.

This issue can occur because of inconsistency in purchase order distributions.

To unblock this issue and reset the purchase order to a *Draft* state, go to **Procurement and sourcing \> Periodic tasks \> Clean up \> Purchase order distribution reset**. For more information, see the following blog post: [Resolve PO distribution errors in Dynamics 365 Supply Chain Management](https://cloudblogs.microsoft.com/dynamics365/it/2020/08/12/resolve-po-distribution-errors-in-dynamics-365-supply-chain-management/).

## When purchase orders are imported through data management, purchase order line numbers don't follow the increment that defined in system parameters.

### Issue description

By default, automatically generated line numbers for purchase order lines that are imported through the *Purchase order lines V2* data entity don't use the system line number increment that is specified in system parameters. If you manually create a purchase order and add lines through the user interface (UI), the line numbers are incremented correctly. However, if you use the Data management framework (DMF), they aren't incremented correctly.

This issue occurs because, when you import lines via DMF, if line numbers aren't already assigned in the imported entity, the system uses DMF's method for assigning them. That method always increments line numbers by one.

### Issue workaround

Make sure that the desired line numbers are already given in the data entity line number fields when you import the purchase order lines. In this case, DMF won't overwrite the line numbers.

## A default tax group and a default cash discount aren't filled in from the invoice account.

If you're using an invoice account that differs from the customer account, a default tax group and a default cash discount aren't filled in from the invoice account when a purchase order is created.

This behavior is by design. The default values for the tax group, cash discounts, and other price information are based on the customer account, not the invoice account.

## I receive an "Object reference not set" error during purchase order confirmation, or an "Exception has been thrown by the target of an invocation" exception occurs during vendor invoice posting.

This issue can occur because of inconsistency in purchase order distributions.

To unblock this issue and reset the purchase order to a *Draft* state, go to **Procurement and sourcing \> Periodic tasks \> Clean up \> Purchase order distribution reset**. For more information, see the following blog post: [Resolve PO distribution errors in Dynamics 365 Supply Chain Management](https://cloudblogs.microsoft.com/dynamics365/it/2020/08/12/resolve-po-distribution-errors-in-dynamics-365-supply-chain-management/).

## One or more accounting distributions are either over-distributed or under-distributed.

### Issue description

You receive the following error: "One or more accounting distributions is either over-distributed or under-distributed."

### Issue resolution

This issue can occur because of inconsistency in purchase order distributions.

To unblock this issue and reset the purchase order to a *Draft* state, go to **Procurement and sourcing \> Periodic tasks \> Clean up \> Purchase order distribution reset**. For more information, see the following blog post: [Resolve PO distribution errors in Dynamics 365 Supply Chain Management](https://cloudblogs.microsoft.com/dynamics365/it/2020/08/12/resolve-po-distribution-errors-in-dynamics-365-supply-chain-management/).

## Can I show only purchase orders that I created?

This functionality isn't currently available.

## Can I reserve inventory and create transactions against registered inventory on a purchase order?

### Issue description

Even when items are in a *Registered* state on a purchase order, you can still reserve the inventory. In other words, you can create transactions against the registered inventory.

### Reproduce the issue

The following procedure shows one way to reproduce the issue.

1. Create a purchase order.
2. Register the purchase order line.
3. Notice that you can generate reservations or transactions against the registered inventory.

### Issue resolution

This behavior is by design. The expectation is that the registered items have physically arrived in the warehouse or inventory, and that they are therefore available for reservation.

## Purchase orders don't reflect the language settings of the legal entity.

### Issue description

The product name on a purchase order is shown in the system language instead of the language that is set for the legal entity where the purchase order was created.

### Reproduce the issue

The following procedure shows one way to reproduce the issue.

1. Set the system language to *EN-US* (US English).
1. Make sure that there is a product where the *EN-US* and *DE* (German) languages are maintained for translations of the product name.
1. Change the language of a legal entity to *DE*.
1. In the legal entity where *DE* is set as the language, create a purchase order that includes the product.
1. Notice that the product name is still shown in US English (the system language).

### Issue resolution

This behavior is by design. On purchase orders, the product is always shown in the system language. The purchase order language is used when a confirmation journal is created.

## The Approved vendor list by product entity doesn't allow the effective date to be changed.

### Issue description

A product has an approved vendor that has, for example, an effective date of January 11, 2018 (*01/11/2018*), and an expiration date of *Never*. If you try to change the effective date to January 10, 2018 (*01/10/2018*), or January 12, 2018 (*01/12/2018*), you receive the following error:

> Cannot create a record in Approved supplier list (PdsApproveVendorList). The 'Expiration' value needs to be greater than or equal to the 'Effective' value.

### Issue resolution

You can only extend the period that the vendor is approved for. The following rules apply:

- To change the effective date so that it's earlier than any of the existing records (periods) for the item vendor, the expiration date of the new period must be before all the expiration dates in the existing records.
- To change the expiration date so that it's later than any of the existing periods, the effective date must be after the latest expiration date in any existing record.
- To reduce the overall period that the vendor is approved for, you must delete or modify existing records. Alternatively, you can use the **truncate** switch during import. This switch deletes all existing records in the table for approved vendors by item.

For the example scenario that is described in the issue description, where a record has an effective date of *01/11/2018* and an expiration date of *Never*, you can import a new record that has an effective date of *01/10/2018* and an expiration date of *Never*. However, you can't reduce the period so that the effective date is updated to *01/12/2018* via data management. You must make this change through the UI.

## After I change the delivery address on a purchase order header, the delivery name isn't synced.

### Issue description

The address on the header of a purchase order is updated to an address that isn't a delivery address. Although the address is updated on the purchase order, the delivery name isn't updated based on the updated address.

### Issue resolution

This behavior is by design. The selected address must be classified as a delivery address. Otherwise, the delivery name isn't updated based on the selected address.

## Can I find the user who canceled a purchase order?

This information is tracked only if the purchase order is subject to change management. If you use change management, you can see who submitted the change (the cancellation), and who approved it.
