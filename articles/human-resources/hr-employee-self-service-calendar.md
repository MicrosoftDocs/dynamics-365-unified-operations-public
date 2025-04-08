---
# required metadata

title: Create a team calendar
description: View and create team calendars in Dynamics 365 Human Resources.
author: twheeloc
ms.date: 07/09/2024
ms.topic: article
# optional metadata

ms.search.form: EssWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: ajitchandran
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# View team and company calendars

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

You can view team and company calendars in Dynamics 365 Human Resources. Team calendars only display direct reports, as defined in the line hierarchy.

## View your team calendar as an employee

- In the **Employee self service** workspace, select **Team absence calendar** under **Summary**.

## View your team calendar as a manager

1. In the **Employee self service** workspace, select **My team**.
2. Select **Leave and absence**, and then select **View manager absence calendar**.

Managers can also access the team calendar from **Pending time off requests from my team**, **Approved time off**, and **Time off requests**. 

## View your absence manager calendar as the absence manager

> [!NOTE]
> To view the absence manager calendar, you must first turn on the **(Preview) Absence manager to manage leave** feature in Feature management. For more information about how to turn on preview features, see [Manage features](hr-admin-manage-features.md).

Users in the Absence manager role can view time-off requests in their calendar. Follow these steps to access the leave calendar.

1. In the **Employee self service** workspace, select **Leave management** and then **Absence manager calendar**.
2. In the **Date** field, enter the desired dates.
3. Update the view options as required.

The absence manager calendar shows all the records for the employees who report to the absence manager in the Leave hierarchy.

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

Calendar configuration on the **Leave and absence parameters** page determines the available view options.

You can also filter calendars by manager or department. The primary position assignment determines the employees displayed when these filters are set. 

> [!IMPORTANT]
> You can turn on the **Cross company leave view** feature in Feature management. You must then enable the feature on the **Human resources shared parameters** page to show the legal entity filter in calendars. For more information, see [Configure leave and absence parameters](hr-leave-and-absence-parameters.md).
> 
> You can filter the calendar by legal entity. To view all employees, regardless of legal entity, clear the filter field, and then select **Enter**. 

For information about calendar settings, see [Configure calendar parameters](hr-leave-and-absence-parameters.md?configure-calendar-parameters).

[!INCLUDE[footer-include](../includes/footer-banner.md)]
