---
# required metadata

title: Troubleshoot procurement and sourcing workflows
description: This topic describes how to fix issues that you might encounter while working with procurement and sourcing workflows.
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
# Troubleshoot procurement and sourcing workflows

This topic describes how to fix common issues that you might encounter while working with procurement and sourcing workflows.

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

## Cancelling of delivery remainder on a purchase order with change management enabled, get the purchase order to a confirmed state
For a purchase order under change management: When a requested change is "just" to cancel a delivery remainder on the line(s) the PO will when it is approved go directly to a Confirmed state and no journal is created. 

**Fix**
The cancelling on the delivery remainder is not having an influence on the contents of the confirmation journal.

Cancelling of delivery remainder functionality should be used for when the line has been partially received and then remainder quality is being cancelled, in the process step after the PO has been confirmed with the Vendor.

In case of the PO confirmation, the line that is not required anymore should be removed from the PO not cancelled. 

## Cancelled purchase orders show in draft list in purchase order preparation workspace
After cancellation of purchase orders that were in a confirmed state, the cancelled Purchase Orders still show in the list of Draft PO's in the "Purchase order preparation" workspace. 

**Resolution** 
This happens only for purchase orders that are under change management because the Cancellation is seen as a change that needs to be approved. The approval can be done automatically by the system. So, the process is to submit the cancelled purchase order to the approval workflow so that it can get into an approved state. Once this is done, the purchase order will not appear in the list of Draft PO's in the "Purchase order preparation" workspace. 


## Additional resources

[Get started with Purchase Orders](get-started.md)

