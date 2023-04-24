---
title: Assign shipments to related route segments
description: This article describes how the system apportions freight costs for multi-segment scheduled routes that use the inbound and outbound logistic process.
author: Weijiesa
ms.author: weijiesa
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 04/20/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Assign shipments to related route segments

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!-- KFM: Preview until further notice -->

This article describes how the system apportions freight costs for multi-segment scheduled routes that use the inbound and outbound logistic process.

## Prerequisites

To use this feature, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.33 or later.
- The feature that's named *(Preview) Assign shipments to related route segments* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## How shipments are assigned to route segments

This feature enables the system to apportion shipment freight costs more accurately, including for loads where multiple shipments are delivered to different segment destinations along a single route. It assigns each shipment to the most suitable route segment, based on the destination addresses of the shipment and segment. The feature then calculates each shipment's freight cost as a proportion of the load's total freight cost, based on the shipment's relative weight, volume, quantity, and distance traveled.

This feature enables correct freight cost apportionment for multi-segment scheduled routes that use the inbound and outbound logistic process. Therefore, you can evaluate the true profitability of sales orders by apportioning freight cost at the item line level. This feature provides a fair and trusted foundation for the billing of freight cost. It also reflects the cost of inbound freight in the material valuation of stock.

This feature applies only to shipments that are managed by using the **Transportation management** (TMS) module.
