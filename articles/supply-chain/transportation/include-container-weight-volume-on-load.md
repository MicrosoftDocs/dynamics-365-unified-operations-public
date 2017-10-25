---
# required metadata

title: Include container weight and volume on load
description: This topic describes how to set up and apply functionality to include container weight and volume on loads.
author: pjacobse
manager: AnnBe
ms.date: 05/26/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: bis
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 269384
ms.search.region: Global
# ms.search.industry: 
ms.author: pjacobse
ms.search.validFrom: 2017-09-20
ms.dyn365.ops.version: AX 7.0.0

---

# Include container weight and volume on load

[!include[banner](../includes/banner.md)]

The functionality for including the container weight and volume on a load gives
a clear representation of the total weight and volume of containers and items
that are going on a load.

A load contains a single shipment or multiple shipments, and these shipments
contain distinct items that belong to a single sales order or multiple sales
orders. The items are stored inside a container, and containers are loaded on a
load. Items that are outside a container can also be part of a load. Based on
these conditions, the system calculates values for the weight and volume on the
load by considering the weight and volume of both containers and items.

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

## How it is set up

The number of containers that should be considered for a load is calculated
based on the weight and volume of the container, and on the percentage of the
container is used.

-   To set the weight and volume for a container, click **Warehouse management**
    \> **Setup** \> **Containers** \> **Container types**.

-   To set the container utilization percentage, click **Warehouse management**
    \> **Setup** \> **Containers** \> **Container groups**, and then enter a
    value in the **Container utilization percentage** field.
