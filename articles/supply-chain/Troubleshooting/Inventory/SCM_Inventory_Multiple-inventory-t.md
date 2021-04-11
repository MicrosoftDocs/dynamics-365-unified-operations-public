---
# required metadata

title: Multiple inventory transactions after adjusting purchase order line when batch number group on item has “On physical update” set to No.
description: Multiple inventory transactions after adjusting purchase order line when batch number group on item has “On physical update” set to No.
author: SmithaNataraj
manager: tfehr
ms.date: 4/11/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: InventNumGroup
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
submittedBy: smnatara@microsoft.com

---

# Multiple inventory transactions after adjusting purchase order line when batch number group on item has “On physical update” set to No.

KB Number: 4613390

When creating an item with batch number group set "On Physical Update" equals to "No", a new batch number will be automatically created upon modifying the purchase line quantity and save purchase order form.


## Resolution
This works as expected. Microsoft has investigated the reported issue. The flag "On physical update" for a batch number group works as following: (1) When the flag is enabled, creation of new batch number only takes place on physical updates (e.g., ship/receive of items); (2) When the flag is updated, new batch number is created on every update when applicable (e.g., adding new quantity on purchase orders).
We acknowledge that this can be counter productive in a scenario such as this adding an overhead on processing resulting vendor invoices. For that reason we encourage you to create an entry on the Ideas Portal to allow Microsoft to understand the extend to which this requested, which in turn will allow Microsoft to decide whether to include this in future feature planning.



