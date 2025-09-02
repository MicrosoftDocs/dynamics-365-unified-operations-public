---
title: Maintenance worker calendar and scheduling
description: Learn about the maintenance worker calendar in relation to scheduling in Asset Management, including an example of a maintenance worker relating to a resource.
author: jodahlMSFT
ms.author: jodahl
ms.reviewer: kamaybac
ms.search.form: EntAssetWorker 
ms.topic: how-to
ms.date: 08/13/2025
ms.custom:
  - bap-template
---

# Maintenance worker calendar and scheduling

[!include [banner](../../includes/banner.md)]

When you schedule work orders, you create a schedule for maintenance workers, tools, and assets. In order to schedule maintenance workers, a calendar must be set up for each maintenance worker. Maintenance workers are related to a resource, and working time calendars are set up for resources. You set up the resource and calendar in **Asset management** \> **Setup** \> **Workers** \> **Workers**, which is described in [Maintenance workers and worker groups](../setup-for-objects/workers-and-worker-groups.md).

The following screenshot shows an example of a maintenance worker who is related to a resource that uses the working time calendar *Production*.

:::image type="content" source="media/01-work-order-scheduling.png" alt-text="An example of a maintenance worker who is related to a resource that uses the working time calendar called Production." lightbox="media/01-work-order-scheduling.png":::

Calendar setup for tools and assets isn't needed in relation to work order scheduling. The assumption is that tools and assets are available 24 hours a day for maintenance.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
