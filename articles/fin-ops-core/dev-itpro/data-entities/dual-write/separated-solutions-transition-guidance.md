---
title: Transition from dual-write application orchestration package to split packages
description: The Dual-write Application Orchestration package is no longer a single package but has been separated into smaller packages. This article explains how to switch from the orchestration package to the individual.
author: abunduc-ms
ms.author: abunduc
ms.date: 04/27/2023
ms.topic: article
---

# Transition from dual-write application orchestration package to split packages

Before March 2022, when setting up dual-write, customers had to install the dual-write application orchestration package from the app source. This package contained solutions for all application logic including all table maps. Customers were in all or nothing situation where they had to have all solutions installed even if they would only require using a subset.

To solve this problem, we split the monolith orchestration package into smaller individual packages. The individual packages contain solutions with the same name, publisher, and map versions as the application orchestration package. Therefore, this is a non-breaking change and environments can easily upgrade by installing the split packages required from app source.

> [!IMPORTANT]
> The orchestration solution is no longer being maintained and it will be deprecated. In order to benefit from enhancements and bug fixes, we recommend installing the split packages.

## What do you need to do to install the split packages?

Repeat these steps for all environments:

1. Identify which are the split solution packages required.

2. Install required packages.

3. If table maps were updated in the split packages, apply the updates in the dual-write workspace.

As with any app updates, we advise to apply these steps in lower environments first and perform regression testing for your specific use cases.

### 1. Identify which are the split solution packages required

You can easily identify the packages required by tracking the entities or table maps that you are syncing today. The entities and maps included in the solutions of each split package are detailed in this article [Separated Dual-write Application Orchestration package](/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/separated-solutions).

:::image type="content" source="media/find-entity-in-split-package.png" alt-text="Find entity in split package." lightbox="media/find-entity-in-split-package.png":::

For example:

- if you are syncing contacts, therefore using Customers V3, you would need to install the Dual-write Application Core and Dual-write Finance packages.

- if you are syncing products, you would need to install Dual-write Supply Chain package and its dependencies.

For a full prospect to cash flow, with customers, products, quotes and orders being synced, the required packages are:

- Dual-write Application Core package

- Dual-write Finance package

- Dual-write Human Resources package

- Dynamics 365 HR Common Tables

- Dual-write Supply Chain

### 2. Install required packages

With an administrator account, open Power Platform Admin Center, then the environment to upgrade, then Resources, Dynamics 365 Apps and click on Open App Source.

Search for dual-write and observe the packages available. Install those that are required. You would need to install the dependencies first.

:::image type="content" source="media/dual-write-packages-app-source.png" alt-text="Dual-write packages in app source." lightbox="media/dual-write-packages-app-source.png":::

### 3. Apply solutions in Dual-write workspace

Once the packages/apps have completed installation (status is Installed), one or more solutions containing the latest features and table maps will be installed in Dataverse.

Based on the information provided in the [Dual-write release notes](/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/whats-new-dual-write), identify if any of the split packages installed have table maps updates. You can identify if a package has table maps updates if the solution containing table maps will have "Has new changes" set to Yes. For example:

:::image type="content" source="media/package-with-update.png" alt-text="Package which has updated table maps." lightbox="media/package-with-update.png":::

If yes, then open Dual-write workspace, click Apply solutions and then choose to install the relevant solutions.

:::image type="content" source="media/apply-solution.png" alt-text="Apply a solution from the dual-write workspace." lightbox="media/apply-solution.png":::

Here is the complete list of solutions containing table maps per each split package:

| **Package**                                        | **Solution table maps to apply in Dual-write workspace**  |
|----------------------------------------------------|-----------------------------------------------------------|
| Dual-write Application Core                        | Dual-write applications core entity maps                  |
| Dual-write Human Resources                         | Dynamics 365 Human Resources entity maps                  |
| Dual-write Supply Chain                            | Dynamics 365 Supply Chain Management extended entity maps |
| Dual-write Finance                                 | Dynamics 365 Finance extended entity map                  |
| Dual-write Notes                                   | Dynamics 365 notes entity maps                            |
| Dual-write Asset Management                        | Dynamics 365 Asset Management entity maps                 |
| Dual-write party and global address book solutions | Dynamics 365 GAB Dual Write Entity Maps                   |
