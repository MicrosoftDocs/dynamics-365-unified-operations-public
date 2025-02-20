---
title: Restrict to sales unit 
description: Learn about the Restrict to sales unit option for products
author: Atapiabailon
ms.author: atapiabailon
ms.topic: article
ms.date: 20/02/2025
ms.custom:
ms.reviewer: kamaybac
ms.search.form:  EcoResProductDetailsExtendedGrid, WHSAutoReleaseToWarehouse
---

# Restrict to sales unit

[!include [banner](../includes/banner.md)]

This article provides an explanation about the **Restrict to sales unit** option, complemented with an example scenario.

The **Restrict to sales unit** functionality is designed to ensure that products are sold in a specific, predefined unit. This functionality is applicable exclusively to sales orders. It specifies the exact unit in which a product should be sold. If the reservation of a product in a sales order leads to incomplete sales units, the system blocks the release of the sales order to the warehouse. Instead, it displays an error message to the customer, indicating that the sales order can't be processed due to the incomplete sales units.

To configure the **Restrict to sales unit** in your product, follow these steps:

1. Navigate to **Product information management** \> **Products**.
1. To see the product details, select a product from the list.
1. Expand the **Warehouse** fast tab.
1. In the **Release to warehouse** section, you can see the **Restrict to unit** dropdown.
1. There are two options, **No restrictions** and **Sales unit**.
1. Select the **Sales unit** from the dropdown.
1. Click on the **Save** button on the action pane.

> [!IMPORTANT]
>
> The sales unit to be used by the **Restrict to sales unit** is the **Unit** indicated under the **Sell** fast tab in the product details.

## Example of releasing a sales order with conversion of units
Consider the following scenario:
1. A product, *item-one* with inventory unit in **Pieces**.
1. A sales unit in **Box**.
1. A conversion of *1 Box* is equals to *5 Pieces*.
1. The **Restrict to unit** set to *Sales unit*.
1. A sales order for *item-one*, with *10 Pieces*.

When trying to release the order to warehouse, there could be 2 scenarios:
1. If the reserved quantity is the full quantity, in this case, *10 Pieces*, the sales order is released to warehouse successfully.
1. If the reserved quantity is, for example, *7 Pieces* which result in one full box and almost half of the other, the releasing of the sales order to warehouse fails, showing an error message to the customer.

> [!NOTE]
>
> There's an exception to the expected behavior of the **Restrict to sales unit** functionality.
> This exception happens when the **Automatic release of sales orders** functionality is enabled with the **Quantity to release** option set to **All**. This setup ignores the **Restrict to sales unit** functionality.

- For information about the **Automatic release of sales orders** functionality, see [Automatic release to the warehouse](release-to-warehouse-process#automatic-release-to-the-warehouse).