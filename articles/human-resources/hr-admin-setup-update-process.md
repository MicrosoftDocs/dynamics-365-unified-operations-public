---
# required metadata

title: Update process
description: Microsoft Dynamics 365 Human Resources is a true software as a service (SaaS) that provides continuous, touchless service updates for application and platform changes.
author: twheeloc
ms.date: 12/01/2022
ms.topic: article
# optional metadata

ms.search.form: SystemAdministrationWorkspaceForm
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-02-27
ms.dyn365.ops.version: Human Resources

---

# Update process

> [!IMPORTANT]
> For more information about the update process, see [Process for moving to the latest update of finance and operations](../fin-ops-core/dev-itpro/migration-upgrade/upgrade-latest-update.md). For more information about hotfixes, see [Download updates from Lifecycle Services (LCS)](/fin-ops-core/dev-itpro/migration-upgrade/download-hotfix-lcs.md). 

Microsoft Dynamics 365 Human Resources is a true software as a service (SaaS) that provides continuous, touchless service updates. These updates contain both application and platform changes that often provide critical improvements to the service, including regulatory updates.

## Update policy

Updates are released on a regular cadence to all environments. Human Resources is supported according to the [Microsoft Lifecycle policy](https://support.microsoft.com/hub/4095338/microsoft-lifecycle-policy), which provides consistent and predictable guidelines for the availability of support.

## Release cadence 

Human Resources updates are applied to all environments automatically. Human Resources provides two types of releases:

- **Service updates**: Service updates include applicable platform updates when they are released. In addition to exception-based updates, regular service updates occur following the General Availability (GA) of Dynamics 365 Finance platform updates. For more information about platform releases, see [What's new or changed in Platform updates](../fin-ops-core/dev-itpro/get-started/whats-new-home-page.md). Updates have a staged global rollout across regions. For more information about updates, see [What's new or changed in Dynamics 365 Human Resources](hr-admin-whats-new.md).

- **Dataverse solution updates**: These updates occur approximately every six weeks, as needed. They include new entities and changes to existing entities in Dataverse. These updates are released to the same regions as the biweekly updates, and they take about six weeks to replicate through all data centers. Solution updates may or may not align with biweekly service updates.

> [!NOTE]
> Solution updates are available on all data centers once they're released. If you don't want to wait for the updates to replicate automatically, you can manually apply these updates on any environment in any data center.

When needed, Human Resources provides the following types of fixes:

- **Revision (hotfix)**: Bug fixes that can occur either with or apart from a biweekly service update release

- **Emergency fix**: Proactive and reactive hotfixes that are standalone in nature, can include configuration-only or code changes to resolve live site issues, and can occur apart from a biweekly service update release

Releases are reviewed, tested, and validated on an internal environment. After builds are signed off, they're then deployed to production.

## Communications

You can find out what's in the works for Human Resources and what we've released in the following locations:

- [Dynamics 365 Human Resources roadmap](https://dynamics.microsoft.com/roadmap/human-resources/)

- [Dynamics 365 Release Plans](/dynamics365/release-plans/)

- [What's new or changed in Dynamics 365 Human Resources](hr-admin-whats-new.md)

- [Issue search in Lifecycle Services (LCS)](../fin-ops-core/dev-itpro/lifecycle-services/issue-search-lcs.md) (for Platform-related bugs only)

- [Human Resources blog](https://community.dynamics.com/365/talent/b/dynamics365fortalent)

- [Human Resources Yammer community](https://www.yammer.com/dynamicsaxfeedbackprograms/#/threads/inGroup?type=in_group&feedId=10542230)

## Preview features in a sandbox environment

You can validate preview features in a sandbox environment before enabling them in your production environment. For more information about enabling features, see [Feature management overview](../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

All new features remain in preview for at least 30 days, and typically 30-60 days. Major features are generally available in October and April of each year following the preview period. As soon as you see new capabilities in the **Feature management** workspace, you can turn them on. Some features may be on by default.

At times, an integral feature will be on by default and can't be turned off (for example, the Feature management workspace).

Once a feature is generally available, it may be turned on or off in production environments. The **Feature management** workspace indicates when a preview feature will become mandatory. This date is usually on October 1 or April 1 to align with the semiannual release plans. You can't turn off mandatory features. Until it becomes mandatory, you can turn a feature on and off in all environments.

We highly recommend previewing features in a sandbox or trial environment. It's best to create a copy of your current production environment or database into a sandbox environment so you can get the complete experience of the new features with your data.

For more information about provisioning a sandbox environment, see [Provision a Human Resources project](hr-admin-setup-provision.md). To remove a test environment, see [Remove an instance](hr-admin-setup-remove-instance.md#remove-a-test-drive-environment). 

## Report bugs

While testing preview features or trying new capabilities, you might find items that don't work as expected. Please report any bugs through [Microsoft Dynamics 365 support](https://dynamics.microsoft.com/support/).

## See also

[Dynamics 365 and Power Platform Release Plans](/dynamics365/release-plans)</br>
[What's new or changed in Dynamics 365 Human Resource](hr-admin-whats-new.md)</br>
[Software lifecycle policy](../fin-ops-core/dev-itpro/migration-upgrade/versions-update-policy.md)



[!INCLUDE[footer-include](../includes/footer-banner.md)]
