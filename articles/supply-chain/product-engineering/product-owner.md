---
# required metadata

title: Product owner
description: The product owner is a group of users who are responsible for certain products. When a product owner group is assigned to a product, the members of the group are the only ones who can release that product. The product owner can also be used in the approval workflow.
author: XXXX
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

The product owner is a group of users who are responsible for certain products. When a product owner group is assigned to a product, the members of the group are the only ones who can release that product. The product owner can also be used in the approval workflow in engineering change management.

Product owners are global setup in therefor immediately available in all legal entities.

## Create a product owner group

1. Go to **Navigation pane \> Modules \> Product engineering \> Setup \> Product owner**.
2. Click **New**.
3. In the **Product owner** field, type a value.
4. In the **Name** field, type a value.
5. Add as much members as there are users in the product owner group.

## Assigning a product owner

On the global product and product master definition, the product owner can be assigned to a product. As soon as a product had a product owner assigned, the members of the product owner group are the only ones that can remove or change the product owner group.

The product owner will be visible on the released product form as well.

## Product owners and releasing products

While product owners know which legal entities need their products, the product can only be released by the members of the product owner group. In case another user will select the product for releasing, the product will not be available in the release form.

This behavior is only applicable in case the product is directly selected for releasing. In the situation the product is via a bill of material line part of a product structure, the product can be released by other users in case the parent of the product is released.

As an example: product X has product owner group &#39;Design cabinets&#39; assigned. Product X is also part of the bill of material of product Y which has product owner group &#39;Design Speakers&#39; assigned. In case a user of the product owner group &#39;Design Speakers&#39; releases product Y and its bill of material, product X will be released along with it.

## Product owners and approval

While product owners know if certain engineering changes will benefit their products, they can be part of the approval cycle in engineering change management. They can be setup as participant providers in the workflows for engineering change management. If this is done, the system will assign approval tasks in the workflows based on the products that are in engineering change requests and engineering change orders. See for more information about using and creating workflows .... See for more information about engineering change management…