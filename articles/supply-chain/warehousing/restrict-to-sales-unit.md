---
title: Restrict to sales unit
description: Learn about the Restrict to sales unit functionality for products.
author: Mirzaab
ms.author: mirzaab
ms.date: 02/20/2025
ms.topic: how-to
ms.reviewer: kamaybac
ms.search.form: EcoResProductDetailsExtendedGrid, WHSAutoReleaseToWarehouse
ms.custom: bap-template
---

# Restrict to sales unit

This article describes the *Restrict to sales unit* functionality and provides an example scenario.

The *Restrict to sales unit* functionality is designed to ensure that products are sold in a specific, predefined unit. This functionality applies exclusively to sales orders. It specifies the exact unit that a product should be sold in. If the reservation of a product on a sales order leads to incomplete sales units, the release of the sales order to the warehouse is blocked. An error message indicates that the sales order can't be processed because of the incomplete sales units.

To configure the *Restrict to sales unit* functionality for a product, follow these steps.

1. Go to **Product information management** \> **Products**.
1. In the list, select a product to view the product details.
1. On the **Warehouse** FastTab, in the **Release to warehouse** section, in the **Restrict to unit** field, select *Sales unit*.
1. Select **Save**.

> [!IMPORTANT]
> The **Unit** field on the **Sell** FastTab of the product details defines the sales unit that the *Restrict to sales unit* functionality uses.

## Example: Releasing a sales order with conversion of units

This example is based on the following scenario:

- Product *item-one* has *Pieces* as the inventory unit.
- The sales unit is *Box*.
- A conversion defines *1 Box* as equal to *5 Pieces*.
- The **Restrict to unit** field is set to *Sales unit*.
- There is a sales order for *10 Pieces* or product *item-one*.

When the sales order is released to the warehouse, the outcome depends on the reserved quantity:

- If the reserved quantity is the full quantity, *10 Pieces*, the sales order is successfully released to the warehouse.
- If the reserved quantity is *7 Pieces*, the result is one full box and almost half of the other box. In this case, the release of the sales order to the warehouse fails, and the customer receives an error message.

> [!NOTE]
> There is an exception to the expected behavior of the *Restrict to sales unit* functionality. If the *Automatic release of sales orders* functionality is enabled, and the **Quantity to release** option is set to *All*, the *Restrict to sales unit* functionality is ignored.
>
> Learn more about the *Automatic release of sales orders* functionality in [Automatic release to the warehouse](release-to-warehouse-process.md#automatic-release-to-the-warehouse).
