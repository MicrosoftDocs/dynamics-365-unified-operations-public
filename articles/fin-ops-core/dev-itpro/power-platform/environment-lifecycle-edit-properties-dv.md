---
title: Edit the properties of a connected Microsoft Dataverse environment
description: This article explains how to edit the properties of a Dataverse environment when finance and operations apps are integrated with Power Platform
author: abunduc-ms
ms.author: abunduc
ms.date: 06/02/2023
ms.topic: conceptual
ms.reviewer: johnmichala
ms.custom: bap-template
---

# Edit the properties connected environments

When Microsoft Power Platform Integration is enabled, the finance and operations apps and the customer engagements apps environments are tightly connected. Administrators should look at these two platforms as a one environment with multiple apps. This article describes how Power Platform Integration impacts editing the properties of an environment.

> [!IMPORTANT]
> Power Platform Integration isn't affected by the environment lifecycle scenarios described in this article.

## Edit the properties of an environment using Power Platform admin center

Administrators can edit the properties of an environment in Power Platform Admin center when there isn't a link with a finance and operations app. Most of these actions are still possible, except:

- **URL**: Microsoft Dataverse environments linked to finance and operations apps the URL can't be updated anymore, an error is thrown:

:::image type="content" source="media/ppi-edit-URL.png" alt-text="Screenshot of editing the URL of a linked Dataverse environment." lightbox="media/ppi-edit-URL.png":::

For more information about editing environment properties, see [Edit properties of an environment](/power-platform/admin/edit-properties-environment). 

## Edit the properties of an environment using Lifecycle Services

It is not possible to edit environment properties such as name or URL using Lifecycle services.

## Recommendations

- If you need a different URL for your Dataverse environment, consider deploying a separate environment from Power Platform Admin center and update the URL there. Afterwards follow the steps in [Connect finance and operations apps with an existing Microsoft Dataverse instance](environment-lifecycle-connect-finops-existing-dv.md).
