---
# required metadata

title: Additional location zones
description: This topic provides an overview of additional location zones added to Dynamics 365 Supply Chain Management.
author: Mirzaab
manager: AnnBe
ms.date: 12/10/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Supply Chain Management
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: perlynne
ms.search.validFrom: 2019-12-31
ms.dyn365.ops.version: 10.0.1

---

# Additional location zones

[!include [banner](../includes/banner.md)]

Dynamics 365 Supply Chain Management added three zone fields, with support for them in the **Location setup** wizard.

The additional location zones features add three additional zone fields to each warehouse location record. These fields can be used by warehouse managers to define additional warehouse organizations/layouts. The new zone fields can be populated manually or via the location wizard. They are valid to be used in any query or filtering that uses the locations table.

Setup

No new setup is needed, the new zone fields use the existing zones that have been setup.

# Process

Navigate to _Warehouse_ management-Setup- Warehouse- _Location setup wizard._ In the from select:

- Warehouse: 62
- Zone ID: FLOOR
- Additional Zone 1: PICKZONE1
- Additional Zone 2: WEBSHOP1
- Location profile ID: FLOOR

In the Floor segment, specify From number = 01, To number = 3

In the Aisle segment, specify From number = 1, To number = 5

Click on Create. You will receive a message that new locations were created.

Navigate to _Warehouse management_ -_Setup_ -_Warehouse setup_ -_Locations_ and view the locations that were created. All 4 zone fields will be available.
