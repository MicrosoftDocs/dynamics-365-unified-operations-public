---
title: Time and attendance information
description: Learn about the various types of time and attendance registrations and the intended users of such registrations in Dynamics 365 Human Resources.
author: twheeloc
ms.author: twheeloc
ms.reviewer: twheeloc
ms.date: 05/14/2026
ms.topic: article
audience: Application User
ms.search.region: Global
---

# Time and attendance information

Time and attendance features enable you to enter and process time and attendance registrations.

## About time and attendance

Workers can make various types of registrations in **Time and attendance**, such as clock-in, clock-out, job, and absence registrations. The features also include tools that you can use to generate payroll data. The main purpose is to:

- Calculate workers’ work hours based on predefined work time profiles and workers’ registrations
- Manage workers’ work time and absence time
- Generate a payroll basis to make sure that workers are paid correctly

In companies that use **Time and attendance**, workers must make time and attendance registrations. Some companies might only require workers to register clock-in and clock-out. In other companies, workers might be required to register time consumption on, for example, projects, indirect activities, and breaks.

The intended users of **Time and attendance** are as follows:

- Workers who are required to register time and attendance at regular intervals, such as daily, weekly, or bi-weekly.
- Supervisors, managers, and payroll officers who calculate, approve, and transfer worker registrations.  

> [!NOTE]
> If you set up **Time and attendance** to handle attendance registrations and payroll calculations, and use that module together with **Manufacturing execution** features, time and attendance functionality such as registration on projects or project activities, absence codes, indirect activities, overtime, and flex, is also available in **Manufacturing execution**.

## Registrations in Time and attendance

Workers can make various types of registrations in **Time and attendance**:

- **Clock-in and clock-out** - A worker clocks in when arriving at work and clocks out when leaving work.
- **Register on projects** - A worker can make time registrations on projects and project activities.
- **Register project fees and project items** - Workers working on projects can register expenses in a project fee journal, such as mileage and bridge toll. It's also possible to register item consumption on projects. This registration is completed in a project item journal.
- **Register absence** - A worker might be able to register time on various absence codes that the system sets up. The worker can indicate absence if they arrive late, require absence during the work day, or leave earlier than expected according to the work time profile.
- **Register breaks** - During the work day, a worker registers breaks. You can set up several break types. When the worker returns and logs on again, the system registers that the worker is back, and the break registration stops.
- **Register indirect activities** - Indirect activities are nonproductive activities that a worker might engage in during a work day, such as a department meeting, a team meeting, or a task not directly related to a specific project or job. Workers might be able to make registrations on the indirect activities that the system sets up.
- **Register overtime** - Workers can register extra hours as either flextime or overtime.

> [!NOTE]
> Set up workers as time registration workers so they can make registrations in **Time and attendance**.

## See also

[Register time for workers](hr-register-time.md)

[Update time and attendance information](hr-update-time-and-attendance-information.md)
