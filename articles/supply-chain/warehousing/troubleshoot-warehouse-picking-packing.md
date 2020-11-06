---
# required metadata

title: Troubleshoot picking and packing
description: This topic describes how to fix common issues that you might encounter while picking and packing in Dynamics 365 Supply Chain Management.
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

This topic describes how to fix common issues that you might encounter while picking and packing in Dynamics 365 Supply Chain Management.

## I receive the error "Dimension location can't be left blank if dimension serial number is set."

### Issue description

This error occurs if you create a transfer order for a serial item using a warehouse enabled for an advanced warehouse management (WMS) and then, after completing the work, you try to confirm the shipment.

### Issue resolution

The "from" warehouse has a transit warehouse that had an empty **Default receipt location** value. To resolve this issue, specify a location for default receipt location in the transit warehouse. Ensure that the default receipt location on the transit warehouse is license plate controlled.

## I receive the error "Invalid license plate."

### Issue description

This error message is received on the warehouse app when scanning a license plate ID.

### Issue resolution

Ensure the license plate ID exists in the license plates table and that the items and quantities on the license plate are available (in other words, not blocked).

## I receive the error "Field 'Load weight'(=-%1) can only contain positive numbers. Update has been canceled."

### Issue description

The *Load weight* error appears when processing work from packing to staging locations, or from staging to dock locations, when there is open work.

### Issue resolution

Run the **System administration \> Periodic tasks \> Database \> Consistency check** process for **Warehouse load weight consistency check** to resolve the issue.

## I receive the error "The quantity is not valid for unit %1."

### Issue description

The error is shown when you can't perform a *split pick* across multiple batches.

### Issue resolution

The warehouse worker must use the *Short picking* process on the warehouse app. If you are trying to pick multiple batches from the same location, then you could also use the **Full** option on the warehouse app.

## I can't move inventory to a license-plate controlled location

### Issue description

You can't reduce picked quantities on a load.

### Issue resolution

This used to be true in earlier versions. However, it's now possible to unpick to a license-plate controlled location. You must specify the **Location** *and* **License Plate ID** in **Reduce picked quantity** on the load line.

## Can I print a delivery note or packing content by warehouse?

### Issue description

Is it possible to print by *Warehouse* or *Site* on the **Work audit template line update** page?

### Issue resolution

When you print a document with print management settings, limit the scope (site/warehouse) through print management instead of by selecting **Edit print settings** on the **Work audit template line update** page.

## I can't cancel a packing slip when posted in a sales order

### Issue description

When picking and shipping processes enabled for advanced warehouse management, you can't cancel the packing slip after it was posted from the sales order.

### Issue resolution

To correct posted packing slips for items that are enabled for advanced warehouse management, the posting must occur from the load, not from the order. Microsoft has evaluated this issue and determined it to be a feature limitation. Generally, a sales order that has been picked and shipped through warehouse management processes can be packing-slip updated from the load or shipment and the sales order document itself. However, if you choose the latter, then packing slip reversal still isn't possible from the load or sales order. We therefore recommend that you use the packing slip posting from the load, in which case the reversal (to be done from the load) will be enabled.

## I receive the error "Not enough work can be found for cluster."

### Issue description

When using the *System directed cluster picking* process, configuring a cluster profile where it's possible to pick, for example, 10 positions, this process works as planned when there is enough work to pick to 10 positions. However, when there are only 8 positions (work) to be picked, the error is shown because there is not enough work for one cluster.

### Issue resolution

Edit the cluster profile by setting the **Activate positions** parameter to *No*, which should resolve this error.
