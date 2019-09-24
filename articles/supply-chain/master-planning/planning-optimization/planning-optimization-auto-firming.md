---
# required metadata

title: Auto firming
description: Auto firming with Planning Optimization
author: ChristianRytt
manager: AnnBe
ms.date: 2019-09-24
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ReqCreatePlanWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: crytt
ms.search.validFrom: 2019-09-24
ms.dyn365.ops.version: AX 10.0.7

---

[!include [banner](../includes/preview-banner.md)]

# Auto firming

With auto firming it is possible to firm (also known as release) planned orders as part of the master planning process. When firmed the planned orders are transformed into actual purchase, transfer, or production orders. Using Planning Optimization planned orders are firmed, during a master planning run, when the **Order date** (start date) is within the firming time fence.

## Enable feature

To use this feature you need to enable the **Auto-firming for Planning Optimization** feature flag.

- Go to **Feature management**
- Select **Auto-firming for Planning Optimization** in the list (If not shown under **New** select **Not enabled** or **All** )
- Click **Enable now**, or use **Schedule** to pick a time to enable the feature

## Firming time fence setup

The **Automatic firming time fence (days)** control what planned orders to firm. The firming time fence is calculated forward from the master planning run date and the period is defined with the number of days entered. Firming time fence can be controlled as follows:

- **Coverage group** > **Other** > **Automatic firming time fence (days):** You can define the default firming time fence for a coverage group.
- **Item coverage** > **General** > **Automatic firming time fence (days):** You can overwrite the firming time fence defined on the **Coverage group** for a specific item **.**
- **Master plans** > **Time fence in days** > **Firming:** For a specific Master plan you can overwrite the firming time fence defined on the **Coverage group** and **Item coverage** by selecting **Yes** and set the number of days. This will apply to all items included during the planning run.

Note that the date used to determine what planned orders to firm differs between the built-in Finance and Operations planning engine and Planning Optimization. The built-in Finance and Operations planning engine use **Requirement date** (end date) from planned orders to determine what planned orders to firm. Planning Optimization use the **Order date** (start date).

**Built-in Finance and Operations planning engine**

- Auto firming based is on **Requirements date** (end date).
- You need the firming time fence to be longer than your lead time to ensure that orders are firmed (released) in due time.
- If you want to firm all orders that needs to start this week, you need to have a firming time fence of: lead time + one week.

**Planning Optimization**

- Auto firming is based on **Order date** (start date).
- With **Order date** (start date) triggering the firming, you don't have to consider lead time as part of the firming time fence.
- If you want to firm all orders that needs to start this week, you need to have a firming time fence of one week.

**Note:** Automatic firming of a planned purchase order can occur only if the item is associated with a vendor.
