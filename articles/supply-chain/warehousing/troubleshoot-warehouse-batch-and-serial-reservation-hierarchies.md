---
# required metadata

title: Troubleshoot warehouse batch and serial reservation hierarchies
description: This topic describes how to fix common issues that you might encounter while you work with reservation hierarchies that use batch or serial dimensions.
author: perlynne
ms.date: 3/12/2021
ms.topic: article
ms.prod: 
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
ms.author: perlynne
ms.search.validFrom: 3/12/2021
---

# Troubleshoot warehouse batch and serial reservation hierarchies

[!include [banner](../includes/banner.md)]

This topic describes how to fix common issues that you might encounter while you work with reservation hierarchies that use batch or serial dimensions.

For more information, see [Flexible warehouse-level dimension reservation policy](flexible-warehouse-level-dimension-reservation.md).

The reservation hierarchy of an item dictates the requirement of storage dimensions that must be fulfilled to assign a location to a demand order. These dimensions can be described as *dimensions above location*, for all the dimensions that must be fulfilled before a location is assigned, and *dimensions below location*, for dimensions that can be allocated after a location has been assigned to the demand order. These reservation hierarchies are also known as *batch-above* and *batch-below* reservation hierarchies, or *serial-above* and *serial-below* reservation hierarchies.

Inventory can be successfully allocated only if there are no gaps in the dimensions above location. For example, in a *batch-above* reservation hierarchy, you expect **Site,** **Warehouse,** and **Batch number** dimensions to be specified on the demand order. If any of these dimensions are missing, the allocation process will fail. By contrast, in a *batch-below* or *serial-below* reservation hierarchy, a batch or serial number might be specified on the demand order, but the allocation process doesn't require it.

## I receive the following error message: "To be assigned to wave, load lines must specify the dimensions above the location. To assign these dimensions, reserve and recreate the load line."

### Issue description

When you use an item that has a *batch-above* reservation hierarchy, the **Release to warehouse** command on the **Load planning workbench** page doesn't work if you try to release a load for a partial quantity. You receive this error message, and no work is created for the partial quantity.

However, when you use an item that has a *batch-below* reservation hierarchy, you can release a load for a partial quantity from the **Load planning workbench** page.

### Issue cause

When a dimension is above the **Location** dimension in the reservation hierarchy, it must be specified before the release to the warehouse. Partial quantities can't be released if one or more dimensions above **Location** aren't specified.

## The auto-reservation prompt for a batch number is triggered even though there is available inventory.

### Issue description

When you use an item that has a *batch-above* reservation hierarchy in a warehouse that hasn't enabled warehouse processes, and automatic reservation is enabled, the auto-reservation prompt for a batch number is shown even if only one batch is available for picking.

However, when you use the same item in a warehouse where warehouse processes are enabled, the auto-reservation prompt isn't shown.

### Issue cause

If a reservation hierarchy is defined as *batch-above* or *serial-above*, the referenced dimension (**Batch number** or **Serial number**) must always be specified on demand orders. Warehouse processes might be able to complete the information if a single batch or serial number is available. However, because the warehouse isn't enabled for warehouse processes, the user must always specify all the dimensions above **Location**.

## Slotting templates that have the Consider on-hand slot criterion don't consider current on-hand inventory for batch-enabled items.

For more information, see [Warehouse slotting](warehouse-slotting.md).

### Issue description

Slotting templates that have the *Consider on-hand* slot criterion don't consider current on-hand inventory for *batch-above* items. They consider it only if the batch number is specified on the sales order line.

However, when you use *batch-below* items, the current on-hand inventory is considered as expected.

### Issue cause

The slotting template header can be defined for the *Ordered,* *Reserved*, or *Released* demand strategy. For the *Ordered* demand strategy, the same reservation hierarchy requirements apply that apply to reservation or release to warehouse processes. Therefore, for items that have *batch-above* and *serial-below* reservation hierarchies, the batch or serial number must be specified on the demand order (sales or transfer). Alternatively, the *Reserved* demand strategy can be used to select the batch or serial number before the warehouse slotting demand is generated.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
