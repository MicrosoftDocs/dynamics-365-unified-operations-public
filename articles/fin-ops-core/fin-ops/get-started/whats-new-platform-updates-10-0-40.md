---
title: Platform updates for version 10.0.40 of finance and operations apps (June 2024)
description: This article lists the features that are included in the platform updates for version 10.0.40 of finance and operations apps.
author: johnmichalak
ms.author: johnmichalak
ms.date: 06/12/2024
ms.topic: whats-new
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: johnmichalak
ms.search.region: Global
---
# Platform updates for version 10.0.40 of finance and operations apps (June 2024)

[!include [banner](../includes/banner.md)]

This article lists the features that are included in the platform updates for version 10.0.40 of finance and operations apps. This version has a build number of 7.0.7279.17 and is available on the following schedule:

- **Preview of release:** April 2024
- **General availability of release (self-update):** June 2024
- **General availability of release (auto-update):** July 2024

## Features included in this release

This section contains a table that lists the features that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Copilot in finance and operations apps | Extend Copilot with client plugins | Developers can extend Copilot in finance and operations apps by creating client actions that are based on application logic and invoked in natural language from the Copilot chat panel. For more information, see [Create client plugins for Copilot in finance and operations apps](../../dev-itpro/copilot/copilot-client-plugins.md). | Default |
| Copilot in finance and operations apps | Extend Copilot with record context | The context of the record that the user is currently viewing in the application is available in Copilot and can be used to create contextual plugins. For more information, see [Use application context with Copilot](../../dev-itpro/copilot/copilot-application-context.md). | Default |
| System administration | Archive with Dataverse long term retention | This feature lets you archive data for select high volume areas of the product. The data is archived using a micro-service and a connection to Dataverse. You must first install the service from the Power platform admin center (PPAC).  For more information, see [Archive with Dataverse long term retention](../../dev-itpro/sysadmin/archive-data.md). | Feature Management |

## Feature enhancements included in this release

This section contains a table that lists the enhancements that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=932660).

### Dynamics 365: 2024 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2024 release wave 1 plan](/dynamics365/release-plan/2024wave1/). All of the details, end to end, top to bottom, are captured in a single document that you can use for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md) topic describes features that have been removed, or that are planned for removal in platform updates of finance and operations apps.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

Deprecation notices are added in the [Removed or deprecated platform features](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md) article 12 months before the removal of any feature from the product.

For breaking changes that affect only compilation time, but that are binary-compatible with sandbox and production environments, the deprecation time is less than 12 months. Typically, these changes are 
functional updates that must be made to the compiler.
