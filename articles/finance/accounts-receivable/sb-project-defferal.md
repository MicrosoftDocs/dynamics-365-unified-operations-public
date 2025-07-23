---
title: Project subscription billing deferral COGS adjustment (preview)
description: Learn how to set up the project subscription billing deferral COGS adjustment feature in Microsoft Dynamics 365 Finance. 
author: JodiChristiansen
ms.author: reetuchopra
ms.topic: how-to
ms.date: 07/25/2025
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2021-11-05
ms.search.form: 
ms.dyn365.ops.version: 10.0.24
---

# Project subscription billing deferral COGS adjustment (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

This article explains how to set up and use the project subscription billing deferral COGS adjustment feature in Microsoft Dynamics 365 Finance. 

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites
Before using the project subscription billing deferral COGS adjustment feature, ensure your environment is updated to version 10.0.45 or later. This feature is currently available in Preview and must be explicitly
enabled via Feature Management. It also depends on the Subscription billing deferral COGS adjustment feature. If the base COGS adjustment feature isn't enabled, this project-specific version can't be activated. 

In Feature management, enable (Preview) Project subscription billing deferral COGS adjustment feature for project-based contract billing or sales orders. 
Once enabled, the system automatically tracks and adjusts COGS for applicable deferral schedules when related to project-based sales orders.
Set up parameters under Revenue and expense deferral parameters
“Adjustment Method parameter enforces the default behaviour for all the deferral COGS schedule. To set this parameter, Navigate to:  Revenue and expense deferral parameters > Adjustment method
There are 2 options which users can select: 
•	Catch up – The amount after all recognized lines are recalculated.
•	Reversal – Any lines after the recalculation date are reversed by using the specified journal name and posting date. The amount after the recalculation date is then recalculated.

### Background automation
This feature introduces background automation to adjust the cost of goods sold (COGS) for deferral schedules in Subscription Billing. To ensure the feature operates as intended, initialize the background process
automation:
1.	Go to System administration > Setup > Process automations.
2.	Select Initialize process automations.
3.	After initialization, verify that the process (Preview) Subscription billing deferral COGS adjustment appears in the Background processes list.

When an inventory closing or recalculation process is triggered, the system:
 - Identifies impacted consumption deferral schedules
 - Updates their COGS values (“Inventory cost adjustment field” in COGS Deferral schedule) to reflect any changes in the original inventory cost
 - Executes the update asynchronously.
These adjustments ensure that any cost changes even those made after the original posting are accurately reflected in deferred COGS recognition.


### Example
If a sales order is created from a project for a stocked item:
Upon posting, the system generates:
 - A revenue deferral schedule with Recognition type as Credit
 - A consumption deferral schedule (COGS) with Recognition type as Debit

After Inventory closing/Recalculation physical inventory adjustment
 - Automatically recalculates the deferred COGS
 - Updates the deferral schedule with Inventory cost adjustment amount in A consumption deferral schedule (COGS)
No new deferral schedule is created; the existing one is updated with the revised cost value.

### Audit trail
An additional line in the Audit trail is added to capture the inventory adjustment amount. 

#### Project posted transaction updates
To review the changes in posted transactions, follow these steps:
1. Go to Project > Posted Transactions, and select View > View Transaction.
2. Ensure that deferral schedules are enabled, and under the Cost section, verify that the Deferral Cost Schedule number is linked.
If inventory adjustments or closings take place, an additional transaction line is added to reflect the updated cost. Importantly, no new deferral schedule is created—the system updates and reuses the original 
schedule with the adjusted values.

With this feature, users can ensure that inventory cost changes from recalculations or closings are properly reflected in project cost tracking. This guarantees that project subledger entries remain accurate and 
that revenue and expense recognition are correctly aligned.

