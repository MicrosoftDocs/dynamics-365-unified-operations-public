---
# required metadata

title: Additional location zones
description: This topic provides an overview of the new location zones that have been added to Microsoft Dynamics 365 Supply Chain Management.
author: Mirzaab
manager: AnnBe
ms.date: 05/05/2020
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

## Enable the Additional location zone feature

Before you can use this feature, it must be enabled on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - *Warehouse management*
- **Feature name** - *Additional location zone*

## Use location zones

1. Go to **Warehouse management \> Setup \> Warehouse \> Location setup wizard**.
2. Set the following values:

    - In the **Warehouse** field, select _62_.
    - In the **Zone ID** field, select _FLOOR_.
    - In the **Additional Zone 1** field, select _PICKZONE1_.
    - In the **Additional Zone 2** field, select _WEBSHOP1_.
    - In the **Location profile ID** field, select _FLOOR_.

3. Select the **Floor** line.
4. In the **From number** field, enter _1_. In the **To number** field, enter _3_.
5. Select the **Aisle** line.
6. In the **From number** field, enter _1_. In the **To number** field, enter _5_.
7. Select **Create**. You will receive messages that state that new locations have been added. Select the **Show messages** icon to view the messages.
8. Go to **Warehouse management \> Setup \> Warehouse \> Locations**. The new locations appear in the list, and all zone fields are available (the existing zone field and the new additional zone fields).
