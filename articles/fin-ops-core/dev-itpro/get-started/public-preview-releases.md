---
title: Service update availability
description: Learn about service update availability and the different release options, including an overview on targeted release schedules.
author: hmahl
ms.author: kschaff
ms.topic: article
ms.date: 08/25/2025
ms.update-cycle: 1095-days
ms.custom: evergreen
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2017-10-31
ms.dyn365.ops.version: Platform update 11
---

# Service update availability

[!include [banner](../includes/banner.md)]

Microsoft is committed to delivering predictable service updates. These service updates are made generally available for self-deployment before Microsoft automatically applies them. The timing of the package release for self-update relative to the production autoupdates varies. Customers can choose from two autoupdate windows that are four weeks apart for each service update. Organizations can select the update window that better accommodates their validation process and operational schedules. To determine the timing of self-update and autoupdates for upcoming releases, including the second autoupdate window see, [Targeted release schedule (dates subject to change)](#targeted-release-schedule-dates-subject-to-change). To learn more about twice autoupdate window options, see [One Version service updates FAQ](../../dev-itpro/get-started/one-version.md).

Customers can take up to four service updates per year and are required to take a minimum of two per year. Customers can choose to pause one update at a time. A pause of a service update can apply to the designated user acceptance testing (UAT) sandbox environment, the production environment, or both environments. After the pause window ends, if the customer hasn't self-updated to a supported service update, Microsoft automatically applies the latest update, based on the configuration in Microsoft Dynamics Lifecycle Services. To learn more about how to pause service updates, see [Pause service updates through Lifecycle Services](../../dev-itpro/lifecycle-services/pause-service-updates.md).

> [!NOTE]
> Service updates are provided four times annually. Autoupdates occur in February, April, July, and October.

## Targeted release schedule (dates subject to change)

> [!IMPORTANT]
> Microsoft releases four service updates annually, in February, April, July, and October. The maximum number of consecutive updates that can be paused is one and taking a minimum of two service updates per year is required. For answers to common questions about how these changes affect the release process, see [One Version service updates FAQ](one-version.md).
>
> [!NOTE]
> A sandbox autoupdate occurs seven days before the production update.

In the following table:

- An asterisk (\*) in the "Release version" column denotes a major release.
- The "autoupdate schedule production start date" column refers to the autoupdate schedule that's configured in the update settings in Lifecycle Services. See [Configure service updates through Lifecycle Services](../../dev-itpro/lifecycle-services/configure-service-updates.md).
- The "End of service" column indicates the date when no new cumulative service updates are provided.

| Release version | Preview availability | Preview latest possible update| General availability (self-update) | First autoupdate schedule for production start date | Second autoupdate schedule for production start date |End of service |
|---|---|---|---|---|---|---|
| CY26Q4: 10.0.49\* | July 27, 2026 | August 17, 2026 | September 11, 2026 | October 2, 2026 |  November 1, 2026 |May 21, 2027 |
| CY26Q3: 10.0.48 | April 24, 2026 | May 11, 2026 | June 5, 2026 | July 3, 2026 | July 31, 2026 | February 16, 2027 |
| CY26Q2: 10.0.47\* | January 26, 2026 | February 16, 2026 | March 13, 2026 | April 3, 2026 | May 1, 2026 |November 20, 2026 |
| CY26Q1: 10.0.46 | October 24, 2025 | November 17, 2025 | December 26, 2025 | February 1, 2026 | March 1, 2026 |August 21, 2026 |
| CY25Q4: 10.0.45\* | July 28, 2025 | August 8, 2025 | September 12, 2025 | October 3, 2025 |  October 31, 2025 |May 22, 2026 |
| CY25Q3: 10.0.44 | April 25, 2025 | May 2, 2025 | June 6, 2025 | July 4, 2025 | August 1, 2025 | February 17, 2026 |
| CY25Q2: 10.0.43\* | January 27, 2025 | February 7, 2025 | March 14, 2025 | April 4, 2025 | May 2, 2025 |November 21, 2025 |
| CY25Q1: 10.0.42 | October 25, 2024 | November 1, 2024 | December 27, 2024 | February 1, 2025 | March 7, 2025 |August 22, 2025 |
| CY24Q4: 10.0.41\* | July 29, 2024 | August 9, 2024 | September 17, 2024 | October 4, 2024 | Nov 1, 2024 | May 23, 2025 |
 
> [!NOTE]
> The [Software lifecycle policy](../../dev-itpro/migration-upgrade/versions-update-policy.md) applies to customers who are enrolled in the First Release program and to the date when the service update is made generally available.
>
> **Release naming convention as of the 10.0.38 release**
>
> The first half of the release label refers to the calendar year and quarter when the auto update production start date is scheduled. The second part is the product version as it appears in Lifecycle Services. An asterisk (\*) at the end of the label indicates a major release. For example: **CY25Q4: 10.0.45\*** is product version 10.0.45 that's made available for autoupdate in the fourth quarter of 2025. It's a major update (the "October" release).
> 
> Previews and preview updates are available as a deployable package in the Shared asset library in Lifecycle Services. For more information, see [One Version service updates FAQ](one-version.md).

## Service update overview

Service updates are continuous, touchless updates that provide new features and functionality. They eliminate the need to do expensive upgrades every few years. Because service updates maintain backward compatibility, there's no need to "merge your code." We recommend that you use tools such as the Regression suite automation tool (RSAT) for regression testing.

You're in control and manage how your organization receives these updates. For example, you can sign up for the First Release program so that your organization receives updates first. You can manually apply the updates to any of your environments (self-update). Alternatively, you can remain on the default release schedule and receive the autoupdates when you schedule them by using Lifecycle Services.

Service updates contain both application changes and platform changes that are critical to the service, including regulatory updates. For more information, see [Service updates](one-version.md#service-updates).

## Release processes

The Dynamics 365 team designs, develops, and validates each new release. Extensive testing is done on various test topologies. A compatibility checker also runs tests to ensure backward compatibility. 

All customers who take advantage of the preview have early access to the upcoming service update. The preview service update is used to validate customizations, learn about new features, and provide feedback to Microsoft. During the preview phase, customers must deploy the service update in a development/test environment. The preview release can't be used in production. After release, customers can download the package from the Shared Asset Library in Lifecycle Services. Customers must agree to the program terms at the time of installation. Sign up for access to preview packages is no longer required. One scheduled update to the preview build is included as standard with every release.

The First Release program is available to all finance and operations apps customers. There are two ways to participate:  

- **Microsoft Managed Update**s: Fill out the [First Release Program: Microsoft Dynamics 365 Finance and Operations applications](https://aka.ms/FirstReleaseFnO) form and receive a service update that Microsoft automatically deploys, first in a UAT sandbox and then in production after seven days. It isn't possible to pause these updates.  

- **Customer Initiated Updates**: Customers can pull the First Release build into their UAT sandbox from Lifecycle Services for testing and into production, without autodeployment from Microsoft.  

Typically, the First Release build is the same as the generally available (GA) build. However, if critical issues arise that can't be fixed with a hot fix, a new First Release build is declared, and customers are informed through various communication channels, including Viva Engage and Lifecycle Services.  Microsoft restarts the sandbox and production environments and deploy any newly declared First Release build for customers that receive Microsoft managed updates.  Customers that initiate updates should deploy newly declared First Release builds that are available on Lifecycle Services.  

The service update is made generally available through the Action Center in Lifecycle Services. When the service update is available, customers can manually apply it to all environments, including production. If the service update isn't applied to the designated sandbox or production environment, Microsoft automatically applies it, based on the update settings for the Lifecycle Services project. To learn more, see [Configure service updates through Lifecycle Services](../../dev-itpro/lifecycle-services/configure-service-updates.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
