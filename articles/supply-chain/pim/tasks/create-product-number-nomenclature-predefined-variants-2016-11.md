--- 
# required metadata 
 
title: Create a product number for predefined product variants
description: This guide shows you how to set up a product number nomenclature for predefined product variants, and how you assign it to the appropriate product dimension group. 
author: BibiSp
manager: AnnBe 
ms.date: 11/03/2017
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: bis
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: bis
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a product number for predefined product variants

[!include[task guide banner](../../includes/task-guide-banner.md)]

This guide shows you how to set up a product number nomenclature for predefined product variants, and how you assign it to the appropriate product dimension group. The demo data company used to create this procedure is USMF. The new product number nomenclature is assigned to the Color and Size product dimension group. This task would typically be done by a product designer.


## Create a product number nomenclature
1. Click Product variant model definition.
2. Click Product nomenclature.
3. Click New.
4. In the Name field, enter a nomenclature name that helps to identify the target product dimension group, for example, ColorSize.
5. In the Description field, type a value.
6. Click Add.
7. Click Product master number.
8. Click Add.
9. Click Text constant.
10. In the Text field, type a value.
11. Click Add.
12. Click Color.
13. Click Add.
14. Click Text constant.
15. In the Text field, type a value.
16. Click Add.
17. Click Size.
18. Close the page.

## Assign the nomenclature to a product master
1. Click Product dimension groups.
2. Select the SizeCol product dimension group.
3. Click Edit.
4. Select Yes in the Use nomenclature field.
5. In the Product variant number nomenclature field, enter or select a value.
6. Close the page.

