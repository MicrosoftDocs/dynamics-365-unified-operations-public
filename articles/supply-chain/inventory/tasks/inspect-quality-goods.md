--- 
# required metadata 
 
title: Inspect the quality of goods
description: This topic explains how to process a quality order. 
author: perlynne
manager: AnnBe 
ms.date: 08/01/2019
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: InventQualityOrderTable, InventQualityOrderLineResults, HcmWorkerLookUp   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: perlynne
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Inspect the quality of goods

[!include [banner](../../includes/banner.md)]

This topic explains how to process a quality order. You can run this guide in demo data company USMF. Before you start this example procedure, you need to confirm purchase order "000016" and post a product receipt. This will automatically create a quality order. Quality inspections are typically carried out by a quality clerk.


## Select a quality order
1. In the navigation pane, go to **Modules > Inventory management > Periodic tasks > Quality management > Quality orders**.
2. Select the quality order that was created before you started this procedure.  

## Record test results
1. Select **Results**.
2. Select **Edit**.
3. In the **Result quantity** field, enter a number.
4. In the **Outcome** field, select the desired record in the drop-down menu.  
- In this example the result is based on a pre-defined outcome. Normally you would record a more specific test result, for example a size or other dimension.  
5. Select **Save**.
6. Close the page.

## Validate the quality order
1. Select **Validate**.
2. In the **Validated by** field, select the user performing the inspection from the drop-down menu.  
3. Click **Select**.
4. Select **OK**.
5. Close the page.

