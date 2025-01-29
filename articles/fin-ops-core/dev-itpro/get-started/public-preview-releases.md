---
title: Service update availability
description: Learn about service update availability and the different release options, including an overview on targeted release schedules.
author: hmahl
ms.author: hmahl
ms.topic: article
ms.date: 11/04/2024
ms.custom: evergreen
ms.reviewer: johnmichalak
audience: IT Pro 
ms.search.region: Global
ms.search.validFrom: 2017-10-31
ms.search.form:
ms.dyn365.ops.version: Platform update 11
---

# Service update availability

[!include [banner](../includes/banner.md)]

Microsoft is committed to delivering predictable service updates. These service updates are made generally available for self-deployment before Microsoft automatically applies them. The timing of the package release for self-update relative to the production autoupdates varies. **Starting April 2024, we are introducing more flexibility in scheduling updates.** Customers can select an autoupdate window of their choice. With the 10.0.39 release, customers can choose from two autoupdate windows that are four weeks apart for each service update. Organizations can select the update window that better accommodates their validation process and operational schedules. To determine the timing of self-update and autoupdates for upcoming releases, including the second autoupdate window see, [Targeted release schedule (dates subject to change)](#targeted-release-schedule-dates-subject-to-change). To learn more about twice autoupdate window options, see [One Version service updates FAQ](../../dev-itpro/get-started/one-version.md).

Customers can take up to four service updates per year and are required to take a minimum of two per year. Customers can choose to pause one update at a time. A pause of a service update can apply to the designated user acceptance testing (UAT) sandbox environment, the production environment, or both environments. After the pause window ends, if the customer hasn't self-updated to a supported service update, Microsoft automatically applies the latest update, based on the configuration in Microsoft Dynamics Lifecycle Services. To learn more about how to pause service updates, see [Pause service updates through Lifecycle Services](../../dev-itpro/lifecycle-services/pause-service-updates.md).

> [!NOTE]
> Service updates are provided four times annually. autoupdates occur in February, April, July, and October.

## Targeted release schedule (dates subject to change)

> [!IMPORTANT]
> Beginning in 2024, Microsoft is releasing four service updates annually, in February, April, July, and October. There are important changes to preview, update, and servicing durations, and a scheduled update to the preview release build is now standard in every release. For answers to common questions about how these changes affect the release process, see [One Version service updates FAQ](one-version.md).
>
> As of February 19, 2024, the maximum number of consecutive updates that can be paused is being reduced from three to one. However, because release durations are being extended, the same minimum of two service updates per year is maintained. For more information, see [One Version service updates FAQ](one-version.md).
>
> To enable the new release cadence to be introduced with the first 2024 service update, some release milestones for 10.0.38 were adjusted. For more information, see [One Version service updates FAQ](one-version.md).

> [!NOTE]
> A sandbox autoupdate occurs seven days before the production update.

In the following table:

- An asterisk (\*) in the "Release version" column denotes a major release.
- The "autoupdate schedule production start date" column refers to the autoupdate schedule that's configured in the update settings in Lifecycle Services. See [Configure service updates through Lifecycle Services](../../dev-itpro/lifecycle-services/configure-service-updates.md).
- The "End of service" column indicates the date when no new cumulative service updates are provided.

| Release version | Preview availability | Preview latest possible update| General availability (self-update) | First autoupdate schedule for production start date | Second autoupdate schedule for production start date |End of service |
|---|---|---|---|---|---|---|
| CY25Q4: 10.0.45\* | July 28, 2025 | August 8, 2025 | September 12, 2025 | October 3, 2025 |  October 31, 2025 |May 22, 2026 |
| CY25Q3: 10.0.44 | April 25, 2025 | May 2, 2025 | June 6, 2025 | July 4, 2025 | August 1, 2025 | February 17, 2026 |
| CY25Q2: 10.0.43\* | January 27, 2025 | February 7, 2025 | March 14, 2025 | April 4, 2025 | May 2, 2025 |November 21, 2025 |
| CY25Q1: 10.0.42 | October 25, 2024 | November 1, 2024 | December 27, 2024 | February 1, 2025 | March 7, 2025 |August 22, 2025 |
| CY24Q4: 10.0.41\* | July 29, 2024 | August 9, 2024 | September 17, 2024 | October 4, 2024 | Nov 1, 2024 | May 23, 2025 |
| CY24Q3: 10.0.40 | April 26, 2024 | May 3, 2024 | June 7, 2024 | July 5, 2024 | August 2, 2024 | February 18, 2025 |
| CY24Q2: 10.0.39\* | January 29, 2024 | February 9, 2024 | March 15, 2024 | April 5, 2024 | May 3, 2024 | November 22, 2024 |
| CY24Q1: 10.0.38 | October 27, 2023 | November 3, 2023 | January 12, 2024 | February 2, 2024 | Not applicable | August 23, 2024 |
| 10.0.37<br>(The "November" release) | September 1, 2023 | Not applicable | October 20, 2023 | November 3, 2023 | Not applicable | March 15, 2024 |
| 10.0.36\*<br>(The "October" release) | July 31, 2023 | Not applicable | September 15, 2023 | September 29, 2023 | Not applicable | January 12, 2024 |
| 10.0.35<br>(The "August" release) | May 26, 2023 | Not applicable | July 14, 2023 | July 28, 2023 | Not applicable | October 20, 2023 |
| 10.0.34<br>(The "July" release) | April 21, 2023 | Not applicable | June 16, 2023 | June 30, 2023 | Not applicable | September 15, 2023 |
 
> [!NOTE]
> The [Software lifecycle policy](../../dev-itpro/migration-upgrade/versions-update-policy.md) applies to customers who are enrolled in the First Release program and to the date when the service update is made generally available.
>
> **Release naming convention as of the 10.0.38 release**
>
> Beginning in 2024, release labels are updated to more clearly convey important details about the release. The first half of the label refers to the calendar year and quarter when the autoupdate production start date is scheduled. The second part is the product version as it appears in Lifecycle Services. An asterisk (\*) at the end of the label indicates a major release. For example: **CY24Q2: 10.0.39\*** is product version 10.0.39 that's made available for autoupdate in the second quarter of 2024. It's a major update (the "April" release).
>
> **Legacy release naming convention (for the 10.0.37 release and earlier)**
>
> For continuity during the transition, release versions before 10.0.38 retain the previous naming convention. This pattern includes the product version, an optional asterisk to indicate a major release, and a broadcast month indicator. An example is **10.0.36\*** (the "October" release). It's important to note that the name of the month that's given to the release doesn't always indicate when the autoupdate might occur. For example, in the preceding table, the autoupdate schedule for the 10.0.36 ("October") release in 2023 actually starts on September 29, 2023.
>
> Previews and preview updates are available as a deployable package in the Shared asset library in Lifecycle Services. For more information, see [One Version service updates FAQ](one-version.md).

## Service update overview

Service updates are continuous, touchless updates that provide new features and functionality. They eliminate the need to do expensive upgrades every few years. Because service updates maintain backward compatibility, there's no need to "merge your code." We recommend that you use tools such as the Regression suite automation tool (RSAT) for regression testing.

You're in control and manage how your organization receives these updates. For example, you can sign up for the First Release program so that your organization receives updates first. You can manually apply the updates to any of your environments (self-update). Alternatively, you can remain on the default release schedule and receive the autoupdates when you schedule them by using Lifecycle Services.

Service updates contain both application changes and platform changes that are critical to the service, including regulatory updates. For more information, see [Service updates](one-version.md#service-updates).

## Release processes

The Dynamics 365 team designs and develops each new release. It validates the new release first, and then the finance and operations apps team validates it. Extensive testing is done on various test topologies. A compatibility checker also runs tests to ensure backward compatibility.

All customers who take advantage of the preview have early access to the upcoming service update. The preview service update is used to validate customizations, learn about new features, and provide feedback to Microsoft. During the preview phase, customers must deploy the service update in a development/test environment. The preview release can't be used in production. After release, customers can download the package from the Shared asset library in Lifecycle Services. Customers must agree to the program terms at the time of installation. Sign-up for access to preview packages (formerly known as the Preview Early Access Program \[PEAP\]) is no longer required. For version 10.0.38 and later, one scheduled update to the preview build is included as standard with every release.

The First Release program is open to all customers. Customers who join it are the first, select group of customers to take the service update all the way to production. Microsoft manages the deployment of this service update to a UAT sandbox environment and then auto-deploys the update to production seven days later. Customers who participate in this program gain the benefit of having dedicated Microsoft engineers closely monitor the environments for any issues after updates are applied. To join First Release, fill in the [First Release Program: Microsoft Dynamics 365 Finance and Operations applications](https://aka.ms/FirstReleaseFnO) form. The First Release build, in most releases, is identical to the build that is promoted to the GA build. It's important to understand that in some situations when critical issues that are impossible to hotfix, or are discovered during the First Release period, Microsoft can declare a new First Release build and restart the First Release sandbox and production environment updates. In these cases, First Release customers are informed before the restart through Lifecycle Services. But it isn't possible to pause these updates.

The service update is made generally available through the Action Center in Lifecycle Services. When the service update is available, customers can manually apply it to all environments, including production. If the service update isn't applied to the designated sandbox or production environment, Microsoft automatically applies it, based on the update settings for the Lifecycle Services project. To learn more, see [Configure service updates through Lifecycle Services](../../dev-itpro/lifecycle-services/configure-service-updates.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
