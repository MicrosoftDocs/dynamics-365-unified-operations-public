---
# required metadata

title: Talent updates
description: This article provides information about the release process and cadence for Microsoft Dynamics 365 Talent.
author: andreabichsel
manager: AnnBe
ms.date: 11/15/2019
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
ms.search.validFrom: 2019-11-15
ms.dyn365.ops.version: Talent October 2019 update
---

# Talent updates

Microsoft Dynamics 365 Talent is a true software as a service (SaaS) that provides continuous, touchless service updates. These updates contain both application and platform changes that often provide critical improvements to the service, including regulatory updates.

## Update policy

Updates are released on a regular cadence to all environments. Talent is supported according to the [Microsoft Lifecycle policy](https://support.microsoft.com/en-us/hub/4095338/microsoft-lifecycle-policy), which provides consistent and predictable guidelines for the availability of support.

## Release cadence

Talent updates are applied to all environments automatically. Talent provides two types of releases:

- **Service updates**: Weekly updates that include bug fixes and new features. Service updates also include applicable Platform updates when they release. To get an idea of when Platform updates are released, see [Table 3: Platform releases](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/migration-upgrade/versions-update-policy#table-3-platform-releases). Weekly updates usually release on Wednesdays. For more information about weekly updates, see [What's new or changed in Dynamics 365 Talent](https://docs.microsoft.com/dynamics365/talent/whats-new).

    All supported data centers update weekly, unless otherwise noted. Weekly updates typically begin on Wednesday and complete by Sunday. US, Australia, Europe, UK, Asia, and Canada regions are included in weekly updates. 

- **Common Data Service solution updates**: These updates occur approximately every six weeks, as needed. They include new entities and changes to existing entities in Common Data Service. These updates release to the same regions as the weekly updates, and they take about six weeks to replicate through all data centers. Solution updates may or may not align with weekly service updates.

The following table shows a sample schedule:

| Week | Update type |
| --- | --- |
| 1 | Service update (all regions) |
| 2 | Service update (all regions) + Solution update (Week 1 regions) |
| 3 | Service update (all regions) + Solution update (Week 2 regions) |
| 4 | Service update (all regions) + Solution update (Week 3 regions) |
| 5 | Service update (all regions) + Solution update (Week 4 regions) |
| 6 | Service update (all regions) + Solution update (Week 5 regions) |
| 7 | Service update (all regions) + Solution update (Week 6 regions) |
| 8 | Service update (all regions) |

> [!NOTE]
> Solution updates are available on all data centers once they're released. If you don't want to wait for the updates to replicate automatically, you can manually apply these updates on any environment in any data center.

When needed, Talent also provides the following types of fixes:

- **Revision (hotfix)**: bug fixes that can occur either with or apart from a weekly service update release

- **Emergency fix**: proactive and reactive hotfixes that are standalone in nature, can include configuration-only or code changes to resolve live site issues, and can occur apart from a weekly service update release

Releases are reviewed, tested, and validated on an internal environment. After builds are signed off, they're then deployed to production.

## Exceptions in 2019

The following dates are exceptions to the regular release schedule:

| Date | Description |
| --- | --- |
| Week of November 25 | No updates |
| Week of December 16 | Minor updates only |
| Week of December 23 | No updates |
| Week of December 30 | No updates |

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

All new features remain in preview for at least 30 days, and typically 30-60 days. Major features are generally available in October and April of each year following the preview period. As soon as you see new capabilities in the Feature management workspace, you can turn them on. Some features may be on by default.

At times, an integral feature will be on by default and can't be turned off (for example, the Feature management workspace).

Once a feature is generally available, it may be turned on or off in production environments. The Feature management workspace indicates when a preview feature will become mandatory. This date is usually on October 1 or April 1 to align with the semiannual release plans. You can't turn off mandatory features. Until it becomes mandatory, you can turn a feature on and off in all environments.

We highly recommend previewing features in a sandbox or trial environment. It's best to create a copy of your current production environment or database into a sandbox environment so you can get the complete experience of the new features with your data.

For more information about provisioning a sandbox environment, see [Provision a Talent project](provisioning-talent.md#provision-a-talent-project). To remove a test environment, see [Removing a test drive environment](remove-talent-environment.md#removing-a-test-drive-environment). 

## Report bugs

While testing preview features or trying new capabilities, you might find items that don't work as expected. Please report any bugs through [Microsoft Dynamics 365 support](https://dynamics.microsoft.com/support/).

## See also

- [Dynamics 365 and Power Platform Release Plans](https://docs.microsoft.com/dynamics365/release-plans)
- [What's new or changed in Dynamics 365 Talent](https://docs.microsoft.com/dynamics365/talent/whats-new)
- [Software lifecycle policy](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/migration-upgrade/versions-update-policy)
