---
title: Platform updates for version 10.0.25 of finance and operations apps (April 2022)
description: Learn about the features that are included in the platform updates for version 10.0.25 of finance and operations apps released in April 2022.
author: sericks007
ms.author: sericks
ms.topic: whats-new
ms.custom: 
  - bap-template
  - evergreen
ms.date: 04/12/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2022-01-31
---

# Platform updates for version 10.0.25 of finance and operations apps (April 2022)

[!include [banner](../../../finance/includes/banner.md)]

This article lists the features that are included in the platform updates for version 10.0.25 of finance and operations apps. This version has a build number of 7.0.6316 and is available on the following schedule:

- **Preview of release:** January 2022
- **General availability of release (self-update):** March 2022
- **General availability of release (auto-update):** April 2022

## Features included in this release

The following table lists the features that are included in this release.

For more information about how to use Feature management, see [Feature management](feature-management/feature-management-overview.md).

| Feature area    | Feature | More information | Enabled by |
|-----------------|---------|------------------|---------------------------|
| Web client | **Priority-based scheduling for batch jobs**<br><br>Priority-based scheduling decouples batch groups from the batch server and allows you to define priorities for batch groups.<br><br>It is no longer necessary to assign batch jobs to batch servers. Instead, relative scheduling priorities based on business requirements are used to determine the order in which tasks are run across available batch servers. | [Priority-based batch scheduling](../../dev-itpro/sysadmin/priority-based-batch-scheduling.md) | Feature management (*Batch priority-based scheduling*) |
| Web client | [Vertically scrolling workspaces](/dynamics365-release-plan/2022wave1/finance-operations/finance-operations-crossapp-capabilities/vertically-scrolling-workspaces)  | <ul><li>[Workspace form pattern](../../dev-itpro/user-interface/workspace-form-pattern.md)</li><li>[Build operational workspaces](../../dev-itpro/user-interface/build-workspaces.md)</li></ul> | Internal workspaces have been migrated to the newest visuals. External workspaces will need to migrate to maintain visual consistency.  |
| Web client  | [Upgrade jQuery UI to 1.13.0](/dynamics365-release-plan/2022wave1/finance-operations/finance-operations-crossapp-capabilities/open-source-software-update-upgrade-jquery-ui-1130) | | Feature management<br>(*Upgrade jQuery UI to 1.13.0*)|
| Web client  | [Saved views support for dialogs](/dynamics365-release-plan/2022wave1/finance-operations/finance-operations-crossapp-capabilities/updates-saved-views-personalization#view-support-for-dialogs)  | [Building forms that fully utilize saved views](../../dev-itpro/user-interface/understanding-saved-views.md)  | Feature management<br>(*Saved views support for dialogs*)  |
| Web client  | [Allow queries to be saved to views on Task Single and Task Double pages](/dynamics365-release-plan/2022wave1/finance-operations/finance-operations-crossapp-capabilities/updates-saved-views-personalization#queries-on-views-on-task-pages)  | [Building forms that fully utilize saved views](../../dev-itpro/user-interface/understanding-saved-views.md)  | Feature management<br>(*Allow queries to be saved to views on Task Single and Task Double pages*)  |
| Web client  | [(Preview) Saved views support for workspaces](/dynamics365-release-plan/2022wave1/finance-operations/finance-operations-crossapp-capabilities/updates-saved-views-personalization#view-support-for-workspaces)  | <ul><li>[Building forms that fully utilize saved views](../../dev-itpro/user-interface/understanding-saved-views.md)</li><li>[Personalize the user experience](../../dev-itpro/get-started/personalize-user-experience.md#adding-tiles-lists-and-links-to-a-workspace)</li></ul>  | Feature management<br>(*Saved views support for workspaces*)  |
| Web client  | <p>**Improved sort support for grouped grids**</p><p>When a user has grouped data in a grid by one or more columns, sorting on a non-grouped column will now leave the grouping intact and will sort the data inside each group based on the selected column</p> | [Grid capabilities](../../dev-itpro/get-started/grid-capabilities.md#sorting-grouped-data) | Default for the **Grouping in grids** feature in Feature management |
| Developer tools | <p>**Opt out individual grids from *Typing ahead of the system***</p><p>For forms with coding patterns that do not work well with the *Typing ahead of the system capability* of the new grid, developers can now opt out of an individual grid from asynchronous row validation and back to the legacy synchronous behavior.</p> | [Grid capabilities](../../dev-itpro/get-started/grid-capabilities.md) | Developer opt-in |
| Developer tools  | <p>**X++ unit testing with different values**</p><p>X++ unit tests can now take advantage of the SysTestRow attribute to re-use a test method with multiple different values.</p>  | [SysTestRow attribute for testing multiple values](../../dev-itpro/perf-test/systest-row.md) | Default   |
| Developer tools  | <p>**Run custom X++ scripts with zero downtime**</p><p>This feature lets you upload and run deployable packages that contain custom X++ scripts without having to go through Microsoft Dynamics Lifecycle Services (LCS) or suspend your system. Therefore, you can correct minor data inconsistences without causing any disruptive downtime.</p> | [Run custom X++ scripts with zero downtime](../../dev-itpro/deployment/run-custom-scripts.md)  | Default |
| Developer tools | <p>**Saved views support for custom filters**</p><p>New APIs are available to allow custom filters to work more seamlessly with saved views. Specifically, custom filters can now trigger a view definition to be marked as having unsaved changes, and custom filter controls can listen for system changes to the query to ensure the control value stays in sync with the query.</p> | [Building forms that fully utilize saved views](../../dev-itpro/user-interface/understanding-saved-views.md) | Developer opt-in |
| Developer tools | <p>**Opt out individual forms from saved views**</p><p>For forms with coding patterns that are not conducive to saved views, developers can now opt out of an individual form of saved views support. This will mean that no view selector is available on the form and there will be no publish capabilities.</p> | [Building forms that fully utilize saved views](../../dev-itpro/user-interface/understanding-saved-views.md) | Developer opt-in |


### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services (LCS), and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=654580&dbType=3&qc=3799fa965b008dd980d27cf740e4582e6384ec6601ae8a35b7eaec6f1287a868).

### Dynamics 365: 2022 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2022 release wave 1 plan](/dynamics365-release-plan/2022wave1). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) article describes features that have been removed, or that are planned for removal in platform updates of finance and operations apps.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

A deprecation notice will be added in the [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) article 12 months before the removal of any feature from the product.

For breaking changes that affect only compilation time, but that are binary-compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these changes are functional updates that must be made to the compiler.

