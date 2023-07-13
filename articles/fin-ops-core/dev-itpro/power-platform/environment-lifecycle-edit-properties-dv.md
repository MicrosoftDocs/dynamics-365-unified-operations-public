---
title: Edit the properties of a connected Microsoft Dataverse environment
description: This article explains how to edit the properties of a Dataverse environment when finance and operations apps are integrated with Power Platform
author: abunduc-ms
ms.author: abunduc
ms.date: 06/02/2023
ms.topic: article
---

# Edit the properties of a connected Microsoft Dataverse environment

When the Power Platform Integration is enabled, the finance and operations apps  and the customer engagements apps environments are tightly connected. The administrators should look at these two platforms as a one single environment, with multiple apps. In this article, we highlight how editing the properties of an environment is impacted by the Power Platform Integration.

> [!IMPORTANT]
> The Power Platform Integration is not affected by the environment lifecycle scenarios described in this article

## Edit the properties of an environment in Power Platform admin center

Article [Edit properties of an environment](/power-platform/admin/edit-properties-environment) highlights how administrators can edit the properties of an environment in Power Platform Admin center when there is no link with a finance and operations app. Most of these actions are still possible, besides:

- **URL**: Dataverse environments linked to finance and operations apps  the URL cannot be updated anymore, an error is thrown:

:::image type="content" source="media/ppi-edit-URL.png" alt-text="Editing the URL of a linked Dataverse environment." lightbox="media/ppi-edit-URL.png":::

## Edit the properties of an environment in Lifecycle Services

It is not possible to edit environment properties such as name or URL in Lifecycle services.

## Recommendations

- If you need a different URL for your Dataverse environment, consider deploying a  separate one from Power Platform Admin center and updating the URL there. Afterwards follow the steps in article [Connect finance and operations apps with an existing Microsoft Dataverse instance](environment-lifecycle-connect-finops-existing-dv.md).
