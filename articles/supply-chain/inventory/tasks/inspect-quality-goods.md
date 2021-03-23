--- 
# required metadata 
 
title: Inspect the quality of goods
description: This topic provides a set of procedures that show how to process a quality order.
author: perlynne
manager: tfehr 
ms.date: 03/23/2021
ms.topic: business-process 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: InventQualityOrderTable, InventQualityOrderLineResults, HcmWorkerLookUp   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
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

This topic provides a set of procedures that show how to process a quality order. Quality inspections are typically carried out by a quality clerk.

You can run these procedures using the standard demo data if you have it installed. To use it, select the *USMF* legal entity before you begin. Then, you must also confirm purchase order "000016" and post a product receipt. This will automatically create a quality order.

## Step 1: Select a quality order

Do the following to select a quality order:

1. Go to **Inventory management > Periodic tasks > Quality management > Quality orders**.
1. Select the quality order that was created before you started this procedure.  

## Step 2: Record test results

Do the following to record test results:

1. Select **Results**.
1. Select **Edit**.
1. In the **Result quantity** field, enter a number.
1. In the **Outcome** field, select the desired record in the drop-down menu. In this example, the result is based on a pre-defined outcome. Normally you would record a more specific test result, for example a size or other dimension.  
1. Select **Save**.
1. Close the page.

## Step 3: Validate the quality order

Do the following to validate the quality order:

1. Select **Validate**.
1. In the **Validated by** field, select the user performing the inspection from the drop-down menu.  
1. Select **Select**.
1. Select **OK**.
1. Close the page.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]