---
# required metadata

title: Additional location zones
description: This topic provides an overview of the new location zones that have been added to Microsoft Dynamics 365 Supply Chain Management.
author: Mirzaab
manager: AnnBe
ms.date: 05/04/2020
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

Three new zone fields are available in Microsoft Dynamics 365 Supply Chain Management. Warehouse managers can use them to define additional warehouse organizations or layouts. The new zone fields can be set manually or by using the **Location setup** wizard. They can be used in any query or filtering that uses the Locations table.

No additional setup is required to use the zone fields.

## Use location zones 

1. Go to **Warehouse management \> Setup \> Warehouse \> Location setup wizard**.
2. Set the following values:

    - In the **Warehouse** field, select **62**.
    - In the **Zone ID** field, select **FLOOR**.
    - In the **Additional Zone 1** field, select **PICKZONE1**.
    - In the **Additional Zone 2** field, select **WEBSHOP1**.
    - In the **Location profile ID** field, select **FLOOR**.

3. Select the **Floor** line.
4. In the **From number** field, enter **01**. In the **To number** field, enter **3**.
5. Select the **Aisle** line.
6. In the **From number** field, enter **1**. In the **To number** field, enter **5**.
7. Select **Create**. You receive a message that states that new locations were added.
6. Go to **Warehouse management \> Setup \> Warehouse setup \> Locations**. The new locations appear in the list, and all four zone fields are available (the existing zone field and the three new zone fields).
