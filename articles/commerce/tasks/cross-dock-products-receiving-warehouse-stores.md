---
title: Cross-dock products from receiving warehouse to stores
description: Learn how to create and process a cross-dock that distributes products from the receiving location of a purchase order to one or many stores.
author: josaw1
ms.author: mirao
ms.reviewer: mirao
ms.topic: how-to
ms.date: 10/09/2026
ms.search.form: RetailBuyersPush, RetailCrossDock, RetailReplenishmentTreeLookup
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.custom:
  - bap-template
ai-usage: ai-assisted
---

# Cross-dock products from receiving warehouse to stores

[!INCLUDE [banner](../includes/banner.md)]

Cross-docking distributes incoming products straight from the receiving location of a purchase order out to your stores, so that the goods never have to be put away and picked again at the distribution center. You choose how much of each purchased product to distribute, and Microsoft Dynamics 365 Commerce either suggests how to spread that quantity across the stores or lets you enter the quantities yourself. When you create the order, the system generates the transfer orders that move the products to each store.

Cross-docking and buyer's push are two modes of the same replenishment feature. Use cross-docking to distribute products that are arriving on a purchase order. Use buyer's push to distribute products that are already on hand at a distribution center. Learn more in [Push products from distribution center to store using buyer's push](push-products-distribution-center-store-buyers-push.md).

## Prerequisites

This procedure uses the USRT demo company. Before you begin, set up the data that the cross-dock relies on:

- Replenishment rules, organizational hierarchies, and store weights. Learn more in [Set up rules and parameters for cross docking and buyer's push](set-up-rules-parameters-cross-docking-buyers-push.md).
- A confirmed purchase order that has the products you want to distribute.

## Create and process a cross-dock

You create the cross-dock from the purchase order that brings the products in. Follow these steps to distribute the incoming quantities to your stores and generate the transfer orders.

1. In Commerce headquarters, go to **All purchase orders**.
1. Select the purchase order to open it.
1. On the Action Pane, on the **Retail** tab, select **Cross docking**.
1. On the Action Pane, select **Edit**.
1. In the **Lines** section, select the product to distribute. To narrow a long list, use the **Category** field to filter the products by retail category.
1. Set the following fields to define how much of each product is distributed:

    - **Cross docking quantity** – Enter how much of the purchased quantity of the selected product to distribute to the stores.
    - **Additional cross docking quantity** – Enter a quantity to distribute from the remaining available quantity of the purchased products.

1. Set the following fields to define how the quantities are spread across the stores:

    - **Distribution** – Select the rule that determines how the quantity is divided:

        - *Location weight* – Divide the quantity in proportion to the weight that's defined on each warehouse.
        - *Replenishment rules* – Divide the quantity by using the weights that are defined on the lines of a replenishment rule.
        - *Fixed quantity* – Send the same specified quantity to every store.

    - **Replenishment hierarchy** – Select the organizational hierarchy that identifies the stores to distribute to.
    - **Respect assortments** – Select *Yes* to distribute a product only to the stores where that product is assorted. If a product isn't assorted for one of the selected stores, order creation stops and an error reports that one or more products aren't available in the distribution location.

        This checkbox is available only when the **Cross docking** field is set to *Manual* on the **Commerce parameters** page (**Retail and Commerce** > **Headquarters setup** > **Parameters** > **Commerce parameters**, on the **Inventory** tab). When that field is set to *Always* or *Never*, the checkbox shows the corresponding value and can't be changed.

1. Select **Calculate quantities**, and then review the quantities that the system added to the rows in the warehouse list.
1. Select **Create order**, and then select **Yes** to confirm. The system creates a transfer order for each warehouse that receives products.

    > [!NOTE]
    > After the orders are created, the **Distribution**, **Replenishment hierarchy**, and **Respect assortments** fields become read-only for this cross-dock. Verify the quantities before you create the orders.

## Review the orders that you created

After you create the orders, you can open them directly from the cross-dock to confirm what was generated.

1. In the list of warehouses, select a warehouse that received products.
1. Select **Order** to view the orders that were created for the selected warehouse.

## Related information

- [Push products from distribution center to store using buyer's push](push-products-distribution-center-store-buyers-push.md)
- [Set up rules and parameters for cross docking and buyer's push](set-up-rules-parameters-cross-docking-buyers-push.md)
- [Create product packages for purchase orders](create-product-packages-purchase-orders.md)
- [Purchase order overview](../../supply-chain/procurement/purchase-order-overview.md)
- [Product receipt against purchase orders](../../supply-chain/procurement/product-receipt-against-purchase-orders.md)
