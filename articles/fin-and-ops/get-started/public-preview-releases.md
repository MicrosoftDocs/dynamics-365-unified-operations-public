---
# required metadata

title: Service update availability
description: This topic provides information about the different release options for Microsoft Dynamics 365 for Finance and Operations.
author: meeramahabala
manager: AnnBe
ms.date: 03/14/2019
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
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: meeram
ms.search.validFrom: 2017-10-31
ms.dyn365.ops.version: Platform update 11
---

# Service update availability

[!include [banner](../includes/banner.md)]

With Dynamics 365 for Finance and Operations, you receive continuous, touchless service updates and features instead of doing expensive upgrades every few years. The service updates maintain backward compatibility, which means there is no need to ‘merge your code’.  We recommend leveraging tools such as the Regression Suite Automation Tool (RSAT) for regression testing.

You are in control and manage how your organization receives these updates. For example, you can sign up for the first release program so that your organization receives updates first. You can apply the updates to any of your environments manually (self-update) or remain on the default release schedule and receive the auto updates when you schedule them using Lifecyle Services. This topic explains the different release options and how you can use them for your organization.

*Service updates* contain both application (including Financial reporting and Retail) and platform changes that are critical improvements to the service, including regulatory updates. 

## Release processes

Each new release is designed and developed by the Dynamics 365 for Finance and Operations team. Any new release is first validated by the feature team, then by the entire Dynamic 365 for Finance and Operations and Retail teams. During this time, extensive testing is done on various test topologies. A compatibility checker also runs tests to ensure backward compatibility. In addition, a [Release Validation Program](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR56j8lZs0FdAvwT75_WNFyxUQVdKVkVORjVDNloxTEkwS1JUSUxWN1pSWi4u) is available for customers to join. This program allows customers to share artifacts, such as databases and code, that is used for benchmarking and tested with automation to provide an additional layer of quality assurance.

Preview Early Access Program (PEAP) is available to partners, customers, and ISV’s who opt in through the [Insider program](https://experience.dynamics.com/).  As a participant in the PEAP program you will have first access and visibility into the preview for the upcoming service update.  The preview service update is used to validate customizations, learn about new features, and provide feedback to Microsoft.  During this phase, the service update must be deployed on a Dev/Test environment.  This release cannot be used in production. To join the PEAP program, sign up via [Insider Program](https://experience.dynamics.com/). 

The First Release program is open to all customers. Customers who join the First Release program will be the first select group of customers to take the service update all the way to production.  Microsoft will manage the deployment of this service update to a UAT sandbox and then 7 days later will auto-deploy the update to production.  Customers participating in this program have the additional benefit of having dedicated Microsoft engineers closely monitoring   the environments for any issues after updates have been applied.  To join First Release, sign up via [Insider Program](https://experience.dynamics.com/).  

The service update will be made generally available using the action center in Lifecycle services (LCS).  When the service update is available, it can be manually applied to all environments including production.  If the service update has not been applied to the designated sandbox or production environment, Microsoft will auto-apply the update based on the “Update settings” for the LCS project. To learn more, see [Configure service updates through Lifecycle Services](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/lifecycle-services/configure-service-updates).

## Release cadence
Microsoft is committed to delivering predictable service updates each month (excluding March and September).  These service updates will be made generally available for self deployment approximately 2 weeks prior to Microsoft automatically applying the update.  

Customers are required to take a minimum of 4 service updates per year and may choose to pause up to 2 consecutive updates at a time.  Pausing a service update can apply to the designated Sandbox UAT, Production or both environments.  Once the pause window has ended and if the customer has not self updated to a supported service update, Microsoft will auto-apply the latest update based on the configuration selection made available in LCS. To learn more about how to pause service updates, see [Pause service updates through Lifecycle Services](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/lifecycle-services/pause-service-updates).

### Targeted release schedule (dates subject to change)

> [NOTE] 
> Sandbox auto-update takes place 7 days prior to the production update.

| Version | Preview availability (PEAP) | Generally available (Self update) | Auto-update schedule (via LCS Update settings)|
|---------|-----------------|---------------------------|---------------------|
|10.0<br>Platform update 24 |  February 1, 2019 | Week of March 18, 2019 | Production: Starting April 1 |
|10.0.1<br>Platform update 25| Week of March 4, 2019 | Week of April 8, 2019 | Production: Starting May 1 |
|10.0.2<br>Platform update 26| Week of April 8, 2019 | Week of May 13, 2019 | Production: Starting June 1  |
|10.0.3<br>Platform update 27| Week of May 6, 2019 | Week of June 10, 2019 | Production: Starting July 1  |
| 10.0.4<br>Platform update 28| Week of June 3, 2019 | Week of July 8, 2019 | Production: Starting August 1  |

> [NOTE]
> The [Software lifecycle policy](../../dev-itpro/migration-upgrade/versions-update-policy.md) applies to customers enrolled in First Release and when the Service Update is made generally available.
> 
> For more details, see [One Version service updates FAQ](one-version.md).  
