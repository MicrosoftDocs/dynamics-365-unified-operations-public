---
title: Delete environments when Power Platform Integration is enabled
description: This article explains how to delete environments when finance and operations apps are integrated with Power Platform
author: abunduc-ms
ms.author: abunduc
ms.date: 06/02/2023
ms.topic: conceptual
ms.reviewer: johnmichalak
ms.custom: bap-template
---

# Delete environments when Power Platform Integration is enabled

When the Microsoft Power Platform Integration is enabled, the finance and operations apps and the customer engagements apps environments are tightly connected. Administrators should look at these two platforms as a one environment with multiple apps. This article describes the options for deleting environments.

## Delete an environment using the Power Platform admin center

It is not possible to delete a linked environment using the Power Platform admin center. If you attempt to delete a linked environment using the Power Platform admin center, you see the following error:

:::image type="content" source="media/ppi-delete-ppac.png" alt-text="Screenshot of the error message when you delete an environment using the Power Platform admin center." lightbox="media/ppi-delete-ppac.png":::

## Delete an environment using Lifecycle Services

The Lifecycle Services portal can be used to delete a finance and operations apps environment. The process is not changed.

## Recommendations

- When the finance and operations apps environment is deleted, the linked Microsoft Dataverse environment **isn't** automatically deleted. However, the link is removed and the environment can be deleted using [Power Platform admin center](/power-platform/admin/delete-environment).
