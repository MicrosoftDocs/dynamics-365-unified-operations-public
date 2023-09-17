---
# required metadata

title: System administration home page
description: This article lists resources that are available for system administrators.
author: sericks007
ms.date: 11/20/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SystemAdministrationWorkspaceForm
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 2bb96ac4-0cef-4f66-a953-bd82c117247b
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# System administration home page

[!include [banner](../includes/banner.md)]

This article points to content for system administrators of finance and operations. This content will help you configure the system so that it works smoothly and effectively for your organization.

## One Version
In July 2018 we announced a change to the way we deliver Dynamics 365 updates that will help you stay current in a consistent, predictable, and seamless manner. The following topics are intended to provide clarity on the finance and operations service updates, processes, and tools you can use to stay current.

- [One Version service updates overview](../lifecycle-services/oneversion-overview.md)
- [One Version service updates FAQ](../../fin-ops/get-started/one-version.md)
- [Service update availability](../../fin-ops/get-started/public-preview-releases.md)
- [Apply updates to cloud environments](../deployment/apply-deployable-package-system.md)
- [Configure service updates through Lifecycle Services (LCS)](../lifecycle-services/configure-service-updates.md)
- [Pause service updates through Lifecycle Services (LCS)](../lifecycle-services/pause-service-updates.md)
- [Get notified about service updates through Lifecycle Services (LCS)](../lifecycle-services/notifications-service-updates.md)

## Implementation management with Lifecycle Services
Microsoft Dynamics Lifecycle Services (LCS) is a collaboration portal that provides an environment and a set of regularly updated services that can help you manage the lifecycle of your finance and operations implementations.

The lifecycle of an implementation spans many phases from pre-sales through Analysis, Design and Development, Test, and Deployment to Operation, possibly in multiple iterative roll-outs. It can last a few months to multiple years, based on the scope and complexity of the project and the chosen deployment model, for example, in the managed cloud or on-premises. 

The management of the implementation involves many different stakeholders from the customer and partner organizations and, especially in the cloud-hosted deployment model, from Microsoft. The implementation is supported through tools provided on LCS and through processes defined within the [Microsoft FastTrack](/dynamics365/fasttrack/) and through the partner's implementation approach. 

- [Lifecycle Services resources](../lifecycle-services/lcs.md)
- [Lifecycle Services (LCS) user guide](../lifecycle-services/lcs-user-guide.md)

## Deployment
You can deploy in the cloud or on-premises. Cloud deployments offer an enterprise resource planning (ERP) service that is fully managed by Microsoft. On-premises deployments are deployed locally in a customer's data center.

- [Software lifecycle policy and cloud releases](../migration-upgrade/versions-update-policy.md)
- [Cloud deployment overview](../deployment/cloud-deployment-overview.md)
- [System requirements for cloud deployments](../../fin-ops/get-started/system-requirements.md)
- [On-premises deployment home page](../deployment/on-premises-deployment-landing-page.md)
- [System requirements for on-premises deployments](../../fin-ops/get-started/system-requirements-on-prem.md)

## Upgrade
An upgrade can involve moving to a new product version, migrating and upgrading code, moving to an update, or deploying a hotfix.

Although the processes for each type of upgrade are similar, they differ enough that you should review the topics for a specific task before you begin.

- [Upgrades, updates, and hotfixes resources](../migration-upgrade/upgrade-home-page.md)

## Database management
For information to help you move a database to new environment and restore a database to a specific point in time, see [Database movement operations home page](../database/dbmovement-operations.md).

## Security
Finance and Operation apps uses role-based security. Access is granted only to security roles, not to individual users. Users are assigned to roles. A user who is assigned to a security role has access to the set of privileges that is associated with that role. A user who isn't assigned to any role has no privileges.

Role-based security is aligned with the structure of the business. The security roles that a user is assigned to depend on the user's responsibilities in the organization, and their participation in business processes. The administrator grants access to the duties that users in a role perform, not to the program elements that users must use.

Because rules can be set up for automatic role assignment, the administrator doesn't have to be involved every time that a user's responsibilities change. After security roles and rules have been set up, business managers can control day-to-day user access, based on business data.

- [Role-based security](role-based-security.md)
- [Security architecture](security-architecture.md)
- [Encryption in finance and operations apps](encryption.md)

## Batch processing
Many tasks can be run as part of batch jobs. For example, batch jobs can include tasks for printing reports, doing maintenance, or sending electronic documents. By using batch jobs, you can avoid slowing down your computer or the server during typical working hours.

- [Batch processing overview](batch-processing-overview.md)
- [Batch processing and batch servers](batch-server-overview.md)

## Optimization advisor
- [Optimization advisor overview](optimization-advisor-overview.md)
- [Optimization advisor (video)](https://www.youtube.com/watch?v=MRsAzgFCUSQ&t=4s)
- [Create rules for Optimization advisor](create-rules-optimization-advisor.md)

## Office integration
The integration with Microsoft Office provides a set of productive, collaborative, and integrated user experiences that take advantage of the Microsoft Office suite. This functionality can help your organization become more efficient and effective.

- [Office integration overview](../office-integration/office-integration.md)
- [Office integration tutorial](../office-integration/office-integration-tutorial.md)
- [Open entity data in Excel and update it by using the Excel add-in](../office-integration/use-excel-add-in.md)
- [Create Open in Excel experiences](../office-integration/office-integration-edit-excel.md)
- [Add templates to the Open lines in Excel menu](../user-interface/add-templates-open-lines-excel-menu.md)
- [Customize the Open in Microsoft Office menu](../office-integration/customize-open-office-menu.md)
- [Configure and send email](../../fin-ops/organization-administration/configure-email.md)
- [Troubleshoot the Office integration](../office-integration/office-integration-troubleshooting.md)

## Mobile
The finance and operations mobile app enables your organization to make its business processes available on mobile devices. After you enable the mobile workspaces for your organization, users can sign in to the app and immediately begin to run business processes from their mobile devices.

- [Mobile app home page](../mobile-apps/Mobile-app-home-page.md)
- [Available mobile workspaces](../mobile-apps/mobile-workspaces-released.md)

## Process Automation
The process automation framework allows administrators to view and create automated processes that will be scheduled with the batch server.  The added layer of visibility of scheduled work is presented in a calendar view that can be extended for use in application areas to allow non-system administrator users to view work that impacts their area. 

- [Process Automation home page](process-automation.md)

## General administration
- [Demo data overview](../../fin-ops/get-started/demo-data.md)
- [Cross-company data sharing](../sysadmin/cross-company-data-sharing.md)
- [Add links to your organization's legal terms and privacy statement](legal-terms-privacy-statement.md)
- [License codes and configuration keys report](license-codes-configuration-keys-report.md)
- [Maintenance mode](maintenance-mode.md)
- [Preconfigured system accounts](pre-configured-system-accounts.md)
- [Export business-to-business (B2B) users to Azure Active Directory](implement-b2b.md)
- [Set the session inactivity timeout](session-idle-timeout.md)
- [Build OData metadata cache when AOS starts](odata-warmup.md)
- [Configure and manage database logging](configure-manage-database-log.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
