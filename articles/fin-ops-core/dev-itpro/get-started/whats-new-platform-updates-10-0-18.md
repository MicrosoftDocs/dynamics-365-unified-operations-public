---
# required metadata

title: Platform updates for version 10.0.18 of Finance and Operations apps (May 2021)
description: This topic lists the features that are included in the platform updates for version 10.0.18 of Finance and Operations apps.
author: sericks007
ms.date: 04/15/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid:
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2021-03-31
ms.dyn365.ops.version: 10.0.18

---
# Platform updates for version 10.0.18 of Finance and Operations apps (May 2021)

[!include [banner](../includes/banner.md)]

This topic lists the features that are included in the platform updates for version 10.0.18 of Finance and Operations apps. This version has a build number of 7.0.5968 and is available on the following schedule:

- **Preview of release:** March 2021
- **General availability of release (self-update):** April 2021
- **General availability of release (auto-update):** May 2021

## Features included in this release

The following features are included in this release. Some of the listed features are still in preview, while others may already be generally available. See the [release plan](/dynamics365-release-plan/2021wave1/finance-operations/finance-operations-crossapp-capabilities/planned-features) for official release dates for each feature.

-  [Authentication for Finance and Operations apps upgraded to OWIN OpenID Connect](/dynamics365-release-plan/2021wave1/finance-operations/finance-operations-crossapp-capabilities/authentication-finance-operations-apps-upgraded-owin-openid-connect)

-  [Allow configuration of the publish batch size for the Excel add-in](/dynamics365-release-plan/2021wave1/finance-operations/finance-operations-crossapp-capabilities/allow-configuration-publish-batch-size-excel-add-in)<br>- For more information, see [View and update entity data with Excel](../office-integration/use-excel-add-in.md).

- [Extra NuGet file requires manual update to hosted Azure DevOps build pipeline](../dev-tools/pipeline-nuget-split.md)

-  [Align interaction patterns for combo boxes with those of look-up controls](/dynamics365-release-plan/2021wave1/finance-operations/finance-operations-crossapp-capabilities/align-interaction-patterns-combo-boxes-those-look-up-controls)

- [(Preview) Ensure required unbound controls are filled in](/dynamics365-release-plan/2021wave1/finance-operations/finance-operations-crossapp-capabilities/ensure-required-unbound-controls-are-filled)

- Allow admins to select default document types<br>- For more information, see [Configure document management](../../fin-ops/organization-administration/configure-document-management.md).

- Updates to the global address book<br>- For more information, see [Address books FAQ](../../fin-ops/organization-administration/qa-address-books.md).

-  [Automatic retry settings for batch jobs](/dynamics365-release-plan/2021wave1/finance-operations/finance-operations-crossapp-capabilities/automatic-retry-settings-batch-jobs)

Most of these features must be enabled using [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md) before you can use them. Some of the listed features are still in preview, while others may already be generally available. 

## Additional resources

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services (LCS), and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=561679&dbType=3&qc=13bb1641c1be430ead8b21ae3d4e0f800d5b81c39b3a56e890db1de7ede59e46).

### Dynamics 365: 2021 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2021 release wave 1 plan](/dynamics365-release-plan/2021wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic describes features that have been removed, or that are planned for removal in platform updates of Finance and Operations apps.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

A deprecation notice will be added in the [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic 12 months before the removal of any feature from the product.

For breaking changes that affect only compilation time, but that are binary-compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these changes are functional updates that must be made to the compiler.