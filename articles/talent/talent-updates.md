---
# required metadata

title: Talent updates
description: This topic provides information about the release process and cadence for Microsoft Dynamics 365 Talent.
author: andreabichsel
manager: AnnBe
ms.date: 10/21/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2019-10-21
ms.dyn365.ops.version: Talent October 2019 update
---

# Talent updates

[!include [banner](../includes/banner.md)]

Microsoft Dynamics 365 Talent provides continuous, touchless service updates. They contain both application and platform changes that often provide critcal improvements to the service, including regulatory updates. These continuous updates eliminate the need for expensive upgrades every few years. Service updates maintain backward compatibility, which means there is no need to merge your code. We recommend leveraging tools such as the Regression Suite Automation Tool (RSAT) for regression testing.

With service updates for Talent, you're in control and can manage how your organization receives them. For example, you can sign up for the First Release program so your organization receives updates first. You can also choose to apply the updates to any of your environments manually or to remain on the default release schedule and receive auto-updates when you schedule them using Lifecycle Services (LCS).

## Release process

The Talent team extensively tests and validates each new release on various test topologies. A compatibility checker also runs tests to ensure backward compatibility.

You can participate in several programs that can help ensure successful releases for your organization and others:

- The [Release Validation Program](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR56j8lZs0FdAvwT75_WNFyxUQVdKVkVORjVDNloxTEkwS1JUSUxWN1pSWi4u) allows you to share artifacts, such as databases and code. We use these for benchmarking and testing with automation to provide an additional layer of quality assurance.

- The Preview Early Access Program (PEAP) is available to partners, customers, and ISVs who opt in through the [Insider Program](https://experience.dynamics.com/). In the PEAP program, you have first access and visibility into the preview for the upcoming service update so you can validate customizations, learn about new features, and provide feedback to Microsoft. You can't use preview releases in a production environment, so you must deploy them in a test environment.

- The First Release program is open to all customers. Customers who join the First Release program will be the first, select group of customers to take the service update all the way to production. Microsoft manages the deployment of this service update to a UAT sandbox and then auto-deploys the update seven days later to production. If you participate in this program, you have the additional benefit of having dedicated Microsoft engineers closely monitoring the environments for any issues after updates have been applied. To join First Release, sign up via the [Insider Program](https://experience.dynamics.com/).  

Service updates are generally available though the action center in LCS. You can manually apply the update to all environments, including production. If you don't apply the update to the designated sandbox or production environment, Microsoft will auto-apply the update based on the update settings for the LCS project. For more information about changing your update settings, see [Configure service updates through Lifecycle Services](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/lifecycle-services/configure-service-updates).

## Release cadence

We're committed to delivering predictable service updates. These are generally available for self-deployment approximately two weeks prior to Microsoft automatically applying the update. 

> [!NOTE] 
> Service updates aren't usually provided during the months of March, June, September, and December.

You can take up to eight service updates per year, and you must take a minimum of two service updates per year. You can choose to pause up to three consecutive updates at a time. You can pause a service update on the designated UAT sandbox, production, or both environments. After the pause window has ended, and if you haven't self-updated to a supported service update, we'll auto-apply the latest update based on the configuration selection made available in LCS. To learn more about how to pause service updates, see [Pause service updates through Lifecycle Services](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/lifecycle-services/pause-service-updates).

## Release schedule

Sandbox auto-updates occur seven days prior to production updates. End of service indicates the date when no new cumulative service updates will be provided.

| Version                   | Preview availability (PEAP) | Generally available (self update) | Auto-update schedule (via LCS update settings) | End of service    |
|---------------------------|-----------------------------|-----------------------------------|-----------------------------------------------|-------------------|


> [!NOTE]
> The [Software lifecycle policy](../../dev-itpro/migration-upgrade/versions-update-policy.md) applies to customers enrolled in First Release and when the service update is made generally available.

Public previews are made available as a deployable package via the shared asset library in Lifecycle Services. For more details, see [One Version service updates FAQ](one-version.md).

## See also

- [Dynamics 365 and Power Platform Release Plans](https://docs.microsoft.com/dynamics365/release-plans)
- [What's new or changed in Dynamics 365 Talent](https://docs.microsoft.com/dynamics365/talent/whats-new)
- [Software lifecycle policy](../../dev-itpro/migration-upgrade/versions-update-policy.md)
- [Configure service updates through Lifecycle Services](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/lifecycle-services/configure-service-updates)

