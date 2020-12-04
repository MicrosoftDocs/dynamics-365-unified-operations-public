---
# required metadata

title: Troubleshoot load building and shipments
description: This topic describes how to fix common issues that you might encounter while you work with load building and shipments in Microsoft Dynamics 365 Supply Chain Management.
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

This topic describes how to fix common issues that you might encounter while you work with load building and shipments in Microsoft Dynamics 365 Supply Chain Management.

## I receive the following error message: "You can't create a load line for this order line because it contains inventory dimensions that are invalid..."

### Issue description

You receive the following error message when you try to release a return sales order to the warehouse:

> You can't create a load line for this order line because it contains inventory dimensions that are invalid. You can't reference inventory dimensions that are located below the location dimension in the reservation hierarchy. Remove the invalid dimensions from the order line.

### Issue resolution

Unfortunately, the product doesn't support load processing for a sales return process. Therefore, you can't release the return sales order to the warehouse.

On sales order transactions, you can't reference inventory dimensions that are located below the **Location** dimension in the reservation hierarchy. The resolution is to remove the invalid dimensions from the order line.

## I receive the following error message: "One of the lines is already on a load. Unable to release to warehouse."

### Issue description

If you manually create loads, or if you set up the process so that loads are already created before sales order line entry occurs, the assumption is that the subsequent release will be done manually, and that the route and rating from the load will be used.

In another possible scenario, you're trying to do an automatic release to the warehouse, but the wave process failed to create work. Therefore, an open shipment or load is still created. This open shipment or load then blocks subsequent attempts to automatically release the order until you either delete the open shipment or load, or manually reprocess the wave.

### Issue resolution

You can release from the sales order page, or automatic release can be done from the release sales order page, only if no load exists before the release to the warehouse. The load will automatically be created after the wave is processed.

## I receive the following error message: "The delivery note correction can't be processed. The delivery note only contains items that are subject to warehouse management processes, as these are not supported by Delivery Note correction."

### Issue description

After you post a delivery note, you can't cancel it, because the **Cancel** button is unavailable. You also can't correct the delivery note. If you try, you receive this error message.

### Issue resolution

To correct posted packing slips for items that are enabled for advanced warehouse management (WMS), you must do the posting from the load, not directly from the order.

## How can I create work from outbound loads instead of waves?

### Issue description

Here is one way to reproduce this issue.

1. Create an outbound load by using a sales order or transfer order.
2. Release the load to the warehouse.
3. Notice that no picking work has yet been generated.

### Issue resolution

If work must be generated immediately when the load is released, you must configure the wave template accordingly. On the wave template, set the following options to *Yes*:

- Automate wave creation
- Process wave at release to warehouse
- Automate wave release

## I can't re-release a partially shipped load.

### Issue description

You can't release a partially shipped load to the warehouse. When you do the release to the warehouse, an "Operation complete" message appears, but nothing happens, and no work is created for the remaining quantity. This issue occurs when you use transport load functionality and there is an incomplete reservation.

### Issue resolution

[KB issue 470069](https://fix.lcs.dynamics.com/Issue/Details?kb=4574490&bugId=470069&dbType=3&qc=84ce1e09d7032d8b8ef86f5a0c68b86badf3dfaf29686c5ebbe97c53c0957b5f) ("Partially shipped loads can be re-waved and re-processed") is fixed in [release 10.0.15](../get-started/whats-new-scm-10-0-15.md).
