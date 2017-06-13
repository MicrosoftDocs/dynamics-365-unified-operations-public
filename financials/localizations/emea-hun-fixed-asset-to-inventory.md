---
# required metadata

title: Move a fixed asset to inventory
description: This article describes country-specific functionality for Hungary that lets you transfer fixed assets to inventory at the net book value. The status of the fixed asset is set to Scrapped, and the net book value is set to 0 (zero). Additionally, the quantity of a product in inventory is set to 1, and the cost price is set to the net book value of the fixed asset.
author: Anasyash
manager: AnnBe
ms.date: 04/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 274423
ms.search.region: Hungary
# ms.search.industry: 
ms.author: anasyash
ms.dyn365.ops.version: Version 1611
ms.search.validFrom: 2016-11-30

---

# Move a fixed asset to inventory

This article describes country-specific functionality for Hungary that lets you transfer fixed assets to inventory at the net book value. The status of the fixed asset is set to Scrapped, and the net book value is set to 0 (zero). Additionally, the quantity of a product in inventory is set to 1, and the cost price is set to the net book value of the fixed asset.

You can transfer fixed assets to inventory at the net book value. As result of this transfer, the status of the fixed asset is set to **Scrapped**, and the net book value is set to **0** (zero). Additionally, the quantity of a product in inventory is set to **1**, and the cost price is set to the net book value of the fixed asset. Use the standard Inventory to fixed assets journal to transfer fixed assets to inventory. 

To transfer a fixed asset to inventory, follow these steps.

1.  Validate that the depreciation for the fixed asset is posted up to the transfer date.
2.  Create a new Inventory to fixed assets journal.
3.  On the journal lines, select the asset to transfer and the product to receive.
4.  Enter a negative quantity.
5.  Validate that the **Cost price** field has the **Net book** value.
6.  Post the journal.
7.  Validate that the fixed asset and inventory transactions were created correctly.


