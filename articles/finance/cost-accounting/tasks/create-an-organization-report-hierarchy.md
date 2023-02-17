--- 
# required metadata 
 
title: Create an organization report hierarchy
description: Use this procedure to create a report hierarchy for organization reporting. 
author: twheeloc
ms.date: 10/30/2017
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create an organization report hierarchy

[!include [banner](../../includes/banner.md)]

Use this procedure to create a report hierarchy for organization reporting. The purpose of this recording is to guide you through the dimension hierarchy so that you can continue until the whole organization reporting structure is created. This recording uses the USP2 demo data company.

1. Go to **Cost accounting > Dimensions > Dimension hierarchies**.
2. Click **New**.
3. In the **HierarchyTypeComboBox** field, select 'Dimension classification hierarchy'.
    * Select Dimension classification hierarchy. The Dimension classification hierarchy type is used to define rules and for reporting purposes. It supports all dimensions, such as cost objects, cost elements, and statistical dimensions.  
4. Click **Create**.
5. In the **Dimension hierarchy name** field, type 'Oganization USP2'.
6. In the **Dimension** field, enter or select a value.
    * Select Cost centers.  
7. Click **Save**.
8. Click **View hierarchy**.
9. Click **New**.
10. In the **Node name** field, type 'CEO'.
11. Click **Save**.
12. Click **New**.
13. In the **Node name** field, type 'CEO cost centers'.
14. Click **Save**.
15. Click **New**.
16. In the **Node name** field, type 'Region East'.
17. Click **Save**.
18. Click **New**.
19. In the list, mark the selected row.
20. In the **From dimension member** field, enter or select a value.
    * Select the dimension member that corresponds to the node.  
21. Click **Save**.
22. In the tree, select 'Oganization USP2\CEO\CEO cost centers'.
23. Click **New**.
24. In the **Node name** field, type 'Region West'.
25. Click **Save**.
26. Click **New**.
27. In the list, mark the selected row.
28. In the **From dimension member** field, enter or select a value.
    * Select the dimension member that corresponds to the node.  
29. Click **Save**.
30. In the tree, select 'Oganization USP2\CEO'.
31. Click **New**.
32. In the **Node name** field, type 'CFO cost centers'.
33. Click **Save**.
34. Click **New**.
35. In the **Node name** field, type 'Marketing campa'.
36. In the **Node name** field, type 'Marketing campaign'.
37. Click **Save**.
38. Click **New**.
39. In the list, mark the selected row.
40. In the **From dimension member** field, enter or select a value.
    * Select the dimension member that corresponds to the node.  
41. Click **Save**.
42. In the tree, select 'Organization USP2\CEO\CFO cost centers'.
43. Click **New**.
44. In the **Node name** field, type 'Trade shows'.
45. Click **Save**.
46. Click **New**.
47. In the list, mark the selected row.
48. In the **From dimension member** field, enter or select a value.
    * Select the dimension member that corresponds to the node.  
49. Click **Save**.
50. In the tree, select 'Oganization USP2\CEO'.
51. In the **Node name** field, type 'CIO cost centers'.
52. Click **Save**.
53. Click **New**.
54. In the **Node name** field, type 'Call centers'.
55. Click **Save**.
56. Click **New**.
57. In the list, mark the selected row.
58. In the **From dimension member** field, enter or select a value.
    * Select the dimension member that corresponds to the node.  
59. Click **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
