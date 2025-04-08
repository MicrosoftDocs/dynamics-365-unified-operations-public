---
title: Time and attendance information
description: Learn about the various types of time and attendance registrations and the intended users of such registrations in Dynamics 365 Human Resources.
author: twheeloc
ms.author: twheeloc
ms.reviewer: twheeloc
ms.date: 01/24/2024
ms.topic: article
audience: Application User
ms.search.region: Global
---

# Time and attendance information

**Time and attendance** features enable you to enter and to process time and attendance registrations.

## About time and attendance

Workers can make various types of registrations in **Time and attendance**, for example, clock-in, clock-out, job, and absence registrations. Also included are features that you can use to generate payroll data. The main purpose is to:

  - Calculate workers’ work hours based on predefined work time profiles and workers’ registrations
  - Manage workers’ work time and absence time
  - Generate a payroll basis to make sure that workers are paid correctly

In companies that use **Time and attendance**, workers must make time and attendance registrations. Some companies may only require workers to register clock-in and clock-out. In other companies, workers may be required to register time consumption on, for example, projects, indirect activities, and breaks.

The intended users of **Time and attendance** are as follows:

  - Workers who are required to register time and attendance at regular intervals, for example daily, weekly, or bi-weekly.
  - Supervisors, managers, and payroll officers who calculate, approve and transfer worker registrations.  

> [!NOTE]
> If **Time and attendance** is set up to handle attendance registrations and payroll calculations, and that module is used together with **Manufacturing execution** features, time and attendance functionality such as registration on projects or project activities, absence codes, indirect activities, overtime, and flex, will also be available in **Manufacturing execution**.

## Registrations in Time and attendance

Workers can make various types of registrations in **Time and attendance**:

  - **Clock-in and clock-out** - A worker clocks in when arriving at work and clocks out when leaving work.
  - **Register on projects** - A worker can make time registrations on projects and project activities.
  - **Register project fees and project items** - Workers working on projects can register expenses in a project fee journal, for example mileage and bridge toll. It's also possible to register item consumption on projects. This is completed in a project item journal.
  - **Register absence** - A worker may be able to register time on various absence codes that are set up in the system. It's possible to indicate absence if the worker arrives late, requires absence during the work day, or leaves earlier than expected according to the work time profile.
  - **Register breaks** - During the work day, a worker register breaks. Several break types can be set up. When the worker returns and logs on again, the system registers that the worker is back, and the break registration stops.
  - **Register indirect activities** - Indirect activities are non-productive activities that a worker may engage in during a work day, for example, a department meeting, a team meeting, or a task not directly related to a specific project or job. Workers may be able to make registrations on the indirect activities that are set up in the system.
  - **Register overtime** - Workers can register extra hours as either flextime or overtime.


> [!NOTE]
> Workers must be set up as time registration workers to be able to make registrations in **Time and attendance**.

## See also

[Register time for workers](hr-register-time.md)

[Update time and attendance information](hr-update-time-and-attendance-information.md)
