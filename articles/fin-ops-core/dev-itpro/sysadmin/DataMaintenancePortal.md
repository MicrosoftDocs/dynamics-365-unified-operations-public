---
title: Data maintenance
description: Learn about how to use simple scheduling processes to find and correct data inconsistencies in your environment.
author: RyanCCarlson2
ms.author: rcarlson
ms.topic: article
ms.date: 06/10/2024
ms.custom:
ms.reviewer: johnmichalak 
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2021-03-31
ms.search.form: DataMaintenance
ms.dyn365.ops.version: AX 10.0.18
---

# Data maintenance

[!include[banner](../includes/banner.md)]

Data maintenance enables simple scheduling processes that you can run to find or correct data inconsistencies in your environment.

Incorrect data can adversely affect your day-to-day, monthly, and yearly operations. Inconsistencies and errors that come from incorrect data has the potential to halt major events like year-end activities and can even halt your daily revenue streams and affect your organization's decision-making capabilities.

The *Data Maintenance Portal* is a tool that lets system administrators schedule and run various actions that will have a direct effect on the data or the system. Some actions can be scheduled to continuously look for opportunities to fix issues, and others can be run on demand to enact some change on the system. Currently there are three basic types of actions: direct, scanning, and fixing.

## Types of actions

- *Direct actions* can be run on-demand only, and can run tasks directly. Microsoft Support may use direct actions, which could be as simple as clearing a cache without the need for downtime or as complicated as running a reference scanner to aid the support process.

- *Scanning actions* will search your data, a few times a day, looking for problems in the data. The problems found will be reported to Microsoft. There are a number of system actions that may not yet have an automated fix, but will provide valuable data to Microsoft to improve the health of your data. Microsoft may reach out to you regarding problems found through this method.

- *Fixing actions* runs on the same cadence as a scanning action, but when an opportunity is found, it will schedule a fix to the data. Fixing actions are meant to be data idempotent and may not fix all of the data on the first run. We recommend that a fixing action only fixes a subset of data each time it runs. Over time, the data will reach a clean state without exposing a significant load on the system. This type of action may help facilitate an in-place upgrade of your system.

## Control of actions
To access the Data Maintenance Portal, administrators can go to **System administration > Periodic tasks > Data maintenance**. On this page, administrators can see the list of actions that are available, and the latest status of each action. Important information about the action can be found in the right panel. If the action can be scheduled, there will be a button labeled **Schedule** available at the bottom of the page. All actions can be run on demand, prior to being run by the automated schedule, by selecting the **Run now** button. System actions, defined by Microsoft, cannot be disabled or enabled. 

> [!NOTE]
> The recurrence of data maintenance processes are handled by the process automation framework as background processes. There are two main types of background processes: one for scanning for opportunities and one for running tasks. For more information, see [Process automation framework development](../process-automation/process-automation-framework.md).
