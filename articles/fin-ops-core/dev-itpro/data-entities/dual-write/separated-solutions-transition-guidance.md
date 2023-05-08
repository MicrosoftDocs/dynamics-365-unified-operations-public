---
title: Transition from the Dual-write Application Orchestration package to split packages
description: The Dual-write Application Orchestration package is no longer a single package but has been split into smaller packages. This article explains how to switch to the split packages.
author: abunduc-ms
ms.author: abunduc
ms.date: 05/04/2023
ms.topic: article
---

# Transition from the Dual-write Application Orchestration package to split packages

[!INCLUDE[banner](../../includes/banner.md)]

Before March 2022, when customers set up dual-write, they had to install the Dual-write Application Orchestration package from Microsoft AppSource. This package contained solutions for all application logic, including all table maps. Therefore, customers were in an "all or nothing" situation, where they had to install all solutions, even if they had to use only a subset.

To fix this issue, Microsoft split the monolithic application orchestration package into smaller individual packages. These individual packages contain solutions that have the same name, publisher, and map versions as the application orchestration package. Therefore, this change is nonbreaking, and customers can easily upgrade environments by installing the required split packages from AppSource.

> [!IMPORTANT]
> The orchestration solution is no longer being maintained and will be deprecated. We recommend that you install the split packages, so that you can continue to benefit from enhancements and updates.

## What you must do to install the split packages

Follow these steps for each environment.

1. Identify which split solution packages are required.
2. Install the required packages.
3. If table maps were updated in the split packages, apply the updates in the **Dual-write** workspace.

As for any app update, we recommend that you first complete these steps in lower environments and do regression testing for your specific use cases.

### Step 1. Identify which split solution packages are required

You can easily identify the packages that are required by tracking the entities or table maps that you're currently syncing. For information about the entities and maps that are included in the solutions of each split package, see [Separated Dual-write Application Orchestration package](/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/separated-solutions). In the following illustration, a user is searching that article for information about contact-related maps in the Dual-write Finance package.

:::image type="content" source="media/find-entity-in-split-package.png" alt-text='Screenshot that shows the "Dual-write Finance" section of the "Separated Dual-write Application Orchestration package" article, where contact-related maps are highlighted by the browser's search functionality.' lightbox="media/find-entity-in-split-package.png":::

Here are some examples:

- If you're syncing contacts and therefore using **Customers V3**, you must install the Dual-write Application Core and Dual-write Finance packages.
- If you're syncing products, you must install the Dual-write Supply Chain package and its dependencies.
- If you're syncing a full prospect-to-cash flow, where customers, products, quotes, and orders are being synced, you must install the following packages:

    - Dual-write Application Core package
    - Dual-write Finance package
    - Dual-write Human Resources package
    - Dynamics 365 HR Common Tables
    - Dual-write Supply Chain

### Step 2. Install the required packages

To install the required packages, follow these steps.

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/) by using an administrator account.
1. Select the environment to upgrade.
1. In the left navigation, under **Resources**, select **Dynamics 365 Apps**.
1. Select **Open App Source**.
1. Search for "dual-write," and review the available packages in the search results. 

    :::image type="content" source="media/dual-write-packages-app-source.png" alt-text="Screenshot of the dual-write packages in AppSource." lightbox="media/dual-write-packages-app-source.png":::

1. Install the available packages that are required. You must first install any dependencies.

For a complete list of split packages and dependencies, see [Separated Dual-write Application Orchestration package](/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/separated-solutions).

### Step 3. Apply solutions in the Dual-write workspace

When installation of the packages/apps is completed, and their status is **Installed**, one or more solutions that contain the latest features and table maps are installed in Dataverse.

Use the information in the [dual-write release notes](/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/whats-new-dual-write) to determine whether any of the split packages that were installed have table map updates. You'll know that a package has table maps updates if the **Has new changes** option is set to **Yes** for the solution that contains table maps. If the **Has new changes** option is set to **Yes** for any table maps, open the **Dual-write** workspace, select **Apply solution**, and then select to install the relevant solutions.

:::image type="content" source="media/apply-solution.png" alt-text="Screenshot that highlights the Apply solution button in the Dual-write workspace." lightbox="media/apply-solution.png":::

The following table shows the complete list of solutions that contain table maps for each split package.

| Package                                            | Solution table maps to apply in the Dual-write workspace  |
|----------------------------------------------------|-----------------------------------------------------------|
| Dual-write Application Core                        | Dual-write applications core entity maps                  |
| Dual-write Human Resources                         | Dynamics 365 Human Resources entity maps                  |
| Dual-write Supply Chain                            | Dynamics 365 Supply Chain Management extended entity maps |
| Dual-write Finance                                 | Dynamics 365 Finance extended entity map                  |
| Dual-write Notes                                   | Dynamics 365 notes entity maps                            |
| Dual-write Asset Management                        | Dynamics 365 Asset Management entity maps                 |
| Dual-write party and global address book solutions | Dynamics 365 GAB Dual Write Entity Maps                   |

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
