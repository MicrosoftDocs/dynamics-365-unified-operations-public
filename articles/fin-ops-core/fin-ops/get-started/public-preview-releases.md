---
# required metadata

title: Service update availability
description: This topic provides information about the different release options.
author: ShellyBakke
ms.date: 01/06/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
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

Customers will be able to take up to 8 service updates per year and are required to take a minimum of 2 service updates per year. Customers can choose to pause up to 3 consecutive updates at a time. Pausing a service update can apply to the designated user acceptance testing (UAT) sandbox, production, or both environments. After the pause window has ended and if the customer has not self-updated to a supported service update, Microsoft will auto-apply the latest update based on the configuration selection made available in Lifecycle Services (LCS). To learn more about how to pause service updates, see [Pause service updates through Lifecycle Services](../../dev-itpro/lifecycle-services/pause-service-updates.md).

> [!NOTE] 
> Service updates will not be provided during the months of March, June, September, and December. 

### Targeted release schedule (dates subject to change)

> [!NOTE] 
> Sandbox auto-update takes place 7 days prior to the production update.  End of service indicates the date when no new cumulative service updates will be provided.

|     Version     | Preview availability (PEAP) | Generally available (self-update) | Auto-update schedule (via LCS Update Settings) production start date |   End of service   |
|-----------------|-----------------------------|-----------------------------------|----------------------------------------------------------------------|--------------------|
|     10.0.30     |      September 2, 2022      |        October 21, 2022           |                          November 4, 2022                            | January 13, 2023   |
|     10.0.29\*    |      August 1, 2022         |        September 16, 2022         |                          September 30, 2022                          | December 9, 2022   |
|     10.0.28     |      May 27, 2022           |        July 15, 2022              |                          July 29, 2022                               | October 21, 2022   |
|     10.0.27     |      April 22, 2022         |        June 17, 2022              |                          July 1, 2022                                | September 16, 2022 |
|     10.0.26     |      March 4, 2022          |        April 15, 2022             |                          April 29, 2022                              | July 15, 2022      |
|     10.0.25\*     |      January 31, 2022       |        March 18, 2022             |                          April 1, 2022                               | June 10, 2022      |
|     10.0.24     |      December 3, 2021       |        January 14, 2022           |                          February 4, 2022                            | April 15, 2022     |
|     10.0.23     |      October 15, 2021       |        December 10, 2021          |                          December 31, 2021                           | March 18, 2022     |
|     10.0.22     |      September 3, 2021      |        October 22, 2021           |                          November 5, 2021                            | January 14, 2022   |
|     10.0.21\*     |      August 2, 2021         |        September 17, 2021         |                          October 1, 2021                             | December 10, 2021  |
|     10.0.20     |      May 28, 2021           |        July 16, 2021              |                          July 30, 2021                               | October 22, 2021   |
|     10.0.19     |      April 23, 2021         |        June 18, 2021              |                          July 2, 2021                                | September 17, 2021 | 

\* Denotes a major release.
 
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

The First Release program is open to all customers. Customers who join the First Release program will be the first, select group of customers to take the service update all the way to production.  Microsoft will manage the deployment of this service update to a UAT sandbox and then 7 days later will auto-deploy the update to production. Customers participating in this program have the additional benefit of having dedicated Microsoft engineers closely monitoring the environments for any issues after updates have been applied. To join First Release, sign up via the [First Release Survey](https://aka.ms/FirstReleaseFnO).  

The service update will be made generally available using the action center in LCS.  When the service update is available, it can be manually applied to all environments including production.  If the service update has not been applied to the designated sandbox or production environment, Microsoft will auto-apply the update based on the Update settings for the LCS project. To learn more, see [Configure service updates through Lifecycle Services](../../dev-itpro/lifecycle-services/configure-service-updates.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
