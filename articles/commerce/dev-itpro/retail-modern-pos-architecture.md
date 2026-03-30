---
title: Modern POS (MPOS) architecture
description: This article provides an overview of POS topology.
author: josaw1
ms.date: 02/19/2026
ms.topic: overview
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.assetid: 210953fb-4d5a-49e6-b4db-6f31b3472789
ms.custom: 
  - bap-template
---

# Modern POS (MPOS) architecture

[!include [banner](../includes/banner.md)]

This article provides an overview of POS topology.

## Modern POS topology

Users of Modern Point of Sale (POS) can perform various tasks on supported laptops, tablets, and phones. These tasks include processing sales transactions, viewing customer orders, managing daily operations and inventory, and viewing role-based reports. Both MPOS and Cloud POS are available in Microsoft Dynamics 365 Commerce. The Cloud POS is a hosted version of the POS app. Both the POS clients don't perform business functions or data processing. Commerce Scale Unit provides all business functions. Modern POS and Cloud POS clients can communicate with Commerce Scale Units. Modern POS client can also communicate with peripheral devices, such as cash drawers, credit card readers, and printers, by using Hardware Station. You must deploy Hardware Station in your store, and all Modern POS clients can connect to the same Hardware Station. The following diagram shows the high-level topology.

:::image type="content" source="./media/retail-topology-1024x606.png" alt-text="Diagram of Commerce topology.":::

## Modern POS architecture

The view, view-controller, and devices layers depend on the operating system (for example, Windows RT) that you plan to deploy Modern POS on. The other layers are independent of the operating system. These layers use TypeScript classes and modules to implement Modern POS functionality such as workflows and entities. The following diagram shows the Modern POS technical architecture.

:::image type="content" source="./media/mpos.png" alt-text="Diagram of Modern POS architecture.":::

## Cloud POS and Modern POS architecture

Cloud POS is a hosted version of Modern POS, and varies only in the way that it's rendered on specific devices or in specific browsers. Additionally, Modern POS supports offline mode and therefore a local CRT. Other native peripheral support is also specific to Modern POS.

:::image type="content" source="./media/cloudpos-and-mpos.png" alt-text="Diagram of Cloud POS and Modern POS architecture.":::

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
