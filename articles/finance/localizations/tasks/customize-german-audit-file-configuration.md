--- 
# required metadata 
 
title: Customize German audit file configuration
description: This procedure shows how to customize the German audit file configuration by adding a new table group and selecting a table with fields for data export definition. 
author: mrolecki
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: ERWorkspace, ERSolutionTable, ERDataModelDesigner, ERModelMappingTable, ERModelMappingDesigner, ERTableNameLookup, ERModelGDPdUFunctionEditor,  ERExpressionDesignerFormula   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Germany
# ms.search.industry: 
ms.author: mrolecki
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Customize German audit file configuration

[!include [banner](../../includes/banner.md)]

This procedure shows how to customize the German audit file configuration by adding a new table group and selecting a table with fields for data export definition. 

This procedure was created using the demo data company DEMF with Germany as the country of legal entity primary address.

1. Go to Organization administration > Workspaces > Electronic reporting.
2. Click Configurations.
3. Click Show filters.
4. Add filter
5. Click Apply.
6. Click Model designer.
7. In the tree, select 'enumTableGroup'.
8. Click New.
9. In the Name field, type a value.
10. In the Description field, type a value.
11. Click Map model to datasource.
12. Click Designer.
13. In the tree, select 'Dynamics Ax\Table records'.
14. Click Add root.
15. In the Name field, type a value.
16. In the Table field, enter or select a value.
17. Click OK.
18. In the tree, select 'Functions\Table metadata'.
19. Click Add root.
20. In the Name field, type a value.
21. In the Label field, type a value.
22. Click Editor.
23. In the tree, select 'AssetTable'.
24. Click Add.
25. In the Name field, type a value.
26. In the tree, expand 'AssetTable'.
27. In the tree, select 'AssetTable\Fixed asset number(AssetId)'.
28. Click Add.
29. In the list, mark the selected row.
30. In the Name field, type a value.
31. Close the page.
32. Click Yes.
33. Click OK.
34. In the tree, select 'TblGroup'.
35. Click Edit.
36. Click Edit formula.
37. In the expressionAsStringText field, type a value.
38. In the tree, expand 'enumTableGroup'.
39. In the tree, select 'enumTableGroup\Anlagen'.
40. Click Add data source.
41. In the expressionAsStringText field, type a value.
42. In the tree, select '_05Anlagen(TblGroup5)'.
43. Click Add data source.
44. In the expressionAsStringText field, type a value.
45. Click Save.
46. Close the page.
47. Click OK.
48. Close the page.
49. Click Yes.
50. Close the page.
51. Close the page.
52. Click Change status.
53. Click Complete.
54. In the Description field, type a value.
55. Click OK.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]