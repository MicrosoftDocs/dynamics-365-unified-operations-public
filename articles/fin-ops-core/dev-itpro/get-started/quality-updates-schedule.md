---
title: Release schedule for proactive quality updates
description: This article provides the release schedule for proactive quality updates (PQUs). 
author: rashmansur
ms.author: rashmim
ms.topic: article
ms.date: 10/23/2023
ms.custom: bap-template
audience: Developer, IT Pro
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

For information about the maintenance windows for each region, see [What are the planned maintenance windows by region?](../deployment/plannedmaintenance-selfservice.md#windows)

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
> 1. The PQU build for every train is typically published to Lifecycle Services after the change cutoff date that's shown in the following high-level PQU train schedule. In this way, customers can download and self-apply the build as needed, to frontload any testing requirements. 
> 2. Standard performance test (tier-4) sandbox environments, Premium performance test (tier-5) sandbox environments, and production environments will receive PQUs on weekends. If a PQU of production environment, Standard performance test (tier4), or Premium performance test (tier5) sandboxes didn't complete on the scheduled weekend then the operation gets rescheduled to the next weekend.

## High-level PQU train schedule

The following table shows the high-level train schedule. It includes a description of the service update that pertains to the train, the cutoff date after which new changes are no longer accepted, and the development duration for the PQU train.

| PQU release train | Change cutoff date | PQU train duration | Status
|---|---|---|---|
| 10.0.35 PQU-2 | August 25, 2023 | September 4, 2023 to October 8, 2023| Completed |
| 10.0.35 PQU-3 | October 20, 2023 | October 30, 2023 to December 17, 2023| Not Started |
| 10.0.36 PQU-1 | September 29, 2023 | October 9, 2023 to November 12, 2023| In-Progress |
| 10.0.36 PQU-2 | October 27, 2023 | November 6, 2023 to December 17, 2023| Not Started |
| 10.0.36 PQU-3 | January 12, 2024 | January 22, 2023 to February 25, 2024| Not Started |
| 10.0.37 PQU-1 | November 3, 2023 | November 13, 2023 to January 7, 2024| Not Started |
| 10.0.37 PQU-2 | December 30, 2023 | January 8, 2024 to February 11, 2024| Not Started |
| 10.0.37 PQU-3 | January 27, 2024 | February 5, 2024 to March 10, 2024| Not Started |
| 10.0.37 PQU-4 | February 23, 2024 | March 4, 2024 to April 7, 2024| Not Started |
| 10.0.38 PQU-1 | February 7, 2024 | February 12, 2024 to March 17, 2024| Not Started |
| 10.0.38 PQU-2 | March 6, 2024 | March 11, 2024 to April 14, 2024| Not Started |
| 10.0.38 PQU-3 | April 3, 2024 | April 8, 2024 to May 12, 2024| Not Started |
| 10.0.38 PQU-4 | May 1, 2024 | May 6, 2024 to June 9, 2024| Not Started |
| 10.0.38 PQU-5 | May 29, 2024 | June 3, 2024 to July 7, 2024| Not Started |
| 10.0.38 PQU-6 | June 26, 2024 | July 1, 2024 to August 4, 2024| Not Started |
| 10.0.38 PQU-7 | July 24, 2024 | July 29, 2024 to September 1, 2024| Not Started |
| 10.0.38 PQU-8 | August 28, 2024 | September 2, 2024 to October 6, 2024| Not Started |
| 10.0.39 PQU-1 | April 10, 2024 | April 15, 2024 to May 19 2024| Not Started |
| 10.0.39 PQU-2 | May 8, 2024 | May 13, 2024 to June 16, 2024| Not Started |
| 10.0.39 PQU-3 | June 5, 2024 | June 10, 2024 to July 14, 2024| Not Started |
| 10.0.39 PQU-4 | July 3, 2024 | July 8, 2024 to August 11, 2024| Not Started |
| 10.0.39 PQU-5 | July 31, 2024 | August 5, 2024 to September 8, 2024| Not Started |
| 10.0.39 PQU-6 | August 28, 2024 | September 2, 2024 to October 6, 2024| Not Started |
| 10.0.39 PQU-7 | September 25, 2024 | September 30, 2024 to November 3, 2024| Not Started |
| 10.0.39 PQU-8 | October 23, 2024 | October 28, 2024 to December 8, 2024| Not Started |
| 10.0.39 PQU-9 | November 27, 2024 | December 4, 2024 to January 19, 2025| Not Started |
| 10.0.40 PQU-1 | July 10, 2024 | July 15, 2024 to August 18, 2024| Not Started |
| 10.0.40 PQU-2 | August 7, 2024 | August 12, 2024 to September 15, 2024| Not Started |
| 10.0.40 PQU-3 | September 4, 2024 | September 9, 2024 to October 13, 2024| Not Started |
| 10.0.40 PQU-4 | October 2, 2024 | October 7, 2024 to November 10, 2024| Not Started |
| 10.0.40 PQU-5 | October 30, 2024 | November 4, 2024 to December 15, 2024| Not Started |
| 10.0.40 PQU-6 | December 4, 2024 | December 9, 2024 to January 19, 2025| Not Started |
| 10.0.40 PQU-7 | January 8, 2025 | January 13, 2025 to February 16, 2025| Not Started |
| 10.0.40 PQU-8 | February 5, 2025 | February 10, 2025 to March 16, 2025| Not Started |
| 10.0.40 PQU-9 | March 5, 2025 | March 10, 2025 to April 13, 2025| Not Started |
| 10.0.41 PQU-1 | October 9, 2024 | October 14, 2024 to November 17, 2024| Not Started |
| 10.0.41 PQU-2 | November 6, 2024 | November 11, 2024 to January 5, 2025| Not Started |
| 10.0.41 PQU-3 | December 31, 2024 | January 6, 2025 to February 9, 2025| Not Started |
| 10.0.41 PQU-4 | January 29, 2025 | February 3, 2025 to March 9, 2025| Not Started |
| 10.0.41 PQU-5 | February 26, 2025 | March 3, 2025 to April 6, 2025| Not Started |
| 10.0.41 PQU-6 | March 26, 2025 | March 31, 2025 to May 4, 2025| Not Started |
| 10.0.41 PQU-7 | April 23, 2025 | April 28, 2025 to June 1, 2025| Not Started |
| 10.0.41 PQU-8 | May 28, 2025 | June 2, 2025 to July 6, 2025| Not Started |
| 10.0.42 PQU-1 | February 12, 2025 | February 17, 2025 to March 23, 2025| Not Started |
| 10.0.42 PQU-2 | March 12, 2025 | March 17, 2025 to April 20, 2025| Not Started |
| 10.0.42 PQU-3 | April 9, 2025 | April 14, 2025 to May 8, 2025| Not Started |
| 10.0.42 PQU-4 | May 7, 2025 | May 12, 2025 to June 15, 2025| Not Started |
| 10.0.42 PQU-5 | June 4, 2025 | June 9, 2025 to July 13, 2025| Not Started |
| 10.0.42 PQU-6 | July 2, 2025 | July 7, 2025 to August 10, 2025| Not Started |
| 10.0.42 PQU-7 | July 30, 2025 | August 4, 2025 to September 7, 2025| Not Started |
| 10.0.42 PQU-8 | August 27, 2025 | September 1, 2025 to October 5, 2025| Not Started |

> [!Note]
> Any new finance and operations apps environment that is provisioned after August 17th, 2023 is automatically signed up to receive PQUs per the schedule as applicable.

### <a name="schedule"></a> Proactive quality update upcoming 10.0.35 Release-3 train schedule

**App version: 10.0.1627.138**

**Platform version: 7.0.6972.170**

| Stations | Upcoming Sandbox Schedule | Upcoming production Schedule |
|---|---|---|
| Station 1 | October 30 to November 2, 2023 | NA |
| Station 2 | November 6 to November 9, 2023 | December 2 to December 3, 2023 |
| Station 3 | November 7 to November 10, 2023 | December 2 to December 3, 2023 |
| Station 4 | November 13 to November 16, 2023 | December 9 to December 10, 2023 |
| Station 5 | November 20 to November 23, 2023 | December 16 to December 17, 2023 |
| Station 6 | November 21 to November 24, 2023 | December 16 to December 17, 2023 |

### <a name="schedule"></a> Proactive quality update upcoming 10.0.36 Release-1 train schedule

**App version: 10.0.1695.68**

**Platform version: 7.0.7036.87**

| Stations | Upcoming Sandbox Schedule | Upcoming production Schedule |
|---|---|---|
| Station 1 | October 9 to October 12, 2023 | NA |
| Station 2 | October 16 to October 19, 2023 | October 28 to October 29, 2023 |
| Station 3 | October 17 to October 20, 2023 | October 28 to October 29, 2023 |
| Station 4 | October 23 to October 26, 2023 | November 4 to November 5, 2023 |
| Station 5 | October 30 to November 2, 2023 | November 11 to November 12, 2023 |
| Station 6 | October 31 to November 3, 2023 | November 11 to November 12, 2023 |

### <a name="schedule"></a> [New] Proactive quality update upcoming 10.0.36 Release-2 train schedule

**App version: 10.0.1695.90**

**Platform version: 7.0.7036.113**

| Stations | Upcoming Sandbox Schedule | Upcoming production Schedule |
|---|---|---|
| Station 1 | November 6 to November 9, 2023 | NA |
| Station 2 | November 13 to November 16, 2023 | December 2 to December 3, 2023 |
| Station 3 | November 14 to November 17, 2023 | December 2 to December 3, 2023 |
| Station 4 | November 20 to November 23, 2023 | December 9 to December 10, 2023 |
| Station 5 | December 4 to December 7, 2023 | December 16 to December 17, 2023 |
| Station 6 | December 5 to December 8, 2023 | December 16 to December 17, 2023 |

> [!IMPORTANT] 
> At least five days in advance, Microsoft updates the preceding schedule and send a notification for the set of environments that are scheduled to receive these quality updates. The preceding schedule is applicable only to environments that have been notified about an upcoming update. For information on the dark hours for each region, see [What are the planned maintenance windows by region?](../deployment/plannedmaintenance-selfservice.md#windows).
>
> For each region group, or *station*, where a quality update is currently scheduled to be rolled out, the schedule shows a range of four days. Quality updates start with only sandbox environments. Then, as the percentage of successfully deployed sandboxes increases, deployment to production environments begins with advance notifications to customers.
> 
> Quality updates always occur in a rolling manner that enables us to target a set of environments per schedule and complete all the sets by the end of the fourth day for a station. However, this doesn't mean that an environment update spans four days. It just means that we can't pre-determine which set of environments is updated on a given day within the four-day range. All updates are done during dark hours, with near-zero downtime. Updates definitively end within the dark-hour window of a given region.

## Additional resources

- [Proactive quality updates overview](quality-updates.md)
- [Proactive quality updates FAQ](quality-updates-faq.md)
