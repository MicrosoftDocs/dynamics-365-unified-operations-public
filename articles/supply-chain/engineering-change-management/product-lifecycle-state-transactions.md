---
title: Product lifecycle states and transactions
description: Learn how you can control which transactions are allowed for each lifecycle state as an engineering product goes through its lifecycle.
author: sgmsft
ms.author: shwgarg
ms.topic: article
ms.date: 02/17/2022
ms.custom:
ms.reviewer: kamaybac
ms.search.form: EngChgEcoResProductLifecycleStateChange
---

# Product lifecycle states and transactions

[!include [banner](../includes/banner.md)]

As an engineering product goes through its lifecycle, you need to control which transactions are allowed for each lifecycle state. For example, don't add products that aren't in a mature state to a sales order. Alternatively, if a product is reaching its end-of-life state, you might want to control the inflow of that product.

For an engineering product, changes to the lifecycle state connect to the product's engineering versions. Therefore, the product's lifecycle state can also connect to its engineering versions. When you connect the product lifecycle state to an engineering version, you can use the lifecycle state to control which transactions are allowed for the engineering version.

## Create and manage product lifecycle states

To work with product lifecycle states, go to **Engineering change management \> Setup \> Product lifecycle state** or **Product information management** \> **Setup** \> **Product lifecycle state**. Both paths open the same **Product lifecycle state** page. For complete details about how to work with the settings here to create and configure your lifecycle states, go to [Product lifecycle states](../pim/product-lifecycle.md).

## Lifecycle states for released products and product variants

For a product that has variants (master and variants), the product (master) has a lifecycle state and each of the variants can have a different lifecycle state.

For specific processes, if either the variant or the product is blocked, the process is blocked. To determine whether a process is blocked, the system makes the following checks:

- For engineering-controlled products:
    - If the current engineering version is blocked, block the process.
    - If the current variant is blocked, block the process.
    - If the released product is blocked, block the process.
- For standard products:
    - If the current variant is blocked, block the process.
    - If the released product is blocked, block the process.

For example, suppose you only want to sell one variant (red) of a given product (t-shirt) and block sales of all other variants for now. You could implement this using the following setup:

- Assign the product a lifecycle state that allows the process. For example, assign the t-shirt product a lifecycle state of *Sellable*, which allows the *Sales order* business process.
- Assign the sellable variant a lifecycle state that allows the process. For example, assign the red variant a lifecycle state of *Sellable*.
- Assign all other variants a lifecycle state that blocks the process. For example, assign the white variant (and all other variants) a lifecycle state of *Not sellable*, which blocks the *Sales order* business process.

## Default product lifecycle states

The **Default when released to a legal entity** setting for lifecycle states doesn't apply to [engineering products](../engineering-change-management/product-engineering-overview.md). Instead, the engineering change category specifies the lifecycle state of an engineering product version after it's created in the engineering company. When you release the product to an operational company, the lifecycle state of the product is copied. In other words, when you release an engineering product to an operational company, it has the same lifecycle state that it had in the engineering company. You can overwrite the lifecycle state in the operational company.

The default lifecycle state for an engineering version is specified by its engineering category. The state defaults when you create a new engineering version, including the first version of a new product.

When you create a new product or engineering product, you can also set the default lifecycle state by specifying it on the template released product of the release policy assigned to the product.

In this case, it's possible for the product to have a different lifecycle state than the version when you create a new engineering product.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
