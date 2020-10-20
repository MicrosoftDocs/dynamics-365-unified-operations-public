---
# required metadata

title: Troubleshoot load building and shipments
description: This topic describes how to fix common issues that you might encounter while working with load building and shipments in Dynamics 365 Supply Chain Management.
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

# Troubleshoot load building and shipments

[!include [banner](../includes/banner.md)]

This topic describes how to fix common issues that you might encounter while working with load building and shipments in Dynamics 365 Supply Chain Management.

## Can't execute Release to warehouse on a Return sales order

### Issue description

The error "You can't create a load line for this order line because it contains inventory dimensions that are invalid. You can't reference inventory dimensions that are located below the location dimension in the reservation hierarchy. Remove the invalid dimensions from the order line." is generated when trying to release to warehouse a return sales order.

### Issue resolution

Unfortunately, the product does not support load processing for a sales return process and thereby not possible to get released to the warehouse.

On Sales Order transactions, you can't reference inventory dimensions that are located below the location dimension in the reservation hierarchy. The resolution would be to remove the invalid dimensions from the order line.

## "One of the lines is already on a load. Unable to release to warehouse."

### Issue description

If you choose the process path of manually creating loads or have the process setup such that Loads are created already upon Sales Order line entry, then the assumption is that the subsequent releasing is done manually following the route and rating from the load.

The other scenario here is that the user is trying to perform an automatic Release To Warehouse, but the wave process failed to create work, which results in an open shipment/load still being created. This then blocks the user from subsequent attempts to automatically release the order until they either (a) delete the open shipment/load, or (b) re-process the wave manually.

### Issue resolution

To release from the Sales Order form, or to release automatically from the release sales order form, no load must exist before releasing to the warehouse. The load will be created automatically once the wave is processed.

## "The delivery note correction can't be processed. The delivery note only contains items that are subject to warehouse management processes, as these are not supported by Delivery Note correction."

### Issue descripiton

After posting of delivery note the user is unable to cancel the posted *Delivery note* since the button **Cancel** is disabled. Also, the user is unable to correct the delivery note, while performing the attempted correction the error is thrown.

### Issue resolution

In order to correct posted packing slips for items which are enabled for advanced warehouse management (WMS), the posting must occur from the load, not from the order directly.

## How to create work from outbound loads rather than waves

### Issue description

Is it possible to create work from outbound loads rather than waves?

One way to reproduce this error is to do the following:

1. Create an outbound load using a sales or transfer order.
2. Release load to warehouse.
3. Currently, no picking work is being generated.

### Issue resolution

If work needs to be generated immediately when the load is released, then Wave template needs to be configured accordingly. On wave template, set the following settings to Yes:

- Automate wave creation.
- Process wave at release to warehouse.
- Automate wave release.

## Partially shipped load can't be released again.

### Issue description

A "Partially shipped" load can't be released again to the warehouse. The message "Operation complete" appears at release to the warehouse, but nothing happens, no work gets created for the remaining quantity. This happens when originally there is an Incomplete reservation and using Transport Load functionality.

### Issue resolution
The issue is resolved by deploying KB number: 4574490: Partially shipped loads can be re-waved and re-processed.
