---
title: Register time for workers
description: Learn how to register planned absences for individual workers and groups of workers in Dynamics 365 Human Resources.
author: twheeloc
ms.author: twheeloc
ms.date: 01/24/2024
ms.topic: article
f1_keywords:
- absence
- plan
audience: Application User
ms.search.region: Global
---

# Register time for workers

Supervisors or team leaders calculate time registrations that have been submitted by the workers on their teams. To help make the process of calculating those registrations more efficient, supervisors and team leaders can plan for absences by creating absence registrations in advance.

By registering absences in advance, you can plan for holidays, external training courses, parental leave, and other types of absence registrations that you know about before they actually occur. You can register a planned absence for a group of workers or for an individual worker.

## Register a planned absence for a group of workers

You can create a query and select a group of workers to include in an absence registration. To do so:

1.  Click **Human resources** \> **Periodic** \> **Time and attendance** \> **Create planned absence**.
2.  In the **Create planned absence** page, in the **From date**, **From**, **To date**, and **To** fields, select the period for the absence registration.
3.  In the **Absence job** field, select the type of absence to register.
4.  If you want the absence registration to stop if a worker clocks in before the planned end time, select the **Interrupt** checkbox.
5.  If you want to create an absence registration for each day in the specified period, select the **Compose** checkbox.
6.  Click **Select**.

## Register a planned absence for one worker

1.  Click **Human resources** \> **Common** \> **Workers** \> **Time registration workers**. On the **Action Pane**, on the **Time registration** tab, click **Set up time registration worker** \> **Absence registrations**.
2.  On the **Absence registration** page, in the **Start date/time** and **End date/time** fields, select the period for the absence registration.
3.  In the **Absence group** and **Absence code** fields, select the absence reasons that must be used for this registration.
4.  If you want the absence registration to stop if the worker clocks in before the planned end time, select the **Interrupt** checkbox.
    
> [!NOTE]
> If the **Interrupt** checkbox was selected when the absence registration was created, and the worker clocks in before the end time of the absence registration, the **Interrupted** checkbox is automatically selected at the time of the clock-in.



## See also

[Update time and attendance information](hr-update-time-and-attendance-information.md)

[Time and attendance information](hr-about-time-and-attendance-information.md)

[Work planner and time profiles](hr-about-work-planner-time-profiles.md)
