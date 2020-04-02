--- 
# required metadata 
 
title: Create a product number nomenclature for configured product variants
description: This procedure shows you how to set up a product number nomenclature for configured product variants, and how it can be attached to a configurable product master. 
author: ShylaThompson
manager: tfehr 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: DefaultDashboard, EcoResProductVariantMaintainWorkspace, EcoResNomenclature, EcoResProductListPage, EcoResProductDetails, PCProductConfigurationModelListPage, PCProductConfigurationModelDetails   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create a product number nomenclature for configured product variants

[!include [banner](../../includes/banner.md)]

This procedure shows you how to set up a product number nomenclature for configured product variants, and how it can be attached to a configurable product master. This procedure also demonstrates how you can build a configuration nomenclature for a product configuration model component. The demo data company used to create this procedure is USMF. The new product number nomenclature is assigned to the D0004 product master. This task would typically be done by a product designer.


## Create a product number nomenclature
1. Click Product variant model definition.
2. Click Product nomenclature.
3. Click New.
4. In the Name field, type a value.
5. In the Description field, type a value.
6. Click Add.
7. Click Product master number.
8. Click Add.
9. Click Text constant.
10. In the list, mark the selected row.
11. In the Text field, type a value.
12. Click Add.
13. Click Configuration.
14. Close the page.

## Assign the product number nomenclature to a product master
1. Click Product masters.
2. Use the Quick Filter to find records. For example, filter on the Product number field with a value of 'D'.
3. In the list, click the link in the selected row.
4. Click Edit.
5. Select Yes in the Use nomenclature field.
6. In the Product variant number nomenclature field, enter or select a value.
7. Close the page.
8. Close the page.

## Create nomenclature for a product configuration model component
1. Click Product configuration models.
2. In the list, find and select the desired record.
3. In the list, click the link in the selected row.
4. Click Edit.
5. Select Yes in the Use configuration nomenclature field.
6. Click Add.
7. Click Attribute value.
8. In the list, mark the selected row.
9. In the Attribute field, enter or select a value.
10. Click Add.
11. Click Text constant.
12. In the list, mark the selected row.
13. In the Text field, type a value.
14. Click Add.
15. Click Attribute value.
16. In the list, mark the selected row.
17. In the Attribute field, enter or select a value.
18. Click Add.
19. Click Text constant.
20. In the list, mark the selected row.
21. In the Text field, type a value.
22. Click Add.
23. Click Attribute value.
24. In the list, mark the selected row.
25. In the Attribute field, enter or select a value.
26. Click Add.
27. Click Text constant.
28. In the list, mark the selected row.
29. In the Text field, type a value.
30. Click Add.
31. Click Attribute value.
32. In the list, mark the selected row.
33. In the Attribute field, enter or select a value.
34. Click Add.
35. Click Text constant.
36. In the list, mark the selected row.
37. In the Text field, type a value.
38. Click Add.
39. Click Number sequence value.
40. In the list, mark the selected row.
41. In the Number sequence field, enter or select a value.
42. Close the page.
43. Close the page.
44. Close the page.

