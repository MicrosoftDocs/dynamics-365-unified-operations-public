---
title: Safety stock pegging options
description: You can choose how strictly the system should peg safety stock as demand against the planned order created for it.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 01/10/2024
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---


# Safety stock pegging options

[!include [banner](../includes/banner.md)]

For most industries, real demand is typically prioritized over [safety stock](safety-stock-replenishment.md). This means that when you need to both replenish safety stock and fulfill a customer order, the system will use any existing planned orders to cover the customer demand instead of leaving those planned orders pegged against safety stock. However, some businesses prefer to allow the system to keep existing planned orders pegged against safety stock, even if that means that customer demand can't be fulfilled. This is called *strict safety stock pegging*.

For each coverage group, you can choose how strictly the system should peg safety stock as demand against the planned order created for it.

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.36 or later.
- The feature that is named *Strict safety stock pegging for Planning Optimization* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Set safety stock pegging options

Safety stock pegging options are set at the coverage group level. Follow these steps to set safety stock pegging options for a coverage group:

1. Go to **Master planning** \> **Setup** \> **Coverage** \> **Coverage groups**.
1. Do one of the following steps:
    - To edit an existing group, select it from the list and then select **Edit** on the Action Pane.
    - To create a new group, select **New** on the Action Pane.
1. On the General FastTab, choose one of the following settings for the **Strict safety stock pegging** field:
    - *No*: Safety stock is considered the least important type of demand, so even if a planned order is created for safety stock, all other demand is prioritized. Safety stock isn't a demand as such and any other demand is prioritized over the safety stock. A planned order can be created to fulfill safety stock, but if actual demand arrives later, that demand can claim the planned-order quantity (the demand will be pegged against the planned order). This option lets you provide a higher service level for your customers.
    - *Yes*: The system applies strict safety stock pegging. When a planned order is created for fulfilling safety stock, it will remain pegged against safety stock.  With this option, whenever the system calculates that a planned order should fulfill safety stock, then safety stock is prioritized over real demand. This option can provide better visibility in some scenarios, such as when you're using a high number of negative days.
