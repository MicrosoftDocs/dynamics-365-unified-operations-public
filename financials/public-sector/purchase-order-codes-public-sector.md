---
# required metadata

title: Purchase order codes in the public sector
description: This article provides information about the codes and special messages that can be used with confirming purchase orders. A confirming purchase order bypasses the typical purchasing process.
author: twheeloc
manager: AnnBe
ms date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: ConfirmingPOCodes, PurchTableListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 27291
ms.assetid: 65032886-4dc6-4411-98c8-8969287fd7df
ms.search.region: Global
ms.search.industry: Public sector
ms.author: brpotter
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Purchase order codes in the public sector

This article provides information about the codes and special messages that can be used with confirming purchase orders. A confirming purchase order bypasses the typical purchasing process.

This article describes the purchase order codes functionality available for the public sector. You must first determine what your codes and messages will be. You can use the **Confirming PO codes** page to create codes and special messages that can be used with confirming purchase orders (POs). A confirming purchase order bypasses the typical purchasing process. For example, you must authorize an unplanned order by using a PO number at the time of a purchase, instead of by using a document that is provided before the item is required. 

After you set up the codes, you can assign the codes to purchase orders on the **All purchase orders** page. 

If you assign a confirming PO code to a purchase order on the **Unplanned purchases** FastTab (for example, when you create a new purchase order), the message that is associated with the confirming PO code will be printed at the top of the purchase order.

## Tips
-   If you change a confirming PO code that was already assigned to a purchase order, the new code will replace the old code. This change affects both new purchase orders and purchase orders that have been posted. For example, a purchase order had a confirming PO code of **Confirming** when it was posted, but that code is later changed to **Emergency**. In this case, every purchase order that had the **Confirming** code will now have the **Emergency** code instead.
-   You can create messages in different languages. This feature is helpful when you are purchasing from merchants in other countries or regions. For example, your organization is located in an English-speaking country or region, and you want to create a Spanish message for confirming purchase orders that have a confirming PO code **Confirming**.

 

