---
# required metadata

title: Manual update of asset counters
description: This topic describes manual update of asset counters in Asset Management.
author: josaw1
manager: AnnBe
ms.date: 06/27/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: CatProcureCatalogEdit, CatProcureCatalogListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 2214
ms.assetid: 2f3e0441-414d-402b-b28b-7ab0d650d658
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Manual update of asset counters

Counters are used to create registrations on an asset regarding, for example, number of hours in operation, or the number of quantities produced.

If the counter type selected for a counter is set to inherit counter values (**Asset management** > **Setup** > **Asset types** > **Counters** > **General** FastTab > **Inherit asset counter values** toggle button set to "Yes"), then, when you create a new counter line of that type, every child asset that uses the same counter type is automatically updated.

In **All assets**, you create hours or quantity counter registrations on an asset, based on your readings on the asset.

1. Click **Asset management** > **Common** > **Assets** > **All assets**.

2. Select the asset in the list, and click **Counters**. In the **Asset counters** form, you see a list of all previous counter registrations on the selected asset.

3. Click **New** to create a new registration. The asset ID is automatically inserted.

4. In the **Counter** field, select the relevant counter. Only counters related to the asset type selected on the asset are available. The related unit is automatically inserted in the **Unit** field.

5. Select date and time for the counter registration.

6. In the **Value** field, insert the number since the last counter registration, or, in the **Aggregated value** field, insert the total count number.

- If you physically install a new counter on an asset, you need to register the change on the asset in **Asset counters**. Next, you must create two registration lines with identical timestamps, and on the line regarding the new counter, you select the **Counter reset** check box. When you create the two registration lines, the first line must be for the counter that you are replacing. In the **Totals** field, the total count number is the sum of the counter total of all registered values on that counter type.  
- If the **Counter reset** check box is selected on an asset using a maintenance plan with a "Once from..." or "Once reached..." interval type, the counter is still active on the new counter line because you create a separate counter line and start over with a new counter.


![Figure 1](media/11-work-orders.png)


If you need to make counter registrations on several assets, that can be done in **Asset management** > **Inquiries** > **Assets** > **Asset counters**.

>[!NOTE]
>You can set up a range to define deviations in manual counter registrations, and the type of message that should be displayed if registrations are outside the defined range. Refer to the [Counters](../setup-for-objects/counters.md) topic regarding setup of counters.
