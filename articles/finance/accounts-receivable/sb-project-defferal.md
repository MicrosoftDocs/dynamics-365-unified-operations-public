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

This article explains how to set up and use the **Project subscription billing deferral cost of goods sold (COGS) adjustment (preview)** feature in Microsoft Dynamics 365 Finance. 

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites
Before using the **Project subscription billing deferral COGS adjustment (preview)** feature, confirm your environment is updated to Microsoft Dynamics 365 Finance version 10.0.45 or later. This feature depends on the **Subscription billing deferral COGS adjustment** feature. If the base COGS adjustment feature isn't enabled, this project-specific version can't be activated. 

To enable the **Project subscription billing deferral COGS adjustment (preview)** feature, follow these steps:
1. Go to **Feature management**.
2. Enable **Project subscription billing deferral COGS adjustment (preview)** feature for project-based contract billing or sales orders. 
  
After the feature is enabled, COGS is automatically tracked and adjusted for applicable deferral schedules when related to project-based sales orders.

### Parameters
To set the **Revenue and expense deferral** parameter, follow these steps:
1. Go to **Revenue and expense deferral parameters** > **Adjustment method**
2. Select one of the following options: 
 - **Catch up** – The amount after all recognized lines are recalculated.
 - **Reversal** – Any lines after the recalculation date are reversed by using the specified journal name and posting date. The amount after the recalculation date is then recalculated.

### Background automation
This feature introduces background automation to adjust COGS for deferral schedules in Subscription billing. 
To ensure the feature operates as intended, initialize the background process automation:
1.	Go to **System administration** > **Setup** > **Process automations**.
2.	Select **Initialize process automations**.
3.	After initialization, verify that the **Subscription billing deferral COGS adjustment (preview)** appears in the **Background processes** list.

When an inventory closing or recalculation process is triggered, the system:
 - Identifies impacted consumption deferral schedules.
 - Updates the **Inventory cost adjustment** field in the COGS Deferral schedule to reflect any change in the original inventory cost.
 - Executes the update asynchronously.
These adjustments ensure that any cost changes, even the cost changes made after the original posting, are accurately reflected in deferred COGS recognition.

### Example
If a sales order is created from a project for a stocked item, when the sales order is posted: 
 - A revenue deferral schedule with **Recognition type** of **Credit**.
 - A consumption deferral schedule (COGS) with **Recognition type** of **Debit**.

After inventory closing or physical inventory adjustment is recalculated:
 - The deferred COGS is automatically recalculated.
 - The deferral schedule is updated with an **Inventory cost adjustment** amount in a consumption deferral schedule (COGS).
 - No new deferral schedule is created and the existing one is updated with the revised cost value.

### Audit trail
An additional line in the **Audit trail** is added to reflect the inventory adjustment amount. 

#### Project posted transaction updates
To review the changes in posted transactions, follow these steps:
1. Go to **Project** > **Posted transactions**.
2. Select **View** > **View transaction**.
3. Go to the **Cost** section, verify that the **Deferral cost schedule number** is linked.
If inventory adjustments or closings take place, an additional transaction line is added to reflect the updated cost. Importantly, no new deferral schedule is created and the original schedule is updated with the adjusted values.



