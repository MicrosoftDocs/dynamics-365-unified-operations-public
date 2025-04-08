--- 
title: Set up transportation constraints for an item
description: This procedure will set up a transportation constraint to prevent a selected item from being transported through a selected hub.
author: lisascholz91
ms.author: lisascholz
ms.topic: how-to
ms.date: 08/27/2024
ms.custom:
ms.reviewer: kamaybac    
ms.search.form: TMSConstraint, InventLocationIdLookup, InventItemIdLookupSimple
---

# Set up transportation constraints for an item

[!include [banner](../../includes/banner.md)]

This procedure sets up a transportation constraint to prevent a selected item from being transported through a selected hub. This task would typically be carried out by a Transportation coordinator.

## Create an item constraint

1. Go to **Transportation management** \> **Setup** \> **Routing** \> **Constraints**.
1. Open the **Item** tab.
1. On the toolbar, select **New**. Enter values for the following columns of the new row:
    - **Item constraint** – Enter a unique identifier for the constraint.
    - **Name** – Enter a name for the constraint.
    - **Site** – Select the site where the constraint applies.
    - **Warehouse** – Select a warehouse where the constraint applies.
    - **Item number** – Select the item number the constraint applies to.
1. With the new row still selected, make the following settings at the bottom of the page:
    - **Shipping carrier** – Select the shipping carrier the constraint applies to.
    - **Carrier service** – Select the carrier service the constraint applies to.
    - **Mode** – Select the mode of delivery where the constraint applies.
    - **Transportation method** – Select the transportation method where the constraint applies.
    - **Hub** – Select the hub where the constraint applies.
    - **Constraint action** – Select the type of constraint to apply.
    - **Effective start date** – Select the first date where the constraint applies.
    - **Effective end date** – Select the last date where the constraint applies.
1. Select **Save**.
1. Close the page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
