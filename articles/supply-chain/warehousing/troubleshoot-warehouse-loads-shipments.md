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

## I get the error "You can't create a load line for this order line because it contains inventory dimensions that are invalid..."

### Issue description

The following error message is shown when trying to release to warehouse a return sales order:

> You can't create a load line for this order line because it contains inventory dimensions that are invalid. You can't reference inventory dimensions that are located below the location dimension in the reservation hierarchy. Remove the invalid dimensions from the order line.

### Issue resolution

Unfortunately, the product does not support load processing for a sales return process, which means you can't release to the warehouse.

On sales order transactions, you can't reference inventory dimensions that are located below the location dimension in the reservation hierarchy. The resolution would be to remove the invalid dimensions from the order line.

## I receive the error "One of the lines is already on a load. Unable to release to warehouse."

### Issue description

If you choose the process path of manually creating loads or have the process set up such that loads are created already upon sales order line entry, then the assumption is that the subsequent releasing will be done manually following the route and rating from the load.

Another possible scenario is that you are trying to perform an automatic release to warehouse, but the wave process failed to create work, which results in an open shipment or load still being created. This then blocks subsequent attempts to automatically release the order until you either (a) delete the open shipment or load, or (b) re-process the wave manually.

### Issue resolution

To release from the sales order page, or to release automatically from the release sales order page, no load must exist before releasing to the warehouse. The load will be created automatically once the wave is processed.

## I receive the error "The delivery note correction can't be processed. The delivery note only contains items that are subject to warehouse management processes, as these are not supported by Delivery Note correction."

### Issue description

After posting a delivery note, you can't cancel the posted delivery note because the  **Cancel** button is disabled. Also, you can't correct the delivery note, and while performing the attempted correction, the error is thrown.

### Issue resolution

To correct posted packing slips for items that are enabled for advanced warehouse management (WMS), the posting must occur from the load, not from the order directly.

## How can I create work from outbound loads rather than waves?

### Issue description

One way to reproduce this error is to do the following:

1. Create an outbound load using a sales or transfer order.
2. Release the load to warehouse.
3. Notice that no picking work has been generated yet.

### Issue resolution

If work needs to be generated immediately when the load is released, then the wave template must be configured accordingly. On the wave template, set the following settings to *Yes*:

- **Automate wave creation**
- **Process wave at release to warehouse**
- **Automate wave release**

## I can't rerelease a partially shipped load.

### Issue description

A partially shipped load can't be released to the warehouse. The message "Operation complete" appears at release to the warehouse, but nothing happens, and no work gets created for the remaining quantity. This happens when you are using transport load functionality and there is an incomplete reservation.

### Issue resolution

[KB issue 470069](https://fix.lcs.dynamics.com/Issue/Details?kb=4574490&bugId=470069&dbType=3&qc=84ce1e09d7032d8b8ef86f5a0c68b86badf3dfaf29686c5ebbe97c53c0957b5f) ("Partially shipped loads can be re-waved and re-processed") is resolved in [release 10.0.15](../get-started/whats-new-scm-10-0-15.md).
