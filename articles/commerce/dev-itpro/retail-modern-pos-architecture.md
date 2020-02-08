---
# required metadata

title: Modern POS (MPOS) architecture
description: This topic describes the POS topology.
author: RobinARH
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 83892
ms.assetid: 210953fb-4d5a-49e6-b4db-6f31b3472789
ms.search.region: Global
# ms.search.industry: 
ms.author: meeram
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update

---

# Modern POS (MPOS) architecture

[!include [banner](../includes/banner.md)]

This topic describes the POS topology.

Modern POS topology
--------------------------

Users of Modern Point of Sale (POS) can perform various tasks on supported laptops, tablets, and phones. These tasks include processing sales transactions, viewing customer orders, managing daily operations and inventory, and viewing role-based reports. Both MPOS and Cloud POS are available in Microsoft Dynamics 365 Commerce. The Cloud POS is a hosted version of the POS app. Both the POS clients don't perform business functions or data processing. All business functions are provided by Commerce Scale Unit. Modern POS and Cloud POS clients can communicate with Commerce Scale Units that are deployed in the cloud. Modern POS client can also communicate with peripheral devices, such as cash drawers, credit card readers, and printers, by using Hardware Station. Hardware Station must be deployed in your store, and all Modern POS clients can connect to the same Hardware Station. The following diagram shows the high-level topology. 

[![Commerce Topology](./media/retail-topology-1024x606.png)](./media/retail-topology.png)

## Modern POS architecture
The view, view-controller, and devices layers depend on the operating system (for example, Windows RT) that you plan to deploy Modern POS on. The other layers are independent of the operating system. These layers use TypeScript classes and modules to implement Modern POS functionality such as workflows and entities. The following diagram shows the Modern POS technical architecture. 

[![MPOS](./media/mpos.png)](./media/mpos.png)

## Cloud POS and Modern POS architecture
Cloud POS is a hosted version of Modern POS, and varies only in the way that it is rendered on specific devices or in specific browsers. Additionally, Modern POS supports offline mode and therefore a local CRT. Other native peripheral support is also specific to Modern POS. 

[![CloudPOS and MPOS](./media/cloudpos-and-mpos.png)](./media/cloudpos-and-mpos.png)



