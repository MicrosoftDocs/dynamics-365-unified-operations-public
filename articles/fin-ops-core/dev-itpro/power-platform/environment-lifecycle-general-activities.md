---
title: Environment lifecycle management when Power Platform Integration is enabled
description: This article explains how to handle environment lifecyle management when finance and operations apps are integrated with Power Platform
author: abunduc-ms
ms.author: abunduc
ms.date: 06/02/2023
ms.topic: article
---

# Environment lifecycle management when Power Platform Integration is enabled

When the Power Platform Integration is enabled, the finance and operations apps  and the customer engagements apps environments are tightly connected. The administrators should look at these two platforms as a one single environment, with multiple apps. In this article, we highlight the environment lifecycle scenarios impacted by the Power Platform Integration.

Scenarios we will be covering:

- Edit properties of an environment in Power Platform admin center

- Delete an environment from Power Platform admin center

- Delete an environment from Lifecycle services

<!--

- Refresh of environments

- Point in time restore

-->

## Edit the properties of an environment in Power Platform admin center

Article [Edit properties of an environment](/power-platform/admin/edit-properties-environment), highlights how administrators can edit properties of an environment in Power Platform Admin center when there is no link with finance and operations app. Most of these actions are still possible, with one notable restriction, the **URL**. Once a Dataverse environment is linked to finance and operations apps, the URL cannot be updated anymore, the error below is thrown:

:::image type="content" source="media/ppi-edit-URL.png" alt-text="Editing the URL of a linked Dataverse environment." lightbox="media/ppi-edit-URL.png":::

> [!TIP]
> If you need a different URL for your Dataverse environment, consider deploying a  separate one from Power Platform Admin center and updating the URL there. Afterwards follow the steps in article [Connect finance and operations apps with an existing Microsoft Dataverse instance](environment-lifecycle-connect-finops-existing-dv.md).

## Delete an environment from Power Platform admin center

It it not possible to delete a linked environment from Power Platform admin center, the following error is shown:

:::image type="content" source="media/ppi-delete-ppac.png" alt-text="Delete an environemtn from Power Platform admin center." lightbox="media/ppi-delete-ppac.png":::

## Delete an environment from Lifecycle services

The Lifecycle services (LCS) portal can still be used to delete a finance and operations apps environment, the process is not changed.

> [!NOTE]
> When the finance and operations apps environment is deleted, the linked Dateverse environment is **not** automatically deleted. However, the link is removed and the environment can be further deleted from [Power Platform admin center](/power-platform/admin/delete-environment).
