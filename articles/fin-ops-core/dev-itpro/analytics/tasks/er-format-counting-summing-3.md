---
title: ER Configure format to do counting and summing (Part 3 - Use computations to make the output)
description: This article describes how to configure an Electronic reporting format to do counting and summing based on data of the already generated text output. (Part 3)
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
ms.search.form: ERWorkspace, ERSolutionTable, EROperationDesigner, ERDataSourceAddDropDialog, ERExpressionDesignerFormula, ERComponentTypeDropDialog
---
# ER Configure format to do counting and summing (Part 3 - Use computations to make the output)

[!include [banner](../../includes/banner.md)]

The following steps explain how a user assigned to the system administrator or electronic reporting developer role can configure an Electronic reporting (ER) format to do counting and summing based on data of the already generated text output. These steps can be performed in any company.

To complete these steps, you must first complete the steps in the "ER Configure format to do counting and summing (Part 2: Configure computations)" procedure.

This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.


## Configure this report to use counting and summing info
1. Go to Organization administration > Workspaces > Electronic reporting.
2. Click Reporting configurations.
3. In the tree, expand 'Intrastat model'.
4. In the tree, expand 'Intrastat model\Intrastat (DE)'.
5. In the tree, select 'Intrastat model\Intrastat (DE)\Intrastat (DE) with counting & summing'.
6. Click Designer.
7. Click the Mapping tab.
8. Click Add root to open the drop dialog.
    * Add a new data source to get the list of memorized blocks.  
9. In the tree, select 'Functions\Calculated field'.
10. In the Name field, type '$BlocksList'.
    * $BlocksList  
11. Click Edit formula.
12. In the tree, select 'Data collection functions\COLLECTEDLIST'.
13. Click Add function.
14. Click Add data source.
15. In the Formula field, enter 'COLLECTEDLIST('$BlockName', '.
    * COLLECTEDLIST('$BlockName',  
16. In the Formula field, enter 'COLLECTEDLIST('$BlockName', "*")'.
    * COLLECTEDLIST('$BlockName', "*")  
17. Click Save.
    * The pattern "*" means that all blocks will be included to the list for this record.  
18. Close the page.
19. Click OK.
20. Click the Format tab.
21. In the tree, select 'Intrastat\Data'.
22. Click Add to open the drop dialog.
23. In the tree, select 'Text\Sequence'.
24. In the Name field, type 'Totals by blocks'.
    * Totals by blocks  
25. In the Special characters field, select 'New line - Windows (CR LF)'.
26. Click OK.
27. In the tree, select 'Intrastat\Data\Totals by blocks'.
28. Click Add to open the drop dialog.
29. In the tree, select 'Text\String'.
30. In the Name field, type 'Block code'.
    * Block code  
31. Click OK.
32. Click Add String.
33. In the Name field, type 'Lines counting'.
    * Lines counting  
34. Click OK.
35. Click Add String.
36. In the Name field, type 'Total amount'.
    * Total amount  
37. Click OK.
38. Click the Mapping tab.
39. In the tree, select '$BlocksList'.
40. Click Bind.
    * Create a summary line for each memorized block.  
41. Click the Format tab.
42. In the tree, select 'Intrastat\Data\Totals by blocks\Block code'.
43. Click the Mapping tab.
44. Click Edit formula.
45. In the Formula field, enter '"Block id: " & '.
    * "Block id: " &  
46. In the tree, expand '$BlocksList'.
47. In the tree, select '$BlocksList\Value'.
48. Click Add data source.
49. Click Save.
50. Close the page.
51. Click the Format tab.
52. In the tree, select 'Intrastat\Data\Totals by blocks\Lines counting'.
53. Click the Mapping tab.
54. Click Edit formula.
    * Create output for the number of lines for each block presented in this report.  
55. In the Formula field, enter '"Number of lines in this block: " & '.
    * "Number of lines in this block: " &  
56. In the Formula field, enter '"Number of lines in this block: " & TEXT('.
    * "Number of lines in this block: " & TEXT(  
57. In the tree, select 'Data collection functions\COUNTIFS'.
58. Click Add function.
59. Click Add data source.
60. In the Formula field, enter '"Number of lines in this block: " & TEXT(COUNTIFS('$BlockName', '.
    * "Number of lines in this block: " & TEXT(COUNTIFS('$BlockName',  
61. In the tree, expand '$BlocksList'.
62. In the tree, select '$BlocksList\Value'.
63. Click Add data source.
64. In the Formula field, enter '"Number of lines in this block: " & TEXT(COUNTIFS('$BlockName', '$BlocksList'.Value, '.
    * "Number of lines in this block: " & TEXT(COUNTIFS('$BlockName', '$BlocksList'.Value,  
65. In the tree, select '$RecName'.
66. Click Add data source.
67. In the Formula field, enter '"Number of lines in this block: " & TEXT(COUNTIFS('$BlockName', '$BlocksList'.Value, '$RecName', "*"))'.
    * "Number of lines in this block: " & TEXT(COUNTIFS('$BlockName', '$BlocksList'.Value, '$RecName', "*"))  
68. Click Save.
69. Close the page.
70. Click the Format tab.
71. In the tree, select 'Intrastat\Data\Totals by blocks\Total amount'.
72. Click the Mapping tab.
73. Click Edit formula.
    * Create output that will be the total of the invoiced amount for each block presented in this report.  
74. In the Formula field, enter '"Sum of invoiced amount: " & TEXT(SUMIFS('$InvName', '$BlockName', '$BlocksList'.Value, '$RecName', "*"))'.
    * "Sum of invoiced amount: " & TEXT(SUMIFS('$InvName', '$BlockName', '$BlocksList'.Value, '$RecName', "*"))  
75. Click Save.
76. Close the page.
77. Click Save.
78. Close the page.



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
