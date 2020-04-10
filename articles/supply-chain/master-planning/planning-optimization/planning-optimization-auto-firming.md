---
# required metadata

title: Auto-firming with Planning Optimization
description: This topic explains how to use automatic firming with Planning Optimization.
author: ChristianRytt
manager: tfehr
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
ms.reviewer: kamaybac
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

# Auto-firming with Planning Optimization

[!include [banner](../../includes/preview-banner.md)]
[!include [banner](../../includes/banner.md)]

Automatic firming lets you firm (that is, release) planned orders as part of the master planning process. When planned orders are firmed, they are transformed into actual purchase orders, transfer orders, or production orders. When Planning Optimization is used, planned orders are firmed during a master planning run when the order date (that is, the start date) is within the time fence for firming.

> [!NOTE]
> Auto-firming of a planned purchase order can occur only if the item is associated with a vendor.

## Turn on auto-firming

To turn on auto-firming, follow these steps.

1. In the **Feature management** workspace, on the **New** tab, select **Auto-firming for Planning Optimization** in the list. If the feature doesn't appear on the **New** tab, look on the **Not enabled** and **All** tabs.
1. Select **Enable now**. Alternatively, select **Schedule**, and then select the time when you want the feature to be turned on.

## Set up the firming time fence

The firming time fence is calculated forward from the master planning run date. It's defined by the number of days that you enter. You can control the firming time fence in the following ways:

- To define the default firming time fence for a coverage group, go to **Master planning** \> **Setup** \> **Coverage** \> **Coverage groups**, and select a coverage group. Then, on the **Other** FastTab, in the **Automatic firming time fence (days)** field, enter the number of days.
- To overwrite the firming time fence that is defined for the coverage group for a specific item, go to **Product information management** \> **Released products**, then from the action pane select **Plan** and then select **Item coverage**. Then, on the **General** tab, select **Override time fence** and in the **Automatic firming time fence (days)** field, enter the number of days.
- To overwrite the firming time fence that is defined for the coverage group and item coverage for a specific master plan, go to **Master planning** \> **Setup** \> **Master plans**, and select a Master plan. Then, on the **Time fence in days** FastTab, set **Freeze** to **Yes**, and enter the number of days.

If auto-firming is turned on for a master planning run that uses Planning Optimization, the auto-firming process is done according to the auto-firming setup. If auto-firming isn't turned on, or if planning is started from the **Net requirements** page, the auto-firming process is skipped.

## Planning Optimization vs. the built-in Supply Chain Management planning engine

Both Planning Optimization and the planning engine that is built into Microsoft Dynamics 365 Supply Chain Management can be used to auto-firm planned orders. However, there are some important differences. For example, whereas Planning Optimization uses the order date (that is, the start date) to determine which planned orders to firm, the built-in Supply Chain Management planning engine uses the requirement date (that is, the end date). Here is a summary of the differences.

**Planning Optimization**

- Auto-firming is based on the order date (start date).
- Because the order date (start date) triggers the firming, you don't have to consider the lead time as part of the firming time fence.
- If you want to firm all orders that must start during the current week, the firming time fence must be one week.

**Built-in Supply Chain Management planning engine**

- Auto-firming is based on the requirement date (end date).
- To help guarantee that orders are firmed in due time, the firming time fence must be longer than the lead time.
- If you want to firm all orders that must start during the current week, the firming time fence must be the lead time plus one week.
