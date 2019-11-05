---
# required metadata

title: Auto-firming with Planning Optimization
description: This topic explains how to use auto-firming with Planning Optimization.
author: ChristianRytt
manager: AnnBe
ms.date: 11/05/2019
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
ms.search.validFrom: 2019-11-30
ms.dyn365.ops.version: AX 10.0.7

---

[!include [banner](../../includes/preview-banner.md)]
[!include [banner](../../includes/banner.md)]

# Auto-firming with Planning Optimization

With auto-firming it is possible to firm (release) planned orders as part of the master planning process. When firmed, the planned orders are transformed into actual purchase, transfer, or production orders. With Planning Optimization, planned orders are firmed during a master planning run when the order date (the start date) is within the firming time fence.

## Turn on auto-firming

To turn on auto-firming, do the following.

1. Go to the **Feature management** workspace.
1. In the list, select **Auto-firming for Planning Optimization**. If the option is not shown under **New**, select **Not enabled** or **All**.
1. Click **Enable now**, or click **Schedule** and pick a time to enable the feature.

## Set up time fence for firming

The time fence for firming is calculated forward from the master planning run date. The period is defined by the number of days entered. You can control the firming time fence in the following ways.

- To define the default firming time fence for a coverage group, go to **Coverage group** > **Other** > **Automatic firming time fence (days)**.
- To overwrite the firming time fence defined on the coverage group for a specific item, go to **Item coverage** > **General** > **Automatic firming time fence (days)**.
- To overwrite the firming time fence defined on the coverage group and item coverage for a specific master plan, go to **Master plans** > **Time fence in days** > **Firming**, select **Yes**, and set the number of days. This will apply to all items included during the planning run.

If auto-firming is enabled on a master planning run with Planning Optimization, the auto-firming process is performed according to the auto-firming setup. If it is not enabled, or in cases where planning is started from the **Net Requirements** page, the auto-firming process is skipped.

> [!NOTE]
> The date used to determine which planned orders to firm differs between the built-in Supply Chain Management planning engine and Planning Optimization. The built-in Supply Chain Management planning engine uses **Requirement date** (end date) from planned orders to determine what planned orders to firm. Planning Optimization use the **Order date** (start date). See below for more details.

   - **Built-in Supply Chain Management planning engine**

      - Auto-firming is based on the **Requirements date** (end date).
      - The firming time fence must be longer than the lead time to ensure that orders are firmed in due time.
      - If you want to firm all orders that need to start this week, you must have a firming time fence of lead time plus one week.

   - **Planning Optimization**

      - Auto-firming is based on order date (start date).
      - With order date (start date) triggering the firming, you don't have to consider lead time as part of the firming time fence.
      - If you want to firm all orders that need to start this week, you need to have a firming time fence of one week.

> [!NOTE]
> Automatic firming of a planned purchase order can occur only if the item is associated with a vendor.
