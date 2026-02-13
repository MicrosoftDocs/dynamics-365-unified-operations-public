---
title: Additional location zones
description: Access an overview of the new location zones that have been added to Microsoft Dynamics 365 Supply Chain Management with a process for using location zones.
author: Mirzaab
ms.author: mirzaab
ms.topic: article
ms.date: 08/09/2022
ms.custom:
ms.reviewer: kamaybac
ms.search.form: WHSLocationBuild, WHSZone
---

# Additional location zones

[!include [banner](../includes/banner.md)]

Three new zone fields are available in Microsoft Dynamics 365 Supply Chain Management. Warehouse managers can use them to define additional warehouse organizations or layouts. The new zone fields can be set either manually or by using the **Location setup** wizard. They can be used in any query or filtering that uses the Locations table.

No additional setup is required to use the zone fields.

## Use location zones

1. Go to **Warehouse management \> Setup \> Warehouse \> Location setup wizard**.
2. Set the following values:

    - In the **Warehouse** field, select *62*.
    - In the **Zone ID** field, select *FLOOR*.
    - In the **Additional Zone 1** field, select *PICKZONE1*.
    - In the **Additional Zone 2** field, select *WEBSHOP1*.
    - In the **Location profile ID** field, select *FLOOR*.

3. Select the **Floor** line.
4. In the **From number** field, enter *1*. In the **To number** field, enter *3*.
5. Select the **Aisle** line.
6. In the **From number** field, enter *1*. In the **To number** field, enter *5*.
7. Select **Create**.
8. You receive messages that state that new locations have been added. Select the **Show messages** button to view the messages.
9. Go to **Warehouse management \> Setup \> Warehouse \> Locations**. The new locations appear in the list, and all zone fields are available (that is, the existing zone field and the new additional zone fields).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]