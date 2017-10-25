--- 
# required metadata 
 
title: Set up fixed asset posting profiles
description: This task guide will set up Fixed asset posting profiles. 
author: saraschi2
manager: AnnBe 
ms.date: 02/24/2017
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
# Set up fixed asset posting profiles

[!include[task guide banner](../../includes/task-guide-banner.md)]

This task guide will set up Fixed asset posting profiles.  It uses the Accountant role and demo data for the USMF legal entity.  Examples given in the task guide are for a basic posting profile, though posting profiles must be created for your specific chart of accounts and financial reporting requirements.

1. Go to Fixed assets > Setup > Fixed asset posting profiles.
2. Click New.
3. In the Posting profile field, type a value.
4. In the Description field, type a value.
    * You will need to create a posting profile for each fixed asset transaction type you will be using when working with fixed assets.  This task guide will start with the Acquisition transaction type.  
5. Click Add.
6. In the Book field, enter or select a value.
    * The Groupings field allows you to define the posting profile down to the Table (one account set up for each fixed asset) or Group (one account set up for each fixed asset group).  For this task guide I will leave the value set to “All” to apply to all fixed assets with the specified Book.  
7. In the Main account field, specify the desired values.
    * For Acquisitions, you can enter an offset account or leave it blank to be filled in for the specific transaction.    
8. In the Transaction type field, select 'Acquisition adjustment'.
    * For Acquisition adjustment transactions, we will use the same accounts as used for Acquisition transactions.  
9. Click Add.
10. In the Book field, enter or select a value.
11. In the Main account field, specify the desired values.
    * For Acquisition adjustments, you can enter an offset account or leave it blank to be filled in for the specific transaction.    
12. In the Transaction type field, select 'Depreciation'.
13. Click Add.
14. In the Book field, enter or select a value.
15. In the Main account field, specify the desired values.
16. In the Offset account field, specify the desired values.
17. In the Transaction type field, select 'Depreciation adjustment'.
    * For Depreciation adjustment transactions, we will use the same accounts as used for Depreciation transactions.  
18. Click Add.
19. In the Book field, enter or select a value.
20. In the Main account field, specify the desired values.
21. In the Offset account field, specify the desired values.
22. In the Transaction type field, select 'Disposal - sale'.
23. Click Add.
24. In the Book field, enter or select a value.
25. In the Main account field, specify the desired values.
    * For Disposals, you can enter an offset account or leave it blank to be filled in for the specific transaction.  
26. In the Transaction type field, select 'Disposal - scrap'.
    * We will use the same accounts for Disposal sale and Disposal scrap.  
27. Click Add.
28. In the Book field, enter or select a value.
29. In the Main account field, specify the desired values.
    * For Disposals, you can enter an offset account or leave it blank to be filled in for the specific transaction.  
30. Expand the Disposal section.
    * You must set up disposal posting profiles for both sale and scrap.  We will start with disposal sale transactions.  
31. Click Add.
32. In the Book field, enter or select a value.
33. In the Post value field, select 'Acquisition value'.
    * Acquisition value will address Acquisition and Acquisition adjustment values for all years.  You can also define accounts for these transaction types separately.  
    * You can set the disposal process to use different accounts depending upon if the disposal results in a gain or loss.  I will set the Sales value type to “All” to use the same accounts for all types of disposals.  
34. In the Main account field, specify the desired values.
35. In the Offset account field, specify the desired values.
36. Click Add.
37. In the Book field, enter or select a value.
    * In the Post value field, select 'Depreciation (prior years)'.  
38. In the Main account field, specify the desired values.
39. In the Offset account field, specify the desired values.
40. Click Add.
41. In the Book field, enter or select a value.
42. In the Post value field, select 'Depreciation (this year)'.
43. In the Main account field, specify the desired values.
44. In the Offset account field, specify the desired values.
45. Click Add.
46. In the Book field, enter or select a value.
47. In the Post value field, select 'Depreciation adjustments (prior years)'.
48. In the Main account field, specify the desired values.
49. In the Offset account field, specify the desired values.
50. Click Add.
51. In the Book field, enter or select a value.
52. In the Post value field, select 'Depreciation adjustments (this year)'.
53. In the Main account field, specify the desired values.
54. In the Offset account field, specify the desired values.
55. Click Add.
56. In the Book field, enter or select a value.
57. In the Post value field, select 'Net book value'.
58. In the Main account field, specify the desired values.
59. In the Offset account field, specify the desired values.
60. In the Sale or scrap field, select 'Scrap'.
61. Click Add.
62. In the Book field, enter or select a value.
63. In the Post value field, select 'Acquisition value'.
64. In the Main account field, specify the desired values.
65. In the Offset account field, specify the desired values.
66. Click Add.
67. In the Book field, enter or select a value.
    * In Post value field, select 'Depreciation (prior years)'.  
68. In the Main account field, specify the desired values.
69. In the Offset account field, specify the desired values.
70. Click Add.
71. In the Book field, enter or select a value.
72. In the Post value field, select 'Depreciation (this year)'.
73. In the Main account field, specify the desired values.
74. In the Offset account field, specify the desired values.
75. Click Add.
76. In the Book field, enter or select a value.
77. In the Post value field, select 'Depreciation adjustments (prior years)'.
78. In the Main account field, specify the desired values.
79. In the Offset account field, specify the desired values.
80. Click Add.
81. In the Book field, enter or select a value.
82. In the Post value field, select 'Depreciation adjustments (this year)'.
83. In the Main account field, specify the desired values.
84. In the Offset account field, specify the desired values.
85. Click Add.
86. In the Book field, enter or select a value.
87. In the Post value field, select 'Net book value'.
88. In the Main account field, specify the desired values.
89. In the Offset account field, specify the desired values.

