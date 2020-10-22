---
# required metadata

title: Troubleshooting warehouse configuration
description: This topic describes how to fix common issues that you might encounter while configuring Dynamics 365 Supply Chain Management.
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

# Troubleshooting warehouse configuration

[!include [banner](../includes/banner.md)]

This topic describes how to fix common issues that you might encounter while configuring Dynamics 365 Supply Chain Management.

## I received the error "The license plate or location is not valid."

### Issue description

Scanning a license plate ID or location generates the error message.

### Issue resolution

Check that the License Plate ID is not reserved by something else. This used to occur when a user scanned a value on the Warehouse Mobile App that was *both* a valid Location and License Plate ID; however, this issue has been resolved in 10.0.11.

## I received the error "License plate must be specified for this location."

### Issue description

The error occurs if you create a transfer order using a warehouse enabled for an advanced warehouse management (WMS) and then, after completing the work, you try to confirm the shipment.

### Issue resolution

The "from" warehouse has a transit warehouse which had an empty Default receipt location value for the transit warehouse. To resolve this, specify a location for default receipt location in the transit warehouse. Ensure that the default receipt location on the transit warehouse is license plate controlled.

## I received the error "You can't create a work template line for Inventory status change because the work type is not valid. Select a different work type."

### Issue description

On a **Work template**, you cannot select a **Work type** of *Inventory status change* in **Work template details**.

### Issue resolution

This is by design. The *inventory status change* **work type** is only used by system processes and is not configurable. Because the list of work types is just enum values, they cannot be filtered out of the Work Template drop-down view.

## I received the error "The Quantity is not valid for unit 1%."

### Issue description

The quantity is not valid for the unit *ea*, when there is picking work with multiple license plates in one location.

### Issue resolution

Verify the defined **Unit Sequence Group ID** and **Unit Conversions** on the Released Product/Product Variant are configured.

The error message was improved with the release of version 10.0.15 on KB number: 486531: Improving the error message so it shows the expected quantity. "The quantity is not valid. Expected %1 %2.".

## Location directives for sales order Put work, Multiple SKU does not evaluate multiple location directive actions.

### Issue description

Location directives of the **Work order type** *Sales orders* and **Work type** of *Put*, with the **Multiple SKU** parameter selected, does not evaluate multiple location directive actions. It is evaluating only the first location directive action.

### Issue resolution

A new feature **Evaluate all actions for Multi SKU location directives** has been added in version 10.0.15. See Lifecycle Services (LCS) [KB number: 4579866:](https://fix.lcs.dynamics.com/Issue/Details?kb=4579866&bugId=475946&dbType=3&qc=1bc41a56de7a3ee419fa76397a6bf282fce5be9b93e427c08a6d916d1dfa3091) Location directives for Sales order put with Multi SKU does not evaluate multiple location directive actions, for more information. Added feature "Evaluate all actions for Multi SKU location directives" to evaluate all actions for Multi SKU location directives.

## I am unable to do partial picking using mobile device.

### Issue description

For sales and transfer orders, you are unable to skip items and do partial picking.

### Issue resolution

On the Sales order and Transfer order menu items, enable **Allow splitting of work** under the **mobile device menu items** General FastTab.

## How can I perform an Inventory Status change for Partial quantity work.

### Issue description

How do you do an Inventory Status change for Partial quantity of a batch?

### Issue resolution

Requirement can be fulfilled if warehouse app is used and change the status with the help of one of the menus. The *Movement* **Work creation process** menu item can be used for this requirement. Note that **Display inventory status** must be **Yes** for the relevant mobile device menu item.
