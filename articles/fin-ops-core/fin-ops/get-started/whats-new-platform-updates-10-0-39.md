---
# required metadata

title: Platform updates for version 10.0.39 of finance and operations apps (March 2024)
description: This article lists the features that are included in the platform updates for version 10.0.39 of finance and operations apps.
author: johnmichalak
ms.date: 12/05/2023
ms.topic: conceptual
ms.custom: 
  - bap-template
audience: Application User
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: johnmichalak

---
# Platform updates for version 10.0.39 of finance and operations apps (March 2024)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article lists the features that are included in the platform updates for version 10.0.39 of finance and operations apps. This version has a build number of 7.0.NNNN and is available on the following schedule:

- **Preview of release:** January 2024
- **General availability of release (self-update):** March 2024
- **General availability of release (auto-update):** April 2024

## Features included in this release

This section will contain a table that lists the features that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| System Administration | Removed or Deprecated - ISV Licenses generated using SHA1 algorithm (signature version 1) | [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md#isv-licenses-generated-using-sha1-algorithm-signature-version-1) | Feature management | 
| Web client | Microsoft Graph mail provider | This is the replacement mail provider for the deprecated Exchange provider, which will no longer work mid September 2024. See [Configure or send email](../../dev-itpro/organization-administration/configure-email.md#send-email-with-microsoft-graph) for more details on configuration. | Admin configuration |
| Web client | Auto-blocking of high-volume notification rules | [Messaging system](../../dev-itpro/user-interface/messaging-user.md#how-do-i-manage-processes-that-generate-lots-of-notifications.md) | On by default (Feature management) |
| System Administration | Clean stale data of Batch Job tables | [Clean up the batch job table](../../fin-ops-core/dev-itpro/sysadmin/batch-job-cleanup.md) | Default |
| System Administration | Batch Header now has a method BatchHeader::isCurrentBatchTaskBeingCancelled() which can be used in batch classes to immediately return and cancel execution if that is needed. | |

## Feature enhancements included in this release

This section will contain a table that lists the enhancements that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Lifecycle Services | Batch Job History cleanup as well as Custom Batch Job History cleanup | [Clean up the batch job history](../../fin-ops-core/dev-itpro/sysadmin/batch-history-cleanup.md) | |
| Business Events | Fixed the issue where Business Events were always raised in DAT entity while Job was in any other business entity. | | |

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=NNNNNN).

### Dynamics 365: 2023 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2023 release wave 1 plan](/dynamics365/release-plan/2023wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md) topic describes features that have been removed, or that are planned for removal in platform updates of finance and operations apps.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

A deprecation notice will be added in the [Removed or deprecated platform features](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md) topic 12 months before the removal of any feature from the product.

For breaking changes that affect only compilation time, but that are binary-compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these changes are 
functional updates that must be made to the compiler.
