---
title: Registration for manufacturing execution
description: This article describes key concepts and terms that you need to understand to configure and use manufacturing execution. 
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

The **Route groups** page lets you configure whether a production job should use estimated or actual time when reported on the [production floor execution interface](production-floor-execution-use.md). Use the following procedure to configure a route group:

1. Go to **Production control > Setup > Routes > Route groups**.
1. Either select or create a route group.
1. On the **General** FastTab, set the **Run time** field to one of the following values:
    - *No* - When a job is stopped or completed, a job card journal with the actual time the worker spent on the job is generated on the production order.
    - *Yes* - When a job is started, a route card journal with the estimated time for the operation is generated on the production order.

## Set up operations to utilize either estimated or actual time for cost calculations (preview)

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner-section.md)]

<!-- KFM: Preview until 10.0.41 GA -->

You can choose whether calculations of actual cost per production order should include time adjustments made to actual recorded work times. Adjustments are applied when a supervisor uses the the Time and attendance module to review and edit the recorded work times registered by each worker (for the purpose of recording time and attendance). Adjustments can reflect events such as registration errors or unpaid time off. If you choose to skip time adjustments, then you'll also be able to end production orders without waiting for supervisor approvals. You can set this option using the **Skip time adjustments** setting on the **Production order defaults** page.

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

### Prerequisites

To use the the **Skip time adjustments** option, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.41 or later.
- The feature that is named *Skip time adjustments when calculating actual cost per production order* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

> [!IMPORTANT]
> This feature changes the way automatic route consumption works. When this feature is enabled, route groups set to use estimated production times for calculating actual production order costs won't also include recorded times. When this feature is disabled, both recorded and estimated times are used in cost calculations, which can produce unexpected results.

### Set the Skip time adjustments option

Use the following procedure to configure whether time adjustments should be made to production orders as part of processing workers' daily registrations:

1. Go to **Production control > Setup > Manufacturing execution > Production order defaults**
1. Open the **General** tab.
1. Set the **Skip time adjustments** field to one of the following values:
    - *No* - Adjustments are applied when a supervisor reviews and edits the recorded work times registered by each worker (for the purpose of recording time and attendance).
    - *Yes* - Only consider recorded start and end times. If you choose to skip time adjustments, then you'll also be able to end production orders without waiting for supervisor approvals.

## Manufacturing execution and registration terminology

The following table contains terms that pertain to manufacturing execution and related registration tasks.

| Term | Description |
|--|--|
| Manufacturing execution | A function that is used to register time, material consumption, costs on production jobs, projects, and indirect activities. Registration is done in a manufacturing execution registration client, such as the [production floor execution interface](production-floor-execution-use.md). |
| Job list | The [production floor execution interface](production-floor-execution-use.md) shows workers the list of jobs that they must perform on a specific resource, such as a machine. A worker can register time and item consumption on each job or task in the job list. |
| Job bundling | If a worker starts more than one job at the same time on the [production floor execution interface](production-floor-execution-use.md), this is called job bundling. The time that is spent on bundled jobs can be allocated to the individual jobs in various ways by using allocation keys. |
| Pilot/assistant registrations | A worker can register as an assistant to a resource, and can create a small team where several workers work on the same production jobs. Resources that workers are connected to as assistants are called pilots. Only the pilot resource must make registrations. All assistants automatically get the same registrations. For example, if a machine acts as the pilot, workers who have registered as assistants to that machine can make registrations on the [production floor execution interface](production-floor-execution-use.md), and both the machine and the workers who are connected as assistants will receive the same registrations. |
| Indirect activity | An activity or task that isn't directly related to a production job or a project, such as a department meeting, a cleaning job, or a maintenance job on the shop floor. Workers can make registrations on indirect activities, in the same way that they can register on production jobs and projects. |

## Registrations in manufacturing execution

Workers can make various types of registrations in manufacturing execution for work that is performed on production jobs. Depending on the system setup, workers might also be able to make registrations on project activities and nonproductive tasks, such as breaks, absences, and indirect activities. Here are the registration types:

- **Clock-in/clock-out** (available with time and attendance) – Workers clock in when they arrive at work and clock out when they leave to go home.
- **Register on production jobs** – Workers can make registrations, such as starting a job and reporting feedback for a job, on the production jobs that appear in their job list. Workers can start several jobs at the same time. This is referred to as job bundling.
- **Register on inventory** – Workers can make registrations on materials that are used on the shop floor, but that aren't directly related to production jobs. Examples include grease, lubricants, or other materials that are used to keep machinery running. Registration is performed in an inventory journal.
- **Register on projects** (available with time and attendance) – Workers can make registrations, such as starting and finishing work on the projects or project activities that appear in their job list.
- **Register project fees and project items** (available with time and attendance) – Workers can register fees (expenses) that are associated with a project in a project fee journal, such as mileage and bridge toll. Workers can also register item consumption on projects. This is done in a project item journal.
- **Register as assistant to another worker** – If two or more workers will work together on a production job or a project, a worker can register as an assistant to a machine, or to another worker, who will then act as the pilot. The pilot can select another worker as the pilot, as required.
- **Register absence** (available with time and attendance) – Workers can register time on various absence codes that are set up. Absence can be indicated if a worker arrives late, requires absence during the work day, or leaves earlier than expected according to the standard work time profile.
- **Register breaks** (available with time and attendance) – During the work day, workers can register that they are leaving their workstation to take a break. Several break types can be set up. When a worker returns and logs on again, the system registers that the worker is back, and the break registration stops.
- **Register indirect activities** (available with time and attendance) – Indirect activities are nonproductive activities that workers might engage in during a workday, such as a department meeting, a team meeting, or a maintenance job that is performed on the shop floor. Workers can make registrations on the indirect activities that are set up.
- **Register overtime** (available with time and attendance) – Workers who have been asked to work longer hours can select whether the extra hours should be registered as flextime or overtime.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
