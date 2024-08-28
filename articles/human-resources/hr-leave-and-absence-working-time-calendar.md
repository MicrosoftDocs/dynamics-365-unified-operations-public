--- 
# required metadata

title: Create a working time calendar
description: Define a working time calendar, holidays, and non-work times in Dynamics 365 Human Resources.
author: twheeloc
ms.date: 07/09/2024
ms.topic: article
# optional metadata

ms.search.form: LeavePlanFormPart, LeaveAbsenceWorkspace
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

# Create a working time calendar


[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

A working time calendar in Dynamics 365 Human Resources shows the days and hours that employees work in your organization. When an employee submits a time-off request, they don't have to worry about holidays and closures.

To streamline time-off requests, configure these items for your organization:

- Working time calendar
- Holidays and closures
- Non-work time

You can add the last two items while you're setting up a working time calendar. You can also configure or update them separately.

## Set up a working time calendar

Set up at least one working time calendar that shows your days and hours of operation. If you have locations in multiple countries and regions, you might want to set up a working time calendar for each area.

1. On the **Organization administration** page, select **Calendars**.
2. Select **New** and enter a name and description for your calendar.
3. Under **Generation options**, select the work days for your organization and enter work times. 
   - To add a holiday or closure, select the **Add** button next to **Holidays and closures**.
   - To add non-work time, like lunches or breaks, select **Add** under **Non-work time** and enter the name and time range.

4. Under **Days**, select **Generate** to generate the days in your calendar. Enter the date range for your calendar and then select **Generate days**.
5. To add work schedules, under **Work schedule**, select **Add** and then enter the times for each work schedule.

## Configure holidays and closures

You can add or change holidays and closures separately from a working time calendar.

1. On the **Organization administration** page, select **Holidays and closures**.
2. Select **New** and enter a name and date for the holiday or closure.

## Configure non-work time

You can add or change non-work times separately from a working time calendar.

1. On the **Organization administration** page, select **Non-work time**.
2. Select **New** and enter a name and time range for the non-work time.

If you've enabled the Leave and absence bank holiday corrections preview feature, Human Resources uses holidays and closure dates to determine the number of days to adjust for employees enrolled in the calendar.

## See also

- [Leave and absence overview](hr-leave-and-absence-overview.md)
- [Configure leave and absence types](hr-leave-and-absence-types.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
