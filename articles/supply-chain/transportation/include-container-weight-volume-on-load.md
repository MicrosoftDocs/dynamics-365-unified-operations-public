---
title: Include container weight and volume on load
description: Learn how to set up and apply functionality to include container weight and volume on loads, including an outline on where this functionality applies.
author: lisascholz91
ms.author: lisascholz
ms.topic: article
ms.date: 05/26/2017
ms.reviewer: kamaybac
ms.search.form: TMSRateRouteWorkbench, TMSDriverLogListPage, TMSTransportationTender
---

# Include container weight and volume on load

[!include [banner](../includes/banner.md)]

The functionality for including the container weight and volume on a load gives
a clear representation of the total weight and volume of containers and items
that are going on a load.

A load contains a single shipment or multiple shipments, and these shipments
contain distinct items that belong to a single sales order or multiple sales
orders. The items are stored inside a container, and containers are loaded on a
load. Items that are outside a container can also be part of a load. Based on
these conditions, the system calculates values for the weight and volume on the
load by considering the weight and volume of both containers and items.

The units used here for the weight and volume are based on the system units in the specific legal entity.

If the calculated values aren’t precise, you can adjust them by entering the
actual values for the weight and volume on the load. The values for the weight
and volume are used in transportation management processes. For example, the
values are used in the rate route workbench, where they help define the rate and
route for loads, and they are also used for transportation tenders and driver
check-in.

## Where it applies

The functionality for including the container weight and volume on a load
applies in transportation management processes, such as the rate route
workbench, transportation tenders, and driver check-in.

When creating a load on the Rate Route Workbench, the **Load template assignment** pop-up page opens, which requires a **Load template ID** to be entered. At the bottom of this page under the Details, Weight and Volume tabs, you will see total quantity, weight and volume of the load as well as your capacity utilization on the selected **Load template ID**. For example, if you select a 40' container as a **Load template ID**, the system will use the configured weight and volume capacity of this container size. Here you will see if you are approaching the weight and/or volume limits of the load template. The system will notify you if you do exceed either on the maximum allowable weight or volume.

## How it is set up

The number of containers that should be considered for a load is calculated
based on the weight and volume of the container, and on the percentage of the
container is used.

-   To set the weight and volume for a container, click **Warehouse management**
    \> **Setup** \> **Containers** \> **Container types**.

-   To set the container utilization percentage, click **Warehouse management**
    \> **Setup** \> **Containers** \> **Container groups**, and then enter a
    value in the **Container utilization percentage** field.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
