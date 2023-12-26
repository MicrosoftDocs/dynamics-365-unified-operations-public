--- 
# required metadata 
 
title: Enter project timesheets
description: This procedure lets you create a timesheet by using an empty timesheet form. 
author: twheeloc
ms.date: 01/10/2022
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
# ms.search.form: HcmPersonnelManagementWorkspace
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Service industries
ms.author: anbichse
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---

# Enter project timesheets


[!INCLUDE [PEAP](../../../../includes/peap-1.md)]

This procedure lets you create a timesheet by using an empty timesheet page. The new timesheet can be based on information from a previous timesheet, or from project and activity assignments on the **My favorites** page. By default, the **All timesheets** list page shows all your timesheets for the current period. You can use the **Show** field on the **My timesheets** page to filter the timesheet list by time period or project, or to view timesheets that were created on behalf of other workers. The **USSI** demo data company was used to create this procedure.

1. Go to **Project management and accounting \> Timesheets \> My timesheets**.
2. Select **New** to enter a new timesheet.

    By default, the **Resource** field shows the worker who is assigned to the current user.

    If the user is designated as a delegate, the names will be listed, so that a user can enter a timesheet on their behalf.

3. In the **Date** field, enter a date. If this option is selected, new timesheet lines will be created by using the timesheet settings that were configured as favorites.
4. Select **OK**.
5. Select **New line**.
6. In the list, mark the selected row. By default, the **Legal entity** field shows the current legal entity.
7. In the **Project** field, select the drop-down arrow to open the lookup.
8. In the list, find and select the desired record.
9. In the list, select the link in the selected row.
10. In the **Activity number** field, select the drop-down arrow to open the lookup.
11. In the list, find and select the desired record.
12. In the list, select the link in the selected row.
13. In the **Category** field, select the drop-down arrow to open the lookup.
14. In the list, find and select the desired record.
15. In the list, select the link in the selected row.
16. Enter the number of hours that are worked each day. Enter the hours in decimal format. For example, if you worked two hours and fifteen minutes, enter **2.25**.

    In the **Line details** section, the following options are available:

    - Add information about taxes and financial dimensions on the **General** and **Financial Dimensions** tabs.
    - Add comments about the timesheet line on the **Comment** tab.

17. On the Action Pane, select **Workflow** to open the drop-down dialog box.
18. Select **Submit**.
19. Select **Submit**.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
