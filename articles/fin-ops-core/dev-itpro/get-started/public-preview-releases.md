---
# required metadata

title: Service update availability
description: This article provides information about the different release options.
author: hmahl
ms.date: 09/29/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: johnmichalak
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: hmahl
ms.search.validFrom: 2017-10-31
ms.dyn365.ops.version: Platform update 11

---

# Service update availability

[!include [banner](../includes/banner.md)]

Microsoft is committed to delivering predictable service updates. These service updates are made generally available for self-deployment before Microsoft automatically applies the update. The timing of the release of packages for self-update relative to the timing of production auto-updates varies. To determine self-update and auto-update timing for upcoming releases, use the [Targeted release schedule (dates subject to change)](#targeted-release-schedule-dates-subject-to-change).

Customers can take up to four service updates per year and are required to take a minimum of two service updates per year. Customers can choose to pause one update at a time. Pausing a service update can apply to the designated user acceptance testing (UAT) sandbox, production, or both environments. After the pause window ends, and if the customer hasn't self-updated to a supported service update, Microsoft will auto-apply the latest update based on the configuration  in Dynamics Lifecycle Services. To learn more about how to pause service updates, see [Pause service updates through Lifecycle Services](../../dev-itpro/lifecycle-services/pause-service-updates.md).

> [!NOTE] 
> Service updates are provided four times annually, with auto-updates occurring in February, April, July, and October.

## Targeted release schedule (dates subject to change)

> [!IMPORTANT]
> Beginning in 2024, Microsoft is releasing four service updates annually in February, April, July, and October. There are important changes to preview, update, and servicing durations, and a scheduled update to the preview release build is now standard in every release. See [One Version service updates FAQ](one-version.md) for answers to common questions about how these changes impact the release process.

> [!IMPORTANT]
> Beginning February 19, 2024, the maximum number of consecutive pauses of updates allowed will be reduced from three to one. With the release durations extended, this change maintains the same minimum of two service updates annually. For more information, refer to [One Version service updates FAQ](one-version.md).

> [!IMPORTANT]
> To introduce the new release cadence with the first 2024 service update, some release milestones for 10.0.38 were adjusted. See [One Version service updates FAQ](one-version.md) for details. 

> [!NOTE] 
> A sandbox auto-update takes place seven days before the production update. End of service indicates the date when no new cumulative service updates are provided.

|	Release Version     |    Preview availability   |   Preview update availability   |   Generally available (self-update)   |   Auto-update schedule** production start date   |    End of service	  |
|---------------------|---------------------------|---------------------------------|---------------------------------------|--------------------------------------------------|---------------------|
|  CY25Q4: 10.0.45*   |         July 28, 2025     |     August 8, 2025              |                September 12, 2025     |                              October 3, 2025     |    May 22, 2026	|
|  CY25Q3: 10.0.44    |       April 25, 2025      |     May 2, 2025                 |                      June 6, 2025     |                                 July 4, 2025     |       February 17, 2026	|
|  CY25Q2: 10.0.43*   |      January 27, 2025     |     February 7, 2025            |                    March 14, 2025     |                                April 4, 2025     |   November 21, 2025	|
|  CY25Q1: 10.0.42    |      October 25, 2024     |     November 1, 2024            |                 December 27, 2024     |                             February 1, 2025     |   August 22, 2025	|
|  CY24Q4: 10.0.41*   |         July 29, 2024     |     August 9, 2024              |                September 13, 2024     |                              October 4, 2024     |    May 23, 2025	|
|  CY24Q3: 10.0.40    |        April 26, 2024     |     May 3, 2024                 |                      June 7, 2024     |                                 July 5, 2024     |       February 18, 2025	|
|  CY24Q2: 10.0.39*   |      January 29, 2024     |     February 9, 2024            |                    March 15, 2024     |                                April 5, 2024     |   November 22, 2024	|
|  CY24Q1: 10.0.38    |      October 27, 2023     |     November 3, 2023            |                 December 22, 2023     |                             February 2, 2024     |   August 23, 2024	|
|  10.0.37<br>(The "November" release)  | September 1, 2023  |        N/A           |                  October 20, 2023     |                             November 3, 2023     |      March 15, 2024	|
|  10.0.36\*<br>(The "October" release) | July 31, 2023      |        N/A           |                September 15, 2023     |                           September 29, 2023     |    January 12, 2024	|
|  10.0.35<br>(The "August" release)    | May 26, 2023       |        N/A           |                     July 14, 2023     |                                July 28, 2023     |    October 20, 2023	|
|  10.0.34<br>(The "July" release)      | April 21, 2023     |        N/A           |                     June 16, 2023     |                                June 30, 2023     |  September 15, 2023	|

\* Denotes a major release.
\** As configured in Lifecycle Services Update Settings. See [Configure service updates through Lifecycle Services](../../dev-itpro/lifecycle-services/configure-service-updates.md).
 
> [!NOTE]
> The [Software lifecycle policy](../../dev-itpro/migration-upgrade/versions-update-policy.md) applies to customers enrolled in the First Release program and when the service update is made generally available.

> [!NOTE]
> **Release naming convention: effective beginning with 10.0.38**
> Beginning in 2024, release labels are updated to convey important details about the release more clearly. The first half of the label refers to the calendar year and quarter in which the auto-update production start date is scheduled. The second part is the product version as displayed in Lifecycle Services. An asterisk (\*) at the end of the label indicates a major release. For example: CY24Q2: 10.0.39* is product version 10.0.39 to be made available for auto-update in the second quarter of 2024. It is a major update (the “April” release).
>
> **Legacy release naming convention: for releases prior to and including 10.0.37.**
> For continuity through the transition, release versions prior to 10.0.38 retain the previous naming convention. This pattern includes the product version, an optional asterisk to indicate a major release, and a broadcast month indicator. For example: 10.0.36* (The “October” release). It is important to note that the name of the month given to the release doesn't always indicate when the auto-update may occur. For example, in the table above, the auto-update schedule for the 10.0.36/"October" release in 2023 actually starts on September 29, 2023.
> 
> Previews and Preview updates are available as a deployable package in the Shared Asset Library in Lifecycle Services. For more details, see [One Version service updates FAQ](one-version.md). 

## Service update overview
Service updates are continuous, touchless updates that provide new features and functionality. They eliminate the need to do expensive upgrades every few years. The service updates maintain backward compatibility, which means there's no need to ‘merge your code.' We recommend using tools such as the Regression suite automation tool (RSAT) for regression testing.

You are in control and manage how your organization receives these updates. For example, you can sign up for the First Release program so that your organization receives updates first. You can apply the updates to any of your environments manually (self-update) or remain on the default release schedule and receive the auto-updates when you schedule them using Lifecycle Services.

Service updates contain both application and platform changes that are critical to the service, including regulatory updates. See the [Service updates section](one-version.md#service-updates) of the One Version service updates FAQ for more details.  

## Release processes

The Dynamics 365 team designs and develops each new release. The team validates the new release first, then the finance and operations apps team validates it. Extensive testing is done on various test topologies. A compatibility checker also runs tests to ensure backward compatibility.

All customers have early access to the upcoming service update if they take advantage of the preview. The preview service update is used to validate customizations, learn about new features, and provide feedback to Microsoft. During the preview phase, customers must deploy the service update on a dev/test environment. The preview release can't be used in production. Once released, customers can download the package from the Shared Asset Library in Lifecycle Services. Customers must agree to the program terms at install time. Signing up for access to preview (formerly known as the Preview Early Access Program (PEAP)) is no longer required. For versions 10.0.38 and later, one scheduled update to the preview build will be included as standard with every release.

The First Release program is open to all customers. Customers who join the First Release program are the first, select group of customers to take the service update all the way to production. Microsoft manages the deployment of this service update to a UAT sandbox, and then auto-deploys the update to production seven days later. Customers participating in this program have the additional benefit of having dedicated Microsoft engineers closely monitoring the environments for any issues after updates are applied. To join First Release, see the [First Release Program: Microsoft Dynamics 365 Finance and Operations applications](https://aka.ms/FirstReleaseFnO) form.

The service update is made generally available using the action center in Dynamics Lifecycle Services. When the service update is available, customers can manually apply it to all environments, including production. If the service update hasn't been applied to the designated sandbox or production environment, Microsoft auto-applies the update based on the Update settings for the Lifecycle Services project. To learn more, see [Configure service updates through Lifecycle Services](../../dev-itpro/lifecycle-services/configure-service-updates.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

