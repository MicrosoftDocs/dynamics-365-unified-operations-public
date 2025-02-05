---
title: Release schedule for proactive quality updates
description: Learn about the release schedule for proactive quality updates (PQUs), including an outline on station-to-region mapping. 
author: rashmansur
ms.author: rashmim
ms.topic: conceptual
ms.date: 02/05/2025
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2022-08-19
ms.dyn365.ops.version: 10.0.29
---

# Release schedule for proactive quality updates

This article provides the release schedule for proactive quality updates (PQUs).

The detailed schedule for each PQU train and its corresponding build app version number is published five days before the start of the PQU train. Five days before the start of release train, Microsoft sends a notification to customers who use the environments that receive the update.

Station 1 is the first release station. It consists of customers who opt in to have their sandbox environments receive the update before all other stations. More details are published after this functionality is made generally available in May 2023.

To determine when your Microsoft Dynamics Lifecycle Service environment is updated, find the region and the station-to-region mapping. Cross-reference the region and station-to-region mapping information with the upcoming PQU train for a service update. For customers that must plan for a PQU ahead of time, there's a high-level schedule that outlines the train schedule for every service update in 2023.

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
> 2. Standard performance test (tier-4) sandbox environments, Premium performance test (tier-5) sandbox environments, and production environments receive PQUs on weekends. If a PQU of production environment, Standard performance test (tier4) sandbox, or Premium performance test (tier5) sandbox didn't complete on the scheduled weekend then the operation gets rescheduled to the next weekend.
> 3. Standard performance test (tier-4) sandbox environments, Premium performance test (tier-5) sandbox environments opted-in for the First release program (station 1) will receive updates on the following weekend of the station 1 schedule.

## High-level PQU train schedule

The following table shows the high-level train schedule. It includes a description of the service update that pertains to the train, the cutoff date after which new changes are no longer accepted, and the development duration for the PQU train.

