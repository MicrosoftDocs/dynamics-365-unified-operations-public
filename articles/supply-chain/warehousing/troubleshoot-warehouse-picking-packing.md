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

## Dimension location cannot be left blank if dimension serial number is set.

**Issue:** This error occurs if you create a transfer order for a serial item using a warehouse enabled for advance warehouse management and then, after completing the work, you try to confirm the shipment.

**Fix:** The "From" warehouse has a transit warehouse which has an empty **Default receipt location** value for the transit warehouse. To solve this, specify a location for default receipt location. Ensure default receipt location on the transit warehouse is license plate controlled.

## Invalid license plate.

**Issue:** Error message is being received on the warehouse app.

**Fix:** Ensure that the License Plate ID exists in the License Plates table and that the item(s)/quantity on the license plate is available (i.e. not blocked).

## Field 'Load weight'(=-%1) can only contain positive numbers. Update has been cancelled.**

**Issue:** Load Weight Error appears from Pack station to Staging location when work is open or from Staging to Dock location.

**Fix:** Run consistency check process for the Warehouse load weight consistency check.

## The quantity is not valid for unit %1.

**Issue:** Unable to split pick across multiple batches.

**Fix:** The warehouse worker will need to use the "Short picking" process on the Warehouse Mobile App. Assuming the issue is that the user is trying to pick multiple batches from the same location, then they could also use the 'Full' option on the Warehouse Mobile App.

## You cannot move inventory to a license plate controlled location.

**Issue:** Unable to reduce picked quantities on a load.

**Fix:** This used to be true in earlier versions; however, it's now possible to unpick to a License Plate controlled location. The user must specify the location *and* License Plate in the reduce picked quantity form from the load line.

## The Item %1 is not in location %2 in warehouse %3.

**Issue:** When a specific Batch and Serial number is reserved for a piece of work, scanning a license plate which doesn't contain that Batch/Serial number gives an incorrect error message.

**Fix** KB number: 4581881: Change the error message to: The license plate [License plate ID] does not contain the reserved dimensions [List of dimensions] for the item [Item ID].

## Printing delivery note or packing content by warehouse.

**Issue:** Is it possible to print by warehouse or site in Work audit template line updates?

**Fix:** If you are printing a document with print management settings, you can limit the scope (site/warehouse) through print management, instead of directly through the work audit template lines update form under edit print settings.

## Unable to cancel packing slip when posted in a sales order.

**Issue:** For picking/shipping processes enabled for advanced warehouse management, cancellation of the packing slip is not possible when it was posted from the sales order.

**Fix:** To correct posted packing slips for items which are enabled for warehouse management, the posting must occur from the load, not from the order directly. Microsoft has evaluated this issue and determined it to be a feature limitation. Generally, a sales order that has been picked and shipped through Warehouse management processes can be packing slip updated from the Load/Shipment and the Sales order document itself. However, if the user chooses the latter, then packing slip reversal is not possible either from the load or sales order. It is therefore recommended to customers to use the Packing slip posting from the load - in which case the reversal (to be done from the load) will be enabled.

## Not enough work can be found for cluster.

**Issue:** When using system directed cluster picking process, using a cluster profile on which it's able to pick, for example, 10 positions. This process works as planned. When start picking when there are only 8 positions (work) to be picked, the following error is shown "Not enough work can be found for cluster".

**Fix:** Edit the cluster profile by setting **Activate positions** to *No*, which should resolve this error.
