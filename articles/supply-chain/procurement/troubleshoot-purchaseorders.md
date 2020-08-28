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

## Unable to link a Purchase Agreement to a Purchase Order Line after creation

A purchase agreement has to be associated to the purchase order at the time of creation. Purchase order lines cannot be associated to purchase agreement lines if the purchase order was not initially associated at the time of purchase order creation.

## Unable to post more than one invoice for a purchase order line with category based items

Quantity is mandatory for posting invoices. So, if the full quantity on the line has been invoiced but only a partial amount and the expectation is to invoice the rest of the amount in another invoice, then that is not possible.

## Changes to purchase order %1 are only allowed in state Draft when change management is active
## Changes to the document are only allowed in draft state because change management is activated.

This issue only occurs if the purchase order was in a 'Confirmed' state before requesting changes. If the user requested changes while the purchase order was in an "Approved" status, then the workflow can be processed successfully. 

**Issue repro steps**
1. An active Purchase order workflow and a purchase order line workflow is created, activated.
2. Change management ie anbled for purchase orders. In Procurement and Sourcing -> Setup -> Procurement and Sourcing parameter, and turn this to Yes.
3. Navigate to Accounts Payable > All purchase orders > purchase order.
4. Create a new purchase order with a purchase order line.
5. Submit the workflow.
6. Approve the workflow from the line level, so that it is approved and completed. Purchase order is also approved at this point.
7. Confirm the purchase order.
8. Click on request change.
9. Click on update line and click on delivery remainder. 
10. Change the delivery remainder.
30.	Submit it back to the workflow.
31.	Check workflow PO order line history.
32.	Getting the workflow error.
 
**Result**
An error occurs in the workflow when a purchase order is resubmitted after a request change.

Stopped (error): X++ Exception: Changes to purchase order PO0000569 are only allowed in state Draft when change management is activated
 at SysWorkflowParticipantProvider-resolve
SysWorkflowParticipantProvider-resolveParticipants
SysWorkflowServiceProvider-resolveParticipant
SysWorkflowQueue-resume

**Fix**
This is an issue that could occur due to inconsistency in purchase order distributions. 

