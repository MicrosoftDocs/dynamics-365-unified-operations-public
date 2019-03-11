---
# required metadata

title: Standard and targeted service updates
description: This topic provides information about the different release options for Microsoft Dynamics 365 for Finance and Operations.
author: meeramahabala
manager: AnnBe
ms.date: 03/11/2019
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

# Standard and First release service updates

[!include [banner](../includes/banner.md)]

With Dynamics 365 for Finance and Operations, you receive new service updates and features monthly instead of doing expensive upgrades every few years. You can manage how your organization receives these updates. For example, you can sign up for a first release so that your organization receives updates first. You can designate that only certain environments receive the updates. Or, you can remain on the default release schedule and receive the auto updates later. This topic explains the different release options and how you can use them for your organization.

*Service updates* contain both application (including Financial reporting and Retail) and platform changes that are critical improvements to the service, including regulatory updates. New features will be included in service updates.

## Release processes

Each new release is designed and developed by the Dynamics 365 for Finance and Operations team. Any new release is first tested and validated by the feature team, then by the entire Dynamic 365 for Finance and Operations and Retail teams. During this time, extensive testing is done on various test topologies. A compatibility checker also runs tests to ensure backward compatibility. In addition, several customer databases and code are benchmark-tested with automation to provide an additional layer of quality assurance.

- Ring 2 is a targeted release. This release is available to channel partners, customers, and ISVs who opt in through the [Insider program](https://experience.dynamics.com) and join the Preview Early Access Program (PEAP). During a targeted release, Microsoft collects feedback, and further validates quality by monitoring key metrics. During this phase, the release must be deployed on Dev/Test environments. In this preview phase, channel partners, customers, and ISVs use the release to validate their customizations and provide feedback. This release cannot be used in production.
- Ring 3 is a production-ready, *first release* for customers who opt in. During this phase, customers have the option of taking the release all the way to production.  Participating in the First release program has the benefit of having the Microsoft engineering team closely monitoring the update for any issues   to ensure a successful update.
- Ring 4 is the final ring and is available to all customers. Microsoft will manage and update the <need the ending from Shelly/Meera>.

> [!NOTE]
> The [Software lifecycle policy](../../dev-itpro/migration-upgrade/versions-update-policy.md) applies to Ring 3 and Ring 4.

The releases are shown in the following image.

![Release process](media/release-process.png)

## Targeted release (Ring 2)

The Preview early access program (PEAP) is available for customers, channel partners, and ISVs to deploy into their sandbox environments. This preview version is not available for production use. The participant is required to self-update to the latest service update when the First release or Standard update is made generally available. The participants can raise issues to Microsoft. This release provides an additional value in that there’s time for testing updates early, prior to updating the production environments, and providing feedback directly to the Finance and Operations team.

## First release (Ring 3)

With the First release, Microsoft makes available the latest production-ready service update to customers.

In this program, Microsoft manages the update to both UAT and production environments. You will be informed when updates will be automatically applied. Updates will first be applied to the default Tier 2 sandbox, and then after 7 calendar days Microsoft will auto apply the update to production. You can sign up for the First release program through the [Insider program](https://experience.dynamics.com/insider). Customers who are in the First release program will also be able to manually apply the service update to any additional environment as needed. 

Microsoft will make the production-ready Service update package available to customers after the First release customers have provided feedback and validation to Microsoft. Notification on when this service update will be available for all customers will be made via the Lifecycle Services Action Center and the Support Lifecycle Policy page.

## Standard release (Ring 4)

The standard release, or Ring 4, is the default option. With this release, you can access the most recent release of Finance and Operations when it is released to all customers. In the standard release, you configure the update day and time to ensure predictability of the Microsoft managed update. You can also designate an environment for user-acceptance testing (UAT). This environment is updated by Microsoft 7 calendar days prior to updating the production environment. For more information, see [One Version service updates FAQ](one-version.md). The self-update option is available for all customers in order to stay current on the most recent service update.  Microsoft will auto-update the environments selected based on the configuration date/time shown in Lifecycle Services if the production environment is not on a supported service update. Microsoft will release a minimum of 10 service updates per calendar year. All service updates will be cumulative and made available via Lifecycle Services. 

## Access targeted releases or First release 

If you are interested in participating in the targeted or First releases of Finance and Operations and would like to learn more about the available options, see the [Insider program](https://experience.dynamics.com).

## Release cadence
Microsoft will be releasing a minimum of 10 service updates per year. Customers are required to take a minimum of 4 service updates per year and can choose to pause up to 2 consecutive updates at a time. Pausing an update can apply to the designated Sandbox UAT, Production, or both environments. When the pause window has ended and if the customer has not self updated to a supported service update, Microsoft will auto-apply the latest update based on the configuration selection made available in LCS.

Standard release, or Ring 4 customers, will be able to pause an update via Lifecycle Services Project Settings. First release customers will work directly with Program Manager for First release if there’s a need to pause any service updates for the interim.

**Targeted release schedule (dates subject to change)**

| Version | Preview, Ring 2 | Available for self update | Ring 4 auto-update* |
|---------|-----------------|---------------------------|---------------------|
|10.0<br>Platform update 24 |  February 1, 2019 | Week of March 18, 2019 | Production: Starting April 1 |
|10.0.1<br>Platform update 25| Week of March 4, 2019 | Week of April 8, 2019 | Production: Starting May 1 |
|10.0.2<br>Platform update 26| Week of April 8, 2019 | Week of May 13, 2019 | Production: Starting June 1  |
|10.0.3<br>Platform update 27| Week of May 6, 2019 | Week of June 10, 2019 | Production: Starting July 1  |
| 10.0.4<br>Platform update 28| Week of June 3, 2019 | Week of July 8, 2019 | Production: Starting August 1  |

\*Sandbox auto-update takes place 7 days prior to Production.
