---
title: Edit the properties of connected Dataverse environments
description: Learn about how to edit the properties of a Microsoft Dataverse environment when finance and operations apps are integrated with Microsoft Power Platform.
author: abunduc-ms
ms.author: abunduc
ms.topic: conceptual
ms.date: 06/19/2024
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
---

# Edit the properties of connected Dataverse environments

When Microsoft Power Platform Integration is enabled, the finance and operations apps environment and the customer engagements apps environment are tightly connected. Administrators should regard these two platforms as one environment that has multiple apps. This article describes how Power Platform Integration affects the process of editing the properties of an environment.

> [!IMPORTANT]
> Power Platform Integration isn't affected by the environment lifecycle scenarios that are described in this article.

## Edit the properties of an environment by using Power Platform admin center

Administrators can edit the properties of an environment in Power Platform admin center when there's no link with a finance and operations app. Although most of the properties can still be edited, there's one exception:

- **URL** – For Dataverse environments that are linked to finance and operations apps, the URL can no longer be updated. If you try, you receive the following error message:

    > The finance and operations environment does not support domain name changes. 

    :::image type="content" source="media/ppi-edit-URL.png" alt-text="Screenshot of the error message for an attempt to edit the URL of a linked Dataverse environment." lightbox="media/ppi-edit-URL.png":::

For more information about how to edit environment properties, see [Edit properties of an environment](/power-platform/admin/edit-properties-environment).

## Edit the properties of an environment by using Lifecycle Services

You can't use Microsoft Dynamics Lifecycle Services to edit environment properties such as the name or URL.

## Recommendations

- If you need a different URL for your Dataverse environment, consider deploying a separate environment from Power Platform admin center and updating the URL there. Then follow the steps in [Connect finance and operations apps with an existing Microsoft Dataverse instance](environment-lifecycle-connect-finops-existing-dv.md).
