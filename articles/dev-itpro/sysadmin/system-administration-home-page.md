---
# required metadata

title: System administration home page
description: This topic lists resources that are available for system administrators.
author: sericks007
manager: AnnBe
ms.date: 11/21/2017
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
ms.custom: 13531
ms.assetid: 2bb96ac4-0cef-4f66-a953-bd82c117247b
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# System administration home page

[!include[banner](../includes/banner.md)]

This topic points to content for system administrators of Microsoft Dynamics 365 for Finance and Operations, Enterprise edition. This content will help you configure the system so that it works smoothly and effectively for your organization.

## Lifecycle Services
Microsoft Dynamics Lifecycle Services (LCS) is a collaboration portal that provides an environment and a set of regularly updated services that can help you manage the application lifecycle of your Finance and Operations implementations.

- [Lifecycle Services for Finance and Operations](../lifecycle-services/lcs.md)
- [Dynamics Lifecycle Services user guide](../lifecycle-services/lcs-user-guide.md)

## Deployment
You can deploy Finance and Operations in the cloud or on-premises. Cloud deployments offer an enterprise resource planning (ERP) service that is fully managed by Microsoft. On-premises deployments are deployed locally in a customer's data center.

- [Online service and on-premises software lifecycle policy](../migration-upgrade/versions-update-policy.md)
- [Dynamics 365 for Finance and Operations, Enterprise edition cloud deployment overview](../deployment/cloud-deployment-overview.md)
- [System requirements for cloud deployments](../../fin-and-ops/get-started/system-requirements.md)
- [On-premises deployment landing page](../deployment/on-premises-deployment-landing-page.md)
- [System requirements for on-premises deployments](../../fin-and-ops/get-started/system-requirements-on-prem.md)

## Upgrade
An upgrade can involve moving to a new product version, migrating and upgrading code, moving to an update, or deploying a hotfix.

Although the processes for each type of upgrade are similar, they differ enough that you should review the topics for a specific task before you begin.

- [Upgrade home page](../migration-upgrade/upgrade-home-page.md)

## Database management
The following content will help you move a database to new environment and restore a database to a specific point in time:

- [Copy a Finance and Operations database from Azure SQL Database to a SQL Server environment](../database/copy-database-from-azure-sql-to-sql-server.md)
- [Copy a Finance and Operations database from SQL Server to a production Azure SQL Database environment](../database/copy-database-from-sql-server-to-azure-sql.md)
- [Restore a database on a non-production environment](../database/request-point-in-time-restore.md)
- [Create a copy of a Finance and Operations database to restore later](../database/copy-operations-database.md)

## Security
Finance and Operations uses role-based security. Access is granted only to security roles, not to individual users. Users are assigned to roles. A user who is assigned to a security role has access to the set of privileges that is associated with that role. A user who isn't assigned to any role has no privileges.

Role-based security is aligned with the structure of the business. The security roles that a user is assigned to depend on the user's responsibilities in the organization, and his or her participation in business processes. The administrator grants access to the duties that users in a role perform, not to the program elements that users must use.

Because rules can be set up for automatic role assignment, the administrator doesn't have to be involved every time that a user's responsibilities change. After security roles and rules have been set up, business managers can control day-to-day user access, based on business data.

- [Role-based security](role-based-security.md)
- [Security architecture](security-architecture.md)

## Batch processing
Many tasks in Finance and Operations can be run as part of batch jobs. For example, batch jobs can include tasks for printing reports, doing maintenance, or sending electronic documents. By using batch jobs, you can avoid slowing down your computer or the server during typical working hours.

- [Batch processing overview](batch-processing-overview.md)
- [Batch server overview](batch-server-overview.md)

## Optimization advisor
- [Optimization advisor (video)](https://www.youtube.com/watch?v=MRsAzgFCUSQ&t=4s)
- [Create rules for Optimization advisor](optimization-advisor.md)

## Office integration
The integration with Microsoft Office provides a set of productive, collaborative, and integrated user experiences that take advantage of the Microsoft Office suite. This functionality can help your organization become more efficient and effective.

- [Office integration](../office-integration/office-integration.md)
- [Office integration tutorial](../office-integration/office-integration-tutorial.md)
- [Use the Excel add-in](../office-integration/use-excel-add-in.md)
- [Create Open in Excel experiences](../office-integration/office-integration-edit-excel.md)
- [Add templates to the Open lines in Excel menu](../user-interface/add-templates-open-lines-excel-menu.md)
- [Customize the Open in Microsoft Office menu](../office-integration/customize-open-office-menu.md)
- [Configure and send email](../../fin-and-ops/organization-administration/configure-email.md)
- [Troubleshoot the Office integration](../office-integration/office-integration-troubleshooting.md)

## Mobile
The Microsoft Dynamics 365 for Unified Operations mobile app enables your organization to make its business processes available on mobile devices. After you enable the mobile workspaces for your organization, users can sign in to the app and immediately begin to run business processes from their mobile devices.

- [Mobile app home page](../mobile-apps/Mobile-app-home-page.md)
- [Mobile workspaces](../mobile-apps/mobile-workspaces-released.md)

## General administration
- [Demo data overview](../../fin-and-ops/get-started/demo-data.md)
- [Cross-company data sharing](../sysadmin/cross-company-data-sharing.md)
- [Add links to your organization's legal terms and privacy statement](legal-terms-privacy-statement.md)
- [License codes and configuration keys report](license-codes-configuration-keys-report.md)
- [Maintenance mode](maintenance-mode.md)
- [Pre-configured system accounts](pre-configured-system-accounts.md)
- [Export B2B users to Azure AD](implement-b2b.md)
