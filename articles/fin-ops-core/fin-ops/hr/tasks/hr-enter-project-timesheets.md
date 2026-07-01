--- 
title: Enter project timesheets
description: Learn about how to enter project timesheets, including a step-by-step process that details how to create timesheets.
author: twheeloc
ms.author: twheeloc
ms.topic: how-to
ms.date: 06/29/2026
ms.custom:
ms.reviewer: twheeloc  
audience: Application User 
ms.search.region: Global
ms.search.industry: Service industries
ms.search.validFrom: 2016-06-30
ms.search.form: HcmPersonnelManagementWorkspace
ms.dyn365.ops.version: AX 7.0.0 
---

# Enter project timesheets

This procedure lets you create a timesheet by using an empty timesheet page. The new timesheet can be based on information from a previous timesheet, or from project and activity assignments on the **My favorites** page. By default, the **All timesheets** list page shows all your timesheets for the current period. You can use the **Show** field on the **My timesheets** page to filter the timesheet list by time period or project, or to view timesheets that were created on behalf of other workers. The **USSI** demo data company was used to create this procedure.

1. Go to **Project management and accounting > Timesheets > My timesheets**.
1. Select **New** to enter a new timesheet.

    By default, the **Resource** field shows the worker who is assigned to the current user.

    If you're designated as a delegate, the names appear so that you can enter a timesheet on their behalf.

1. In the **Date** field, enter a date. When you select this option, new timesheet lines are created by using the timesheet settings that you configured as favorites.
1. Select **OK**.
1. Select **New line**.
1. In the list, mark the selected row. By default, the **Legal entity** field shows the current legal entity.
1. In the **Project** field, select the drop-down arrow to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **Activity number** field, select the drop-down arrow to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **Category** field, select the drop-down arrow to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Enter the number of hours that you worked each day. Enter the hours in decimal format. For example, if you worked two hours and fifteen minutes, enter **2.25**.

    In the **Line details** section, the following options are available:

    - Add information about taxes and financial dimensions on the **General** and **Financial Dimensions** tabs.
    - Add comments about the timesheet line on the **Comment** tab.

1. On the Action Pane, select **Workflow** to open the drop-down dialog box.
1. Select **Submit**.
1. Select **Submit**.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
