---
# required metadata

title: Additional location zones
description: This topic provides an overview of additional location zones added to Dynamics 365 Supply Chain Management.
author: Mirzaab
manager: AnnBe
ms.date: 12/17/2019
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

There are three new zone fields available in Dynamics 365 Supply Chain Management. 

The additional fields can be used by warehouse managers to define additional warehouse organizations or layouts. The new zone fields can be populated manually or via the **Location setup wizard**. They can be used in any query or filtering that uses the locations table.

No additional setup is required to use the zone fields.

## Use location zones 

1. Go to **Warehouse management > Setup > Warehouse > Location setup wizard**. 

2. In the dialog, do the following:

  - In the **Warehouse** field, select "62".
  - In the **Zone ID** field, select "FLOOR".
  - In the **Additional Zone 1** field, select "PICKZONE1".
  - In the **Additional Zone 2** field, select "WEBSHOP1".
  - In the **Location profile ID** field, select "FLOOR".

3. Select the "Floor" line. In the **From number** field, enter "01". In the **To number** field, enter "3".

4. Select the "Aisle" line. In the **From number** field, enter "1". In the **To number** field, enter "5".

5. Click **Create**. You will receive a message that new locations were added.

6. Go to **Warehouse management > Setup > Warehouse setup > Locations**. The new locations appear in the list and all four zone fields will be available (the existing zone and the three new zones). 

