---
title: Change the type of connected environments
description: This article explains how to change the type of a Microsoft Dataverse environment when finance and operations apps are integrated with Power Platform
author: abunduc-ms
ms.author: abunduc
ms.date: 06/02/2023
ms.topic: conceptual
ms.reviewer: johnmichalak
ms.custom: bap-template
---

# Change the type of connected environments

When Power Platform Integration is enabled, the finance and operations apps and the customer engagements apps environments are tightly connected. Administrators should look at these two platforms as a one environment with multiple apps. This article highlights the environment lifecycle scenarios that are affected by Power Platform Integration.

> [!IMPORTANT]
> The Power Platform Integration isn't affected by the environment lifecycle scenarios described in this article.

## Change the environment type using Power Platform admin center

It's possible to [convert a Power Platform admin center environment](/power-platform/admin/switch-environment) from sandbox environment to a production environment or from a production environment to a sandbox environment. However, it **isn't recommended** for linked environments because this option isn't available for finance and operations apps.

The following sections contain aspects to consider when changing the environment type.

### Sandbox to production

In this scenario, the Microsoft Dataverse environment becomes a production environment, while the linked finance and operations apps remains a sandbox environment.

To link your Dataverse environment to a production finance and operations environment, complete the following steps.

1. Deploy the finance and operations production environment without enabling the Power Platform Integration.
1. Refresh the database from the finance and operations environment linked to the production Dataverse environment. For more information, see [Refresh the database](/dynamics365/fin-ops-core/dev-itpro/database/database-refresh).
1. Delete the finance and operations sandbox environment to remove the link with the production Dataverse environment.
1. Link the production finance and operations apps environment to the production Dataverse environment by following the steps in [Connect finance and operations apps with an existing Microsoft Dataverse instance](environment-lifecycle-connect-finops-existing-dv.md).

### Production to sandbox

In this scenario, the Dataverse environment becomes a sandbox environment, while the linked finance and operations apps remains a production environment. This configuration **isn't recommended**. Because the Power Platform Integration link is irreversible, you can't link the production finance and operations apps environment to another production Dataverse environment without deletion.

## Change the environment type using Lifecycle services

It isn't possible to change the environment type in Lifecycle services. Finance and operations apps environments have predefined types that can't be changed.

## Recommendations

It **isn't recommended** to run production workloads in a sandbox environment. Sandbox environments don't benefit from the same level of SLAs as production environments.
