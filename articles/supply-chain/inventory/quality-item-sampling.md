--- 
# required metadata 
 
title: Set up quality orders
description: Use item sampling as part of a quality association to define the amount of current physical inventory that must be inspected. Sampling can be based on fixed quantities, a percentage, or full license plate. 
author: rachel-profitt
manager: tfehr 
ms.date: 03/23/2021
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: InventItemSampling
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: raprofit
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---

# Quality management item sampling

Use item sampling as part of a quality association to define the amount of current physical inventory that must be inspected. Sampling can be based on fixed quantities, a percentage, or full license plate.

## Set up item sampling

Do the following to set up item sampling:

1. Go to **Inventory management > Setup > Quality control > Item sampling**.
2. Select **New**.
3. In the **Item sampling** field, type a value.
4. In the **Description** field, type a value.
5. In the **Value** field, enter a number. This value relates to the **Quantity specification** that's selected in the adjacent field.  
6. Expand or collapse the **Process** section.
7. Select or clear the **Full blocking** check box. If you select this option, the whole lot or order line quantity is blocked if a test is failed. If you don't select it, only the items in the quality order are blocked.  
8. Select **Save**.
9. Close the page.

> [!NOTE]
> The *Quality management for warehouse processes* feature provides additional item sampling capabilities. It adds a concept of *item sampling scope* and the ability to define a full license plate as the quantity specification. If you have enabled this feature, then see [Quality management for warehouse processes](quality-management-for-warehouses-processes.md).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]