It is possible to reset the purchase order to a draft state using Procurement and Sourcing > Periodic Task > Clean up > Purchase Order Distribution Reset. See more [here](https://cloudblogs.microsoft.com/dynamics365/it/2020/08/12/resolve-po-distribution-errors-in-dynamics-365-supply-chain-management/).

The issue  will be resolved with this [KB](https://msdyneng.visualstudio.com/FinOps/_workitems/edit/467138).

## One or more accounting distributions is either over-distributed or under-distributed.

**Fix**
This is an issue that could occur due to inconsistency in purchase order distributions. 

It is possible to unblock the above issues and reset the purchase order to a draft state using Procurement and Sourcing > Periodic Task > Clean up > Purchase Order Distribution Reset. See more [here](https://cloudblogs.microsoft.com/dynamics365/it/2020/08/12/resolve-po-distribution-errors-in-dynamics-365-supply-chain-management/).

## This action can only be completed after the line number %1 is fully distributed.

**Fix**
This is an issue that could occur due to inconsistency in purchase order distributions. 

It is possible to unblock the above issues and reset the purchase order to a draft state using Procurement and Sourcing > Periodic Task > Clean up > Purchase Order Distribution Reset. See more [here](https://cloudblogs.microsoft.com/dynamics365/it/2020/08/12/resolve-po-distribution-errors-in-dynamics-365-supply-chain-management/).

## Object reference not set, for purchase order confirmation, or exception has been thrown by the target of an invocation, for vendor invoice posting.

**Fix**
This is an issue that could occur due to inconsistency in purchase order distributions. 

It is possible to unblock the above issues and reset the purchase order to a draft state using Procurement and Sourcing > Periodic Task > Clean up > Purchase Order Distribution Reset. See more [here](https://cloudblogs.microsoft.com/dynamics365/it/2020/08/12/resolve-po-distribution-errors-in-dynamics-365-supply-chain-management/).

## Updating Purchase Order in Received State creates Error

Planning Optimization differs from the built-in master planning design in some areas. This can also be caused by pending features.

**Fix**: Run Planning Optimization fit analysis and then analyze the results while referring to the related documentation to understand the impact. For more information, see [Planning Optimization fit analysis](planning-optimization-fit-analysis.md).

## Unable to edit the unit price for a purchase order line linked to an agreement

This is caused by a pending feature for Planning Optimization.

**Fix**: Until the pending feature is available, filter or delete planned orders to remove supply suggestions outside of the coverage time fence.

## What check triggers the prompt 'Update prices and discounts entered manually or external document' message?

We prompt this when changing the shipping date because often times this means that a different trade or sales agreement can get triggered, resulting in a price change. It can also effect warehouse schedules and other related information. It gets triggered whenever any of the dates have been changed, to ensure that the user is aware of price changes that can happen due to this change.

## Can I show only Purchase orders created by me?

This functionality is not available currently.

## Able to reserve inventory and transact against goods in Registered status on the purchase order.

When items are Registered on a Purchase order, it is possible to reserve the inventory, that is we can create transactions against the Registered Inventory.

**Repro steps**
		1. Create PO
		2. Register the PO line
		3. It is possible to generate reservation or transaction against Registered inventory. 
  Is there a way to block this?
		
**Resolution/Fix:**
The Registered items are expected to be phyiscally arrived in the warehouse orinventory, hence this is available for reservation.

## Language settings on legal entity not reflected in purchase orders - the product name is shown in the company language.

The product name in a purchase order shows up in system language, and not in the language set for the legal entity in which the purchase order has been created.

**Repro steps**
1. System language EN-US
2. Make sure there is a product that has languages en-us and de maintained for translations for the product name.
3. Change the language of a legal entity to DE.
4. Create a  purchase order with this product in the legal entity DE.
5. Result: The product name is still shown in EN-US, the same as what was set as the system language.

**Resolution**
On the purchase orders, the product is always show in the system language. When a confirmation journal is created, then the PO language 

## Purchase order receipt does not include all charges

**Repro steps**
1. Make sure the procurement and sourcing parameter > Delivery > Generate charges on product receipt option is set to yes.
2. Create purchase order that includes charges.
3. Confirm the PO.
4. Receive the PO.
5. Look at the receipt total and compare it to the expected total. 
6. Result: The charges on the purchase order receipt does not include all the charges.

**Resolution**
This is dependent on how the miscellaneous charges have been setup. Please see this blog for how to set this according your requirements. [Post Misc. charges at time of Product receipt] (https://cloudblogs.microsoft.com/dynamics365/no-audience/2014/11/11/post-misc-charges-at-time-of-product-receipt/)

## Trade agreement price and discounts are not applied on purchase order lines imported through data management
Trade agreements that are applicable for purchase order lines do not get applied to lines imported through data management, though the same trade agreements are applied on regular purchase order lines created manually.

**Repro steps**
1. Create a purchase order for a vendor that has a trade agreement set up for line discount percentage.
2 Import purchase order lines with price set for eg., through the entity Purchase Order Lines V2
3. Check field "Line discount percentage".
4. Result: The line discount percentage is not updated after import of these lines.

**Resolution**
When purchase order lines that are imported via data management  already are decorated with price information, then the trade agreement will not be re-evaluated for these lines. 

**Workaround**
Import the purchase order lines without setting any of the price information, then the trade agreements will get kicked in and the purcase order lines would get updated based on the defined trade agreements.

## Cannot consolidate multiple Product Receipts (PR) into a single Purchase order
Cannot consolidate multiple PR into a single PO when the different PR lines have different accounting dates.

**Resolution**
This was possibility in an earlier version that allowed for consolidating PR lines with different accounting dates. However, this is error prone. The accounting date on the created PO lines - which is the same as the accounting date on the header of the PO - should not be different from the accounting date on the PR line from which the PO line was created. Hence, the consolidation of multiple product receipts into a single purchase orders will is not allowed. 

The accounting date is used e.g. for budget reservations and encumbrance, this should be kept when transitioning from PR to PO. 

## Cancelling Product Receipts allows to post transactions to the suspended ledger account.
System is allowing the posting of transactions to suspended ledger accounts on cancelling of the Product Receipt even though the main accounts are “suspended”.

**Repro Steps**
1. Ensure the “Post product receipt in ledger “enabled in parameter.
2. Create a purchase order and create a line with a product, with 1000 quantity and confirm the purchase order.
3. Post the Product receipt and check the vouchers.
4. Suspend the relevant main accounts 200140 and 140200.
5. Cancel the posted product receipt.

Result: This allows posting transactions to the suspended leger accounts.

**Resolution**
With reversals, our recommendation is to skip all validations to ensure that the same transaction that was posted is also reversed.  The customer will have to post an adjusting entry in GL, so as to move the balance from the suspended account to the new main account that replaces the suspended account.

## Vendor rebate is not cumulated based on invoices.
Posting invoices with different due dates is not reflected to the vendor rebates that is generated from the invoices.

**Resolution**
Due date is not considered when calculating the vendor rebate.
Customization as extension could be considered so that the due date and the relation to the invoice is more apparent in relation to the actual vendor rebate.

## Unit price in purchase order is not calculated based on UOM conversion
Trade agreement Prices are not recalculated according to unit conversion definitions when a unit is changed on a purchase order.

Price is always obtained from trade agreements (or other price settings in the system e.g. sales agreements; item price) and the price is set for a Unit. 

If the unit is changed on an order line then the system will look for a price for that particular unit and apply that price; if no price is found for the unit it will not apply the price. The unit conversion cannot be used to recalculate the price into an other unit. Theoretically, it could be that the price is different for a box with 10 than 10xthe price of 1.

**Workaround**
A way to overcome this is to make sure that there are trade agreements for the particular units that are expected to be used on order lines for the item.

## After changing the Delivery address on the purchase order header, the Delivery name is not synchronized.
The address on the header of a purchase order is changed to an address that is not a delivery address. The address updates - however the delivery name does not update with the selected address.

**Resolution**
 Only if the address selected is classified as a delivery address, then the delivery name will also be updated according to the selected address. Otherwise, the delivery name is not updated but not the address.

## Cancelling of delivery remainder on a purchase order with change management enabled, get the purchase order to a confirmed state
For a purchase order under change management: When a requested change is "just" to cancel a delivery remainder on the line(s) the PO will when it is approved go directly to a Confirmed state and no journal is created. 

**Resolution**
The cancelling on the delivery remainder is not having any influence of the contents of thes confirmation journal.

However, the cancelling of the delivery remainder functionality should be used for when the line has been partially received and then remainder quality is being cancelled, in the process step after the PO has been confirmed with the Vendor.

In case of the PO confirmation, the line that is not required anymore should be removed from the PO not cancelled. 

## Tax group and Cash discount are not defaulted from Invoice account
The customer has a different invoice account than the customer account. When a Purchase order is created, Tax group and Cash discount are not defaulted from the Invoice account. 

**Resolution**
The defaulting of of tax group, cash discounts and other price information that should be defaulted based on the customer, is always based on the customer account and not the invoice account.

## Product receipt Voucher number is consumed even if no financial voucher is generated
When the "Accrue liability on product receipt" is OFF on the item model group, then no postings to GL will happen. However, there is a physical event that is recorded for the purpose of accounting in subledger and that needs a voucher number. This is what is referenced in the Inventory transactions.

In the following blogpost, we recommend the "Accrue liability on product receipts" to be YES: [Post Misc. charges at time of Product receipt] (https://cloudblogs.microsoft.com/dynamics365/no-audience/2014/11/11/post-misc-charges-at-time-of-product-receipt/)

## Cancelled purchase orders show in draft list in purchase order preparation workspace
After cancellation of purchase orders that were in a confirmed state, the cancelled Purchase Orders still show in the list of Draft PO's in the "Purchase order preparation" workspace. 

**Resolution** 
This happens only for purchase orders that are under change management because the Cancellation is seen as a change that needs to be approved. The approval can be done automatically by the system. So, the process is to submit the cancelled purchase order to the approval workflow so that it can get into an approved state. Once this is done, the purchase order will not appear in the list of Draft PO's in the "Purchase order preparation" workspace. 

## Setting - 'Post to charge account in ledger' is not active

**Repro steps**
1. Go to Accounts payable> Setup>Accounts payable parameters; Activate “Post to charge account in ledger “
2. Go to Inventory Management > Setup > Posting > Posting > Purchase Order 
3. Make sure you have deleted all of the lines in purchase expenditure for product
4. Go to Accounts payable > Purchase orders > All Purchase order and create a new PO. Select for Vendor Account – 1001 Acme Office Supplies
5.For Item number select D0011 Laser Projector; Site 1 ; Warehouse 11; Quantity 4
6. Confirm the PO by clicking on PURCHASE > Action > Confirm
7. Click on RECEIVE > Product receipt. And add a product receipt number (random number)
8. After that Invoice > Invoice
9. Add an Invoice Number (random number); Update match status and Post

Result:
Error “Account number for transaction type Purchase expenditure for product does not exist” when we generate Invoice form a PO.

**Resolution**
This is dependent on the parameter settings for invoices and invoice groups. Please find more details on in this blog: [Accounting for Purchase charge and Stock variation]
(https://cloudblogs.microsoft.com/dynamics365/no-audience/2014/12/15/accounting-for-purchase-charge-and-stock-variation/).

## When opening the Purchase agreement form in a line view mode, it is not possible to personalize the screen to add the Price unit field in the overview of the line.
Certain shared fields in the agreement framework cannot be included in personalization as requested. This is due to the implemented datamodel. Hence, the price unit field cannot be personalized.


## Additional resources

[Get started with Purchase Orders](get-started.md)

