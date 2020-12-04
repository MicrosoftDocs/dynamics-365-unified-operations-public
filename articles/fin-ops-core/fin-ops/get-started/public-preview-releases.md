---
# required metadata

title: Service update availability
description: This topic provides information about the different release options.
author: ShellyBakke
manager: AnnBe
ms.date: 11/12/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
#ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: smiller
ms.search.validFrom: 2017-10-31
ms.dyn365.ops.version: Platform update 11
---

# Service update availability

[!include [banner](../includes/banner.md)]

Microsoft is committed to delivering predictable service updates. These service updates will be made generally available for self-deployment approximately 2 weeks prior to Microsoft automatically applying the update. 

Customers will be able to take up to 8 service updates per year and are required to take a minimum of 2 service updates per year. Customers can choose to pause up to 3 consecutive updates at a time. Pausing a service update can apply to the designated user acceptance testing (UAT) sandbox, production, or both environments. After the pause window has ended and if the customer has not self-updated to a supported service update, Microsoft will auto-apply the latest update based on the configuration selection made available in Lifecycle Services (LCS). To learn more about how to pause service updates, see [Pause service updates through Lifecycle Services](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/lifecycle-services/pause-service-updates).

> [!NOTE] 
> Service updates will not be provided during the months of March, June, September, and December. 

### Targeted release schedule (dates subject to change)

> [!NOTE] 
> Sandbox auto-update takes place 7 days prior to the production update.  End of service indicates the date when no new cumulative service updates will be provided.

|          Version          | Preview availability (PEAP) | Generally available (self-update) | Auto-update schedule (via LCS Update Settings) production start date |   End of service   |
|:-------------------------:|:---------------------------:|:---------------------------------:|:--------------------------------------------------------------------:|:------------------:|
|          10.0.20          |         May 28, 2021        |           July 16, 2021           |                             July 30, 2021                             |  October 22, 2021  |
|          10.0.19          |        April 23, 2021       |            June 18, 2021           |                             July 2, 2021                             | September 17, 2021 |
|          10.0.18          |        March 5, 2021        |           April 16, 2021          |                            April 30, 2021                            |    July 16, 2021   |
|          10.0.17          |       February 1, 2021      |           March 19, 2021          |                             April 2, 2021                            |    June 11, 2021   |
|          10.0.16          |      November 20, 2020      |          January 22, 2021         |                           February 1, 2021                           |   April 30, 2021   |
|          10.0.15          |       October 9, 2020       |          December 4, 2020         |                            January 1, 2021                           |   March 19, 2021   |
|          10.0.14          |      September 4, 2020      |          October 23, 2020         |                           November 1, 2020                           |  January 22, 2021  |
|          10.0.13          |        August 3, 2020       |         September 18, 2020        |                            October 1, 2020                           |  December 4, 2020  |
|          10.0.12          |         May 29, 2020        |           July 22, 2020           |                            August 1, 2020                            |  October 23, 2020  |
|          10.0.11          |        April 17, 2020       |            May 29, 2020           |                             July 1, 2020                             | September 11, 2020 |
|          10.0.10          |        March 6, 2020        |           April 10, 2020          |                              May 1, 2020                             |    July 3, 2020    |
| 10.0.9/Platform update 33 |       February 1, 2020      |           March 13, 2020          |                             April 1, 2020                            |    June 5, 2020    |
| 10.0.8/Platform update 32 |      November 29, 2019      |          January 17, 2020         |                           February 1, 2020                           |     May 1, 2020    |
| 10.0.7/Platform update 31 |       October 25, 2019      |         November 29, 2019         |                            January 1, 2020                           |    March 9, 2020   |
| 10.0.6/Platform update 30 |      September 6, 2019      |          October 11, 2019         |                           November 1, 2019                           |  January 13, 2020  |
| 10.0.5/Platform update 29 |        August 2, 2019       |         September 13, 2019        |                            October 1, 2019                           |  December 2, 2019  |
| 10.0.4/Platform update 28 |         June 7, 2019        |           July 12, 2019           |                            August 1, 2019                            |  October 14, 2019  |
| 10.0.3/Platform update 27 |         May 10, 2019        |           June 14, 2019           |                             July 1, 2019                             |  September 9, 2019 |
| 10.0.2/Platform update 26 |        April 12, 2019       |            May 17, 2019           |                             June 1, 2019                             |   August 12, 2019  |
| 10.0.1/Platform update 25 |                             |                                   |                              May 1, 2019                             |    June 10, 2019   |
|                           |                             |                                   |                                                                      |                
> [!NOTE]
> The [Software lifecycle policy](../../dev-itpro/migration-upgrade/versions-update-policy.md) applies to customers enrolled in First Release and when the service update is made generally available.

Sign up for the PEAP program by joining the Insider Program available at https://experience.dynamics.com. After your nomination has been accepted, join the program.

Public previews are made available as a deployable package via the Shared Asset Library in Lifecycle Services. For more details, see [One Version service updates FAQ](one-version.md). 

## Service update overview
Service updates are continuous, touchless updates that provide new features and functionality. They eliminate the need to do expensive upgrades every few years. The service updates maintain backward compatibility, which means there is no need to ‘merge your code’.  We recommend leveraging tools such as the Regression suite automation tool (RSAT) for regression testing.

You are in control and manage how your organization receives these updates. For example, you can sign up for the First Release program so that your organization receives updates first. You can apply the updates to any of your environments manually (self-update) or remain on the default release schedule and receive the auto-updates when you schedule them using LCS.

Service updates contain both application and platform changes that are critical improvements to the service, including regulatory updates. 

## Release processes

Each new release is designed and developed by the Dynamics 365 team. Any new release is first validated by the feature team, then by the Finance and Operations teams. During this time, extensive testing is done on various test topologies. A compatibility checker also runs tests to ensure backward compatibility. In addition, a [Release Validation Program](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR56j8lZs0FdAvwT75_WNFyxUQVdKVkVORjVDNloxTEkwS1JUSUxWN1pSWi4u) is available for customers to join. This program allows customers to share artifacts, such as databases and code, that is used for benchmarking and tested with automation to provide an additional layer of quality assurance.

Preview Early Access Program (PEAP) is available to partners, customers, and ISV’s who opt in through the [PEAP Survey](https://aka.ms/PEAP).  As a participant in the PEAP program you will have first access and visibility into the preview for the upcoming service update.  The preview service update is used to validate customizations, learn about new features, and provide feedback to Microsoft.  During this phase, the service update must be deployed on a Dev/Test environment.  This release cannot be used in production. To join the PEAP program, sign up via the [PEAP Survey](https://aka.ms/PEAP). 

The First Release program is open to all customers. Customers who join the First Release program will be the first, select group of customers to take the service update all the way to production.  Microsoft will manage the deployment of this service update to a UAT sandbox and then 7 days later will auto-deploy the update to production. Customers participating in this program have the additional benefit of having dedicated Microsoft engineers closely monitoring the environments for any issues after updates have been applied. To join First Release, sign up via the [First Release Survey](https://aka.ms/FirstRelease).  

The service update will be made generally available using the action center in LCS.  When the service update is available, it can be manually applied to all environments including production.  If the service update has not been applied to the designated sandbox or production environment, Microsoft will auto-apply the update based on the Update settings for the LCS project. To learn more, see [Configure service updates through Lifecycle Services](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/lifecycle-services/configure-service-updates).
