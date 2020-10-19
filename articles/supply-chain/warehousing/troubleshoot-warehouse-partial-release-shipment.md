---
# required metadata

title: Troubleshoot partial releases and partial shipments
description: This topic describes how to fix common issues that you might encounter while working with partial releases and partial shipments in Dynamics 365 Supply Chain Management.
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

# Troubleshoot partial releases and partial shipments

[!include [banner](../includes/banner.md)]

This topic describes how to fix common issues that you might encounter while working with partial releases and partial shipments in Dynamics 365 Supply Chain Management.

## Release status on a sales order stays as partially released even after sales order is invoiced.

**Issue:** When a sales order is a delivery order but the same order has one or more items with a different mode of delivery, once the order is invoiced, it still sits with a released status of *Partially released*. On a sample sales order there were two items, one item was for delivery and a second item was for pick up. The delivery was done and so was the pickup, so both lines are invoiced, so with the status of Partially Released which is misleading.

**Fix:** The release status only applies to order lines with items that are enabled for warehouse management, which is why in this scenario it remains at *Partially released*. Microsoft has evaluated this issue and determined it to be a feature limitation. An extension could be added as part of the packing slip and invoicing process to update the release status.
