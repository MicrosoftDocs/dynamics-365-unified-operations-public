---
title: Include container weight and volume on load
description: Learn how to set up and apply functionality to include container weight and volume on loads, including an outline on where this functionality applies.
author: lisascholz91
ms.author: lisascholz
ms.reviewer: kamaybac
ms.search.form: TMSRateRouteWorkbench, TMSDriverLogListPage, TMSTransportationTender
ms.topic: how-to
ms.date: 06/17/2025
ms.custom: 
  - bap-template
---

# Include container weight and volume on load

[!include [banner](../includes/banner.md)]

The functionality for including the container weight and volume on a load provides a clear representation of the total weight and volume of containers and items in a load.

A load contains one or more shipments, and these shipments contain distinct items that belong to one or more sales orders. The items are stored inside a container, and containers are loaded on a load. Items outside a container can also be part of a load. Based on these conditions, the system calculates values for the weight and volume on the load by considering the weight and volume of both containers and items.

## Where it's used

The functionality for including the container weight and volume on a load applies in transportation management processes. For example, the values are used on the **Rate route workbench** page, where they help define the rate and route for loads. They're also used for transportation tenders and driver check-in.

When creating a load on the **Rate route workbench** page, you can also see and track capacity utilization against the maximum weight and volume of the chosen load template. On the **Load template assignment** dialog that opens when creating a load, the **Details**, **Weight**, and **Volume** tabs show the total quantity, weight, and volume of the load respectively. The **Weight** and **Volume** tabs also show how close you're to the maximum defined weight and volume for the selected load template, and the system notifies you if you exceed either the maximum allowable weight or volume.

If the calculated values aren't precise, you can adjust them by entering the actual values for the weight and volume on the load.

## How it's set up

The number of containers considered for a load is calculated based on the weight, volume, and percentage of the container used.

- To set the weight and volume for a container, go to **Warehouse management** \> **Setup** \> **Containers** \> **Container types**.
- To set the container utilization percentage, go to **Warehouse management** \> **Setup** \> **Containers** \> **Container groups**. Then enter a value in the **Container utilization percentage** field.

To learn more about how to set up the dimensions of a load template, go to [Load templates](/dynamics365/supply-chain/transportation/tasks/load-template).

The units used for weight and volume are based on the configured system units for the specific legal entity.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
