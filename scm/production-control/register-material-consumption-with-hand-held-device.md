---
# required metadata

title: Register material consumption with a handheld device
description: This topic describes a workflow that enables registration of raw material consumption in production by using a handheld device.
author: BibiSp
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
# ms.reviewer: bis
# ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: [Global for most topics. Set Country/Region name for localizations]
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: johanho
ms.search.validFrom: 2017/07
ms.dyn365.ops.version: AX 7.0.2
---

# Register material consumption with a handheld device

[!include[banner](../includes/banner.md)]

This workflow is relevant if there is a strict requirement for material traceability. In those cases, to maintain traceability of the materials, the exact time and quantity must be reported for the consumption. This process can be seen as opposed to pre- or back-flushing operations, where there is an offset between the time of registration and the time when the actual consumption takes place. This explains why a strategy of automatic consumption cannot be used for some materials with traceability requirements.
Let’s look at a simple scenario that explains how to set up a workflow to enable registration of raw material consumption in production by using a handheld device. 

![Workflow](media/Scenario3.png "Workflow") 

A continuous production process ⑤ consumes the batch-controlled raw material RM-100. The material is on-hand on location Bulk-001 ① on license plate PL-1 with two batches, B1 and B2, both with a quantity of 100 lbs. Warehouse work ② is released and processed for RM-100, and the material is picked from Bulk-001 to the production input location PIL-01 ③, which is defined as non-license plate controlled. From the production input location, a portion of the material is manually added to the production process in defined time intervals. When the machine operator adds material, it is weighed on a scale and the batch number is registered.
Set up the workflow to register consumption using a handheld device
Create a finished-good product, FG-100, with a bill of material that has the batch-controlled raw material RM-100. Add two batches, B1 and B2, of RM-100 in a quantity of 100 to location: Bulk-001 on license plate: PL-1. The flushing principle on the bill of material line for RM-100 is set to Manual. Set  the production input location to PIL-01. You can do that by selecting this location as the default production input location on warehouse 51.
Create a new mobile device menu item:
– Menu item name – Register material consumption.
– Title – Register material consumption.
– Mode – Indirect.
– Activity code – Register material consumption.
Add the menu item to the Production Mobile device menu.
Create a production order for the finished product:
– Item number – FG-100
– Site – 5
– Warehouse – 51
– Quantity – 150
The production order is Estimated and Released and warehouse work is created.
Complete the work using the workflow for raw material picking for the handheld device.
This will bring the material from the bulk location to the production input location PIL-01. After the work is completed, the material has the status Picked on the production input location. The status after work has been processed can be either Picked or Reserved physical. This is configured with the parameter Issue status after put on the warehouse form.
Start the production order either from the client or from the handheld device by using the Production start menu item.
After the production order has been started, you can register material consumption with the workflow for the handheld device. Let’s start by registering consumption of 25 lbs of batch B1.
Select the Register material consumption menu item in the menu for the hand held device, enter the following details:
– The production order number.
– The location on which the material is going to be consumed, in this case PIL-01.
– Item number RM-100.
– Batch number B1.
– A quantity of 25.
Select OK.
Note that the message “Journal line is created” appears on the display. On the production order there is an open journal of the type Production picking list for item number RM-100 and batch number B1.
You can now choose to continue your registration, for example on batch number B2, and each time you select OK, a new journal line is added to the open journal.
After you have finished your registration, select Done to post the journal and end the workflow.
Additional comments 
If a user cancels the workflow after a journal line is created, the journal is in an unposted state but if the user at a later point uses the workflow for the same production order, then the lines will be added to the open journal rather than to a new journal.
The new workflow also supports the registration of serial numbers. 
It is only possible to register an item number that is defined in the bill of material or in the formula for the selected production order or batch order. 
Material can be overconsumed. For example, if the material is estimated to be consumed with the quantity of 100 lbs, then it can be overconsumed with a quantity of, for example, 105 lbs.
