---
# required metadata

title: Troubleshoot partial releases and partial shipments
description: This topic describes how to fix common issues that you might encounter while you work with partial releases and partial shipments in Microsoft Dynamics 365 Supply Chain Management.
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

This topic describes how to fix common issues that you might encounter while you work with partial releases and partial shipments in Microsoft Dynamics 365 Supply Chain Management.

## The release status of a sales order remains Partially released even after the sales order is invoiced.

### Issue description

A sales order is a delivery order, but one or more items on it have a different mode of delivery. After the order is invoiced, it still has a release status of *Partially released*.

For example, a sales order has two items: one for delivery and one for pickup. Both the delivery and the pickup have been done. Therefore, both lines have been invoiced. However, the release status is still shown as *Partially released*, which is misleading.

### Issue resolution

The release status applies only to order lines where the items are enabled for warehouse management. Therefore, the release status remains *Partially released* in this scenario. Microsoft has evaluated this issue and has determined that it's a feature limitation. An extension could be added as part of the packing slip and invoicing process to update the release status.
