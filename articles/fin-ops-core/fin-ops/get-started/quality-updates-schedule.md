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
| Station 1 | Only for opted-in environments |
| Station 2 | Canada Central, Canada East, France Central, India Central, Norway East, Switzerland West |
| Station 3 | France South, India South, Norway West, Switzerland North, South Africa North, Australia East, UK South, UAE North, Japan East, Australia South East, South East Asia |
| Station 4 | East Asia, UK West, Japan West, Brazil South, North Europe, East US, UAE Central |
| Station 5 | West Europe, Central US, West US |
| Station 6 | DoD, Government Community Cloud, China |

> [!IMPORTANT]
> 1. The PQU build for every train is typically published to Lifecycle Services after the change cutoff date that's shown in the high-level PQU train schedule below. In this way, customers can download and self-apply the build as needed, to frontload any testing requirements. 
> 2. Standard performance test (tier-4) sandbox environments, Premium performance test (tier-5) sandbox environments, and production environments will receive PQUs on weekends. If a PQU of production environment, Standard performance test (tier4), or Premium performance test (tier5) sandboxes didn't complete on the scheduled weekend then the operation gets rescheduled to the next weekend.

## High-level PQU train schedule

The following table shows the high-level train schedule. It includes a description of the service update that pertains to the train, the cutoff date after which new changes are no longer accepted, and the development duration for the PQU train.

| PQU release train | Change cutoff date | PQU train duration | Status
|---|---|---|---|
| 10.0.30 PQU-2 | December 16th 2022 | January 2 to January 29 2023 | Completed |
| 10.0.30 PQU-3 | January 13th 2023 | January 30 to February 26 2023 | Completed |
| 10.0.30 PQU-4 | February 24, 2023 | March 6 to April 9, 2023 | Completed |
| 10.0.31 PQU-1 | February 3, 2023 | February 13, 2023 to March 19, 2023| Completed |
| 10.0.31 PQU-2 | March 3, 2023 | March 13, 2023 to April 16, 2023| Completed |
| 10.0.31 PQU-3 | April 14, 2023 | April 24, 2023 to May 28, 2023| Completed |
| 10.0.32 PQU-1 | March 31, 2023 | April 10, 2023 to May 14, 2023| Completed |
| 10.0.32 PQU-2 | April 28, 2023 | May 8, 2023 to June 11, 2023| Completed |
| 10.0.32 PQU-3 | May 26, 2023 | June 5, 2023 to July 9, 2023| In-Progress |
| 10.0.33 PQU-1 | April 28, 2023 | May 8, 2023 to June 11, 2023| Completed |
| 10.0.33 PQU-2 | May 26, 2023 | June 5, 2023 to July 9, 2023| In-Progress |
| 10.0.33 PQU-3 | July 14, 2023 | July 24, 2023 to August 27, 2023| Not Started |
| 10.0.34 PQU-1 | June 23, 2023 | July 3, 2023 to August 6, 2023| Not Started |
| 10.0.34 PQU-2 | July 21, 2023 | July 31, 2023 to September 3, 2023| Not Started |
| 10.0.34 PQU-3 | September 1, 2023 | September 11, 2023 to October 15, 2023| Not Started |
| 10.0.35 PQU-1 | July 28, 2023 | August 7, 2023 to September 10, 2023| Not Started |
| 10.0.35 PQU-2 | August 25, 2023 | September 4, 2023 to October 8, 2023| Not Started |
| 10.0.35 PQU-3 | October 20, 2023 | October 30, 2023 to December 17, 2023| Not Started |
| 10.0.36 PQU-1 | September 29, 2023 | October 9, 2023 to November 12, 2023| Not Started |
| 10.0.36 PQU-2 | October 27, 2023 | November 6, 2023 to December 17, 2023| Not Started |
| 10.0.36 PQU-3 | January 12, 2024 | January 22, 2023 to February 25, 2024| Not Started |
| 10.0.37 PQU-1 | November 3, 2023 | November 13, 2023 to January 7, 2024| Not Started |
| 10.0.37 PQU-2 | December 30, 2023 | Janurary 8, 2024 to February 11, 2024| Not Started |
| 10.0.37 PQU-3 | January 27, 2024 | February 5, 2024 to March 10, 2024| Not Started |
| 10.0.37 PQU-4 | February 23, 2024 | March 4, 2024 to April 7, 2024| Not Started |

