--- 
# required metadata 
 
title: Set up fixed asset groups
description: This procedure shows how to create a new fixed asset group. 
author: saraschi2
manager: AnnBe 
ms.date: 02/23/2017
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: saraschi
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up fixed asset groups

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows how to create a new fixed asset group. It uses the Accountant role and demo data for the USMF legal entity.

1. Go to Fixed assets > Setup > Fixed asset groups.
2. Click New.
3. In the Fixed asset group field, type a value.
4. In the Name field, type a value.
    * Autonumber fixed assets and Number sequence code on the Fixed asset group will override the settings on the Fixed assets parameters. You can change it here if the assets in this fixed asset group will have different numbering from other groups.  
5. Click Books.
6. In the Book field, enter or select a value.
    * The Calculate depreciation field is set to Yes, so the asset book will be included in depreciation proposals. If Calculate depreciation is set to No, the asset will not be automatically depreciated.  
7. Set the Service life of the asset, in years.
    * Note that the Depreciation periods field value is calculated after setting the Service life.  
8. In the Depreciation convention field, select an option.
9. Close the page.

