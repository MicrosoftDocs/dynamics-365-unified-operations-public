---
# required metadata

title: Working time calendars
description: This topic describes working time calendars in Dynamics 365 Human Resources as well as how to set up calendars.
author: andreabichsel
manager: AnnBe
ms.date: 09/12/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form:
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Core, Operations, Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2018-07-01
ms.dyn365.ops.version: AX 7.0.0, Talent July 2017 update

---

# Working time calendars

The working time calendar enables you to create a calendar with the hours and days that employees work in your organization. Calendars streamline the time off request process by default in the hours or days. When an employee submits a time off request, they don't have to worry about holidays and closures, which is handled for them through the working time calendar.

## Setting up a working time calendar

Calendars include generation details, the days and hours you want to included, the days of the calendar, working times for those days as well as enrolled employees. 

To set up a calendar, follow these steps:

1. On the **Organization Administration** page, click **Calendars**.

2. On the Action Pane, select **New** and enter a name and description.

3. Choose the work days for your organization and enter work time.

4. Add Holidays and closures by using the **Add** button.

5. Enter the name and description for the holidays and closures, such as US holidays or Bank holidays. Enter the dates for the holidays and closures. Save the Holidays and closures list and close the page.

6. Select the holidays and closures list from the drop-down menu.

7. If your employees have non-work time, such as lunches or breaks, add those as well. Select **Non-work time** and enter the name and time range. Close the page. 

8. Click **Add** to add the non-work time to your calendar.

9. On the **Days** tab, select **Generate** to generate the days in your calendar. Enter the date range for the calendar. The days and working times are generated based on the work days and times defined under the generation options in conjunction with the dates selected.

10. To assign a calendar to employees, select **Assign to employees** in the Action Pane. Select the that employees you would like to assign this calendar to, and then click **Assign**.

Employees aren't required to have calendars assigned. If there is a working time calendar defined, off days are automatically excluded from the request. The amount, in hours or days, defaults to the working times defined in the calendar. If an employee doesn't have a calendar assigned, all days are available for time off and the amount of time off is not the default for the request. 
