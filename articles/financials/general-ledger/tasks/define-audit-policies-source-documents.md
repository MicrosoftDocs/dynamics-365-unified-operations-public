--- 
# required metadata 
 
title: Define audit policies for source documents
description: This procedure shows how to set up and run audit policy rules. 
author: ryansandness
manager: AnnBe 
ms.date: 11/10/2016
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
ms.author: ryansand
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Define audit policies for source documents

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows how to set up and run audit policy rules. The example uses expense reports with the hotel expense type. This procedure uses the USMF demo company. The auditor role contains the correct permissions in order to perform these tasks.

1. Go to Audit workbench > Setup > Policy rule type.
2. Click New.
3. In the Rule name field, type a value.
4. In the Description field, type a value.
5. In the Query name field, select Expense report line
6. In the query type field, select Aggregate
7. In the Legal entity field, select Legal entity
8. In the Document date reference field, select Modified date and time
9. Click Save.
10. Go to Audit workbench > Setup > Audit policies.
11. Click New.
12. In the Name field, type a value.
13. Expand the Policy organizations section.
14. In the tree, select 'Contoso Entertainment System USA'.
15. Click Add.
16. In the tree, select 'Contoso Consulting USA'.
17. Click Add.
18. In the tree, select 'Contoso Retail USA'.
19. Click Add.
20. Collapse the Policy organizations section.
21. Expand the Policy rules section.
22. In the list, find and select the Policy Rule that was created previously.
23. Click Create policy rule.
24. In the Effective date field, enter a date and time.
25. Click Filter.
26. In the list, select the row for Expense category, and set the details to Hotel
27. In the Criteria field, enter or select a value.
28. Click the Aggregate tab.
29. Click Add.
30. In the list, select a field value of Transaction amount
31. In the Field field, enter or select a value.
32. In the AggregateFunction field, select 'Sum'.
33. Click the Group by tab.
34. Click Add.
35. In the list, select a value of Employee 
36. Click Add.
37. In the list, select a value of Expense category
38. In the Field field, enter or select a value.
39. Click the Having tab.
40. Click Add.
41. Select Transaction amount
42. In the Field field, enter or select a value.
43. In the AggregateFunction field, select 'Sum'.
44. In the Criteria field, type '>2000'.
45. Click OK.
46. Click Test.
47. In the Document selection starting date field, enter a date and time.
48. In the Document selection ending date field, enter a date and time.
49. Click Run test.
50. On the Action Pane, click Audit policy.
51. Click Additional options.
52. In the Starting date field, enter a date and time.
53. In the Ending date field, enter a date and time.
54. Click Batch.
55. Expand the Run in the background section.
56. Select Yes in the Batch processing field.
57. Click OK.
58. Go to Audit workbench > Audit cases.
59. In the list, find and select the desired record.
60. In the list, click the link in the selected row.
61. Expand the Associations section.
62. In the list, find and select the desired record.
63. In the list, click the link in the selected row.

