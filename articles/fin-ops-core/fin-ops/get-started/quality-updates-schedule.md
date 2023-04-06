---
title: Release schedule for proactive quality updates
description: This article provides the release schedule for proactive quality updates (PQUs). 
author: rashmansur
ms.author: rashmim
ms.topic: article
ms.date: 04/05/2023
ms.custom: bap-template
audience: Application User, Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2022-08-19
ms.search.form:
ms.dyn365.ops.version: 10.0.29

---

# Release schedule for proactive quality updates

This article provides the release schedule for proactive quality updates (PQUs).

The schedule for each PQU train and its corresponding build app version number is published seven days before the start of the PQU train. Five days before a PQU is applied, Microsoft sends a notification to customers who use the environments that will receive the update.

Station 1 is the first release station. It consists of customers who opt in to have their sandbox environments receive the update before all other stations. More details will be published after this functionality is made generally available in May 2023.

To determine when your Microsoft Dynamics Lifecycle Service environment will be updated, find the region and the station-to-region mapping, and cross-reference that information with the upcoming PQU train for a service update. For customers that must plan for a PQU ahead of time, there's a high-level schedule that outlines the train schedule for every service update in 2023.

For information about the maintenance windows for each region, see [What are the planned maintenance windows by region?](../../dev-itpro/deployment/plannedmaintenance-selfservice.md#windows)

## Station-to-region mapping

| Station | Regions |
|---|---|
| Station 1 | To be determined later |
| Station 2 | Canada Central, Canada East, France Central, India Central, Norway East, Switzerland West |
| Station 3 | France South, India South, Norway West, Switzerland North, South Africa North, Australia East, UK South, UAE North, Japan East, Australia South East, South East Asia |
| Station 4 | East Asia, UK West, Japan West, Brazil South, North Europe, East US, UAE Central |
| Station 5 | West Europe, Central US, West US |
| Station 6 | DoD, Government Community Cloud, China |

> [!IMPORTANT]
> The PQU build for every train is typically published to Lifecycle Services on the same day or the day after the change cutoff date that's shown in the high-level PQU train schedule. In this way, customers can download and self-apply the build as needed, to frontload any testing requirements. Standard performance test (tier-4) sandbox environments, Premium performance test (tier-5) sandbox environments, and production environments will receive PQUs on weekends. If a PQU of production environment, Standard performance test (tier4), or Premium performance test (tier5) sandboxes didn't complete on the scheduled weekend then the operation gets rescheduled to the next weekend.

## PQU 10.0.30 PQU-3 schedule

The following table shows the schedule for the upcoming PQU deployment.

**App version:** 10.0.1362.124

| Station | Upcoming sandbox schedule | Upcoming production schedule |
|---|---|---|
| Station 1 | Not available | Not available |
| Station 2 | January 30 to February 2, 2023 | February 11 to February 12, 2023 |
| Station 3 | January 31 to February 3, 2023 | February 11 to February 12, 2023 |
| Station 4 | February 6 to February 9, 2023 | February 18 to February 19, 2023 |
| Station 5 | February 13 to February 16, 2023 | February 25 to February 26, 2023 |
| Station 6 | Not available | Not available |

## High-level PQU train schedule

The following table shows the high-level train schedule. It includes a description of the service update that pertains to the train, the cutoff date after which new changes are no longer accepted, and the development duration for the PQU train.

| PQU release train | Change cutoff date | PQU train duration |
|---|---|---|
| 10.0.30 PQU-4 | February 24, 2023 | March 6 to April 8, 2023 |
| 10.0.31 PQU-1 | February 3, 2023 | February 13 to March 18, 2023 |
| 10.0.31 PQU-2 | March 3, 2023 | March 13 to April 15, 2023 |
| 10.0.31 PQU-3 | April 14, 2023 | April 24 to May 27, 2023 |
| 10.0.32 PQU-1 | March 31, 2023 | April 10 to May 13, 2023 |
| 10.0.32 PQU-2 | April 28, 2023 | May 8 to June 10, 2023 |
| 10.0.32 PQU-3 | May 26, 2023 | June 5 to July 8, 2023 |
| 10.0.33 PQU-1 | April 28, 2023 | May 8 to June 10, 2023 |
| 10.0.33 PQU-2 | May 26, 2023 | June 5 to July 8, 2023 |
| 10.0.33 PQU-3 | July 14, 2023 | July 24 to August 26, 2023 |
| 10.0.34 PQU-1 | June 23, 2023 | July 3 to August 5, 2023 |
| 10.0.34 PQU-2 | July 21, 2023 | July 31 to September 2, 2023 |
| 10.0.34 PQU-3 | September 1, 2023 | September 11 to October 14, 2023 |
| 10.0.35 PQU-1 | July 28, 2023 | August 7 to September 9, 2023 |
| 10.0.35 PQU-2 | August 25, 2023 | September 4 to October 7, 2023 |
| 10.0.35 PQU-3 | October 20, 2023 | October 30 to December 16, 2023 |
| 10.0.36 PQU-1 | September 29, 2023 | October 9 to November 11, 2023 |
| 10.0.36 PQU-2 | October 27, 2023 | November 6 to December 16, 2023 |
| 10.0.36 PQU-3 | January 12, 2024 | January 22, 2023, to February 24, 2024 |
| 10.0.37 PQU-1 | November 3, 2023 | November 13, 2023, to January 6, 2024 |
| 10.0.37 PQU-2 | December 30, 2023 | January 8 to February 10, 2024 |
| 10.0.37 PQU-3 | January 27, 2024 | February 5 to March 9, 2024 |
| 10.0.37 PQU-4 | February 23, 2024 | March 4 to April 6, 2024 |
