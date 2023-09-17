---
title: ER Configure format to do counting and summing (Part 2 - Configure computations)
description: This article describes how to configure an Electronic reporting format to do counting and summing based on data of the already generated text output. (Part 2)
author: kfend
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: ERWorkspace, ERSolutionTable, ERSolutionCreateDropDialog, EROperationDesigner, ERDataSourceAddDropDialog, ERExpressionDesignerFormula
---
# ER Configure format to do counting and summing (Part 2 - Configure computations)

[!include [banner](../../includes/banner.md)]

The following steps explain how a user assigned to the system administrator or electronic reporting developer role can configure an Electronic reporting (ER) format to do counting and summing based on data of the already generated text output. These steps can be performed in any company.

To complete these steps, you must first complete the steps in the "ER Configure format to do counting and summing (Part 1: Create format)" procedure.

This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.


## Create a format configuration to add counting and summing details
1. Go to Organization administration > Workspaces > Electronic reporting.
2. Click Reporting configurations.
3. In the tree, expand 'Intrastat model'.
4. In the tree, select 'Intrastat model\Intrastat (DE)'.
    * Assume that you need to customize the format provided by Microsoft by adding lines with summary details at the end of the Intrastat report. You need to do that by deriving our own instance of the Intrastat configuration from the Microsoft instance to make modifications.  
5. Click Create configuration to open the drop dialog.
6. In the New field, enter 'Derive from Name: Intrastat (DE), Microsoft'.
7. In the Name field, type 'Intrastat (DE) with counting & summing'.
8. Click Create configuration.

## Configure this report to do counting and summation based on output details
1. Click Designer.
2. Select Yes in the Collect output details field.
    * This flag will activate at run-time the process of collecting output details for generating the Intrastat file.  
    * You need to do counting for different Intrastat directions, so add a dedicated model enumeration to the data sources' list of this format configuration.  
3. Click the Mapping tab.
4. Click Add root to open the drop dialog.
5. In the tree, select 'Data model\Enumeration '.
6. In the Name field, type 'Direction'.
7. In the Model enumeration field, enter or select a value.
    * Select the value Direction.  
8. Click OK.
9. Click Add root to open the drop dialog.
10. In the tree, select 'Functions\Calculated field'.
11. In the Name field, type '$BlockName'.
12. Click Edit formula.
13. In the Formula field, enter '"block"'.
14. Click Save.
15. Close the page.
16. Click OK.
17. Click Add root to open the drop dialog.
18. In the tree, select 'Functions\Calculated field'.
19. In the Name field, type '$RecName'.
20. Click Edit formula.
21. In the Formula field, enter '"record"'.
22. Click Save.
23. Close the page.
24. Click OK.
25. Click Add root to open the drop dialog.
26. In the tree, select 'Functions\Calculated field'.
27. In the Name field, type '$InvName'.
28. Click Edit formula.
29. In the Formula field, enter '"InvoicedAmountEUR"'.
30. Click Save.
31. Close the page.
32. Click OK.
33. In the tree, select 'Intrastat\Data'.
34. Click Edit button for the 'Collected data key name' field
35. Click Add data source.
    * $BlockName  
36. Click Save.
37. Close the page.
38. Click the Edit button for the Collected data key value field.
39. In the Formula field, enter 'IF(Intrastat.CommodityRecord.Direction=Direction.Import, "Import", "Export")'.
    * IF(Intrastat.CommodityRecord.Direction=Direction.Import, "Import", "Export")  
40. Click Save.
41. Close the page.
    * Count the lines of this sequence. The results will be used with the name "block" separately for different directions. Value "Import" will be used for any arrivals Intrastat transactions. The value "Export" will be used for any Intrastat dispatches transactions. Consider this to be a virtual Excel spreadsheet. For each transaction a row where the first column "block" is filled with the values "Import" and "Export" accordingly.  
42. In the tree, expand 'Intrastat\Data: Sequence'.
43. In the tree, select 'Intrastat\Data: Sequence\Arrivals?'.
44. Click Edit button for the 'Collected data key name' field.
    * Count the lines of this sequence. The results will be memorized using the name "record".  
45. In the tree, select '$RecName'.
46. Click Add data source.
47. Click Save.
48. Close the page.
49. Click Edit button for the 'Collected data key value' field
50. In the Formula field, enter 'Intrastat.CommodityRecord.CommodityCode'.
51. Click Save.
52. Close the page.
    * Count the lines of this sequence. The results will be used with the name "record" separately for different commodity codes. Consider this to be a virtual Excel spreadsheet. For each transaction a row where the first column "block" is filled with the values "Import" and "Export" accordingly and the second block "record" is filled with the commodity code value.  
53. In the tree, select 'Intrastat\Data: Sequence\Dispatches?'.
54. Click Edit button for the 'Collected data key name' field
55. In the tree, select '$RecName'.
56. Click Add data source.
57. Click Save.
58. Close the page.
59. Click the Edit button for the 'Collected data key value' field.
60. In the Formula field, enter 'Intrastat.CommodityRecord.CommodityCode'.
61. Click Save.
62. Close the page.
63. In the tree, expand 'Intrastat\Data: Sequence\Dispatches: Sequence?'.
64. In the tree, expand 'Intrastat\Data: Sequence\Dispatches: Sequence?\Record =  Intrastat.CommodityRecord'.
65. Click the Format tab.
66. In the tree, select 'Intrastat\Data\Dispatches\Record\Invoice amount EUR'.
67. Click the Mapping tab.
68. Click the Edit button for the 'Collected data key name' field.
69. In the tree, select '$InvName'.
70. Click Add data source.
71. Click Save.
72. Close the page.
    * Summarize the invoiced amount values for lines of this sequence. The results will be used with the name "InvoicedAmountEUR" separately for different Intrastat directions and commodity codes. Consider this to be a virtual creation in Excel spreadsheet. For each transaction a row where the first column "block" is filled with the values "Import" and "Export" accordingly. The second block "record" is filled with the commodity code value, and the third column "InvoicedAmountEUR" is filled with the invoice amount value.  
73. In the tree, expand 'Intrastat\Data\Arrivals?'.
74. In the tree, expand 'Intrastat\Data\Arrivals?\Record =  Intrastat.CommodityRecord'.
75. Click the Format tab.
76. In the tree, select 'Intrastat\Data\Arrivals\Record\Invoice amount EUR'.
77. Click the Mapping tab.
78. Click the Edit button for the 'Collected data key name' field.
79. In the tree, select '$InvName'.
80. Click Add data source.
81. Click Save.
82. Close the page.
83. Click Save.
84. Close the page.



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
