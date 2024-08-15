---
title: Product owners
description: Learn about product owner, including overviews and step-by-step processes for creating product owner groups and assigning a product owner to a product.
author: t-benebo
ms.author: benebotg
ms.topic: article
ms.date: 09/28/2020
ms.custom:
ms.reviewer: kamaybac
ms.search.form: EngChgProductOwner
---

# Product owners

[!include [banner](../includes/banner.md)]

The product owner is a group of users who are responsible for specific products. When a product owner group is assigned to a product, only the members of that group can release the product. The product owner can also be used in the approval workflow in engineering change management.

Product owners are global settings. Therefore, they are available to all legal entities.

## Create a product owner group

To create a product owner group and add members to it, follow these steps.

1. Go to **Engineering change management \> Setup \> Product owners**.
2. On the Action Pane, select **New**.
3. In the **Product owner** field, enter a name for the group.
4. In the **Name** field, enter a description of the group.
5. On the **Members** FastTab, add the workers who should be members of the group.

## Assign a product owner to a product

To assign a product owner to a product, follow these steps.

1. Open the **Product details** page for the relevant product or product master.
1. On the **General** FastTab, set the **Product owner** field to the name of the relevant product owner group.

While a product owner is assigned to a product, only the members of the product owner group can edit the **Product owner** setting.

The product owner is also visible on the **Released products** page.

## Product owners and product releases

Only users from a product's product owner group can release that product. However, there is an exception when the product is a child item, and its parent is released by the parent's owner. In other words, if the product is part of the BOM of another product, the system doesn't check the product owner of each item in the BOM. It checks only the product owner of the parent item.

For example, product X is assigned to the *Design cabinets* product owner group. Product X is also part of the BOM of product Y, which is assigned to the *Design Speakers* product owner group. If a user from the *Design Speakers* product owner group releases product Y and its BOM, product X will be released together with product Y.

## Product owners and approvals

Because product owners know whether specific engineering changes will benefit their products, it often makes sense to include them as part of the approval process in engineering change management. You can implement this approach by setting up the product owners as participant providers in the workflows that are used for engineering change management. The system will then assign approval tasks in the workflows, based on the products that are in engineering change requests and engineering change orders. Learn more in [Manage changes to engineering products](engineering-change-management.md).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]