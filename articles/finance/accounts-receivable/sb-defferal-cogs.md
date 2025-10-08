---
title: Subscription billing deferral COGS adjustment (preview)
description: Learn how to set up the Subscription billing deferral COGS adjustment feature in Microsoft Dynamics 365 Finance. 
author: JodiChristiansen
ms.author: reetuchopra
ms.topic: how-to
ms.date: 07/29/2025
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2021-11-05
ms.search.form: 
ms.dyn365.ops.version: 10.0.24
---

# Subscription billing deferral COGS adjustment (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

This article explains how to set up and use the subscription billing deferral cost of goods sold (COGS) adjustment feature in Microsoft Dynamics 365 Finance. 

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites


Before using the Subscription billing deferral COGS adjustment feature, make sure your environment is updated to version 10.0.45 or later. In Feature management, enable the **Subscription billing deferral COGS adjustment 
(preview)** feature for contract billing and sales orders. This feature is currently available in preview and must be explicitly enabled via Feature Management. Once enabled, the system automatically tracks and 
adjusts COGS for applicable deferral schedules.


### Set up parameters 

To set the **Revenue and expense deferral** parameter, follow these steps:

1. Go to **Revenue and expense deferral parameters** > **Adjustment method**
2. Select one of the following options: 
 - **Catch up**: Recalculates the amount after all recognized lines.
 - **Reversal**: Reverses any lines after the recalculation date using the specified journal name and posting date. The amount after the recalculation date is then recalculated.

### Background automation

This feature introduces background automation to adjust COGS for deferral schedules in Subscription billing. 
To ensure the feature operates as intended, initialize the background process automation:

1.	Go to **System administration** > **Setup** > **Process automations**.
2.	Select **Initialize process automations**.
3.	After initialization, verify that **Subscription billing deferral COGS adjustment (preview)** appears in the **Background processes** list.

When an inventory closing or recalculation process is triggered, the system:
 - Identifies impacted consumption deferral schedules.
 - Updates the COGS values using the **Inventory cost adjustment** field.
 - Executes adjustments asynchronously.
This ensures that inventory cost changes even if updated after posting are accurately reflected in deferred cost of goods sold recognition.

### Example 

If a sales order is created for a stocked item, when the sales order is posted:
 - A revenue deferral schedule is created with a **Recognition type** of **Credit**.
 - A consumption deferral schedule (COGS) is created with a **Recognition type** of **Debit**.

After inventory closing or physical inventory adjustment is recalculated:
 - The deferred COGS is automatically recalculated.
 - The deferral schedule is updated with an **Inventory cost adjustment** amount in the consumption deferral schedule (COGS).

### Audit trail

An additional line in the **Audit trail** is added to capture the inventory adjustment amount. 
