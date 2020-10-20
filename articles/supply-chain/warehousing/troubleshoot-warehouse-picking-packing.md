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

## "Dimension location cannot be left blank if dimension serial number is set."

### Issue description

This error occurs if you create a transfer order for a serial item using a warehouse enabled for an advanced warehouse management (WMS) and then, after completing the work, you try to confirm the shipment.

### Issue resolution

The "From" warehouse has a transit warehouse which had an empty **Default receipt location** value for the transit warehouse. To resolve this, specify a location for default receipt location in the transit warehouse. Ensure that the default receipt location on the transit warehouse is license plate controlled.

## "Invalid license plate."

### Issue description

This error message is received on the warehouse app when scanning a license plate ID.

### Issue resolution

Ensure the License Plate ID exists in the License Plates table and that the item(s) and quantities on the license plate are available (i.e. not blocked).

## "Field 'Load weight'(=-%1) can only contain positive numbers. Update has been cancelled."

### Issue description

The *Load Weight* error appears when processing work from Pack station to Staging locations, or from Staging to Dock locations, when there is open work.

### Issue resolution

Run the **System administration \> Periodic tasks \> Database \> Consistency check** process for **Warehouse load weight consistency check** to resolve the issue.

## "The quantity is not valid for unit %1."

### Issue description

The error is generated when the user is unable to perform a *split pick* across multiple batches.

### Issue resolution

The warehouse worker will need to use the *Short picking* process on the Warehouse Mobile App. Assuming that the issue is the user is trying to pick multiple batches from the same location, then they could also use the *Full* option on the Warehouse Mobile App.

## You cannot move inventory to a license plate controlled location

### Issue description

Users are unable to reduce picked quantities on a load.

### Issue resolution

This used to be true in earlier versions; however, it's now possible to unpick to a License Plate controlled location. The user must specify the **Location** *and* **License Plate ID** in **Reduce picked quantity** on the load line.

## "The Item %1 is not in location %2 in warehouse %3."

### Issue description

When a specific Batch and Serial number is reserved for a piece of work, scanning a license plate ID which doesn't contain that Batch/Serial number gives an incorrect error message.

### Issue resolution

The issue is resolved by deploying KB number: 4581881: Change the error message to: The license plate [License plate ID] does not contain the reserved dimensions [List of dimensions] for the item [Item ID].

## Printing delivery note or packing content by warehouse

### Issue description

Is it possible to print by *Warehouse* or *Site* in **Work audit template line update**?

### Issue resolution

If you are printing a document with print management settings; you can limit the scope (site/warehouse) through print management, instead of directly through the work audit template lines update form, under edit print settings.

## Unable to cancel packing slip when posted in a sales order

### Issue description

For picking/shipping processes enabled for advanced warehouse management, cancellation of the packing slip is not possible when it was posted from the sales order.

### Issue resolution

To correct posted packing slips for items which are enabled for warehouse management, the posting must occur from the load, not from the order directly. Microsoft has evaluated this issue and determined it to be a feature limitation. Generally, a sales order that has been picked and shipped through Warehouse management processes can be packing slip updated from the Load/Shipment and the Sales order document itself. However, if the user chooses the latter, then packing slip reversal is not possible either from the load or sales order. It is therefore recommended to customers to use the Packing slip posting from the load - in which case the reversal (to be done from the load) will be enabled.

## "Not enough work can be found for cluster."

### Issue description

When using the **System directed cluster picking** process; configuring a cluster profile on which it's able to pick, for example, 10 positions, this process works as planned when there is enough work to pick to 10 positions. However, when there are only 8 positions (work) to be picked, the error is shown because there is not enough work for one cluster.

### Issue resolution

Edit the cluster profile by setting the **Activate positions** parameter to *No*, which should resolve this error.
