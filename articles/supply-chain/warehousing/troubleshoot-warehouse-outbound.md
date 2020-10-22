---
# required metadata

title: Troubleshoot outbound warehouse operations
description: This topic describes how to fix common issues that you might encounter while working with outbound warehouse operations in Dynamics 365 Supply Chain Management.
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

This topic describes how to fix common issues that you might encounter while working with outbound warehouse operations in Dynamics 365 Supply Chain Management.

## I received the error "Sales order could not be released."

### Issue description

This error can be for several reasons. One reason is that the order is in credit management hold and a valid postal address must be entered for all sales lines associated with sales order %1 before shipments can be created.

Another reason is that there is an order hold that must be addressed before the order can be released to the warehouse. The hold could be order specific or on the customer account.

### Issue resolution

Add or update the address on the sales order/line(s) and then release to warehouse. Orders cannot be released to the warehouse without a valid delivery address (per the address format set-up in the Organization Administration module).

Investigate the order hold and address the issues then remove the hold from the order/customer and release to the warehouse.

## The message "The shipment for load 1% has been confirmed." is displayed but no lines are posted.

### Issue description

A shipment on a load was confirmed but no further posting happened.

### Issue resolution

Shipment confirmation has no impact on posting; it only updates the shipment and load status. Posting must occur in a separate process.

## I received the error "Direct delivery is not able to process for warehouse 1% as it has warehouse management enabled. Please specify another warehouse that is not enabled for warehouse management."

### Issue description

An item is added to a sales line for direct delivery from a warehouse management enabled warehouse (WMS). The error message is displayed when updating the sales line.

### Issue resolution

Microsoft has evaluated this issue and determined it to be a feature limitation. At the moment Direct delivery is not supported. You'll need to select a non-WMS Item and warehouse.