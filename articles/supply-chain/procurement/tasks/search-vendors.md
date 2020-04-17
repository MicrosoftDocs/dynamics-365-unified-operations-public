--- 
# required metadata 
 
title: Search for vendors
description: Learn how to search for vendors based on specific criteria. 
author: mkirknel
manager: tfehr 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: VendSearchCriterion, VendSearchAddCategory   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Search for vendors

[!include [banner](../../includes/banner.md)]

Learn how to search for vendors based on specific criteria. This example shows you how to search for vendors that are approved for a particular procurement category and have their primary address in a specific country. You can run this procedure in demo data company USMF, or on your own data. This task would usually be carried out by a procurement professional.

1. Go to Procurement and sourcing > Vendors > Vendor search.
2. Click on the Plus icon to open the Procurement category selection page.  
3. In the tree, select 'CORP PROCUREMENT CATEGORIES\OFFICE MACHINES'.
    * If you're running this procedure as a task guide, you may have to click the Unlock button before you can select the correct node. If you're not using USMF, select one of the categories that you have.  
4. Click Add.
    * It's possible to select more than one category here. If you do so, the search will find all the vendors that are approved for at least one of the categories.  
5. Click OK.
6. In the Country/region field, type a value.
7. Click OK.

