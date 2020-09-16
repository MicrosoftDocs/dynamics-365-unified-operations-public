---
# required metadata

title: Troubleshoot purchase orders
description: This topic describes how to fix issues that you might encounter while working with purchase orders.
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
# Troubleshoot purchase orders

This topic describes how to fix common issues that you might encounter while working with purchase orders.

## This action can only be completed after the line number is fully distributed

This issue may occur due to inconsistencies in purchase order distributions.

To unblock this issue and reset the purchase order to a *Draft* state, go to **Procurement and sourcing > Periodic tasks > Clean up > Purchase order distribution reset**. For more information, see the blog post [Resolve PO distribution errors in Dynamics 365 Supply Chain Management](https://cloudblogs.microsoft.com/dynamics365/it/2020/08/12/resolve-po-distribution-errors-in-dynamics-365-supply-chain-management/).

## Purchase order line numbers don't follow the increment defined in system parameters when purchase orders are imported through data management

### Issue description

Auto-generated line numbers for purchase order lines imported through the data entity "Purchase order lines V2" don't default to system line number increment specified in system parameters. When you create a purchase order and add lines manually through user interface, the line numbers increment correctly. However, when using the data management framework (DMF), they don't.

This occurs because, when importing lines via the data management framework (DMF), the system uses the data management framework's methods of assigning line numbers when they aren't already assigned in the imported entity. That method always increments by 1.

### Workaround

Make sure that the desired line numbers are already given in the entity data when importing the purchase order lines. Then they won't be overwritten by the data management framework.

## Tax group and cash discount are not defaulted from the invoice account

If you are using an invoice account that differs from the customer account, when a purchase order is created, the tax group and cash discount are not defaulted from the invoice account.

This is by design. The default values for tax group, cash discounts and other price information is based on the customer account and not the invoice account.

## "Object reference not set" error is shown while confirming a purchase order, or "Exception has been thrown by the target of an invocation" occurs during vendor invoice posting

This issue could occur due to inconsistency in purchase order distributions.

To unblock this issue and reset the purchase order to a *Draft* state, go to **Procurement and sourcing > Periodic tasks > Clean up > Purchase order distribution reset**. For more information, see the blog post [Resolve PO distribution errors in Dynamics 365 Supply Chain Management](https://cloudblogs.microsoft.com/dynamics365/it/2020/08/12/resolve-po-distribution-errors-in-dynamics-365-supply-chain-management/).

## One or more accounting distributions is either over-distributed or under-distributed

### Issue description

You see the error "One or more accounting distributions is either over-distributed or under-distributed."

### Issue fix

This issue can occur due to inconsistency in purchase order distributions.

To unblock this issue and reset the purchase order to a *Draft* state, go to **Procurement and sourcing > Periodic tasks > Clean up > Purchase order distribution reset**. For more information, see the blog post [Resolve PO distribution errors in Dynamics 365 Supply Chain Management](https://cloudblogs.microsoft.com/dynamics365/it/2020/08/12/resolve-po-distribution-errors-in-dynamics-365-supply-chain-management/).

## Can I show only purchase orders created by me?

This functionality is not currently available.

## Able to reserve inventory and transact against registered inventory on a purchase order

### Issue description

When items are in the *Registered* state on a purchase order, it is still possible to reserve the inventory. In other words, it is possible to create transactions against the registered inventory.

### Reproduce the issue

One way to reproduce this issue is do the following:

1. Create a purchase order.
2. Register the purchase order line.
3. Note that it is possible to generate reservations or transactions against the registered inventory.

### Issue resolution

This is by design. The registered items are expected to have physically arrived in the warehouse or inventory, hence they are available for reservation.

## Language settings on the legal entity aren't reflected in purchase orders

### Issue description

The product name in a purchase order is shown using the system language rather than the language set for the legal entity in which the purchase order was created.

### Reproduce the issue

One way to reproduce this issue is do the following:

1. Set the system language to *EN-US* (US English).
1. Make sure there is a product that has languages *EN-US* and *DE* (German) maintained for translations for the product name.
1. Change the language of a legal entity to *DE*.
1. Create a  purchase order with this product in the legal entity where *DE* is set as the language.
1. Note that the product name is still shown in US English, which matches the system language.

### Issue resolution

This is by design. On purchase orders, the product is always show in the system language. When a confirmation journal is created, then the purchase order language is used.

## Approved vendor list by product entity doesn't allow the effective date to be changed

### Issue description

Suppose a product has an approved vendor with effective date *01/11/2018* and expiration date *Never*, but if you try to change the effective date to *01/10/2018* or *01/12/2018*, the following error is shown:

> Cannot create a record in Approved supplier list (PdsApproveVendorList). The 'Expiration' value needs to be greater than or equal to the 'Effective' value.

### Issue fix

It is only possible to extend the period that the vendor is approved for. The following rules apply:

- To bring the effective date to an earlier date than any of the existing records (periods) given for that item vendor, the expiration date on the new period must be before any of the expiration dates in the existing records.
- To bring the expiration date to a later date than any of the existing periods, the effective date must be after the latest expiration date of any existing record.
- To reduce the overall time period that the vendor is approved, you must either delete records or modify existing records&mdash;or use the truncate switch when importing, which deletes all existing records in the table for approved vendors by item.

For the example scenario described in the issue description, where there is a record of effective date *01/11/2018* and expiration date *Never*, it would be possible to import a new record with effective date *01/10/2018* and expiration date before *Never*. However it isn't possible to reduce the period so that the effective date is updated to *01/12/2018* via data management. You would have to do this through the user interface.

## After changing the delivery address on the purchase order header, the delivery name isn't synchronized

### Issue description

The address on the header of a purchase order is updated to an address that is not a delivery address. The address updates on the purchase order, but the delivery name doesn't update based on the updated address.

### Issue resolution

This is by design. Only if the selected address is classified as a delivery address will the delivery name also be updated according to the selected address. Otherwise, the delivery name isn't updated.

## Is it possible to find the user who cancelled a purchase order?

This information is not tracked unless the purchase order is under change management. If you use change management, then you can see who submitted the change (a cancellation) and who approved it.

## Additional resources

[Get started with Purchase Orders](purchase-order-overview.md)  
[Creation of Purchase Orders](create-purchase-order.md)