| PQU release train | Change cutoff date | PQU train duration | Status
|---|---|---|---|
| 10.0.39 PQU-1 | April 10, 2024 | April 15, 2024 to May 19 2024| Completed |
| 10.0.39 PQU-2 | May 8, 2024 | May 13, 2024 to June 16, 2024| Completed |
| 10.0.39 PQU-3 | June 5, 2024 | June 10, 2024 to July 14, 2024| Completed |
| 10.0.39 PQU-4 | July 3, 2024 | July 8, 2024 to August 11, 2024| Completed |
| 10.0.39 PQU-5 | July 31, 2024 | August 5, 2024 to September 8, 2024| Completed |
| 10.0.39 PQU-6 | August 28, 2024 | September 2, 2024 to October 6, 2024| Completed |
| 10.0.39 PQU-7 | September 25, 2024 | September 30, 2024 to November 3, 2024| Completed |
| 10.0.39 PQU-8 | October 23, 2024 | October 28, 2024 to December 15, 2024| Canceled |
| 10.0.39 PQU-9 | November 22, 2024 | December 2, 2024 to January 19, 2025| Completed |
| 10.0.40 PQU-1 | July 10, 2024 | July 15, 2024 to August 18, 2024| Completed |
| 10.0.40 PQU-2 | August 7, 2024 | August 12, 2024 to September 15, 2024| Completed |
| 10.0.40 PQU-3 | September 4, 2024 | September 9, 2024 to October 13, 2024| Completed |
| 10.0.40 PQU-4 | October 2, 2024 | October 7, 2024 to November 10, 2024| Completed |
| 10.0.40 PQU-5 | October 30, 2024 | November 4, 2024 to December 15, 2024| Canceled |
| 10.0.40 PQU-6 | December 4, 2024 | December 9, 2024 to January 19, 2025| Completed |
| 10.0.40 PQU-7 | January 8, 2025 | January 13, 2025 to February 16, 2025| In-Progress |
| 10.0.40 PQU-8 | February 5, 2025 | February 10, 2025 to March 16, 2025| In-Progress |
| 10.0.40 PQU-9 | February 18, 2025 | March 10, 2025 to April 13, 2025| Not Started |
| 10.0.41 PQU-1 | October 9, 2024 | October 14, 2024 to November 17, 2024| Completed |
| 10.0.41 PQU-2 | November 8, 2024 | November 11, 2024 to January 5, 2025| Canceled |
| 10.0.41 PQU-3 | December 31, 2024 | January 6, 2025 to February 9, 2025| In-Progress |
| 10.0.41 PQU-4 | January 29, 2025 | February 3, 2025 to March 9, 2025| In-Progress |
| 10.0.41 PQU-5 | February 26, 2025 | March 3, 2025 to April 6, 2025| Not Started |
| 10.0.41 PQU-6 | March 26, 2025 | March 31, 2025 to May 4, 2025| Not Started |
| 10.0.41 PQU-7 | April 23, 2025 | April 28, 2025 to June 1, 2025| Not Started |
| 10.0.41 PQU-8 | May 23, 2025 | June 2, 2025 to July 6, 2025| Not Started |
| 10.0.42 PQU-1 | February 12, 2025 | February 17, 2025 to March 23, 2025| Not Started |
| 10.0.42 PQU-2 | March 12, 2025 | March 17, 2025 to April 20, 2025| Not Started |
| 10.0.42 PQU-3 | April 9, 2025 | April 14, 2025 to May 8, 2025| Not Started |
| 10.0.42 PQU-4 | May 7, 2025 | May 12, 2025 to June 15, 2025| Not Started |
| 10.0.42 PQU-5 | June 4, 2025 | June 9, 2025 to July 13, 2025| Not Started |
| 10.0.42 PQU-6 | July 2, 2025 | July 7, 2025 to August 10, 2025| Not Started |
| 10.0.42 PQU-7 | July 30, 2025 | August 4, 2025 to September 7, 2025| Not Started |
| 10.0.42 PQU-8 | August 22, 2025 | September 1, 2025 to October 5, 2025| Not Started |
| 10.0.43 PQU-1 | April 9, 2025 | April 14, 2025 to May 18, 2025| Not Started |
| 10.0.43 PQU-2 | May 7, 2025 | May 12, 2025 to June 15, 2025| Not Started |
| 10.0.43 PQU-3 | June 4, 2025 | June 9, 2025 to July 13, 2025| Not Started |
| 10.0.43 PQU-4 | July 2, 2025 | July 7, 2025 to August 10, 2025| Not Started |
| 10.0.43 PQU-5 | July 30, 2025 | August 4, 2025 to September 7, 2025| Not Started |
| 10.0.43 PQU-6 | August 27, 2025 | September 1, 2025 to October 5, 2025| Not Started |
| 10.0.43 PQU-7 | September 24, 2025 | September 29, 2025 to November 2, 2025| Not Started |
| 10.0.43 PQU-8 | October 22, 2025 | October 27, 2025 to December 7, 2025| Not Started |
| 10.0.43 PQU-9 | November 26, 2025 | December 1, 2025 to January 18, 2026| Not Started |
| 10.0.44 PQU-1 | July 9, 2025 | July 14, 2025 to August 17, 2025| Not Started |
| 10.0.44 PQU-2 | August 6, 2025 | August 11, 2025 to September 14, 2025| Not Started |
| 10.0.44 PQU-3 | September 3, 2025 | September 8, 2025 to October 12, 2025| Not Started |
| 10.0.44 PQU-4 | October 1, 2025 | October 6, 2025 to November 9, 2025| Not Started |
| 10.0.44 PQU-5 | October 29, 2025 | November 3, 2025 to January 11, 2026| Not Started |
| 10.0.44 PQU-6 | November 26, 2025 | December 1, 2025 to January 18, 2026| Not Started |
| 10.0.44 PQU-7 | December 31, 2025 | January 5, 2026 to February 8, 2026| Not Started |
| 10.0.44 PQU-8 | January 21, 2026 | January 26, 2026 to February 28, 2026| Not Started |
| 10.0.44 PQU-9 | February 22, 2026 | February 27, 2026 to April 1, 2026| Not Started |
| 10.0.45 PQU-1 | October 8, 2025 | October 13, 2025 to November 16, 2025| Not Started |
| 10.0.45 PQU-2 | November 5, 2025 | November 10, 2025 to December 14, 2025| Not Started |
| 10.0.45 PQU-3 | December 3, 2025 | December 8, 2025 to January 25, 2026| Not Started |
| 10.0.45 PQU-4 | December 31, 2025 | January 5, 2026 to February 8, 2026| Not Started |
| 10.0.45 PQU-5 | January 28, 2026 | February 2, 2026 to March 8, 2026| Not Started |
| 10.0.45 PQU-6 | February 25, 2026 | March 2, 2026 to April 5, 2026| Not Started |
| 10.0.45 PQU-7 | March 25, 2026 | March 30, 2026 to May 3, 2026| Not Started |
| 10.0.45 PQU-8 | April 22, 2026 | April 27, 2026 to May 30, 2026| Not Started |
| 10.0.45 PQU-9 | May 27, 2026 | June 1, 2026 to July 5, 2026| Not Started |

> [!Note]
> Any new finance and operations apps environment that is provisioned after August 17th, 2023 is automatically signed up to receive PQUs per the schedule as applicable.

