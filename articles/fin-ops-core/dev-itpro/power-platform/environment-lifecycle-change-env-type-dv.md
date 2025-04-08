---
title: Change the type of connected environments
description: Learn about how to change the type of a Microsoft Dataverse environment when finance and operations apps are integrated with Microsoft Power Platform.
author: abunduc-ms
ms.author: abunduc
ms.topic: conceptual
ms.date: 06/19/2024
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
---

# Change the type of connected environments

When Microsoft Power Platform Integration is enabled, the finance and operations apps environment and the customer engagements apps environment are tightly connected. Administrators should regard these two platforms as one environment that has multiple apps. This article describes the environment lifecycle scenarios that are affected by Power Platform Integration.

> [!IMPORTANT]
> Power Platform Integration isn't affected by the environment lifecycle scenarios that are described in this article.

## Change the environment type by using Power Platform admin center

You can [convert a Power Platform admin center environment](/power-platform/admin/switch-environment) from a sandbox environment to a production environment, or from a production environment to a sandbox environment. However, we do **not** recommend this approach for linked environments, because this option isn't available for finance and operations apps.

The following sections describe aspects that you should consider when you change the environment type.

### Sandbox to production

In this scenario, the Dataverse environment becomes a production environment, whereas the linked finance and operations apps environment remains a sandbox environment.

To link your Dataverse environment to a production finance and operations environment, follow these steps.

1. Deploy the finance and operations production environment without enabling Power Platform Integration.
1. Refresh the database from the finance and operations environment that's linked to the production Dataverse environment. For more information, see [Refresh the database](/dynamics365/fin-ops-core/dev-itpro/database/database-refresh).
1. Delete the finance and operations sandbox environment to remove the link with the production Dataverse environment.
1. Link the production finance and operations apps environment to the production Dataverse environment by following the steps in [Connect finance and operations apps with an existing Microsoft Dataverse instance](environment-lifecycle-connect-finops-existing-dv.md).

### Production to sandbox

In this scenario, the Dataverse environment becomes a sandbox environment, whereas the linked finance and operations apps environment remains a production environment. This configuration is **not** recommended. Because the Power Platform Integration link is irreversible, you can't link the production finance and operations apps environment to another production Dataverse environment without deletion.

## Change the environment type by using Lifecycle Services

You can't change the environment type in Microsoft Dynamics Lifecycle Services. Finance and operations apps environments have predefined types that can't be changed.

## Recommendations

We do **not** recommend that you run production workloads in a sandbox environment. Sandbox environments don't benefit from the same level of service level agreements (SLAs) as production environments.
