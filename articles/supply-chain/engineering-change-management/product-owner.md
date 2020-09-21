---
# required metadata

title: Product owner
description: The product owner is a group of users who are responsible for certain products. When a product owner group is assigned to a product, the members of the group are the only ones who can release that product. The product owner can also be used in the approval workflow.
author: t-benebo
manager: tfehr
ms.date: 07/31/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: benebotg
ms.search.validFrom: 2020-07-31
ms.dyn365.ops.version: Release 10.0.13
---

# Product owner

[!include [banner](../includes/banner.md)]

The product owner is a group of users who are responsible for certain products. When a product owner group is assigned to a product, the members of the group are the only ones who can release that product. The product owner can also be used in the approval workflow in engineering change management.

Product owners are global settings and are therefore available to all legal entities.

## Create a product owner group

To create and populate a product owner group:

1. Go to **Engineering change management \> Setup \> Product owners**.
2. Select **New** on the Action Pane.
3. In the **Product owner** field, enter a name for the group. <!-- KFM: What kind of value? How is this different from the name? BNG it is like when you use Name and Description for other fields, Name would be Product owner and name would be description, labels should be name and description here... KFM: OK, I wrote it like that for now (though it looks kind of silly). If we change these labels, we need to remember to update these steps.  -->
4. In the **Name** field, enter a description of the group.
5. Use the **Members** FastTab to add each worker that should be a member of this product owner group.

## Assign a product owner to a product

To assign a product owner group to a product:

1. Open the **Product details** page for the relevant product or product master.
1. On the **General** FastTab, set **Product owner** to the name of the relevant product owner group.

While a product had an owner assigned, only the members of that product owner group can edit the **Product owner** setting.

The product owner is also visible on the released product form. 

## Product owners and releasing products

Only users from a product's owner group can release that product. However, there is an exception when the item is a child item and its parent is released by the parent's owner. In other words, if the product is part of the BOM of another product (the product is a child item and the parent is released), then the system will not check the product owner of each of the items in the BOM. Only the product owner of the parent item will be checked.

For example: product X is assigned to the product owner group *Design cabinets*. Product X is also part of the bill of material of product Y, which is assigned to product owner group *Design Speakers*. If a user from the product owner group *Design Speakers* releases product Y and its bill of materials, then product X will be released along with it.

## Product owners and approval

Because product owners know whether certain engineering changes will benefit their products, it often makes sense to include them as part of the approval process in engineering change management. You can implement this by setting them up as participant providers in the workflows used for engineering change management. The system will then assign approval tasks in the workflows based on the products that are in engineering change requests and engineering change orders. For more information, see [Engineering change management](engineering-change-management.md).

<!-- KFM: I think this section misses some details about whether and how we can use owner-group records as part of a workflow.  BNG let's leave this for later-->
