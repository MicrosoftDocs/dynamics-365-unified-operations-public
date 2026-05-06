---
title: Safety stock pegging options
description: Learn how to specify how strictly the system should peg safety stock as demand against the planned order that's created for it.
author: Henrikan
ms.author: henrikan
ms.topic: how-to
ms.date: 05/05/2026
ms.custom: bap-template
ai-usage: ai-assisted
ms.reviewer: kamaybac
ms.search.form:
---

# Safety stock pegging options

[!include [banner](../includes/banner.md)]

Most industries prioritize customer demand over [safety stock](safety-stock-replenishment.md). Therefore, when you must both replenish safety stock and fulfill a customer order, the system uses existing planned orders to cover the customer demand instead of leaving those planned orders pegged against safety stock.

However, some businesses prefer to allow the system to keep existing planned orders pegged against safety stock, even if customer demand can't be fulfilled as a result. This approach is known as *strict safety stock pegging*.

For each coverage group, you can specify how strictly the system should peg safety stock as demand against the planned order that's created for it.

## Prerequisites

Before you can use the features described in this article, ensure your system meets the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.36 or later.
- The feature that's named *Strict safety stock pegging for Planning Optimization* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). As of Supply Chain Management version 10.0.43, this feature is turned on by default.

## Set safety stock pegging options

Safety stock pegging options are set at the coverage group level. Follow these steps to set safety stock pegging options for a selected coverage group.

1. Go to **Master planning** \> **Setup** \> **Coverage** \> **Coverage groups**.
1. Follow one of these steps:

    - To edit an existing group, select it in the list pane, and then select **Edit** on the Action Pane.
    - To create a new group, select **New** on the Action Pane.

1. On the **General** FastTab, in the **Strict safety stock pegging** field, select one of the following options:

    - *No* – The system doesn't consider safety stock as actual demand, and it prioritizes any actual demand over safety stock. Although you can create a planned order to fulfill safety stock, any actual demand that arrives later can claim the planned safety stock quantity. (The actual demand is pegged against the planned order.) This option lets you provide a higher level of service for your customers.
    - *Yes* – The system applies strict safety stock pegging. Any planned order that you create to fulfill safety stock remains pegged against safety stock. If you select this option, whenever the system calculates that a planned order is needed to fulfill safety stock, the system prioritizes that safety stock over real demand. This option can provide better visibility in some scenarios, such as when you're using a large number of negative days.

> [!IMPORTANT]
> When you enable strict safety stock pegging, the system ignores pegging priority for safety stock planned orders. This behavior can lead to unreliable net requirements pegging and the creation of unwanted planned orders, because the safety stock demand is always prioritized regardless of any pegging priority rules you configured. Before you enable this option, carefully evaluate whether the trade-off between safety stock visibility and potential over-ordering is acceptable for your planning scenario. Learn more about how safety stock behavior differs between the deprecated master planning engine and Planning Optimization in [Safety stock fulfillment with the deprecated master planning engine](safety-stock-replenishment-in-deprecated-engine.md#differences-in-safety-stock-functionality).

## Related information

- [Safety stock fulfillment for items](safety-stock-replenishment.md)
- [Safety stock fulfillment with the deprecated master planning engine](safety-stock-replenishment-in-deprecated-engine.md)
