---
# required metadata

title: Troubleshoot Purchase orders
description: This topic describes how to fix issues that you might encounter while working with Purchase Orders.
author: SmithaNataraj
manager: tfehr
ms.date: 05/07/2020
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
ms.search.validFrom: 2020-5-7
ms.dyn365.ops.version: AX 10.0.14

---
# Troubleshoot Purchase Orders 

This topic describes how to fix common issues that you might encounter while working with Purchase Orders.

## This action can only be completed after the line number %1 is fully distributed.

This is an issue that could occur due to inconsistency in purchase order distributions. 

**Resolution**
It is possible to unblock the above issues and reset the purchase order to a draft state using Procurement and Sourcing > Periodic Task > Clean up > Purchase Order Distribution Reset. See more in the blog[Resolve PO distribution errors in Dynamics 365 Supply Chain Management](https://cloudblogs.microsoft.com/dynamics365/it/2020/08/12/resolve-po-distribution-errors-in-dynamics-365-supply-chain-management/).

## Purchase order Line Numbers are not following the increment defined in system parameter, when purchase orders are imported through data management (DMF)
The line numbers for imported purchase order lines through data entity "Purchase order lines V2" are not defaulting to system line number increment specified in system parameters when adding auto-generated line numbers in DMF. When you create a PO and add lines manually through UI, it is correctly incrementing. However, when using DMF it is not.

**Resolution**
When importing the lines via the Data Management framework it will use the data management frameworks methods of assigning line numbers, when the line number is not already assigned in the imported entity. And that method is increments of 1.

**Workaround**
A way to do this could be to make sure that the desired line numbers are already given in the entity data when importing the purchase order line, then they will not be overwritten by the data management framework.

## Tax group and Cash discount are not defaulted from Invoice account
The customer has a different invoice account than the customer account. When a Purchase order is created, Tax group and Cash discount are not defaulted from the Invoice account. 

**Resolution**
The defaulting of of tax group, cash discounts and other price information that should be defaulted from the customer is based on the customer account and not the invoice account.

## "Object reference not set" error seen during purchase order confirmation, or "Exception has been thrown by the target of an invocation", exception thrown during vendor invoice posting.

**Resolution**
This is an issue that could occur due to inconsistency in purchase order distributions. 

It is possible to unblock the above issues and reset the purchase order to a draft state using Procurement and Sourcing > Periodic Task > Clean up > Purchase Order Distribution Reset. See more in the blog[Resolve PO distribution errors in Dynamics 365 Supply Chain Management](https://cloudblogs.microsoft.com/dynamics365/it/2020/08/12/resolve-po-distribution-errors-in-dynamics-365-supply-chain-management/).

## One or more accounting distributions is either over-distributed or under-distributed.
The user sees the error "One or more accounting distributions is either over-distributed or under-distributed".

**Fix**
This is an issue that could occur due to inconsistency in purchase order distributions. 

It is possible to unblock the above issues and reset the purchase order to a draft state using Procurement and Sourcing > Periodic Task > Clean up > Purchase Order Distribution Reset. See more in the blog [Resolve PO distribution errors in Dynamics 365 Supply Chain Management](https://cloudblogs.microsoft.com/dynamics365/it/2020/08/12/resolve-po-distribution-errors-in-dynamics-365-supply-chain-management/).

## Can I show only Purchase orders created by me?

This functionality is not available currently.

## Able to reserve inventory and transact against goods in Registered status on the purchase order.

When items are Registered on a Purchase order, it is possible to reserve the inventory, i.e. it is possible to create transactions against the Registered Inventory.

**Scenario**
1. Create PO
2. Register the PO line
3. It is possible to generate reservation or transaction against Registered inventory. 
*Is there a way to block this?*
		
**Resolution:**
The Registered items are expected to be phyiscally arrived in the warehouse or inventory, hence this is available for reservation.

## Language settings on legal entity not reflected in purchase orders - the product name is shown in the company language.

The product name in a purchase order shows up in system language, and not in the language set for the legal entity in which the purchase order has been created.

**Scenario**
1. System language EN-US
2. Make sure there is a product that has languages en-us and de maintained for translations for the product name.
3. Change the language of a legal entity to DE.
4. Create a  purchase order with this product in the legal entity DE.
*Issue: The product name is still shown in EN-US, the same as what was set as the system language.*

**Resolution**
On the purchase orders, the product is always show in the system language. When a confirmation journal is created, then the PO language is used. 

## Approved vendor list by product entity does not allow to change effective date.
The "Approved vendor list by product" doesn’t allow to change effective date by using the entity. 

**Scenario**
1. Suppose, a product has an approved vendor with effective date 01/11/2018 and expiration date ‘never’.
2. Then, it is not possible to change the effective date to 01/10/2018 Or 01/12/2018. 
3. The following error is seen: "Cannot create a record in Approved supplier list (PdsApproveVendorList). The 'Expiration' value needs to be greater than or equal to the 'Effective' value."

**Resolution**
It is only possible to extend the period that the vendor is approved for. 

1. To bring the effective date to an earlier date than any of existing records (periods) given for that item-vendor, the expiration date on the new period has to be before any of the expiration dates in the existing records.
2. To bring the expiration date to a later date than any of the existing periods, the effective date has to be after the latest expiration date of any existing records.
3. To reduce the overall time period that the vendor is approved, this has to be done through UI by either deleting records or modifying existing records - or by using the truncate switch when importing which deletes all existing records in the table for approved vendors by item. 

For this example scenario described above, where there is a record of effective date 01/11/2018 and expiration date ‘never’, it would be possible to import a new record with effective date 01/10/2018 and expiration date before "never". However it is not possible to reduce the period so that the effective date is updated to 01/12/2018 via data management. This would have to be done through the UI.

## After changing the Delivery address on the purchase order header, the Delivery name is not synchronized.
**Scenario**
1. The address on the header of a purchase order is updated to an address that is not a delivery address. 
*Issue: The address updates on the purchase order - however the delivery name does not update based on the updated address.*

**Resolution**
 Only if the address selected is classified as a delivery address, then the delivery name will also be updated according to the selected address. Otherwise, the delivery name is not updated.

## Is it possible to find the User who cancelled a Purchase Order (PO)
This information is not tracked, if the purchase order is not under change management. If you use change management you can see who submitted the change (a cancellation) and who approved it.


## Additional resources

[Get started with Purchase Orders](purchase-order-overview.md)
[Creation of Purchase Orders](create-purchase-order.md)
