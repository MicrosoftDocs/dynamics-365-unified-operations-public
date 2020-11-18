---
# required metadata

title: Troubleshoot picking and packing
description: This topic describes how to fix common issues that you might encounter while you pick and pack in Microsoft Dynamics 365 Supply Chain Management.
author: perlynne
manager: tfehr
ms.date: 10/19/2020
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
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: perlynne
ms.search.validFrom: 2020-10-19
ms.dyn365.ops.version: 10.0.15
---

# Troubleshoot picking and packing

[!include [banner](../includes/banner.md)]

This topic describes how to fix common issues that you might encounter while you pick and pack in Microsoft Dynamics 365 Supply Chain Management.

## I receive the following error message: "Dimension location can't be left blank if dimension serial number is set."

### Issue description

You receive this error message if you create a transfer order for a serial item by using a warehouse that is enabled for advanced warehouse management (WMS), and then, after the work is completed, you try to confirm the shipment.

### Issue resolution

The **Default receipt location** field is blank for a transit warehouse of the "from" warehouse. To fix this issue, specify a default receipt location in the transit warehouse. Make sure that this location is license plate–controlled.

## I receive the following error message: "Invalid license plate."

### Issue description

You receive this error message in the warehouse app when you scan a license plate ID.

### Issue resolution

Make sure that the license plate ID exists in the license plates table, and that the items and quantities on the license plate are available (in other words, they aren't blocked).

## I receive the following error message: "Field 'Load weight'(=-%1) can only contain positive numbers. Update has been canceled."

### Issue description

You receive this error message if there is open work when you process work from packing locations to staging locations, or from staging locations to dock locations.

### Issue resolution

To fix this issue, go to **System administration \> Periodic tasks \> Database \> Consistency check**, and run the process for **Warehouse load weight consistency check**.

## I receive the following error message: "The quantity is not valid for unit %1."

### Issue description

You receive this error message when you try to perform a *split pick* across multiple batches.

### Issue resolution

The warehouse worker must use the *Short picking* process in the warehouse app. If you're trying to pick multiple batches from the same location, you can also use the **Full** option in the warehouse app.

## I can't move inventory to a location that is license plate–controlled.

### Issue description

You can't reduce picked quantities on a load.

### Issue resolution

In earlier versions, you can't reduce picked quantities on a load. However, you can now unpick to a license plate–controlled location. You must specify both a **Location** value and a **License Plate ID** value in **Reduce picked quantity** on the load line.

## Can I print a delivery note or packing content by warehouse?

### Issue description

You want to print a delivery note or packing content by warehouse or site on the **Work audit template line update** page.

### Issue resolution

When you print a document by using Print management settings, limit the scope (site/warehouse) through Print management instead of by selecting **Edit print settings** on the **Work audit template line update** page.

## I can't cancel a packing slip after it's posted from a sales order.

### Issue description

When picking and shipping processes are enabled for advanced warehouse management, you can't cancel a packing slip after it's posted from a sales order.

### Issue resolution

To correct posted packing slips for items that are enabled for advanced warehouse management, the posting must occur from the load, not from the order. Microsoft has evaluated this issue and has determined that it's a feature limitation. In general, a sales order that has been picked and shipped through warehouse management processes can be packing slip–updated from the load or shipment and the sales order document itself. However, if you packing slip–update the sales order from the shipment, packing slip reversal still can't be done from the load or sales order. Therefore, we recommend that you use the packing slip posting from the load. In this case, the reversal that must be done from the load will be enabled.

## I receive the following error message: "Not enough work can be found for cluster."

### Issue description

When you use the *System directed cluster picking* process, if you configure a cluster profile where, for example, 10 positions can be picked, the process works as planned when there is enough work to pick to 10 positions. However, if there are only eight positions to pick, you receive this error message, because there isn't enough work for one cluster.

### Issue resolution

To fix this issue, edit the cluster profile, and set the **Activate positions** option to *No*.
