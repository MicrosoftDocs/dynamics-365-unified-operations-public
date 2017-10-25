---
# required metadata

title: Ship an order from a different store
description: This topic describes the Charge send feature.
author: ashishmsft
manager: AnnBe
ms.date: 10/10/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Operations, Core, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: asharchw
ms.search.validFrom: 2017-10-10
ms.dyn365.ops.version: Retail Version

---

# Ship an order from a different store

With the Charge send feature in Dynamics 365 for Retail, customer orders can be placed in one store and shipped from another store. 
Customer orders in the point of sale (POS) client support multiple fulfillment options. Some examples of fulfillment options include:
-	Pick up from the same store on a different date.
-	Pick up from a different store on the same date or a different date.
-	Ship from the default shipping warehouse that is assigned to the store, and deliver on a specific date.

The Charge send feature uses the following POS operations: Ship all products and Ship selected products. This allows the store clerk to select the “ship from” location that the order or order line can be fulfilled from. By default, the “ship from” location is the shipping warehouse that is associated with the store. However, the store clerk can change this location and select any store that is defined in the store locator group that is assigned to the store. 

The ability to select “ship to” addresses remains unchanged. 

The shipping methods that can be used to fulfill the order line are based on the configuration of valid modes of delivery for products and addresses. Because the rules about valid of modes of delivery are maintained only in the Retail headquarters (HQ), the POS client makes a real-time call to fetch the valid modes of delivery for a ship line. 

