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

## The error "The license plate or location is not valid" is shown.
<!-- KFM: I think this is an error message, so I put it in quotes. Does this look right? -->

**Issue:** Scanning a license plate ID or location generates an error message.

**Fix:** Check that the License Plate ID is not reserved by something else. This used to occur when a user scanned a value on the Warehouse Mobile App that was *both* a valid Location and License Plate ID; however, this issue has been resolved in 10.0.11.

## The error "License plate must be specified for this location" is shown.
<!-- KFM: I think this is an error message, so I put it in quotes. Does this look right? -->

**Issue:** Transfer order required license plate to be specified.

**Fix:** Transfer orders must maintain a License Plate ID throughout the process (From &gt; Transit &gt; To). Ensure default receipt location on the transit warehouse is license plate controlled.

## The error "You can't create a work template line for inventory status change because the work type isn't valid. Select a different work type" is shown.
<!-- KFM: I think this is an error message, so I put it in quotes. Does this look right? -->
**Issue:** Cannot select work type of inventory status change in Work template details.

**Fix:** This is by design. The inventory status change work order type is only used by system processes and is not configurable. Because the list of work order types is just enum values, they cannot be filtered out of the Work Template drop-down view.

## The Quantity is not valid for unit ea.

**Issue:** The quantity is not valid for unit ea, when Picking Work with Multiple LP´s in one Location.

**Fix:** Verify defined Unit Sequence Group and Unit Conversions on the Released Product/Product Variant. KB number: 486531: Improving the error message so it shows the expected quantity. "The quantity is not valid. Expected %1 %2.".
<!-- KFM: This looks like internal text. Do we really want to show this to customers? -->
## Location directives for sales order put multi SKU does not evaluate multiple location directive actions.

**Issue:** Location directives for sales order put with Multi SKU does not evaluate multiple location directive actions. It is evaluating only the first location directive action.

**Fix:** KB number: 4579866: Added feature "Evaluate all actions for Multi SKU location directives" to evaluate all actions for Multi SKU location directives.

## Unable to do partial picking using mobile device.

**Issue:** For sales and transfer orders, unable to skip items and do partial picking.

**Fix:** Enable "Allow splitting of work" under mobile device menu items General FastTab.

## Inventory Status change for Partial quantity.

**Issue:** How do you do an Inventory Status change for Partial quantity of a batch?

**Fix:** Requirement can be fulfilled if warehouse app is used and change the status with the help of one of the menus. The movement menu item can be used for this requirement. Note that **Display inventory status** must be enabled for the relevant  mobile device menu item.
