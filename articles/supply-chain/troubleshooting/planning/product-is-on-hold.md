---
# required metadata

title: Product is on hold for transactions.
description: Product is on hold for transactions.
author: ankubik@microsoft.com
manager: tfehr
ms.date: 5/18/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ReqTransPo
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: ankubik@microsoft.com
ms.assetid: 
ms.search.region: Global
ms.author: ankubik@microsoft.com

---

# Product is on hold for transactions.

Error code: SYS13295

The system displays the followign error message:
	SYS13295



## Symptoms
After firming planning orders the system shows the following error message: > Item %1 is on hold for transactions in %2.

## Cause
The item is set as stopped in default order settings.
When an item is blocked and you enter a purchase or sales line, a warning message appears. When the item is blocked, inventory transactions that are related to the purchase or sales order line cannot be modified, for example, when you post a packing slip or an invoice. You can block a purchased item, and at the same time, sell the item. In this case, this field is selected on a purchase order, but it is not blocked in inventory or on a sales order. An item number can be blocked from being sold, for example, if: The item is still under development or manufacture, and you do not want the item to be sold or reserved. You have received many defective items. The defects must be corrected before the item can be sold. Therefore, you can block the item until the issue is resolved. When an item is blocked and you create a return order line, a message is displayed. You cannot block a series or a lot of the item. If parts of the item are to be blocked, you can block them by moving inventory or by blocking the full stock of the item for that period.

## Resolution
Go to default order settings for the item and disable "Stopped" option.



