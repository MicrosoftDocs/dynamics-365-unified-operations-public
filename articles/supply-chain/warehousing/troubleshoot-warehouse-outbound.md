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

## Sales order could not be released.

**Issue:** Order is in credit management and a valid postal address must be entered for all sales lines associated with sales order XXXX before shipments can be created. Orders cannot be released to the warehouse without a valid delivery address (per the address format set-up in the Organization Administration module).

**Fix:** Add or update the address on the sales order/line(s) and then release to warehouse.

## The shipment for load has been confirmed. No lines for posting or quantity=0.

**Issue:** Shipment was confirmed but no posting happened.

**Fix:** Shipment confirmation has no impact on posting; it only updates the shipment and load status. Posting must occur in a separate process.

## Direct delivery activation on sales order line.

**Issue:** Sales order: XXXX Item number: XXXX Direct delivery is not able to process for warehouse XXXX as it has warehouse management enabled. Please specify another warehouse that is not enabled for warehouse management.
 <!-- KFM: Is that an error message? Is there a fix for this? -->