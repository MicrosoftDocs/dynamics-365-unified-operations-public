---
title: Product lifecycle states
description: Learn how to create and use lifecycle states, which document the lifecycle state of a released product or product variant with an outline on creating new lifecycle states.
author: sgmsft
ms.author: shwgarg
ms.reviewer: kamaybac
ms.search.form: EcoResProductLifecycleState, EcoResReleasedProductLifecycleStateChanges
ms.topic: overview
ms.date: 12/10/2025
ms.custom: 
  - bap-template
---

# Product lifecycle states

[!include [banner](../includes/banner.md)]

*Product lifecycle states* document the lifecycle state of a released product or variant. They control which business processes (such as purchase orders, production, planning, or forecasts) can use released products or variants assigned to a given lifecycle state.

You can define any number of product lifecycle states to represent the different stages in a product's lifecycle, such as *Prototype*, *Active*, *Obsolete*, or *End-of-life*. Associate these lifecycle states to released products and released product variants to manage their availability and usage within your organization. Select one lifecycle state as the default for new released products. Released product variants inherit their product lifecycle state from their released product master when you create them. When you change the lifecycle state on a released product master, you can choose to update all existing variants that have the same original state.  

## Create, configure, and manage product lifecycle states

The following procedure describes how to create, configure, and manage product lifecycle states. It explains how to mark a lifecycle state as the default for new released products and how to control which business processes are allowed or blocked for products in a specific lifecycle state.

1. Go to **Product information management** \> **Setup** \> **Product lifecycle state**.
1. On the Action Pane, select **Refresh processes** to make sure all of the latest business processes are available for use with your product lifecycle states.
1. Follow one of these steps:
    - To create a new lifecycle state, select **New** on the Action Pane.
    - To edit an existing lifecycle state, select it in the list pane, select **Edit** on the Action Pane.
    - To delete an existing lifecycle state, select it in the list pane, and then select **Delete** on the Action Pane.

1. Make the following settings in the header of your new or selected lifecycle state:
    - **State** – Enter a name for the product lifecycle state (such as *Prototype*, *Active*, *Obsolete*, or *End-of-life*).
    - **Description** – Enter a description of the product lifecycle state.

1. Make the following settings on the **General** FastTab:
    - **Default when released to a legal entity** – Set to *Yes* if this lifecycle state should be applied to all products by default when they're first released. Set it to *No* if this lifecycle state is manually applied later.
    - **Is active for planning** – Set to *Yes* to include products that are in this lifecycle state in calculations at the master planning and bill of materials (BOM) levels. Set it to *No* to exclude products that are in this lifecycle state from the calculations.

    > [!IMPORTANT]
    > The **Default when released to a legal entity** setting doesn't apply to [engineering products](../engineering-change-management/product-engineering-overview.md). Learn more in [Product lifecycle states and transactions](../engineering-change-management/product-lifecycle-state-transactions.md).

1. Use the **Enabled business processes** FastTab to control which of the available business processes can be used with products in the current lifecycle state. For each process that is listed on the FastTab, set the following fields:

    - **Process** – This read-only field shows the name of an existing business process. The table at the end of this procedure lists and describes the business processes that might appear here.
    - **Process area** – This read-only field shows the name of an existing process area. It might be editable, in which case you shouldn't change it.
    - **Policy** – Select one of the following values to control whether and how the current process is permitted for products that are in this lifecycle state:
        - *Enabled* – The business process is allowed to use products in this lifecycle state.
        - *Blocked* – The business process isn't allowed to use products in this lifecycle state. If a user tries to use the process on a product that is in this lifecycle state, the system blocks the attempt and shows an error instead. For example, you might block end-of-life products from being purchased.
        - *Enabled with warning* – The process is allowed, but a warning is shown. For example, you might want a prototype product to be put on a production order that is created by the Research and Development department. However, other departments should be aware that they shouldn't produce the product yet.

1. On the Action Pane, select **Save** to save your new or updated product lifecycle state.

The following table lists and describes the business processes available on the **Enabled business processes** FastTab.

