--- 
# required metadata 
 
title: Set up short picking item reallocation
description: This procedure shows you how to enable warehouse workers to quickly find alternative locations if there isn't sufficient inventory at the location they've been directed to. 
author: ShylaThompson
manager: AnnBe 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: WHSWorkException, WHSWorker   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: mirzaab
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Set up short picking item reallocation

[!include [banner](../../includes/banner.md)]

This procedure shows you how to enable warehouse workers to quickly find alternative locations if there isn't sufficient inventory at the location they've been directed to. It's possible to use an automatic re-allocation process, which uses location directives to retrieve the goods if they're available at another location. Alternatively, when manual re-allocation is used, a list of the locations with the available quantity is shown on the mobile device, allowing the warehouse worker to choose which location to use inventory from. You can use this procedure in demo data company USMF. This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.


## Set up work exceptions
1. In the **Navigation pane**, go to **Warehouse management > Setup > Work > Work exceptions**.
2. Click **New**. It's possible to define several work exceptions with different item reallocation policies to enable the warehouse worker to choose one based on the needs of the shipment that they are processing.  
3. In the **Work exception code** field, type a value. Give the work exception a title to indicate what it's used for. For example, Short picking manual.  
4. In the **Description** field, type a value.
5. In the **Exception** type field, select 'Short pick'.
6. Select the **Adjust inventory** check box. This option means that inventory will automatically be adjusted to 0 at the short picked location.  
7. In the **Default adjustment type code** field, enter or select a value. For example, in USMF you can select 'Remove Res Adj Out'.  
8. In the **Item reallocation** field, select 'Manual'. If you select Manual, or Automatic and Manual, the warehouse worker needs to be enabled to use manual reallocation.  

## Set up a worker to use manual item reallocation
1. Close the page.
2. In the **Navigation pane**, go to **Warehouse management > Setup > Worker**.
3. Click **Edit**.
4. In the list, select worker 24.
5. Expand the **Work** fastTab.
6. Select 'Yes' in the **Allow manual item reallocation** field.

