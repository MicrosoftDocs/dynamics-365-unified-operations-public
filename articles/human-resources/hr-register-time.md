---
title: Register time for workers
description: Learn how to register planned absences for individual workers and groups of workers in Dynamics 365 Human Resources.
author: twheeloc
ms.author: twheeloc
ms.date: 06/11/2026
ms.topic: how-to
f1_keywords:
- absence
- plan
audience: Application User
ms.search.region: Global
---

# Register time for workers

Supervisors or team leaders calculate time registrations that workers on their teams submit. To make the process of calculating those registrations more efficient, supervisors and team leaders can plan for absences by creating absence registrations in advance.

By registering absences in advance, you can plan for holidays, external training courses, parental leave, and other types of absence registrations that you know about before they actually occur. You can register a planned absence for a group of workers or for an individual worker.

## Register a planned absence for a group of workers

You can create a query and select a group of workers to include in an absence registration. To do so:

1. Select **Human resources** > **Periodic** > **Time and attendance** > **Create planned absence**.
1. In **Create planned absence**, select the period for the absence registration in the **From date**, **From**, **To date**, and **To** fields.
1. In the **Absence job** field, select the type of absence to register.
1. If you want the absence registration to stop if a worker clocks in before the planned end time, select the **Interrupt** checkbox.
1. If you want to create an absence registration for each day in the specified period, select the **Compose** checkbox.
1. Select **Select**.

## Register a planned absence for one worker

1. Select **Human resources** > **Common** > **Workers** > **Time registration workers**. On the **Action Pane**, on the **Time registration** tab, select **Set up time registration worker** > **Absence registrations**.
2. On the **Absence registration** page, in the **Start date/time** and **End date/time** fields, select the period for the absence registration.
3. In the **Absence group** and **Absence code** fields, select the absence reasons that must be used for this registration.
4. If you want the absence registration to stop if the worker clocks in before the planned end time, select the **Interrupt** checkbox.

> [!NOTE]
> If you select the **Interrupt** checkbox when you create the absence registration, and the worker clocks in before the end time of the absence registration, the system automatically selects the **Interrupted** checkbox at the time of the clock-in.

## See also

[Update time and attendance information](hr-update-time-and-attendance-information.md)

[Time and attendance information](hr-about-time-and-attendance-information.md)

[Work planner and time profiles](hr-about-work-planner-time-profiles.md)
