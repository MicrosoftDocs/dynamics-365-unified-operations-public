---
# required metadata

title: Platform updates for version 10.0.25 of Finance and Operations apps (April 2022)
description: This topic lists the features that are included in the platform updates for version 10.0.25 of Finance and Operations apps.
author: sericks007
ms.date: 01/11/2022
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: sericks
ms.search.validFrom: 2022-01-31

---
# Platform updates for version 10.0.25 of Finance and Operations apps (April 2022)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic lists the features that are included in the platform updates for version 10.0.25 of Finance and Operations apps. This version has a build number of 7.0.XXXX and is available on the following schedule:

- **Preview of release:** January 2022
- **General availability of release (self-update):** March 2022
- **General availability of release (auto-update):** April 2022

## Features included in this release

The following table lists the features that are included in this release.

| Feature area    | Feature | More information | Enabled by |
|-----------------|---------|------------------|---------------------------|
| Developer tools  | <p>**Run custom X++ scripts with zero downtime**</p><p>This feature lets you upload and run deployable packages that contain custom X++ scripts without having to go through Microsoft Dynamics Lifecycle Services (LCS) or suspend your system. Therefore, you can correct minor data inconsistences without causing any disruptive downtime.</p> | [Run custom X++ scripts with zero downtime](../deployment/organization-administration/run-custom-scripts.md)  | Default |
| Web client | [Vertically scrolling workspaces](https://docs.microsoft.com/en-us/dynamics365-release-plan/2022wave1/finance-operations/finance-operations-crossapp-capabilities/vertically-scrolling-workspaces)  | <ul><li>[Workspace form pattern](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/user-interface/workspace-form-pattern)</li><li>[Build operational workspaces](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/user-interface/build-workspaces)</li></ul> | Internal workspaces have been migrated to the newest visuals. External workspaces will need to migrate to maintain visual consistency.  |
| Web client  | <p>**Upgrade jQuery UI to 1.13.0**</p><p>This feature upgrades jQuery UI to version 1.13.0 (from 1.12.1) for Finance and Operations applications. Before enabling this feature, you should test any extensible controls or custom JavaScript code, specifically those utilizing jQuery UI APIs. This feature is targeted to be required with the Fall 2022 release, but is currently optional to allow time for migration of affected APIs.</p> | | [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md)<br>(*Upgrade jQuery UI to 1.13.0*)|
| Web client  | [Saved views support for dialogs](https://docs.microsoft.com/en-us/dynamics365-release-plan/2022wave1/finance-operations/finance-operations-crossapp-capabilities/updates-saved-views-personalization#view-support-for-dialogs)  | [Building forms that fully utilize saved views](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/user-interface/understanding-saved-views)  | [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md)<br>(*Saved views support for dialogs*)  |
| Web client  | [Allow queries to be saved to views on Task Single and Task Double pages](https://docs.microsoft.com/en-us/dynamics365-release-plan/2022wave1/finance-operations/finance-operations-crossapp-capabilities/updates-saved-views-personalization#queries-on-views-on-task-pages)  | [Building forms that fully utilize saved views](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/user-interface/understanding-saved-views)  | [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md)<br>(*Allow queries to be saved to views on Task Single and Task Double pages*)  |
| Web client  | [(Preview) Saved views support for workspaces](https://docs.microsoft.com/en-us/dynamics365-release-plan/2022wave1/finance-operations/finance-operations-crossapp-capabilities/updates-saved-views-personalization#view-support-for-workspaces)  | <ul><li>[Building forms that fully utilize saved views](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/user-interface/understanding-saved-views)</li><li>[Personalize the user experience](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/get-started/personalize-user-experience#adding-tiles-lists-and-links-to-a-workspace)</li></ul>  | [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md)<br>(*Saved views support for workspaces*)  |
| Developer tools | <p>**Saved views support for custom filters**</p><p>New APIs are available to allow custom filters to work more seamlessly with saved views. Specifically, custom filters can now trigger a view definition to be marked as having unsaved changes, and custom filter controls can listen for system changes to the query to ensure the control value stays in sync with the query.</p> | [Building forms that fully utilize saved views](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/user-interface/understanding-saved-views) | Developer opt-in |
| Developer tools | <p>**Opt individual forms out of saved views**</p><p>For forms with coding patterns that are not conducive to saved views, developers can now opt an individual form out of saved views support. This will mean that no view selector is available on the form and there will be no publish capabilities.</p> | [Building forms that fully utilize saved views](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/user-interface/understanding-saved-views) | Developer opt-in |
| Web client  | <p>**Improved sort support for grouped grids**</p><p>When a user has grouped data in a grid by one or more columns, sorting on a non-grouped column will now leave the grouping intact and will sort the data inside each group based on the selected column</p> | [Grid capabilities](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/jasongre-update49/articles/fin-ops-core/fin-ops/get-started/grid-capabilities.md#sorting-grouped-data) | Default for the **Grouping in grids** feature in Feature management |
| Developer tools | <p>**Opt out individual grids from *Typing ahead of the system***</p><p>For forms with coding patterns that do not lend themselves to working well with the *Typing ahead of the system capability* of the new grid, developers can now opt an individual grid out of asychronous row validation and back to the legacy synchronous behavior.</p> | [Grid capabilities](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/jasongre-update49/articles/fin-ops-core/fin-ops/get-started/grid-capabilities.md#developer-opting-out-individual-grids-from-typing-ahead-of-the-system) | Developer opt-in |
| Developer Tools  | <p>**X++ Unit Testing with different values**</p><p>X++ unit tests can now take advantage of the SysTestRow attribute to re-use a test method with multiple different values.</p>  | [SysTestRow attribute for testing multiple values](../perf-test/systest-row.md) | How do you turn this feature on? If you turn it on in Feature management, say: [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md)   |
| Feature area  | [Name of feature](URL to feature description in the Release Plans)  | [Topic name](URL to topic with more information in core documentation)  | How do you turn this feature on? If you turn it on in Feature management, say: [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md)   |

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services (LCS), and view the [KB article](https://lcs.dynamics.com/).

### Dynamics 365: 2021 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2021 release wave 2 plan](/dynamics365-release-plan/2021wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic describes features that have been removed, or that are planned for removal in platform updates of Finance and Operations apps.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

A deprecation notice will be added in the [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic 12 months before the removal of any feature from the product.

For breaking changes that affect only compilation time, but that are binary-compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these changes are functional updates that must be made to the compiler.
