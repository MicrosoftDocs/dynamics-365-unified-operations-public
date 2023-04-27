--- 
# required metadata 
 
title: Create a mobile device menu item for license plate consolidation
description: This procedure shows you how to create a mobile device menu item for license plate consolidation work. 
author: Mirzaab
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: WHSRFMenuItem   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: mirzaab
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a mobile device menu item for license plate consolidation

[!include [banner](../../includes/banner.md)]

This procedure shows you how to create a mobile device menu item for license plate consolidation work. This enables warehouse workers to consolidate items on one license plate with items on another license place within the same location. For example, they might use this if subsequent staging steps were the same on both work orders, so that the work only needs to be performed once for the merged items. You can use this procedure in demo data company USMF. The task would typically be carried out by a warehouse manager. This procedure is for a feature that was added in Dynamics 365 for Operations, version 1611.

1. Go to Warehouse management > Setup > Mobile device > Mobile device menu items.
2. Click New.
3. In the Menu item name field, type a value.
4. In the Title field, type a value.
5. In the Mode field, select 'Indirect'.
6. In the Activity code field, select 'Consolidate license plates'.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]