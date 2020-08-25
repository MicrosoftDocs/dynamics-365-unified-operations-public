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

ms.search.form: ReqCreatePlanWorkspace
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

## Changes to purchase orders are only allowed in state Draft when change management is activated

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
This is a known issue that will be resolved with this [KB](https://msdyneng.visualstudio.com/FinOps/_workitems/edit/467138).

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


## Additional resources

[Get started with Planning Optimization](get-started.md)

[Planning Optimization fit analysis](planning-optimization-fit-analysis.md)
