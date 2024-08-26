---
title: Registration for manufacturing execution
description: Learn about key concepts and terms that you need to understand to configure and use manufacturing execution with a table defining various terms. 
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: JmgRegistration
ms.topic: how-to
ms.date: 07/29/2024
ms.custom: 
  - bap-template
---

# Registration for manufacturing execution

[!include [banner](../includes/banner.md)]

This article describes key concepts and terms that you need to understand to configure and use manufacturing execution.

Manufacturing execution is intended to be used primarily by manufacturing companies. Workers can register time and item consumption on production jobs by using the [production floor execution interface](production-floor-execution-use.md). All registrations are approved and are later transferred to the relevant modules. Continuous approval and transfer of registrations lets managers easily track actual costs on production orders.

## Set up operations to use cost for estimated or actual time

On the **Route groups** page, you can configure whether a production job uses estimated or actual time when it's reported in the [production floor execution interface](production-floor-execution-use.md).

Follow these steps to configure a route group.

1. Go to **Production control** \> **Setup** \> **Routes** \> **Route groups**.
1. Either select or create a route group.
1. On the **General** FastTab, set the **Run time** option to one of the following values:

    - *No* – When a job is stopped or completed, generate a job card journal on the production order. This journal has the actual time that the worker spent on the job.
    - *Yes* – When a job is started, generate a route card journal on the production order. This journal has the estimated time for the operation.

## Set up operations to use either estimated or actual time for cost calculations (preview)

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner-section.md)]

<!-- KFM: Preview until 10.0.41 GA -->

You can use the **Skip time adjustments** option on the **Production order defaults** page to specify whether calculations of actual cost per production order include time adjustments that are made to actual recorded work times. Adjustments are applied when a supervisor uses the **Time and attendance** module to review and edit the recorded work times that each worker registers to record time and attendance. Adjustments can reflect events such as registration errors or unpaid time off. If you skip time adjustments, you can end production orders without waiting for supervisor approvals.

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

### Prerequisites

Before you can use the **Skip time adjustments** option, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.41 or later.
- The feature that is named *Skip time adjustments when calculating actual cost per production order* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

> [!IMPORTANT]
> This feature changes the way that automatic route consumption works.
>
> - When the feature is enabled, route groups that are set up to use estimated production times to calculate actual production order costs don't also include recorded times.
> - When the feature is disabled, both recorded and estimated times are used in cost calculations. This behavior can produce unexpected results.

### Set the Skip time adjustments option

Follow these steps to configure whether time adjustments are made to production orders as part of the processing of workers' daily registrations.

1. Go to **Production control** \> **Setup** \> **Manufacturing execution** \> **Production order defaults**.
1. On the **General** tab, set the **Skip time adjustments** option to one of the following values:

    - *No* – Apply adjustments when a supervisor reviews and edits the recorded work times that each worker registers to record time and attendance.
    - *Yes* – Consider only recorded start and end times. If you skip time adjustments, you can end production orders without waiting for supervisor approvals.

## Manufacturing execution and registration terminology

The following table defines terms that pertain to manufacturing execution and related registration tasks.

| Term | Definition |
|---|---|
| Manufacturing execution | A function that is used to register time, material consumption, and costs on production jobs, projects, and indirect activities. Registration is done in a manufacturing execution registration client, such as the [production floor execution interface](production-floor-execution-use.md). |
| Job list | The [production floor execution interface](production-floor-execution-use.md) shows workers the list of jobs that they must perform on a specific resource, such as a machine. A worker can register time and item consumption on each job or task on the job list. |
| Job bundling | An approach where a worker starts more than one job at the same time in the [production floor execution interface](production-floor-execution-use.md). The time that a worker spends on bundled jobs can be allocated to the individual jobs in various ways by using allocation keys. |
| Pilot/assistant registrations | A worker can register as an assistant to a resource, and can also create a small team where several workers work on the same production jobs. Resources that workers are connected to as assistants are known as *pilots*. Only the pilot resource must make registrations. All assistants then automatically get the same registrations. For example, if a machine acts as the pilot, workers who are registered as assistants to that machine can make registrations in the [production floor execution interface](production-floor-execution-use.md). In this case, both the machine and the workers who are connected as assistants receive the same registrations. |
| Indirect activity | An activity or task that isn't directly related to a production job or a project. Examples include a department meeting, a cleaning job, and a maintenance job on the shop floor. Workers can make registrations on indirect activities in the same way that they make registrations on production jobs and projects. |

## Registrations in manufacturing execution

Workers can make various types of registrations in manufacturing execution for work that is performed on production jobs. Depending on the system setup, workers might also be able to make registrations on project activities and nonproductive tasks, such as breaks, absences, and indirect activities. The following list describes the registration types:

- **Clock-in/clock-out** (available with time and attendance) – Workers clock in when they arrive at work, and they clock out when they leave to go home.
- **Register on production jobs** – Workers can make registrations on the production jobs that appear on their job list. Examples of these registrations include starting a job and reporting feedback for a job. Workers can start several jobs at the same time. This approach is known as job bundling.
- **Register on inventory** – Workers can make registrations on materials that are used on the shop floor, but that aren't directly related to production jobs. Examples of these materials include grease, lubricants, and other materials that are used to keep machinery running. Registration is done in an inventory journal.
- **Register on projects** (available with time and attendance) – Workers can make registrations on the projects or project activities that appear on their job list. Examples of these registrations include starting work and finishing work.
- **Register project fees and project items** (available with time and attendance) – Workers can register fees (expenses) that are associated with a project in a project fee journal. Examples of these fees include mileage and a bridge toll. Workers can also register item consumption on projects. This registration is done in a project item journal.
- **Register as assistant to another worker** – If two or more workers will work together on a production job or a project, a worker can register as an assistant to a machine or another worker. That machine or other worker acts as the pilot. The pilot can select another worker as the pilot, as required.
- **Register absence** (available with time and attendance) – Workers can register time on various absence codes that are set up. Absence can be indicated if a worker arrives late, requires absence during the workday, or leaves earlier than expected according to the standard work time profile.
- **Register breaks** (available with time and attendance) – During the workday, workers can register that they are leaving their workstation to take a break. Several break types can be set up. When a worker returns and signs in again, the system registers that the worker is back, and the break registration stops.
- **Register indirect activities** (available with time and attendance) – Indirect activities are nonproductive activities that workers might engage in during a workday. Examples include a department meeting, a team meeting, and a maintenance job that is performed on the shop floor. Workers can make registrations on the indirect activities that are set up.
- **Register overtime** (available with time and attendance) – Workers who are asked to work longer hours can select whether the extra hours should be registered as flextime or overtime.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
