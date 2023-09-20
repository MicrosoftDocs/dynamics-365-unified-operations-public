---
# required metadata

title: Service update availability
description: This article provides information about the different release options.
author: hmahl
ms.date: 09/15/2023
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

Microsoft is committed to delivering predictable service updates. These service updates are made generally available for self-deployment approximately two weeks prior to Microsoft automatically applying the update. 

Customers can take up to seven service updates per year and are required to take a minimum of two service updates per year. Customers can choose to pause up to three consecutive updates at a time. Pausing a service update can apply to the designated user acceptance testing (UAT) sandbox, production, or both environments. After the pause window has ended and if the customer hasn't self-updated to a supported service update, Microsoft will auto-apply the latest update based on the configuration selection made available in Dynamics Lifecycle Services. To learn more about how to pause service updates, see [Pause service updates through Lifecycle Services](../../dev-itpro/lifecycle-services/pause-service-updates.md).

> [!NOTE] 
> Service updates are not provided during the months of January, March, June, September, and December. 

### Targeted release schedule (dates subject to change)
> [!IMPORTANT]
> There are important changes coming to the service update release schedule. Details on the changes and updated schedule dates will be published by the end of September, 2023.

> [!NOTE] 
> Sandbox auto-update takes place 7 days prior to the production update. End of service indicates the date when no new cumulative service updates are provided.

|     Version     | Preview availability        | Generally available (self-update) | Auto-update schedule (via Lifecycle Services Update Settings) production start date | End of service     |
|-----------------|-----------------------------|-----------------------------------|----------------------------------------------------------------------|--------------------|
|     10.0.38<br>(The "February" release)     | October 13, 2023            | January 12, 2024                  | February 2, 2024                                                     | April 12, 2024     |
|     10.0.37<br>(The "November" release)     | September 1, 2023           | October 20, 2023                  | November 3, 2023                                                     | March 15, 2024   |
|     10.0.36\*<br>(The "October" release)   | July 31, 2023               | September 15, 2023                | September 29, 2023                                                   | January 12, 2024   |
|     10.0.35<br>(The "August" release)     | May 26, 2023                | July 14, 2023                     | July 28, 2023                                                        | October 20, 2023   |
|     10.0.34<br>(The "July" release)     | April 21, 2023              | June 16, 2023                     | June 30, 2023                                                        | September 15, 2023 |
|   10.0.33<br>(The "May" release)    | March 3, 2023               | April 14, 2023                    | April 28, 2023                                                       | July 14, 2023      |
|     10.0.32\*<br>(The "April" release)   | January 30, 2023            | March 17, 2023                    | March 31, 2023                                                       | June 9, 2023       |
|     10.0.31<br>(The "February" release)     | October 14, 2022            | January 13, 2023                  | February 3, 2023                                                     | April 14, 2023     |
|     10.0.30<br>(The "November" release)     | September 2, 2022           | October 21, 2022                  | November 4, 2022                                                     | March 17, 2023   |
|     10.0.29\*<br>(The "October" release)  | August 1, 2022              | September 16, 2022                | September 30, 2022                                                   | January 13, 2023   |
|     10.0.28<br>(The "August" release)     | May 27, 2022                | July 15, 2022                     | July 29, 2022                                                        | October 21, 2022   |
|     10.0.27<br>(The "July" release)     | April 22, 2022              | June 17, 2022                     | July 1, 2022                                                         | September 16, 2022 |
|     10.0.26<br>(The "May" release)    | March 4, 2022               | April 15, 2022                    | April 29, 2022                                                       | July 15, 2022      |
|     10.0.25\*<br>(The "April" release)   | January 31, 2022            | March 18, 2022                    | April 1, 2022                                                        | June 10, 2022      |

\* Denotes a major release.
 
> [!NOTE]
> The [Software lifecycle policy](../../dev-itpro/migration-upgrade/versions-update-policy.md) applies to customers enrolled in First Release and when the service update is made generally available.

> [!NOTE]
> In 2022 we made adjustments to end-of-year service update availability. Servicing for the major October release was extended into January. Similarly, servicing for the November release was extended into March. The January release was cancelled.

> [!Note]
> The name of the month given to a release doesn't always indicate when the auto-update may occur. For example, in the table above, the auto-update schedule for the "October" release in 2022 actually starts on September 30, 2022.

Previews are available as a deployable package via the Shared Asset Library in Lifecycle Services. For more details, see [One Version service updates FAQ](one-version.md). 

## Service update overview
Service updates are continuous, touchless updates that provide new features and functionality. They eliminate the need to do expensive upgrades every few years. The service updates maintain backward compatibility, which means there's no need to ‘merge your code.' We recommend using tools such as the Regression suite automation tool (RSAT) for regression testing.

You are in control and manage how your organization receives these updates. For example, you can sign up for the First Release program so that your organization receives updates first. You can apply the updates to any of your environments manually (self-update) or remain on the default release schedule and receive the auto-updates when you schedule them using Lifecycle Services.

Service updates contain both application and platform changes that are critical improvements to the service, including regulatory updates. 

## Release processes

The Dynamics 365 team designs and develops each new release. The feature team validates the new release first, then the finance and operations teams validates it. During this time, extensive testing is done on various test topologies. A compatibility checker also runs tests to ensure backward compatibility.

All customers have early access to the upcoming service update if they take advantage of its preview. The preview service update is used to validate customizations, learn about new features, and provide feedback to Microsoft. During the preview phase, customers must deploy the service update on a Dev/Test environment. The preview release can't be used in production. Once released, customers can download the package from the Shared Asset Library in Lifecycle Services. Customers must agree to the program terms at install time. Signing up for access to preview (formerly known as the Preview Early Access Program (PEAP)) is no longer required.

The First Release program is open to all customers. Customers who join the First Release program are the first, select group of customers to take the service update all the way to production. Microsoft manages the deployment of this service update to a UAT sandbox, and then auto-deploys the update to production seven days later. Customers participating in this program have the additional benefit of having dedicated Microsoft engineers closely monitoring the environments for any issues after updates are applied. To join First Release, see the [First Release Program: Microsoft Dynamics 365 Finance and Operations applications](https://aka.ms/FirstReleaseFnO) form.

The service update is made generally available using the action center in Dynamics Lifecycle Services. When the service update is available, customers can manually apply it to all environments, including production. If the service update hasn't been applied to the designated sandbox or production environment, Microsoft auto-applies the update based on the Update settings for the Lifecycle Services project. To learn more, see [Configure service updates through Lifecycle Services](../../dev-itpro/lifecycle-services/configure-service-updates.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

