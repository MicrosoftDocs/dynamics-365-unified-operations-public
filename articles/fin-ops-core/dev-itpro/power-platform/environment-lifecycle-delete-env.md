---
title: Delete environments when Power Platform Integration is enabled
description: Learn about how to delete environments when finance and operations apps are integrated with Microsoft Power Platform.
author: abunduc-ms
ms.author: johnmichalak
ms.topic: article
ms.custom: 
  - bap-template
ms.date: 01/22/2026
ms.reviewer: johnmichalak
---

# Delete environments when Power Platform Integration is enabled

When you enable Microsoft Power Platform Integration, you connect the finance and operations apps environment and the customer engagements apps environment. Administrators should regard these two platforms as one environment that has multiple apps. This article describes the options for deleting environments.

## Delete an environment by using Power Platform admin center

You can't use Power Platform admin center to delete a linked environment. If you try, you receive the following error message:

> Delete cannot be performed on Power Platform environments that are linked to Finance and Operations environments. Please use Lifecycle Services to perform this operation.

:::image type="content" source="media/ppi-delete-ppac.png" alt-text="Screenshot of the error message for an attempt to delete an environment by using Power Platform admin center." lightbox="media/ppi-delete-ppac.png":::

## Delete an environment by using Lifecycle Services

Use Microsoft Dynamics Lifecycle Services to delete a finance and operations apps environment. The process doesn't change.

## Recommendations

- When you delete the finance and operations apps environment, you don't automatically delete the linked Dataverse environment. However, the link is removed, and you can then delete the environment by using [Power Platform admin center](/power-platform/admin/delete-environment).
