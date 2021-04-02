---
# required metadata

title: Mixed license plate receiving
description: This topic describes how to use mixed license plate receiving to register and create work for multiple items with a mobile device.
author: Mirzaab
ms.date: 05/26/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  WHSRFAutoConfirm, WHSLicensePlate
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 269384
ms.search.region: Global
# ms.search.industry: 
ms.author: mirzaab
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Mixed license plate receiving

[!include [banner](../includes/banner.md)]

Mixed license plate receiving allows you to build a license plate consisting of multiple items before you register and create put-away work. 

A license plate that consists of multiple items does not have to be split at the receiving dock for you to register each item. 

When using an item-related flow to identify the source document lines, you can scan bar codes on the item control. If the bar code has a quantity and a unit of measure (UOM) configured on it, the item and quantity will automatically be added to the mixed license plate, and you will be returned to the screen to scan another item. This allows you to quickly scan all the items without having to make a confirmation at each step. 

In the flow for mixed license plate receiving, you can display the list of items that are already scanned to the license plate and from here you can modify or correct the quantity of an item.

## Where it applies

Mixed license plate receiving is a mobile device receiving flow to register and create work for multiple lines/items at the same time. This is useful if you receive inbound license plates with multiple items. 

## How to set up mixed license plate receiving
Mixed license plate receiving is set up as a mobile device menu item.

You need to create a new menu item with mode work that does not use existing work and use one of the following methods:

- Mixed license plate receiving
- Mixed license plate receiving and put away

The options to identify the source document lines are purchase order item, purchase order line, return order, transfer order item, and transfer order line. These options can change the receiving order on a single license plate. The last option is by load item. You can add multiple items to a license plate, but you cannot switch between multiple loads.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]