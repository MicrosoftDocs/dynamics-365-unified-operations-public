---
title: Data maintenance
description: Learn about how to use simple scheduling processes to find and correct data inconsistencies in your environment.
author: twheeloc
ms.author: twheeloc
ms.topic: article
ms.date: 04/09/2026
ms.custom:
ms.reviewer: twheeloc 
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2021-03-31
ms.search.form: DataMaintenance
ms.dyn365.ops.version: AX 10.0.18
---

# Data maintenance

[!include[banner](../includes/banner.md)]

Data maintenance enables simple scheduling processes that you can run to find or correct data inconsistencies in your environment.

Incorrect data can adversely affect your day-to-day, monthly, and yearly operations. Inconsistencies and errors that come from incorrect data can halt major events like year-end activities. They can even halt your daily revenue streams and affect your organization's decision-making capabilities.

System administrators use the **Data maintenance portal** to schedule and run various actions that directly affect the data or the system. Some actions continuously look for opportunities to fix issues, and others run on demand to enact some change on the system. Currently, there are three basic types of actions: direct, scanning, and fixing.

## Types of actions

- Direct - These actions run on demand only. They run tasks directly. Microsoft Support might use direct actions. They can be as simple as clearing a cache without the need for downtime or as complicated as running a reference scanner to aid the support process.

- Scanning - These actions search your data a few times a day, looking for problems in the data. The problems found are reported to Microsoft. A number of system actions might not yet have an automated fix but provide valuable data to Microsoft to improve the health of your data. Microsoft might reach out to you regarding problems found through this method.

- Fixing - These actions run on the same cadence as a scanning action. When an opportunity is found, it schedules a fix to the data. Fixing actions are data idempotent and might not fix all of the data on the first run. Fixing actions only fix a subset of data each time they run. Over time, the data reaches a clean state without exposing a significant load on the system. This type of action might help facilitate an in-place upgrade of your system.

### Action control

To access the **Data maintenance portal**, follow these steps:

1. Administrators - go to **System administration > Periodic tasks > Data maintenance**.
1. On this page, administrators can see the list of available actions and the latest status of each action.
1. Important information about the action appears in the right panel. If you can schedule the action, a **Schedule** button appears at the bottom of the page. You can run all actions on demand by selecting the **Run now** button. You can't disable or enable system actions defined by Microsoft.

> [!NOTE]
> The process automation framework handles the recurrence of data maintenance processes as background processes. Two main types of background processes exist: one for scanning for opportunities and one for running tasks. For more information, see [Process automation framework development](/dynamics365/fin-ops-core/dev-itpro/process-automation/process-automation-framework).

## Pause data maintenance actions when in maintenance mode

Data maintenance jobs can interfere with schema-changing operations that you perform in maintenance mode. These operations include deploying new packages, servicing updates, version upgrades, license configuration key changes, country/region-specific key changes, and financial dimension activation. If data maintenance jobs run during these operations, they block tables and cause timeouts or failures.

To prevent interference, follow these steps:

1. Go to **System administration** > **Setup** > **Process automations** and select the **Background processes** tab.
1. Select **Data maintenance job to find opportunities** and select **Edit**. Set a sleep period to prevent the job from running while you're in maintenance mode.
1. Repeat the preceding step for **Data maintenance job to run fixes**.
1. Go to **System administration** > **Inquiries** > **Batch jobs** and cancel any currently running data maintenance jobs.
1. Use maintenance mode to perform the schema change operation (for example, activate financial dimensions).
1. After the operation completes, return to **Process automations** and remove the sleep period so data maintenance resumes normally.
