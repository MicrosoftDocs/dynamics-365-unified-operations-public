---
title: Safety stock pegging options
description: Learn how to specify how strictly the system should peg safety stock as demand against the planned order that's created for it.
author: t-benebo
ms.author: benebotg
ms.topic: how-to
ms.date: 01/10/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Safety stock pegging options

[!include [banner](../includes/banner.md)]

For most industries, customer demand is prioritized over [safety stock](safety-stock-replenishment.md). Therefore, when you must both replenish safety stock and fulfill a customer order, the system uses existing planned orders to cover the customer demand instead of leaving those planned orders pegged against safety stock.

However, some businesses prefer to allow the system to keep existing planned orders pegged against safety stock, even if customer demand can't be fulfilled as a result. This approach is known as *strict safety stock pegging*.

For each coverage group, you can specify how strictly the system should peg safety stock as demand against the planned order that's created for it.

## Prerequisites

Before you can use the features that are described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.36 or later.
- The feature that's named *Strict safety stock pegging for Planning Optimization* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). As of Supply Chain Management version 10.0.43, this feature is turned on by default.

## Set safety stock pegging options

Safety stock pegging options are set at the coverage group level. Follow these steps to set safety stock pegging options for a selected coverage group.

1. Go to **Master planning** \> **Setup** \> **Coverage** \> **Coverage groups**.
1. Follow one of these steps:

    - To edit an existing group, select it in the list pane, and then select **Edit** on the Action Pane.
    - To create a new group, select **New** on the Action Pane.

1. On the **General** FastTab, in the **Strict safety stock pegging** field, select one of the following options:

    - *No* – Safety stock isn't considered actual demand, and any actual demand is prioritized over it. Although a planned order can be created to fulfill safety stock, any actual demand that arrives later can claim the planned safety stock quantity. (The actual demand will be pegged against the planned order.) This option lets you provide a higher level of service for your customers.
    - *Yes* – The system applies strict safety stock pegging. Any planned order that's created to fulfill safety stock remains pegged against safety stock. If this option is selected, whenever the system calculates that a planned order is needed to fulfill safety stock, that safety stock remains prioritized over real demand. This option can provide better visibility in some scenarios, such as when you're using a large number of negative days.
