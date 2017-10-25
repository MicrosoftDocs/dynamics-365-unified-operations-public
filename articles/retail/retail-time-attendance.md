---
# required metadata

title: Retail time and attendance
description: This topic describes the scenarios that are supported for time and attendance management in Microsoft Dynamics 365 for Retail. 
author: aamirallaqaband
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations, Retail
# ms.tgt_pltfrm: 
ms.custom: 62813
ms.assetid: 821994a6-cd29-45a3-a526-ce204064f080
ms.search.region: global
ms.search.industry: Retail
ms.author: aamiral
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update


---

# Retail time and attendance

[!include[banner](includes/banner.md)]


This topic describes the scenarios that are supported for time and attendance management in Microsoft Dynamics 365 for Retail. 

Manage worker setup and scheduling
----------------------------------

### Initial configuration

-   Run the configuration wizard.
-   Register workers as time registration workers.

### Plan worker schedules

-   Apply profiles by using the work planner. For more information, see <https://technet.microsoft.com/en-us/library/aa551234.aspx>.

For information about the configuration steps, see <https://technet.microsoft.com/en-us/library/aa496971.aspx>.

### Retail-specific configuration

-   Enable a functionality profile for Time Clock, for workers that you want to enable time registrations for. Click **POS functionality profiles** &gt; **Functions** &gt; **POS time registrations** &gt; **Enable time registrations**.
-   Configure point of sale (POS) permissions groups to enable the View timeclock entries permission. This permission lets a user view the time clock registrations of other workers in the store (and from any other store that the user is associated with, via the address book). You might want to enable this permission for a manager role but not for a cashier role. Click **POS permission groups** &gt; **View time clock entries**.

## Register time
### Cashier and non-cashier time registrations

-   On POS:
    -   Clock-in operations:
        -   Log on with a non-drawer operation or New shift.
        -   Select a Time Clock operation.
        -   Select a desired operation:
            -   Clock-in
            -   Break for Work
            -   Break for Lunch
            -   Clock-out

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Current state</th>
    <th>Available operations</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Clock-in</td>
    <td><ul>
    <li>Break for Work</li>
    <li>Break for Lunch</li>
    <li>Clock-out</li>
    </ul></td>
    </tr>
    <tr class="even">
    <td>Break for Work</td>
    <td>Clock-in</td>
    </tr>
    <tr class="odd">
    <td>Break for Lunch</td>
    <td>Clock-in</td>
    </tr>
    <tr class="even">
    <td>Clock-out</td>
    <td>Clock-in</td>
    </tr>
    </tbody>
    </table>

    [![TimeClockStates](./media/timeclockstates.png)](./media/timeclockstates.png)
-   View the confirmation message, and validate that the current activity time is correct.
-   Logbook:
    -   Click **Logbook** to view time clock activity.
    -   Use time filters to select different time windows.
    -   If you work at multiple store locations, you see your time registrations from all the stores where you recorded time. You can use the store filter to view time registrations from a selected store.

<!-- -->

-   Different time zones:
    -   If you view time from a different location (for the cashier logbook, or by using **View timeclock entries** for a manager scenario), and that location is in a different time zone, the time records that you see are converted to your local time zone. For example, you are a manager for two stores, one in Arizona and the other in Nevada. A cashier registers a clock-in at 9:00 A.M. in Arizona. At that moment, the time in Nevada is 8:00 A.M. Therefore, if you are in the Nevada store and look at time registration records, the time registration is marked as 8 A.M.

## View worker time registrations
### View worker time registrations, and filter by store or activity type

On POS:

-   Select **View timeclock entries**.
-   You see time clock registration activities from all workers that are assigned to the same stores that you're assigned to.
-   You can use the activity type and store filters to filter on time registrations.

## Process and manage time registrations
A Dynamics 365 for Retail user follows the workflow to calculate, approve, and transfer time registrations to payroll.

### Primary operations

-   Calculate
-   Approve
-   Submit to payroll

### Other common operations

-   Bulk Clock-out
-   Register Absence

For more information about how to process time and attendance registrations, see <https://technet.microsoft.com/en-us/library/aa573180.aspx>.



