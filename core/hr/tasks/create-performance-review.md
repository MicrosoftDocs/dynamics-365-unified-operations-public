--- 
# required metadata 
 
title: Create a performance review
description: This procedure shows how to create a performance review and describes the purpose for each section of the review. 
author: kherr75
manager: AnnBe 
ms.date: 10/13/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: rschloma
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: kherr
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a performance review

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows how to create a performance review and describes the purpose for each section of the review. This procedure was created using the USMF demo data company. This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.

1. Click Employee self service.
2. Click New review to create a new review.
3. In the Review type field, enter or select a value.
4. In the Performance period field, enter or select a value.
5. In the End date field, enter a date.
6. Click OK.
    * You can also create a review from a template. This is the best way to create a review because each section will contain the information that you need to start a review.  
7. Click Show sections to open the drop dialog.
8. Select No in the Show attachments field.
9. Click Save.
    * Notice that the attachments tab is now hidden.  
10. Click Show sections to open the drop dialog.
11. Select Yes in the Show attachments field.
12. Click Save.
13. Click Add goal to review.
14. Click Cancel.
15. Click Add competency to open the drop dialog.
16. In the Title field, type a value.
17. In the Description field, enter 'Increase customer skills by working with the support team'.
18. Click OK.
19. Click Collapse all.
20. Click Expand all.
21. Click Add comment.
22. Click Post.
23. Click the Measurements tab.
24. Click Add measurement to open the drop dialog.
25. In the Measurement field, enter or select a value.
26. In the Target amount field, enter a number.
27. Click OK.
28. Click the Activities tab.
29. Click Add.
30. In the Title field, type a value.
31. In the Description field, type a value.
32. In the Start date field, enter a date.
33. In the Date completed field, enter a date.
34. Select Yes in the Development plan field.
35. In the Keywords field, type a value.
36. Click Save.
37. Click the Ratings tab.
    * The rating details FastTab allows employees to rate themselves and the manager to rate the employee. If weights are used, the weight value of the scores will be calculated automatically.    To see this section, enable the parameter settings for showing employee ratings.  
38. Click the Sign offs tab.
    * If the review uses workflow, then the signoffs will appear only after the workflow is complete. If no workflow is used, then both the worker and the manager are listed here. The required check box is selected based on the settings of the review type.  
39. Click the General tab.
    * The performance period creates the default start and end dates. Those dates are editable.  
    * The statuses control the access to the review. The Not started status allows everyone to edit the review. The In progress status allows only the employee to view and edit the review. Ready for review allows only the manager to view and edit the review. Final review status allows both the employee and manager to view the review and also edit it if set up in the review type. The Completed, Rejected, and Canceled statuses make the review read-only.  
40. In the Overview field, type a value.
41. Click the Review tab.
    * As the review moves through the statuses, the employee and manager can add comments for each goal or competency.  
42. Click the Sign offs tab.
    * The worker and manager can sign off on the review. When all required signoffs are complete, the status is changed to Completed and no more changes can be made.  

