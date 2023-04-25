--- 
# required metadata 
 
title: Create calendars and generate working times
description: Calendars describe the capacity and working times of operations resources. This article explains how to define a work calendar based on a working time template.  
author: twheeloc
ms.date: 10/28/2021
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: OpResLifeCycleManagementWorkspace, WorkCalendarTable, WorkCalendarDate, HcmPersonnelManagementWorkspace, WrkCtrGroupDateCalendar, WrkCtrDateCalendar
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
# Create calendars and generate working times

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

> [!IMPORTANT]
> The functionality noted in this article is currently available for Human Resources customers on the Finance infrastructure.  


Calendars describe the capacity and working times of operations resources. This article explains how to define a work calendar based on a working time template. You can walk through this procedure in demo data company USMF, or using your own data.

1. On the home page, select **Resource lifecycle management**.
2. Select **Calendars**.
3. Select **New**.
4. In the **Calendar** field, classify your calendar. This is the ID of the calendar, which is used as a reference when assigning calendars, such as to an operations resource or a resource group.  
5. In the **Name** field, enter a name for your calendar.
6. In the **Standard work day in hours** field, enter a number.
7. Make sure the row is selected, then select **Working times** from the **Action Pane**.
8. Select **Compose working times**. Generate working hours for each day in the period where you want to be able to schedule work. As time goes by, you can generate working times for additional periods.  
9. In the **From date** field, enter a date. This is the first day that this calendar must be open.  
10. In the **To date field**, enter a date. This is the last day that this calendar is open.  
11. In the **Working time template** field, enter or select a value. The working time template defines the working hours for each day of the week.  
12. Select **OK**.
13. Close the page.



[!INCLUDE[footer-include](../includes/footer-banner.md)]
