---
title: Product lifecycle state overview
description: A product lifecycle state documents the lifecycle state of a released product or product variant.  
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: EcoResProductLifecycleState, EcoResReleasedProductLifecycleStateChanges
ms.topic: overview
ms.date: 01/05/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Product lifecycle state overview

[!include [banner](../includes/banner.md)]

A product lifecycle state documents the lifecycle state of a released product or product variant. Product lifecycle states are defined by the user, typically a product manager or a product master data manager. Specific business processes, such as master planning, can be affected by a specific lifecycle state.

A released product or product variant can be associated with a product lifecycle state that documents in which lifecycle state a specific product or variant is currently in. You can define any number of product lifecycle states by assigning a state name and description. You can select one lifecycle state as the default state for new released products. Released product variants inherit their product lifecycle state from their released product master on creation. When changing the lifecycle state on a released product master, you can choose to update all existing variants that have the same original state.  

## Create a new product lifecycle state

- To create a new product lifecycle state, see [Create a new product lifecycle state](tasks/new-product-lifecycle-state.md).
- To create a default product lifecycle state, see [Create a default product lifecycle state](tasks/default-product-lifecycle-state.md).

## Associate product lifecycle states to released products  

There are multiple ways to associate a product lifecycle state to released products or product variants.

- On creation of a new released product, the default **Product lifecycle state** is automatically assigned.
- On release of a product to a legal entity, the default **Product lifecycle state** is automatically assigned.
- On release of a product variant to a legal entity, the **Product lifecycle state** associated to the released product master in this legal entity is automatically assigned to the new variant.

You can manually update the product lifecycle state by using:

- The **Released products** list page or **Details view**.
- The **Released product variants** list page or **Details view**.
- Find the obsolete products or product variants based on demand and associate a lifecycle state.  

For more information:

- To associate a product lifecycle state to a released product master, see [Assign a product lifecycle state to a released product master](tasks/product-lifecycle-state-released-product-master.md).

- To associate a product lifecycle state to a release product, see [Assign a product lifecycle state to a released product](tasks/product-lifecycle-state-released-product.md).

## Impact on master planning

The product lifecycle state has only one control flag: **Is active for planning**. By default, this option is set to *Yes* for all created product lifecycle states, but it can be changed to *No*. When set to *No*, the associated released products or released product variants are:

- Excluded from master planning.
- Excluded from BOM-level calculation.

For detailed information about how to use product lifecycle state to exclude products from master planning and BOM-level calculation, see [Create a product lifecycle state to exclude products from Master planning](tasks/exclude-products-master-planning.md)

> [!NOTE]
> For performance reasons, it is highly recommended to associate all obsolete released products or product variants, especially when working with non-reusable product configuration variants, with a product lifecycle state that is deactivated for master planning.  

## Enable and apply detailed control of business processes

It's possible set up your system to provide control over which business processes should be allowed or blocked by the system for a specific lifecycle state. This capability can be useful when introducing new products (where, for example, it may be possible to purchase the item but receive a warning that it's still a prototype) or to discontinue or end-of-life of a product (where it may be possible to sell the existing on-hand but not to purchase it or to produce it).

To enable this level of control over your business processes, the *Engineering Change Management* configuration key must be enabled for the processes to appear (see also [Engineering change management overview](../engineering-change-management/product-engineering-overview.md)). You can set up the control of business processes in products, variants, and engineering products. You can safely enable the configuration key and use the lifecycle state for standard products even if you don't use any other aspects of the engineering change management processes. For more information about how to work with lifecycle states using the features provided by engineering change management, see [Product lifecycle states and transactions](../engineering-change-management/product-lifecycle-state-transactions.md).

## Default migration, import, and export

The product lifecycle states are supported by data entities, and the lifecycle state can be set to a variable state through either the released product data entity or the released variant data entity.

## Find obsolete products and products variants

You can run a simulation analysis to find the obsolete released products or product variants and then update their product lifecycle status. To find obsolete products, see [Find obsolete product variants and assign a product lifecycle state](tasks/obsolete-product-variants.md). This article shows how to find obsolete released products or product variants and how to associate a product lifecycle state to the obsolete products. It also shows hot to view the simulation results and assess how many products and product variants will be associated with a new product lifecycle state when running the update without simulation.  

By running the analysis in a simulation mode, the products and product variants identified as obsolete are displayed in a specific form, where they can easily be reviewed. The analysis searches for transactions and specific master data to identify products that have no demand within a variable period and no master data that can result in demand. New released products within a variable period can be excluded from the analysis. When the analysis simulation returns the expected result, the user can run the analysis and set a new product lifecycle state to all products identified as obsolete by the analysis.  

> [!NOTE]
> Note that all analysis and updates must be done within the same legal entity.  

## Criteria to select and update released products or product variants

Use the following criteria to select and update the released products and product variants:

- The product lifecycle state of the product or product variant must be different from the new desired state.
- The product or product variant was created some days ago based on the number of days that you enter in the selection dialog box.
- There are no open production orders (= status < ended) for the product or product variant.
- There are no open inventory transactions (= status issue ReservPhysical to QuotationIssue or status receipt Registered to QuotationReceipt) for the product or product variant.
- There are no inventory transactions within the last number of days for the product or product variant.
- There's no future demand or supply forecast for the product or product variant.  
- No minimum stock level has been set in item coverage for the product or product variant.
- No active fixed quantity kanban rule for the product or product variant.  
- No service order line for the product or product variant.
- No active or future sales or purchase agreement lines for the product or product variant.
- The product or product variant isn't used in a BOM that is associated with a non-expired approved BOM version for a product or variant that is active for planning.

## Additional resources

- [Create a new product lifecycle state](tasks/new-product-lifecycle-state.md)
- [Create a default product lifecycle state](tasks/default-product-lifecycle-state.md)
- [Assign a product lifecycle state to a released product master](tasks/product-lifecycle-state-released-product-master.md)
- [Assign a product lifecycle state to a released product](tasks/product-lifecycle-state-released-product.md)
- [Find obsolete product variants and assign a product lifecycle state](tasks/obsolete-product-variants.md)
- [Create a product lifecycle state to exclude products from Master planning](tasks/exclude-products-master-planning.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