| Process  | Process area | Description |
|---|---|---|
| BOM report as finished | Production | Enables or blocks reporting the item as finished in a production order. |
| Inbound order | Warehouse | Enables or blocks inserting or updating the item on an inbound warehouse shipment line. |
| Inbound order creation | Warehouse | Enables or blocks inserting the item on an inbound warehouse shipment line during creation. |
| Inventory adjustment | Inventory | Enables or blocks adding the item to an inventory adjustment journal line. |
| Inventory journal | Inventory | Enables or blocks adding the item to inventory transfer, adjustment, or movement journal lines. |
| Inventory movement | Inventory | Enables or blocks adding the item to an inventory movement journal line. |
| Inventory transfer | Inventory | Enables or blocks adding the item to an inventory transfer journal line. |
| Item forecast | Planning | Enables or blocks creating manual demand forecasts for the item in Master Planning. |
| Outbound order | Warehouse | Enables or blocks inserting or updating the item on an outbound warehouse shipment line. |
| Outbound order creation | Warehouse | Enables or blocks inserting the item on an outbound warehouse shipment line during creation. |
| Production BOM | Production | Enables or blocks creating a production order if the item appears in the BOM. |
| Production order | Production | Enables or blocks creating a production order for the item. |
| Production picking list | Production | Enables or blocks adding the item to a production picking list journal line. |
| Purchase order | Purchasing | Enables or blocks adding the item to a purchase order line,  and posting product receipt or invoice. |
| Purchase order creation | Purchasing | Enables or blocks adding the item to a purchase order line during creation. |
| Request for quote | Purchasing | Enables or blocks creating a request for quote for the item. |
| Return order | Sales | Enables or blocks adding the item to a return order line. |
| Sales order | Sales | Enables or blocks adding the item to a sales order line, and posting packing slip or invoice. |
| Sales order creation | Sales | Enables or blocks adding the item to a sales order line during creation. |
| Sales picking list | Sales | Enables or blocks generating a sales picking list for the item in a sales order. |
| Sales quotation | Sales | Enables or blocks adding the item to a sales quotation line. |
| WBS estimate for items | Planning | Enables or blocks creating a transaction of type *Item* in a work breakdown structure for a project. |

## Associate product lifecycle states to released products  

You can associate a product lifecycle state to newly released products or product variants in several ways.

- *When you create a new released product* – The system assigns the lifecycle state that has **Default when released to a legal entity** selected to the **Product lifecycle state** field of the new released product.
- *When you release a product to a legal entity* – The system assigns the lifecycle state that has **Default when released to a legal entity** selected to the **Product lifecycle state** field of the new released product.
- *When you release a product variant to a legal entity* – The system assigns the lifecycle state assigned to the released product master in this legal entity to the **Product lifecycle state** field of the new variant.

> [!IMPORTANT]
> The **Default when released to a legal entity** setting doesn't apply to [engineering products](../engineering-change-management/product-engineering-overview.md). The engineering change category specifies the lifecycle state of an engineering product version after you create it in the engineering company. When you release the product to an operational company, the lifecycle state of the product is copied. In other words, when an engineering product is released to an operational company, it has the same lifecycle state that it had in the engineering company. You can overwrite the lifecycle state in the operational company. Learn more in [Product lifecycle states and transactions](../engineering-change-management/product-lifecycle-state-transactions.md).

To manually update the product lifecycle state of existing released products or released product variants, follow these steps:

1. Go to one of the following pages:
    - Go to **Product information management** \> **Products** \> **Released products**.
    - Go to **Product information management** \> **Products** \> **Released product variants**.

1. Find the product, product master, or product variant that you want to update. Product masters show a **Product subtype** of *Product master* on the **Released products** page.  

1. Do one of the following steps:
    - From the list view, select **Edit** on the Action Pane and then change the **Product lifecycle state** field to the desired lifecycle state.
    - Open the record, select **Edit** on the Action Pane, and then, on the **General** FastTab, change the **Product lifecycle state** field to the desired lifecycle state.

1. On the Action Pane, select **Save**.

1. If you edited a product master, you're asked to confirm whether you want to update the variants. Select one of the following options:
    - Select **Yes** to update all related released product variants that have the same original status as the released product master.
    - Select **No** to keep the actual state of all variants. Variants that have a different product lifecycle state from the released product master aren't updated.

1. If you chose to update product variants related to a product master, you can view and edit the new lifecycle states of the variants by going to the Action Pane, opening the **Product** tab, and from the **Product master** group, selecting **Released product variants**.

## Impact on master planning

Master planning and bill of materials (BOM) level calculations exclude items assigned a product lifecycle state when the **Is active for planning** option is set to *No*.

> [!TIP]
> For performance reasons, associate all obsolete released products and variants with a product lifecycle state that deactivates master planning, especially when working with non-reusable product configuration variants.  

## Default migration, import, and export

Data entities support product lifecycle states. You can set the lifecycle state to a variable state through either the *released product* data entity or the *released variant* data entity.

## Find obsolete products and products variants

The *Change lifecycle state for obsolete products* periodic task makes it easy to find obsolete products or variants and update their product lifecycle status. Learn more in [Find obsolete released products or variants](tasks/obsolete-product-variants.md).

## Related information

- [Find obsolete released products or variants](tasks/obsolete-product-variants.md)
- [Product lifecycle states and transactions](../engineering-change-management/product-lifecycle-state-transactions.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
