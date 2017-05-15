---
# required metadata

title: [Piece picking confirmation]
description: [This topic describes how you set up and apply piece picking confirmation from a mobile device.
author: [BibiSp]
manager: AnnBe
ms.date: 05/26/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
# ms.reviewer: bis
# ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 269384
ms.assetid: fe7244d9-8858-43b0-b14f-0b769bc4f2ca
ms.search.region: Global
# ms.search.industry: 
ms.author: mirzaab
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Piece picking information

[!include[banner](../includes/banner.md)]

Piece picking allows you to confirm each piece of inventory through picking or counting work on the mobile device. For picks, it lets you confirm the quantity of work to be processed up to the quantity that is specified on work to be picked. For counting work, it allows you to scan the inventory that you are counting and track the total amount

When you enable piece picking, product confirmation is automatically selected. For work-type picks, a maximum number of pieces is enabled. This allows you to set a maximum to the number of pieces that must be confirmed during the work process. The maximum quantity is based on the current work unit that is being processed. The counting work type does not allow a maximum.

You can also use the quantity and unit of measure (UOM) that is associated with a scanned barcode. This will work for receiving on inbound flows including mixed license plate receiving, purchase order item, transfer order item, and load item. It also works for piece picking where scanning the barcode will add the quantity to the total number of confirmed pieces converting between the UOM on the barcode and the work unit. If, when counting the UOM on the barcode, it is confirmed that the quantity is allowed for counting on the sequence group, the quantity will be added to the total count.

## Where it applies

Piece picking works for all counting work and for the initial pick for any type of work. Piece picking does not apply if the item is controlled by serial numbers or if it is a production or Kanban pick from an LP location and the item is set to staging.

## Set up piece picking

-	From a mobile device menu item, open the setup form for work confirmation. 

The following options become available for selection when the work type is pick or counting.

| Option        | Description   | 
| ------------- |:-------------:|
| Piece picking confirmation   | Available for pick and counting work types. Product cofirmation is automatically slected. Allows you to confirm each piece of inventory from the mobile device. | 
| Maximum number of pieces     | Available for pick work, if piece picking confirmation is enabled. Sets a limit to the number of pieces that you must confirm. |  




