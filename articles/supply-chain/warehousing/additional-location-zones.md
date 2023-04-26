---
# required metadata

title: Additional location zones
description: This article provides an overview of the new location zones that have been added to Microsoft Dynamics 365 Supply Chain Management.
author: Mirzaab
ms.date: 08/09/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: WHSLocationBuild, WHSZone
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: perlynne
ms.search.validFrom: 2020-07-01
ms.dyn365.ops.version: 10.0.8

---

# Additional location zones

[!include [banner](../includes/banner.md)]

Three new zone fields are available in Microsoft Dynamics 365 Supply Chain Management. Warehouse managers can use them to define additional warehouse organizations or layouts. The new zone fields can be set either manually or by using the **Location setup** wizard. They can be used in any query or filtering that uses the Locations table.

No additional setup is required to use the zone fields.

## Turn the Additional location zone feature on or off

To use this feature, it must be turned on for your system. As of Supply Chain Management version 10.0.25, the feature is turned on by default. As of Supply Chain Management version 10.0.29, the feature is mandatory and can't be turned off. If you're running a version older than 10.0.29, then admins can turn this functionality on or off by searching for the *Additional location zone* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

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
7. Select **Create**.
8. You receive messages that state that new locations have been added. Select the **Show messages** button to view the messages.
9. Go to **Warehouse management \> Setup \> Warehouse \> Locations**. The new locations appear in the list, and all zone fields are available (that is, the existing zone field and the new additional zone fields).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]