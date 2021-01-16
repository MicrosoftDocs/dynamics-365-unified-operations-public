---
# required metadata

title: Create a team calendar
description: View and create team calendars in Dynamics 365 Human Resources.
author: andreabichsel
manager: tfehr
ms.date: 11/02/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-human-resources
ms.technology: 

# optional metadata

ms.search.form: EssWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# View team and company calendars

You can view team and company calendars in Dynamics 365 Human Resources. Team calendars only display direct reports, as defined in the line hierarchy.

## View your team calendar as an employee

1. In the **Employee self service** workspace, select **Team absence calendar** under **Summary**.

## View your team calendar as a manager

1. In the **Employee self service** workspace, select **My team**.

2. Select **Leave and absence**, and then select **View manager absence calendar**.

Managers can also access the team calendar from **Pending time off requests from my team**, **Approved time off**, and **Time off requests**. 

## View a company calendar

People who are in human resources roles can view company calendars. Company calendars display all employees. By default, the calendar displays today's date plus 28 days, but you can change the date range. You can also filter the calendar by **Name**, **Personnel number**, and **Leave type**.

1. In the **Leave and absence** workspace, select **Links**.

2. Select **Leave and absence calendar**.

Human resources roles can also access the company calendar from **Leave and absence requests**, **Approved time off**, and **Time off requests**. 

Calendars now contain additional filters and options. All calendars include view options for:

- Approved requests
- Pending requests
- Employees with leave requests
- Employees without leave requests
- Employee birthdays
- Time-off requests 
- Leave of absence requests

Calendar configuration in Leave and absence parameters determine available view options.

You can also filter calendars by manager or department. The primary position assignment determines the employees displayed when these filters are set. 

>[!IMPORTANT]
>Viewing leave and absence across companies is currently in preview. You'll need to enable it in your **Sandbox** environment. For more information about enabling preview features, see [Manage features](hr-admin-manage-features.md).<br><br>
>Then you must enable the feature in **Human resources shared parameters** to display the legal entity filter in calendars. For more information, see [Configure leave and absence parameters](hr-leave-and-absence-parameters.md).<br><br>
>You can filter the calendar by legal entity. If you want to see all employees regardless of legal entity, clear the filter box and select enter. 

For information about calendar settings, see [Configure calendar parameters](hr-leave-and-absence-parameters.md?configure-calendar-parameters).

