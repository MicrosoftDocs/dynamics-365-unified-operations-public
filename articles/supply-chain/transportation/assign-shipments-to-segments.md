---
title: Assign shipments to related route segments
description: Learnhow to configure the system to apportion freight costs for multi-segment scheduled routes that use the inbound and outbound logistic process.
author: lisascholz
ms.author: lisascholz
ms.topic: how-to
ms.date: 01/17/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Assign shipments to related route segments

[!include [banner](../includes/banner.md)]

This article describes how to configure the system to apportion freight costs for multi-segment scheduled routes that use the inbound and outbound logistic process. It also describes how this feature works.

## Enable the feature

To configure the system to apportion freight costs for multi-segment scheduled routes, follow these steps:

1. Go to **Transportation management \> Setup \> Transportation management parameters**.
1. Open the **General** tab.
1. On the **Shipment** FastTab, set **Assign shipment to related route segments** to *Yes*.
1. On the Action Pane, select **Save**.

## How shipments are assigned to route segments

This feature enables the system to apportion shipment freight costs more accurately, including for loads where multiple shipments are delivered to different segment destinations along a single route. It assigns each shipment to the most suitable route segment, based on the destination addresses of the shipment and segment. The feature then calculates each shipment's freight cost as a proportion of the load's total freight cost, based on the shipment's relative weight, volume, quantity, and distance traveled.

This feature enables correct freight cost apportionment for multi-segment scheduled routes that use the inbound and outbound logistic process. Therefore, you can evaluate the true profitability of sales orders by apportioning freight cost at the item line level. This feature provides a fair and trusted foundation for the billing of freight cost. It also reflects the cost of inbound freight in the material valuation of stock.

This feature applies only to shipments that are managed by using the **Transportation management** (TMS) module.
