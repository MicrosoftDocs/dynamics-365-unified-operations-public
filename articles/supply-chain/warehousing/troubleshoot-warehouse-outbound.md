---
# required metadata

title: Troubleshoot outbound warehouse operations
description: This topic describes how to fix common issues that you might encounter while you work with outbound warehouse operations in Microsoft Dynamics 365 Supply Chain Management.
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

# Troubleshoot outbound warehouse operations

[!include [banner](../includes/banner.md)]

This topic describes how to fix common issues that you might encounter while you work with outbound warehouse operations in Microsoft Dynamics 365 Supply Chain Management.

## I receive the following error message: "Sales order could not be released."

### Issue description

This issue can occur for several reasons. For example, the order is on credit management hold, and no shipments can be created until a valid postal address is entered for all sales lines that are associated with a sales order. Alternatively, there is an order hold that must be addressed before the order can be released to the warehouse. This hold might be order-specific, or it might be on the customer account.

### Issue resolution

Add or update the address on the sales order and order lines, and then release the order to the warehouse. Orders can be released to the warehouse only if they have a valid delivery address (per the address format setup in the **Organization administration** module).

Investigate the order hold, and address the issues. Then remove the hold from the order or customer, and release the order to the warehouse.

## I receive the following message: "The shipment for load 1% has been confirmed." However, no lines are posted.

### Issue description

A shipment on a load was confirmed, but no further posting occurred.

### Issue resolution

Shipment confirmation doesn't affect posting. It just updates the shipment and load status. Posting must occur in a separate process.

## I receive the following error message: "Direct delivery is not able to process for warehouse 1% as it has warehouse management enabled. Please specify another warehouse that is not enabled for warehouse management."

### Issue description

An item is added to a sales line for direct delivery from a warehouse that is enabled for warehouse management (WMS). You receive this error message when the sales line is updated. 

### Issue resolution

Microsoft has evaluated this issue and has determined that it's a feature limitation. Currently, WMS doesn't support direct delivery. Therefore, to use direct delivery, you must select a non-WMS item and warehouse.
