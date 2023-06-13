---
title: Delete environments when Power Platform Integration is enabled
description: This article explains how to delete environments when finance and operations apps are integrated with Power Platform
author: abunduc-ms
ms.author: abunduc
ms.date: 06/02/2023
ms.topic: article
---

# Delete environments when Power Platform Integration is enabled

When the Power Platform Integration is enabled, the finance and operations apps  and the customer engagements apps environments are tightly connected. The administrators should look at these two platforms as a one single environment, with multiple apps. In this article, we highlight the environment lifecycle scenarios impacted by the Power Platform Integration.

> [!IMPORTANT]
> The Power Platform Integration is not affected by the environment lifecycle scenarios described in this article, besides when the environments are deleted.

## Delete an environment from Power Platform admin center

It it not possible to delete a linked environment from Power Platform admin center, the following error is shown:

:::image type="content" source="media/ppi-delete-ppac.png" alt-text="Delete an environemnt from Power Platform admin center." lightbox="media/ppi-delete-ppac.png":::

## Delete an environment from Lifecycle services

The Lifecycle services (LCS) portal can still be used to delete a finance and operations apps environment, the process is not changed.

> [!NOTE]
> When the finance and operations apps environment is deleted, the linked Dateverse environment is **not** automatically deleted. However, the link is removed and the environment can be further deleted from [Power Platform admin center](/power-platform/admin/delete-environment).
