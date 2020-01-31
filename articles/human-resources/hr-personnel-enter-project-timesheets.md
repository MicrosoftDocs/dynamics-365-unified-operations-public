--- 
# required metadata 
 
title: Enter project timesheets
description: This procedure lets you create a timesheet by using an empty timesheet form. 
author: andreabichsel
manager: AnnBe 
ms.date: 08/08/2019
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: anbichse
ms.search.scope: Operations, Human Resources 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Service industries
ms.author: anbichse
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Enter project timesheets



This procedure lets you create a timesheet by using an empty timesheet form. The new timesheet can be based on information from a previous timesheet, or from project and activity assignments in the **My favorites** page. By default, the **All timesheets** list page displays all your timesheets for the current period. You can use the drop-down list for the **Show** field in the **My timesheets** page to filter the timesheet list by time period or project, or to view timesheets that were created on behalf of other workers. The demo data company used to create this procedure is USSI. 

1. In the **Navigation pane**, go to **Modules > Project management and accounting > Timesheets > My timesheets**.
2. To enter a new timesheet, click **New**.
    - The Resource drop-down list shows the worker assigned to the current user, by default.  
    - If the user is designated as a delegate, this will list the names so that a user can enter a timesheet on their behalf.  
3. In the **Date** field, enter a date. If this option is selected, new timesheet lines will be created by using the timesheet settings that were configured as favorites.  
4. Click **OK**.
5. Click **New line**.
6. In the list, mark the selected row. The **Legal Entity** field displays the current Legal entity by default.   
7. In the **Project** field, click the drop-down button to open the lookup.
8. In the list, find and select the desired record.
9. In the list, click the link in the selected row.
10. In the **Activity number** field, click the drop-down button to open the lookup.
11. In the list, find and select the desired record.
12. In the list, click the link in the selected row.
13. In the **Category** field, click the drop-down button to open the lookup.
14. In the list, find and select the desired record.
15. In the list, click the link in the selected row.
16. Enter the number of hours worked each day. Enter the hours in decimal format. For example, if you worked for two hours and fifteen minutes, enter 2.25.   
17. In **Line details**, the following options are available:
    - Add information about taxes and financial dimensions in the **General** and the **Financial Dimensions** tab.
    - Add comments about the timesheet line in the **Comment** tab.
20. In the **Action pane**, click **Workflow** to open the drop dialog.
21. Click **Submit**.
22. Click **Submit**.

