--- 
# required metadata 
 
title: Create performance reviews
description: This article explains how to create a performance review and describes the purpose for each section of the review. 
author: twheeloc
ms.date: 08/26/2021
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: DefaultDashboard, EssWorkspace, HcmDiscussionNewDialog, HcmDiscussion, HcmDiscussionChangeSettings, HcmDiscussionAddGoalDialog, HcmTopicCreate, HcmMeasurementDetailDialog, HcmPerfJournalAdd, HcmEmployeeDevelopmentWorkspace  
audience: Application User 
# ms.devlang:  

# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create performance reviews


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]


This article explains how to create a performance review and describes the purpose for each section of the review. This procedure was created using the USMF demo data company.

1. On the home page, select the **Employee self service** workspace.
2. Select **New review** to create a new review.
3. In the **Review type** field, enter or select a value.
4. In the **Performance period** field, enter or select a value.
5. In the **End date** field, enter a date.
6. Select **OK**. You can also create a review from a template. This is the best way to create a review because each section will contain the information that you need to start a review.  
7. You can show or hide tabs such as the attachments tab:

    1. On the Action Pane, select **Show sections** to open the dialog menu.
    1. Select **Yes** or **No** in the **Show attachments** field to show or hide the attachments tab.
    1. Select **Save**.

8. Select **Add goal to review** to add a goal. Select **OK** when finished.
9. Select **Add competency** to open the drop dialog.
10. In the **Title** field, type a value.
11. In the **Description** field, enter `Increase customer skills by working with the support team`.
12. Select **OK**.
13. Select **Collapse all**.
14. Select **Expand all**.
15. Select **Add comment**.
16. Select **Post**.
17. Select the **Measurements** tab.
18. Select **Add measurement** to open the dialog menu.
19. In the **Measurement** field, enter or select a value.
26. In the **Target amount** field, enter a number.
20. Select **OK**.
21. Select the **Activities** tab.
22. Select **Add**.
23. In the **Title** field, type a value.
24. In the **Description** field, type a value.
25. In the **Start date** field, enter a date.
26. In the **Date completed** field, enter a date.
27. Select **Yes** in the **Development plan** field.
28. In the **Keywords** field, type a value.
29. Select **Save**.
30. Select the **Ratings** tab.  

    - The **Rating details** FastTab allows employees to rate themselves and the manager to rate the employee. If weights are used, the weight value of the scores will be calculated automatically.  
    - To view this section, enable the parameter settings for showing employee ratings on the **Human resources shared parameters** page.  

31. Select the **Sign offs** tab. If the review uses workflow, then the signoffs will appear only after the workflow is complete. If no workflow is used, then both the worker and the manager are listed here. The **Required** check box for **Sign offs** is selected based on the settings of the review type.  
32. Select the **General** tab.

    - The performance period creates the default start and end dates. Those dates are editable.  
    - The statuses control the access to the review. The **Not started** status allows everyone to edit the review. The **In progress** status allows only the employee to view and edit the review. **Ready for review** allows only the manager to view and edit the review. **Final review** status allows both the employee and manager to view and edit the review if the **Allow edit in final review** option is selected in the review type. The **Completed** and **Canceled** statuses make the review read only. If a review is **Rejected** and sent back to the employee, both the employee and manager can make necessary edits so the employee can resubmit.

33. In the **Overview** field, type a value.
34. Select the **Review** tab. As the review moves through the statuses, the employee and manager can add comments for each goal or competency.  
35. Select the **Sign offs** tab. The worker and manager can sign off on the review. When all required sign offs are complete, the status is changed to **Completed** and no more changes can be made.  



[!INCLUDE[footer-include](../includes/footer-banner.md)]
