---
# required metadata

title: Consolidated batch orders | Microsoft Docs
description: This article describes the concept of consolidated batch orders.
author: YuyuScheller
manager: AnnBe
ms.date: 2015-12-07 09:17:20
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

keywords: PmfAddToConsOrder, PmfBulkItemConv, PmfBulkPackOnHand, PmfConsOrderListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: YuyuScheller
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 19291
ms.assetid: 8cd9ca77-6b50-4540-b8ee-353c4bae426e
ms.region: Global
ms.industry: Manufacturing
ms.author: yuyus

---

# Consolidated batch orders

This article describes the concept of consolidated batch orders.

A bulk item that is produced is considered a parent item, whereas a packed item is considered a child item. The relation between the bulk item and the packed item is expressed in a bulk item conversion. This bulk item conversion is defined on the bulk item itself. Packed items can be packaged into containers of either a single size or multiple sizes that are considered one unit. By consolidating the orders for a bulk item, you can see all the related batch orders in a single view that can help you determine any remaining work that must be completed. A consolidated batch order can contain any combination of the following orders:

-   A single bulk order and multiple packed orders
-   Multiple bulk orders and multiple packed orders
-   Multiple bulk orders and a single packed order
-   Only packed orders


