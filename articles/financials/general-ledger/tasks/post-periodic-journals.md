--- 
# required metadata 
 
title: Post periodic journals
description: Periodic journals are sometimes called recurring journals because the amount, text, and other information are repeated each time that the periodic journal is retrieved. 
author: aprilolson
manager: AnnBe 
ms.date: 02/24/2016
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
ms.author: aolson
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Post periodic journals

[!include[task guide banner](../../includes/task-guide-banner.md)]

Periodic journals are sometimes called recurring journals because the amount, text, and other information are repeated each time that the periodic journal is retrieved. When you create the periodic journal, you specify the period interval for the recurrence, such as days or months. This task guide will create a periodic journal with a monthly recurrence.



1. Go to General ledger > Periodic tasks > Periodic journals.
2. Click New.
3. In the Name field, enter or select a value.
4. In the list, click the link in the selected row.
5. In the Description field, type a value.
    * The description will be the name of the Periodic journal when retrieved later so make sure to give it a relevant name.  
6. Click Lines.
    * A periodic journal will typically include several journal lines. this task guide will however only add one line.  
7. In the Date field, enter a date.
    * The Date field contains the posting date for the next transfer to the daily journal. For journals that will be retrieved each month it is recommended to use the date in the month when it will be posted, typically the first or last date in the period. It is possible to leave the Date field blank and to give a date when the journal is retrieved, using the Empty date field.    The field is automatically updated to the next recurring date when transactions are retrieved.  
8. In the Account field, specify the desired values.
9. In the Description field, type a value.
10. Close the page.
11. In the Debit field, enter a number.
12. In the Offset account field, specify the desired values.
13. In the Unit field, select 'Months'.
14. In the Number of units field, enter '1'.
15. In the Last date field, enter a date.
    * Entering last date in the preceding period will prevent that the recurring journal by mistake is created in the wrong starting period. Last date will later on be updated each time the periodic journal is retrieved.  
16. Click Save.
17. Go to Default dashboard.
18. Go to General ledger > Journal entries > General journals.
19. Click New.
20. In the Name field, enter or select a value.
21. In the list, find and select the desired record.
22. In the list, click the link in the selected row.
23. In the Description field, type a value.
24. Click Lines.
25. Click Period journal.
26. Click Retrieve journal.
27. In the To date field, enter a date.
    * The To date serves as the cutoff date for the periodic voucher lines. Based on the recurrence setting, the Last date and To date the same line might be included more than once in the resulting journal. To date is automatically updated based on  session date of the last time the periodic line was transferred to a journal.  
28. In the Periodic journal number field, enter or select a value.
29. In the list, click the link in the selected row.
30. Click OK.
    * The period journal can now be reviewed, approved or posted depending on requirement and setup.  

