---
# required metadata

title: Talent updates
description: This topic provides information about the release process and cadence for Microsoft Dynamics 365 Talent.
author: andreabichsel
manager: AnnBe
ms.date: 10/31/2019
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
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Talent October 2019 update
---

# Talent updates

[!include [banner](includes/banner.md)]

Microsoft Dynamics 365 Talent is a true software as a service (SaaS) that provides continuous, touchless service updates. These updates contain both application and platform changes that often provide critical improvements to the service, including regulatory updates.

## Update policy

Updates are released on a regular cadence to all environments. Talent is supported according to the [Microsoft Support Lifecycle policy](https://support.microsoft.com/en-us/hub/4095338/microsoft-lifecycle-policy), which provides consistent and predictable guidelines for product support availability.

## Release cadence

Talent updates are applied to all environments automatically. Talent provides two types of releases:

- **Service updates**: Weekly updates that include bug fixes and new features. Service updates also include applicable Platform updates when they release. To get an idea of when Platform updates are released, see [Table 3: Platform releases](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/migration-upgrade/versions-update-policy#table-3-platform-releases). Weekly updates usually release on Wednesdays. For more information about weekly updates, see [What's new or changed in Dynamics 365 Talent](https://docs.microsoft.com/dynamics365/talent/whats-new).

- **Common Data Service solution updates**: These updates occur approximately every six weeks, as needed. They include new entities and changes to existing entities in Common Data Service. These updates take about six weeks to replicate through all data centers. They're available on all data centers once they're released, so you can manually apply these updates on any environment in any data center if you don't want to wait for the updates to replicate automatically.

## Testing and Validation
 
The Talent team performs different testing depending on whether the release is one of the following:
 
- Minor: regular, weekly releases

- Revision (hotfix): bug fixes that can occur either with or apart from a minor release

- Emergency fix: proactive and reactive hotfixes that are standalone in nature, and can include configuration-only or code changes to resolve live site issues

Our processes for each type of release are described below. Talent uses two deployment environments during the release process:
 
- An internal environment for internal testing

- A production environment used by customers

### Minor (weekly) releases

Product, component, and leadership teams perform the following for minor (weekly) releases before rolling out to production:
 
1. On Mondays, roll out the candidate build to the internal environment.

2. Validate functionality through ad hoc testing and validating bugs.

3. Complete the validation and sign off on the build by Friday afternoon.

4. Verify all validation is complete, review configuration changes, and approve the build for rolling out to production.

5. Verify readiness to begin the rollout to production.

### Revisions (hotfixes)

Revision (hotfix) releases are initiated by the product teams, and are based on the build that is currently released to production. Product, component, and leadership teams perform the following for revision releases before rolling out to production:
 
1. Review and approve the changes.

2. Roll out the changes to the internal environment.

3. Review and sign off on the changes.

4. Verify that all validation is complete and approve the build for rolling out to production.

### Emergency fixes

Emergency fixes are initiated by the product team in response to a live site issue. These fixes might be configuration-only changes that can be completed by the product team, or they can include code changes if that’s the proper mitigation for the incident.
 
The product team can initiate changes in response to live site events without pre-approval for rolling out to the production environment. In these cases, the changes are reviewed during the post-incident review with the leadership team within one business day of the incident. 

## Communications

You can find out what's in the works for Talent and what we've released in the following locations:

- [Dynamics 365 Talent roadmap](https://dynamics.microsoft.com/en-us/roadmap/talent/)

- [Dynamics 365 Release Plans](https://docs.microsoft.com/dynamics365/release-plans/)

- [What's new or changed in Dynamics 365 Talent](https://docs.microsoft.com/dynamics365/talent/whats-new)

- [Issue search in Lifecycle Services (LCS)](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/lifecycle-services/issue-search-lcs) (for Platform-related bugs only)

- [Talent blog](https://community.dynamics.com/365/talent/b/dynamics365fortalent)

- [Talent Yammer community](https://www.yammer.com/dynamicsaxfeedbackprograms/#/threads/inGroup?type=in_group&feedId=10542230)

## Preview features in a sandbox environment

You can validate preview features in a sandbox environment before enabling them in your production environment. For more information about enabling features, see [Feature management overview](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview).

We highly recommend previewing features in a sandbox or trial environment. It's best to create a copy of your current production environment or database into a sandbox environment so you can get the complete experience of the new features with your data.

For more information about provisioning a sandbox environment, see [Provision a Talent project](provisioning-talent.md#provision-a-talent-project). To remove a test environment, see [Removing a test drive environment](remove-talent-environment.md#removing-a-test-drive-environment). 

## Report bugs

While testing preview features or trying new capabilities, you might find items that don't work as expected. Please report any bugs through [Microsoft Dynamics 365 support](https://dynamics.microsoft.com/support/).

## See also

- [Dynamics 365 and Power Platform Release Plans](https://docs.microsoft.com/dynamics365/release-plans)
- [What's new or changed in Dynamics 365 Talent](https://docs.microsoft.com/dynamics365/talent/whats-new)
- [Software lifecycle policy](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/migration-upgrade/versions-update-policy)