> [!Note]
> Only the onboarded productions environments will receive the updates, onboarded environments will receive explicit communication.

### <a name="schedule"></a> Proactive quality update upcoming 10.0.32 Release-3 train schedule

**App version: 10.0.1515.111**

| Stations | Upcoming Sandbox Schedule | Upcoming production Schedule |
|---|---|---|
| Station 1 | June 5 to June 8, 2023 | NA |
| Station 2 | June 12 to June 15, 2023 | June 24 to June 25, 2023 |
| Station 3 | June 13 to June 16, 2023 | June 24 to June 25, 2023 |
| Station 4 | June 19 to June 22, 2023 | July 1 to July 2, 2023 |
| Station 5 | June 26 to June 29, 2023 | July 8 to July 9, 2023 |
| Station 6 | June 27 to June 30, 2023 | July 8 to July 9, 2023 |

[Build Details](quality-updates-build-details-10-0-32.md)

### <a name="schedule"></a> Proactive quality update upcoming 10.0.33 Release-2 train schedule

**App version: 10.0.1549.86**

| Stations | Upcoming Sandbox Schedule | Upcoming production Schedule |
|---|---|---|
| Station 1 | June 5 to June 8, 2023 | NA |
| Station 2 | June 12 to June 15, 2023 | June 24 to June 25, 2023 |
| Station 3 | June 13 to June 16, 2023 | June 24 to June 25, 2023 |
| Station 4 | June 19 to June 22, 2023 | July 1 to July 2, 2023 |
| Station 5 | June 26 to June 29, 2023 | July 8 to July 9, 2023 |
| Station 6 | June 27 to June 30, 2023 | July 8 to July 9, 2023 |

### <a name="schedule"></a> Proactive quality update upcoming 10.0.34 Release-1 train schedule

**App version: 10.0.1591.76**

| Stations | Upcoming Sandbox Schedule | Upcoming production Schedule |
|---|---|---|
| Station 1 | July 3 to July 6, 2023 | NA |
| Station 2 | July 10 to July 13, 2023 | July 22 to July 23, 2023 |
| Station 3 | July 11 to July 14, 2023 | July 22 to July 23, 2023 |
| Station 4 | July 17 to July 20, 2023 | July 29 to July 30, 2023 |
| Station 5 | July 24 to July 27, 2023 | August 5 to August 6, 2023 |
| Station 6 | June 25 to June 28, 2023 | August 5 to August 6, 2023 |

> [!IMPORTANT] 
> At least five days in advance, Microsoft will update the preceding schedule and send a notification for the set of environments that are scheduled to receive these quality updates. The preceding schedule is applicable only to environments that have been notified about an upcoming update. For information on the dark hours for each region, see [What are the planned maintenance windows by region?](../../dev-itpro/deployment/plannedmaintenance-selfservice.md#windows).
>
> For each region group, or *station*, where a quality update is currently scheduled to be rolled out, the schedule shows a range of four days. Quality updates will start with only sandbox environments. Then, as the percentage of successfully deployed sandboxes increases, deployment to production environments will begin with advance notifications to customers.
> 
> Quality updates will always occur in a rolling manner that enables us to target a set of environments per schedule and complete all the sets by the end of the fourth day for a station. However, this doesn't mean that an environment update will span four days. It just means that we can't pre-determine which set of environments will be updated on a given day within the four-day range. All updates will be done during dark hours, with near-zero downtime. Updates will definitively end within the dark-hour window of a given region.

## Additional resources

- [Proactive quality updates overview](quality-updates.md)
- [Proactive quality updates FAQ](quality-updates-faq.md)
