---
# required metadata

title: Troubleshoot warehouse configuration
description: This topic describes how to fix common issues that you might encounter while you configure Microsoft Dynamics 365 Supply Chain Management.
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

# Troubleshoot warehouse configuration

[!include [banner](../includes/banner.md)]

This topic describes how to fix common issues that you might encounter while you configure Microsoft Dynamics 365 Supply Chain Management.

## I receive the following error message: "The license plate or location is not valid."

### Issue description

You receive this error message when you scan a license plate ID or location.

### Issue resolution

Make sure that the license plate ID isn't reserved by something else. This issue used to occur when the value that a user scanned in the warehouse app was both a valid location and a valid license plate ID. However, this issue was resolved in version 10.0.11.

## I receive the following error message: "License plate must be specified for this location."

### Issue description

You receive this error message if you create a transfer order by using a warehouse that is enabled for advanced warehouse management (WMS), and then, after the work is completed, you try to confirm the shipment.

### Issue resolution

The **Default receipt location** field is blank for a transit warehouse of the "from" warehouse. To fix this issue, specify a default receipt location in the transit warehouse. Make sure that this location is license plate–controlled.

## I receive the following error message: "You can't create a work template line for Inventory status change because the work type is not valid. Select a different work type."

### Issue description

For a work template, you can't select *Inventory status change* in the **Work type** field in **Work template details**.

### Issue resolution

This behavior is by design. The *Inventory status change* work type is used only by system processes. It can't be configured. Because the list of work types is fixed as an enumeration, the extra entries can't be filtered out of the **Work template** drop-down menu.

## I receive the following error message: "The Quantity is not valid for unit 1%."

### Issue description

The quantity isn't valid for the *ea* unit when there is picking work that has multiple license plates in one location.

### Issue resolution

Verify that the **Unit sequence group ID** and **Unit conversions** fields on the released product or product variant are set correctly.

Note that the error message has been improved in version 10.0.15 (see [KB 4581627](https://fix.lcs.dynamics.com/Issue/Details/?bugId=486531)). The new error message is, "The quantity is not valid. Expected %1 %2."

## In location directives for sales order put work, the multiple SKU option doesn't evaluate multiple location directive actions.

### Issue description

Location directives of the *Sales orders* work order type and the *Put* work type don't evaluate multiple location directive actions when the **Multiple SKU** option is selected. Only the first location directive action is evaluated.

### Issue resolution

A new feature, *Evaluate all actions for Multi SKU location directives*, has been added in version 10.0.15 (see [KB 4579866](https://fix.lcs.dynamics.com/Issue/Details?kb=4579866&bugId=475946&dbType=3&qc=1bc41a56de7a3ee419fa76397a6bf282fce5be9b93e427c08a6d916d1dfa3091)). This feature evaluates all actions for multi-SKU location directives. If you require this feature, use [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) to turn it on.

## I can't use the warehouse app to do partial picking.

### Issue description

For sales and transfer orders, you can't skip items and do partial picking.

### Issue resolution

On the **Mobile device menu items** page, for each menu item that is set up to process sales orders or transfer orders, set the **Allow splitting of work** option on the **General** FastTab to *Yes*.

## How can I do an inventory status change for partial quantity work?

### Issue description

You want to do an inventory status change for a partial quantity of a batch.

### Issue resolution

To enable workers to make this change, you can create a menu item for the warehouse app. On the **Mobile device menu items** page, create (or edit) a menu item that has the following settings:

- **Mode:** *Work*
- **Use existing work:** *No*
- **Work creation process:** *Movement*
- **Display inventory status:** *Yes*

You can set other fields on the page as you require.
