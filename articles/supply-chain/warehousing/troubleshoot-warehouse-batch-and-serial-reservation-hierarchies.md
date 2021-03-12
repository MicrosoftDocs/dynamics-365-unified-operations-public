---
# required metadata

title: Troubleshoot warehouse batch and serial reservation hierarchies
description: This topic describes how to fix common issues that you might encounter while reservation hierarcies that use batch or serial dimensions in Microsoft Dynamics 365 Supply Chain Management.
author: clmontor
manager: okryva
ms.date: 3/12/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: clmontor
ms.search.validFrom: 3/12/2021
---

# Troubleshoot warehouse batch and serial reservation hierarchies

[!include [banner](../includes/banner.md)]

This topic describes how to fix common issues that you might encounter while you work with warehouse reservations that include batch or serial numbers in Microsoft Dynamics 365 Supply Chain Management.

For more information, see [Flexible warehouse-level dimension reservation policy](flexible-warehouse-level-dimension-reservation.md).

The reservation hierarchy of an item dictates the requirement of storage dimensions that must be fulfilled in order to assign a location to a demand order. These can be described as dimensios above location, for all the necessary dimensions to fullfil before assigning a location; and dimensions below location that may be allocated after a location has been assigned to the demand order. This is also known as "Batch-above" and "Batch-below," or "Serial-above" and "Serial-below" reservation hierarchies.

Whenever allocating inventory there must not be gaps in the dimensions above location in order for the allocating process to succeed. For example, in a batch-above reservation hierarchies we expect to have **Site,** **Warehouse,** and **Batch number** dimensions specified in the demand order, missing any of these dimensions will cause the allocation process to fail. In contrast, a batch-below or serial-below reservation hierarchy may have a batch or serial number specified in the demand order but it is not a necessary specification for the allocation process.


## I receive the following error message: "To be assigned to wave, load lines must specify the dimensions above the location. To assign these dimensions, reserve and recreate the load line."

### Issue description

When you use an item that has a "batch-above" reservation hierarchy, the **Release to warehouse** command on the **Load planning workbench** page for a partial quantity doesn't work. You receive this error message, and no work is created for the partial quantity.

However, if you use an item that has a "batch below" reservation hierarchy, you can release a load from the **Load planning workbench** page for a partial quantity.

## Issue cause

When a dimension is above the **Location** dimension in the reservation hierarchy, it must be specified before the release to the warehouse. Partial quantities can't be released if one or more dimensions above **Location** aren't specified.


## Auto-reservation prompt for Batch number is triggering despite having available inventory 

### Issue description

When you use an item that has "batch-above" reservation hierarchy in a warehouse that has not enabled warehouse processes and automatic reservation enabled, even if there is a single batch available for picking, the Auto-reservation prompt for Batch number is shown.

However, when you use the same item in a warehouse with warehouse processes enabled the autoreservation prompt is not shown.

### Issue cause

Defining a reservation hierarchy as "batch-above" or "serial-above" requires for this dimension to always be specified on the demand order; whenever possible, warehouse processes may be able to complete the information if a single batch or serial is available. However, given that the warehouse is not enabled for warehouse processes, all the above location dimensions must always be specified by the user.


## Slotting templates with slot criteria: Consider on-hand doesn't consider current on-hand for batch enabled items.

For more information, see [Warehouse slotting](warehouse-slotting.md).

### Issue description

The slotting template with slot criteria: Consider on-hand doesn't consider current on-hand for batch-above items and only consider it if the batch number is specified on the sales order line.

However, when you use batch-below items the current on-hand is considered as expected.

### Issue cause

The slotting template header may be defined for **Ordered,** **Reserved,** or **Released** demand strategies. For the **Ordered** demand strategy the same reservation hierarchy requirements apply as they would to reservation or releasing to warehouse processes. For items with "batch-above" and "serial-below" reservation hierarchies this menas that the batch or serial number must be specified in the demend order (sales or transfer). Alternatively, the **Reserved** demand strategy may be used to select the batch or serial number before generating the warehouse slotting demand.