### <a name="schedule"></a> Proactive quality update upcoming 10.0.40 Release-7 train schedule

**App version: 10.0.1935.200**

**Platform version: 7.0.7279.196**

**Unified Environment Provisioning Application Version: 10.0.40.9**

| Stations | Upcoming Sandbox Schedule | Upcoming production Schedule |
|---|---|---|
| Station 1 | January 13 to January 16, 2025 | NA |
| Station 2 | January 20 to January 23, 2025 | February 1 to February 2, 2025 |
| Station 3 | January 21 to January 25, 2025 | February 1 to February 2, 2025 |
| Station 4 | January 27 to January 30, 2024 | February 8 to February 9, 2025 |
| Station 5 | February 3 to February 6, 2025 | February 15 to February 16, 2025 |
| Station 6 | February 4 to February 7, 2025 | February 15 to February 16, 2025 |

### <a name="schedule"></a> [NEW] Proactive quality update upcoming 10.0.40 Release-8 train schedule

**App version: 10.0.1935.208**

**Platform version: 7.0.7279.202**

**Unified Environment Provisioning Application Version: 10.0.40.10**

| Stations | Upcoming Sandbox Schedule | Upcoming production Schedule |
|---|---|---|
| Station 1 | February 10 to February 13, 2025 | NA |
| Station 2 | February 17 to February 20, 2025 | March 1 to March 2, 2025 |
| Station 3 | February 18 to February 21, 2025 | March 1 to March 2, 2025 |
| Station 4 | February 24 to February 27, 2024 | March 8 to March 9, 2025 |
| Station 5 | March 3 to March 6, 2025 | March 15 to March 16, 2025 |
| Station 6 | March 4 to March 7, 2025 | March 15 to March 16, 2025 |

### <a name="schedule"></a> Proactive quality update upcoming 10.0.41 Release-3 train schedule

**App version: 10.0.2015.145**

**Platform version: 7.0.7367.133**

**Unified Environment Provisioning Application Version: 10.0.41.6**

| Stations | Upcoming Sandbox Schedule | Upcoming production Schedule |
|---|---|---|
| Station 1 | January 6 to January 9, 2024 | NA |
| Station 2 | January 13 to January 16, 2024 | January 25 to January 26, 2025 |
| Station 3 | January 14 to January 27, 2024 | January 25 to January 26, 2025 |
| Station 4 | January 20 to January 23, 2024 | February 1 to February 2, 2025 |
| Station 5 | January 27 to January 30, 2025 | February 8 to February 9, 2025 |
| Station 6 | January 28 to January 31, 2025 | February 8 to February 9, 2025 |

### <a name="schedule"></a> [NEW] Proactive quality update upcoming 10.0.41 Release-4 train schedule

**App version: 10.0.2015.165**

**Platform version: 7.0.7367.145**

**Unified Environment Provisioning Application Version: 10.0.41.7**

| Stations | Upcoming Sandbox Schedule | Upcoming production Schedule |
|---|---|---|
| Station 1 | February 3 to February 6, 2024 | NA |
| Station 2 | February 10 to February 13, 2024 | February 22 to February 23, 2025 |
| Station 3 | February 11 to February 14, 2024 | February 22 to February 23, 2025 |
| Station 4 | February 17 to February 20, 2024 | March 1 to March 2, 2025 |
| Station 5 | February 24 to February 27, 2025 | March 8 to March 9, 2025 |
| Station 6 | February 25 to February 28, 2025 | March 8 to March 9, 2025 |

> [!IMPORTANT] 
> At least five days in advance, Microsoft updates the preceding schedule and send a notification for the set of environments that are scheduled to receive these quality updates. The preceding schedule is applicable only to environments that have been notified about an upcoming update. For information on the dark hours for each region, see [What are the planned maintenance windows by region?](../deployment/plannedmaintenance-selfservice.md#windows).
>
> For each region group, or *station*, where a quality update is currently scheduled to be rolled out, the schedule shows a range of four days. Quality updates start with only sandbox environments. Then, as the percentage of successfully deployed sandboxes increases, deployment to production environments begins with advance notifications to customers.
> 
> Quality updates always occur in a rolling manner that enables us to target a set of environments per schedule and complete all the sets by the end of the fourth day for a station. However, this doesn't mean that an environment update spans four days. It just means that we can't predetermine which set of environments is updated on a given day within the four-day range. All updates are done during dark hours, with near-zero downtime. Updates definitively end within the dark-hour window of a given region.

## More information

- [Proactive quality updates overview](quality-updates.md)
- [Proactive quality updates FAQ](quality-updates-faq.md)
