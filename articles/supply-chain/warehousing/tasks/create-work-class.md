--- 
# required metadata 
 
title: Create a work class
description: This procedure shows you how to set up a work class. 
author: Mirzaab
ms.date: 11/14/2016
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: WHSWorkClass
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
# Create a work class

[!include [banner](../../includes/banner.md)]

This procedure shows you how to set up a work class. Work classes are used to direct and/or limit the type of work order lines that a warehouse worker can process on a mobile device. The lines that a worker can process are determined from the work classes on the mobile device menu items that the warehouse worker has access to and the work class that's specified on the work lines. Work classes can also be used to validate the put location for a work order line. You can run this procedure in demo data company USMF or on your own data. This procedure is intended for the warehouse manager.

1. Go to Warehouse management > Setup > Work > Work classes.
2. Click New.
3. In the Work class ID field, type a value.
4. In the Description field, type a value.
5. In the Work order type field, select an option.
6. Click New.
7. In the Location type field, type a value.
    * If you select a location type, this sets a restriction on where items can be put after they've been picked. This setting is used when a location directive tries to resolve the location, or if a warehouse worker manually provides the location for the mobile device menu item.  
8. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]