--- 
# required metadata 
 
title: Use model mapping configurations for aggregate calculations at the database level
description: This topic describes how to design a new Electronic reporting model mapping configuration and use built-in ER functions for efficient aggregate calculations. 
author: NickSelin
ms.date: 12/12/2017
ms.topic: business-process 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 

---
# Use model mapping configurations for aggregate calculations at the database level

[!include [banner](../../includes/banner.md)]

This procedure provides information about how to design a new Electronic reporting (ER) model mapping configuration and use built-in ER functions for efficient aggregate calculations. In this procedure you will create a configuration for the sample company, Litware, Inc. 

This procedure is created for users with the assigned role of System administrator or Electronic reporting developer. These steps can be completed using any dataset.

 To complete these steps, you must first complete the steps in the procedure, "ER improves the efficiency of aggregate calculations by performing them on database level (Part 1: Prepare configurations)."

1. Go to Organization administration > Electronic reporting > Configurations.
2. In the tree, expand 'Intrastat model'.
3. In the tree, select 'Intrastat model\Intrastat sample mapping'.
4. Click Designer.
5. Click Designer.
6. In the tree, select 'Dynamics 365 for Operations\Table records'.
7. Click Add root.
    * Add a new data source representing records you want to group.  
8. In the Name field, type 'Transactions'.
    * Transactions  
9. In the Table field, type 'Intrastat'.
    * Intrastat  
10. Click OK.
11. In the tree, select 'Functions\Group by'.
    * This data source type is used to introduce a new data source at run-time to group records and to calculate required aggregations.  
12. Click Add root.
13. In the Name field, type 'TransactionsGroups'.
    * TransactionsGroups  
14. Click Edit group by.
15. In the tree, select 'Transactions'.
    * Select the added data source of the 'Record list' type that represents the records that you want to group.  
16. Click Add field to.
17. Click What to group.
18. In the tree, expand 'Transactions'.
19. In the tree, select 'Transactions\Direction'.
20. Click Add field to.
21. Click Grouped fields.
    * Select the field to specify the grouping level. Based on this selection, the data source will return at run-time as many groups of transactions as there are direction codes that will be met in the Intrastat table.  
22. In the tree, select 'Transactions\Invoice amount(AmountMST)'.
    * Select the field to specify the source for aggregation calculation.  
23. Click Add field to.
24. Click Aggregation fields.
25. In the list, mark the selected row.
26. In the Method field, select 'Sum'.
    * Select the aggregation type.  
27. In the Name field, type 'SumOfAmountMST'.
    * Specify the name of this aggregation in the configured data source.  
28. Click Save.
    * Note that the 'Execution at' field indicates that this grouping will be performed at run-time in the SQL database.  
29. Close the page.
30. Click OK.
31. In the tree, expand 'Totals'.
32. In the tree, expand 'TransactionsGroups'.
33. In the tree, expand 'TransactionsGroups\aggregated'.
34. In the tree, select 'TransactionsGroups\aggregated\SumOfAmountMST'.
35. In the tree, select 'Totals\Total invoice value(TotalInvoiceValue) = IF(ISEMPTY(IntrastatTotals), 0.0, IntrastatTotals.aggregated.'$AmountMSTRounded')'.
36. Click Bind.
    * Based on this setting, this data source will calculate the sum of values of the 'AmountMST' field for each groups of transactions. This aggregation calculation will be available as TransactionsGroups.aggregated.TotalAmount item.  
37. In the tree, expand 'TransactionsGroups'.
38. In the tree, select 'TransactionsGroups'.
39. Click Edit.
40. Click Edit group by.
41. In the tree, expand 'Transactions'.
42. In the tree, select 'Transactions\Invoice amount(AmountMST)'.
43. Click Add field to.
44. Click Aggregation fields.
45. In the list, mark the selected row.
46. In the Method field, select 'Max'.
47. In the Name field, type 'MaxOfAmountMST'.
48. Click Save.
    * Currently, the execution of GROUPBY data sources can be translated to the SQL database level with some limitations. Translation can be done for either data sources of the 'Record list' type or data sources represented as an expression using the FILTER function. It can also be done when the only one aggregation is configured for a single field of the grouping records.  
    * Note that even though more than one aggregation was configured for the AmountMST field, the 'Execution at' field still indicates that this grouping will be performed at run-time in the SQL database. This is because only one aggregation is bound to the data model item and will be used at run-time to pull data from this data source.  
49. Close the page.
50. Click OK.
51. In the tree, expand 'TransactionsGroups'.
52. In the tree, expand 'TransactionsGroups\aggregated'.
53. In the tree, select 'TransactionsGroups\aggregated\MaxOfAmountMST'.
54. In the tree, select 'Totals\Total statistical value(TotalStatisticalValue) = IF(ISEMPTY(IntrastatTotals), 0.0, IntrastatTotals.aggregated.'$StatisticalValueRounded')'.
55. Click Bind.
56. In the tree, expand 'TransactionsGroups'.
57. In the tree, select 'TransactionsGroups'.
58. Click Edit.
59. Click Edit group by.
    * Note that the 'Execution at' field indicates that this grouping will be performed at run-time in memory because both aggregations of the same field are bound to the data model items.   
60. In the list, mark or unmark all rows.
61. Click Delete.
62. Click Yes.
63. Click Delete.
64. Click Yes.
65. Click Add field to.
66. Click What to group.
67. In the tree, expand 'Commodity record(Intrastat)'.
68. Click Save.
    * Note that the 'Execution at' field indicates that this grouping will be performed at run-time in memory even though there are no aggregations defined and the selected data source of 'Table records' type refers to the same 'Intrastat' table. This is because the data source contains some calculated fields which can't yet be translated to the SQL database level.  



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]