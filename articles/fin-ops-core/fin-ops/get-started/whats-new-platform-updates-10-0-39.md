---
title: Platform updates for version 10.0.39 of finance and operations apps (February 2024)
description: Learn about the features that are included in the platform updates for version 10.0.39 of finance and operations apps released in February 2024.
author: johnmichalak
ms.author: johnmichalak
ms.topic: whats-new
ms.custom: 
  - bap-template
  - evergreen
ms.date: 04/12/2024
ms.reviewer: johnmichalak
ms.search.region: Global
---

# Platform updates for version 10.0.39 of finance and operations apps (February 2024)

[!include [banner](../includes/banner.md)]

This article lists the features that are included in the platform updates for version 10.0.39 of finance and operations apps. This version has a build number of 7.0.7198.18 and is available on the following schedule:

- **Preview of release:** January 2024
- **General availability of release (self-update):** February 2024
- **General availability of release (auto-update):** March 2024

## Features included in this release

This section contains a table that lists the features that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| System Administration | Removed or Deprecated - ISV Licenses generated using SHA1 algorithm (signature version 1) | [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md#isv-licenses-generated-using-sha1-algorithm-signature-version-1) | Feature management | 
| Web client | Microsoft Graph mail provider | This is the replacement mail provider for the deprecated Exchange provider, which no longer works mid September 2024. For more information, see [Configure or send email](../../dev-itpro/organization-administration/configure-email.md#send-email-with-microsoft-graph). | Admin configuration |
| Web client | Autoblocking of high-volume notification rules | For more information, see [Messaging system](../../dev-itpro/user-interface/messaging-user.md#how-do-i-manage-processes-that-generate-lots-of-notifications) | On by default (Feature management) |
| System Administration | Clean stale data of Batch Job tables | For more information, see [Clean up the batch job table](../../dev-itpro/sysadmin/batch-job-cleanup.md) | Default |
| System Administration | Batch Header now has a method BatchHeader::isCurrentBatchTaskBeingCancelled() which can be used in batch classes to immediately return and cancel execution if that is needed. | |
| Row version change tracking for tables and data entities | Row version change tracking | Finance and operations apps have a change tracking functionality option available that's known as row version change tracking. Change tracking enables incremental synchronization of Finance and Operations apps to Microsoft Dataverse and is a prerequisite for several features. This feature is available since version 10.0.34. With version 10.0.39 the feature is enabled by default in all finance and operations apps environments. In version 10.0.39, the **SysRowVersionNumber** column is deprecated and replaced with SysRowVersion column for all out-of-the-box tables. For more information, see [Enable row version change tracking functionality](../../dev-itpro/data-entities/rowversion-change-track.md#enable-row-version-change-tracking-functionality). | Default |
| Power Platform Integration | Enable Finance and Operations user impersonation in Dataverse | Beginning March 1, 2024 the [Enable Finance and Operations user impersonation in Dataverse](/power-platform/admin/settings-features#Finance-and-Operations-in-Dataverse) toggle in the Power Platform Admin Center is removed. With continued efforts to unify finance and operations apps with the Power Platform through the [Power Platform integration](../../dev-itpro/power-platform/overview.md) and [unified admin experiences](/power-platform/admin/unified-experience/finance-operations-apps-overview), finance and operations apps are now considered applications within the unified Business Application Platform (BAP) environment. In a unified environment, the capabilities granted by the toggle are now assumed to be true for any environment with finance and operations apps installed. | Default |

## Feature enhancements included in this release

This section contains a table that lists the enhancements that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| System Administration | Batch Job History and Custom Batch Job History cleanup | For more information, see [Clean up the batch job history](../../dev-itpro/sysadmin/batch-history-cleanup.md) | Default |
| System Administration | Batch Job History | If the batch job has more than 5,000 batch tasks, then the corresponding job history would only save first 2,500 tasks, preferring tasks with status in following order: **Error -> Canceled -> Finished -> Not Run**. This measure has been implemented to prevent blocking batch related tables that may occur due to such large jobs. For more information, see [Create a batch job](../sysadmin/create-batch-job.md). | Default |
| Business Events | Fixed the issue where Batch Business Events were always raised in DAT entity while Job was in any other business entity. | | |
| Row version change tracking for tables and data entities | Row version change tracking | Finance and operations apps have a change tracking functionality option available that's known as row version change tracking. Change tracking enables incremental synchronization of Finance and Operations apps to Microsoft Dataverse and is a prerequisite for several features. This feature is available since version 10.0.34. With version 10.0.39 the feature is enabled by default in all finance and operations apps environments. In version 10.0.39, the SysRowVersionNumber column is deprecated and replaced by SysRowVersion column for all out-of-the-box tables. For more information on  managing risks, see [Enable row version change tracking functionality](../../dev-itpro/data-entities/rowversion-change-track.md#enable-row-version-change-tracking-functionality). | Default |
| Generating ISV licenses | SHA256 algorithm for generating ISV licenses | SHA256 - To ensure the security and integrity of your system and data, we strongly encourage all our customers to migrate to the more secure SHA256 algorithm for generating ISV licenses. This [replaces](removed-deprecated-features-platform-updates.md#isv-licenses-generated-using-sha1-algorithm-signature-version-1) the SHA1 algorithm. | Default |
| System Administration | Application users must be present in your Microsoft Entra ID tenant. | Admins can use the new Invalid Users form to determine and [fix invalid users](/dynamics365/fin-ops-core/fin-ops/sysadmin/invalid-users) in the application. | Default |


This replaces the SHA1 algorithm. 


### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=886261).

### Dynamics 365: 2023 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2024 release wave 1 plan](/dynamics365/release-plan/2024wave1/). All of the details, end to end, top to bottom, are captured in a single document that you can use for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md) topic describes features that have been removed, or that are planned for removal in platform updates of finance and operations apps.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

Deprecation notices are added in the [Removed or deprecated platform features](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md) article 12 months before the removal of any feature from the product.

For breaking changes that affect only compilation time, but that are binary-compatible with sandbox and production environments, the deprecation time is less than 12 months. Typically, these changes are 
functional updates that must be made to the compiler.
