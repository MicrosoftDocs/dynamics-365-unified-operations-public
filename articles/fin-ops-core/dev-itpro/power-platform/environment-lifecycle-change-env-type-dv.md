---
title: Change the type of connected environments
description: Learn about how to change the type of a Microsoft Dataverse environment when finance and operations apps are integrated with Microsoft Power Platform.
author: abunduc-ms
ms.author: johnmichalak
ms.topic: how-to
ms.date: 01/22/2026
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
---

# Change the type of connected environments

When you enable Microsoft Power Platform Integration, the finance and operations apps environment and the customer engagements apps environment connect tightly. Administrators should regard these two platforms as one environment that has multiple apps. This article describes the environment lifecycle scenarios that Power Platform Integration affects.

> [!IMPORTANT]
> Power Platform Integration isn't affected by the environment lifecycle scenarios that this article describes.

## Change the environment type by using Power Platform admin center

You can [convert a Power Platform admin center environment](/power-platform/admin/switch-environment) from a sandbox environment to a production environment, or from a production environment to a sandbox environment. However, don't use this approach for linked environments, because finance and operations apps don't support this option.

The following sections describe aspects that you should consider when you change the environment type.

### Sandbox to production

In this scenario, the Dataverse environment becomes a production environment, whereas the linked finance and operations apps environment remains a sandbox environment.

To link your Dataverse environment to a production finance and operations environment, follow these steps:

1. Deploy the finance and operations production environment without enabling Power Platform Integration.
1. Refresh the database from the finance and operations environment that's linked to the production Dataverse environment. For more information, see [Refresh the database](/dynamics365/fin-ops-core/dev-itpro/database/database-refresh).
1. Delete the finance and operations sandbox environment to remove the link with the production Dataverse environment.
1. Link the production finance and operations apps environment to the production Dataverse environment by following the steps in [Connect finance and operations apps with an existing Microsoft Dataverse instance](environment-lifecycle-connect-finops-existing-dv.md).

### Production to sandbox

In this scenario, the Dataverse environment becomes a sandbox environment, whereas the linked finance and operations apps environment remains a production environment. Don't use this configuration. Because the Power Platform Integration link is irreversible, you can't link the production finance and operations apps environment to another production Dataverse environment without deletion.

## Change the environment type by using Lifecycle Services

You can't change the environment type in Microsoft Dynamics Lifecycle Services. Finance and operations apps environments have predefined types that you can't change.

## Recommendations

Don't run production workloads in a sandbox environment. Sandbox environments don't have the same level of service level agreements (SLAs) as production environments.
