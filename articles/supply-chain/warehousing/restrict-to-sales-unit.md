---
title: Restrict to sales unit
description: Learn about the Restrict to sales unit functionality for products.


author: Atapiabailon
ms.date: 02/20/2025
ms.topic: article
ms.reviewer: kamaybac
ms.search.form: EcoResProductDetailsExtendedGrid, WHSAutoReleaseToWarehouse
ms.custom:



[!include [banner](../includes/banner.md)]

[!include [banner](../includes/banner.md)]

# Restrict to sales unit

To configure the *Restrict to sales unit* functionality for a product, follow these steps.

1. Go to **Product information management** \> **Products**.

1. In the list, select a product to view the product details.
1. Select **Save**.

> [!IMPORTANT]
> The **Unit** field on the **Sell** FastTab of the product details defines the sales unit that the *Restrict to sales unit* functionality uses.
> The **Unit** field on the **Sell** FastTab of the product details defines the sales unit that the *Restrict to sales unit* functionality uses.
1. On the **Warehouse** FastTab, in the **Release to warehouse** section, in the **Restrict to unit** field, select *Sales unit*.
This example is based on the following scenario:
This example is based on the following scenario:
- The **Restrict to unit** field is set to *Sales unit*.
- Product *item-one* has *Pieces* as the inventory unit.
- The sales unit is *Box*.
- A conversion defines *1 Box* as equal to *5 Pieces*.
- The **Restrict to unit** field is set to *Sales unit*.

- There is a sales order for *10 Pieces* of product *item-one*.
When the sales order is released to the warehouse, the outcome depends on the reserved quantity:
- If the reserved quantity is the full quantity, *10 Pieces*, the sales order is successfully released to the warehouse.
- If the reserved quantity is the full quantity, *10 Pieces*, the sales order is successfully released to the warehouse.
> There is an exception to the expected behavior of the *Restrict to sales unit* functionality. If the *Automatic release of sales orders* functionality is enabled, and the **Quantity to release** option is set to *All*, the *Restrict to sales unit* functionality is ignored.





When the sales order is released to the warehouse, the outcome depends on the reserved quantity:



- If the reserved quantity is the full quantity (*10 Pieces*), the sales order is successfully released to the warehouse.

- If the reserved quantity is *7 Pieces*, the result is one full box and almost half of the other box. In this case, the release of the sales order to the warehouse fails, and the customer receives an error message.



> [!NOTE]

> There's an exception to the expected behavior of the *Restrict to sales unit* functionality. If the *Automatic release of sales orders* functionality is enabled, and the **Quantity to release** option is set to *All*, the *Restrict to sales unit* functionality is ignored.

>

> Learn more about the *Automatic release of sales orders* functionality in [Automatic release to the warehouse](release-to-warehouse-process#automatic-release-to-the-warehouse).

