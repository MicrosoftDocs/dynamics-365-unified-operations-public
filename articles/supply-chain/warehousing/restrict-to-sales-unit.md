---
title: Restrict to sales unit 
description: Learn about the Restrict to sales unit option for products
author: Atapiabailon
ms.author: atapiabailon
ms.topic: article
ms.date: 02/20/2025
ms.custom:
ms.reviewer: kamaybac
ms.search.form:  EcoResProductDetailsExtendedGrid, WHSAutoReleaseToWarehouse
---

# Restrict to sales unit

[!include [banner](../includes/banner.md)]

This article describes the **Restrict to sales unit** option with an example scenario.

The **Restrict to sales unit** functionality is designed to ensure that products are sold in a specific, predefined unit. This functionality applies exclusively to sales orders. It specifies the exact unit in which a product should be sold. If the reservation of a product in a sales order leads to incomplete sales units, the release of the sales order to the warehouse is blocked. An error message is displayed, indicating that the sales order can't be processed due to the incomplete sales units.

To configure the **Restrict to sales unit** in your product, follow these steps:

1. Go to **Product information management** \> **Products**.
1. To see the product details, select a product from the list.
1. Expand the **Warehouse** FastTab.
1. In the **Release to warehouse** section, in the **Restrict to unit** dropdown, select the **Sales unit**.
1. Click **Save**.

> [!IMPORTANT]
> The sales unit used by the **Restrict to sales unit** is the **Unit** indicated under the **Sell** FastTab in the product details.

## Example of releasing a sales order with conversion of units
Consider the following scenario:
 - A product, *item-one* with inventory unit in **Pieces**.
 - A sales unit in **Box**.
 - A conversion of *1 Box* is equals to *5 Pieces*.
 - The **Restrict to unit** set to *Sales unit*.
 - A sales order for *item-one*, with *10 Pieces*.

When releasing the order to warehouse, there could be 2 scenarios:
1. If the reserved quantity is the full quantity, *10 Pieces*, the sales order is released to warehouse successfully.
1. If the reserved quantity is, *7 Pieces*, which results in one full box and almost half of the other, the release of the sales order to warehouse fails, showing an error message to the customer.

> [!NOTE]
> There's an exception to the expected behavior of the **Restrict to sales unit** functionality.
> When the **Automatic release of sales orders** functionality is enabled with the **Quantity to release** option set to **All**. This setup ignores the **Restrict to sales unit** functionality.

- For information about the **Automatic release of sales orders** functionality, see [Automatic release to the warehouse](release-to-warehouse-process#automatic-release-to-the-warehouse).
