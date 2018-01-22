---
# required metadata

title: Inspect the quality of goods
description: This procedure shows you how to process a quality order.
author: perlynne
manager: AnnBe
ms.date: 11/14/2016
ms.topic: business-process
ms.prod:  
ms.service: dynamics-ax-applications
ms.technology:  

# optional metadata

# ms.search.form:   
audience: Application User
# ms.devlang:  
ms.reviewer: yuyus
ms.search.scope: Operations
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: perlynne
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.0.0
---
# Inspect the quality of goods

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows you how to process a quality order. You can run this guide in demo data company USMF. Before you start this example procedure, you need to confirm purchase order “000016” and post a product receipt. This will automatically create a quality order. Quality inspections are typically carried out by a quality clerk.


## Select a quality order
1. Go to Inventory management > Periodic tasks > Quality management > Quality orders.
2. In the list, mark the selected row.
    * Select the quality order that was created before you started this procedure.  

## Record test results
1. Click Results.
2. Click Edit.
3. In the Result quantity field, enter a number.
4. In the list, mark the selected row.
5. In the Outcome field, click the drop-down button to open the lookup.
6. In the list, find and select the desired record.
    * In this example the result is based on a pre-defined outcome. Normally you would record a more specific test result, for example a size or other dimension.  
7. In the list, click the link in the selected row.
8. Click Save.
9. Close the page.

## Validate the quality order
1. Click Validate.
2. In the Validated by field, click the drop-down button to open the lookup.
    * Select the user performing the inspection.  
3. In the list, click the link in the selected row.
4. Click Select.
5. Click OK.
6. Close the page.
