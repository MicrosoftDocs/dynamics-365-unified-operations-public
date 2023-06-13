---
title: Reset and change the type of a connected Microsoft Dataverse environment
description: This article explains how to reset or change the type of a Dataverse environment when finance and operations apps are integrated with Power Platform
author: abunduc-ms
ms.author: abunduc
ms.date: 06/02/2023
ms.topic: article
---

# Reset and change the type of a connected Microsoft Dataverse environment

When the Power Platform Integration is enabled, the finance and operations apps  and the customer engagements apps environments are tightly connected. The administrators should look at these two platforms as a one single environment, with multiple apps. In this article, we highlight the environment lifecycle scenarios impacted by the Power Platform Integration.

> [!IMPORTANT]
> The Power Platform Integration is not affected by the environment lifecycle scenarios described in this article, besides when the environments are deleted.

## Reset an environment from Power Platform admin center

It is not possible to Reset a linked environment from Power Platform admin center, the Reset button is not available.

:::image type="content" source="media/ppi-reset.png" alt-text="Reset option not available in Power Platform admin center." lightbox="media/ppi-reset.png":::

## Change the environment type from Power Platform admin center

It is possible to [convert a Power Platform admin center environment](/power-platform/admin/switch-environment) from sandbox to production or from production to sandbox, but it is **not recommended** for linked environments as this option is not available for finance and operations apps.

Aspects to consider when changing the environment type:

- **Sandbox to production**: The Dataverse environment becomes of type production, while the linked finance and operations apps remains of sandbox type. To link your Dataverse environment to a production finance and operations environment, the following steps need to be done:
  - Step 1: Deploy the finance and operations production environment without enabling the Power Platform Integration.
  - Step 2: [Refresh the database](/dynamics365/fin-ops-core/dev-itpro/database/database-refresh) from the finance and operations environment linked to the production Dataverse environment
  - Step 3: Delete the finance and operations sandbox environment to remove the link with the production Dataverse environment
  - Step 4: Apply the steps in [Connect finance and operations apps with an existing Microsoft Dataverse instance](environment-lifecycle-connect-finops-existing-dv.md) to link the production finance and operations apps environment to the production dataverse environment.

- **Production to sandbox**: The Dataverse environment becomes of type sandbox, while the linked finance and operations apps remains of type production. This configuration is not recommended. Since the Power Platform Integration link is irreversible, the customer cannot link the production finance and operations apps environment to another production Dataverse environment without deletion.

> [!IMPORTANT]
> It is highly **not recommended** to run production workloads in a sandbox environment. Sandbox environments do not benefit from the same level of SLAs as production ones.
