---
# required metadata

title: Vendor settings added for Landed cost
description: When you enable the Landed cost module, several new fields are added to the existing Vendors page. Use these settings to set up the vendors that you will use together with Landed cost features.
author: RichardLuan
manager: tfehr
ms.date: 12/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: riluan
ms.search.validFrom: 2020-12-07
ms.dyn365.ops.version: Release 10.0.17
---

# Vendor settings added for Landed cost

[!include [banner](../includes/banner.md)]

When you enable the Landed cost module, several new fields are added to the existing **Vendors** page. Use these settings to set up the vendors that you will use together with Landed cost features.

To find the relevant settings, go to **Procurement and sourcing \> Vendors \> All vendors**. Then open (or create) a vendor and expand the **Miscellaneous details** FastTab. The Landed cost settings are all under the **Voyages** heading. The following table describes the settings that the Land cost modules adds here.

| Setting | Description |
| --- | --- |
| **Shipping type** | <p>Identifies the role of the vendor in relation to Landed cost. Select one of the following values:</p><ul><li>**None:** This is the default setting. It identifies a vendor that has no specific role related to Landed cost. Most vendors will probably have this value.</li><li>**Shipping company:** Identifies the vendor as a shipping company. Vendors with this value are available in the **Shipping company** drop-down list on the **Voyages** page.</li><li>**Customs broker:** Identifies the vendor as a customs broker. Vendors with this value are available in the **Customs broker** drop-down list on the **Folios** page.</li><li>**Agent:** Identifies the vendor as an agent. Vendors with this value are available in the **Agent** drop-down list on the **Vendors** and **Purchase orders** pages. |
| **Cost type group** | Assign the vendor to a cost type group for the purpose of selecting [auto costs](auto-cost-setup.md). |
| **From port** | Select the port of origin for the voyage. |
| **Agent** | The default agent when purchasing from this vendor. |
| **Import costing vendor** | <p>This indicates whether the vendor is a Landed cost vendor.</p><p>**Tip**: You can use this to restrict the purchase orders displayed on the **Voyage creation** page. Use record level security to achieve this. |
| **Shipping Company** | Select the defaults the shipping company to use when creating purchase orders for this vendor. |
| **Services Provider** | This indicates whether the vendor is services provider. |
| **Over/Under Tolerance Group** | Select the default over/under tolerance group for this vendor. |
