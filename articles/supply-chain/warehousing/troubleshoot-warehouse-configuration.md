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

Check that the license plate ID is not reserved by something else. This used to occur when a user scanned a value on the warehouse app that was *both* a valid location and a valid license plate ID; however, this issue was resolved as of version 10.0.11.

## I received the error "License plate must be specified for this location."

### Issue description

The error occurs if you create a transfer order using a warehouse enabled for an advanced warehouse management (WMS) and then, after completing the work, you try to confirm the shipment.

### Issue resolution

The "from" warehouse has a transit warehouse that had an empty **Default receipt location** value for the transit warehouse. To resolve this issue, specify a location for the **Default receipt location** in the transit warehouse. Ensure that the default receipt location on the transit warehouse is license plate controlled.

## I received the error "You can't create a work template line for Inventory status change because the work type is not valid. Select a different work type."

### Issue description

On a work template, you can't select a **Work type** of *Inventory status change* in **Work template details**.

### Issue resolution

This is by design. The *Inventory status change* **Work type** is only used by system processes and is not configurable. Because the list of work types is fixed as an enum, the extra entries can't be filtered out of the **Work template** drop-down menu.

## I received the error "The Quantity is not valid for unit 1%."

### Issue description

The quantity is not valid for the unit *ea*, when there is picking work with multiple license plates in one location.

### Issue resolution

Verify the defined **Unit sequence group ID** and **Unit conversions** on the released product or product variant are configured correctly.

The error message was improved with the release of version 10.0.15 ([KB number: 4581627](https://fix.lcs.dynamics.com/Issue/Details/?bugId=486531)). The new error message is "The quantity is not valid. Expected %1 %2."

## In location directives for sales order put work, the multiple SKU option doesn't evaluate multiple location directive actions.

### Issue description

Location directives of the **Work order type** *Sales orders* and **Work type** of *Put*, with the **Multiple SKU** parameter selected, don't evaluate multiple location directive actions. The system only evaluates the first location directive action.

### Issue resolution

A new feature *Evaluate all actions for Multi SKU location directives* has been added in version 10.0.15 ([KB number: 4579866](https://fix.lcs.dynamics.com/Issue/Details?kb=4579866&bugId=475946&dbType=3&qc=1bc41a56de7a3ee419fa76397a6bf282fce5be9b93e427c08a6d916d1dfa3091). The new feature evaluates all actions for multi-SKU location directives. If you require this feature, use [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) to enable it.

## I am unable to do partial picking using the warehouse app.

### Issue description

For sales and transfer orders, you are unable to skip items and do partial picking.

### Issue resolution

Go to the **Mobile device menu items** page. For each menu item set up to process sales order or transfer orders, open the **General** FastTab and set **Allow splitting of work** to *Yes*.

## How can I perform an inventory status change for partial quantity work.

### Issue description

It isn't clear how to do an inventory status change for partial quantity of a batch.

### Issue resolution

You can create a menu item for the warehouse app that will enable workers to do this. To do so, go to the **Mobile device menu items** page and create (or edit) a menu item that has the following properties:

- **Mode** - *Work*
- **Use existing work** - *No*
- **Work creation process** - *Movement*
- **Display inventory status** - *Yes*

You can make other settings as needed.
