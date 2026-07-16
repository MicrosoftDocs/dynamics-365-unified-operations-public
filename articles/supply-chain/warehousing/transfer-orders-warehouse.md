---
title: Set up warehouses for transfer orders
description: Learn how you can set up warehouses for transfer orders, including a step-by-step process for setting up warehouses for transfer orders.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 05/28/2026
ms.custom: bap-template
ms.reviewer: kamaybac 
ms.search.form: InventLocation,CustVendTransportPoint2Point
---

# Set up warehouses for transfer orders

[!include [banner](../includes/banner.md)]

Use warehouse levels to create a hierarchy that supports transfer orders between warehouses. With this setup, master scheduling calculates item requirements at the individual warehouse level and generates planned transfer orders from an assigned source warehouse to fulfill them.

1. Select **Inventory management** > **Setup** > **Inventory breakdown** > **Warehouses**.

1. Select the warehouse that you want to refill.

1. On the **Master planning** FastTab, select the **Refilling** check box.

1. In the **Main warehouse** field, select the warehouse that you want to assign as the refilling warehouse. Master scheduling calculates a transfer requirement for the selected warehouse and generates a planned transfer order from the assigned **Main warehouse**.

    > [!NOTE]
    > If you clear the **Refilling** check box, the selected warehouse is assigned a warehouse level in regard to the **Main warehouse**, but the **Main warehouse** isn't set up as a refilling warehouse.

1. Close the page to apply the new setup.

> [!TIP]
> To assign a warehouse for refilling, first set up the warehouse as a storage dimension on the <STRONG>Storage dimension groups</STRONG> page. On this page, select the <STRONG>Active</STRONG> field and the <STRONG>Coverage plan by dimension</STRONG> field for the warehouse.</P>

## Set up transport lead time

Set up the transport lead time between the warehouses on the **Transport days** page.

1. Go to **Inventory management > Setup > Distribution > Transport days**.
1. In the **Receiving point** field, select **Warehouse**.
1. Select the **Shipping warehouse**, **Receiving warehouse**, and **Transport days**.
1. (Optional) Under the **Transport days per mode of delivery** tab, set the transport time depending on the mode of delivery.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
