---
title: Process kit assembly and disassembly orders
description: This article describes how to process kit assembly and disassembly orders for retail product kits in Microsoft Dynamics 365 Commerce.
author: rickwyang
ms.date: 11/03/2023
ms.topic: article
audience: Application User
ms.reviewer: josaw
ms.search.region: Global
ms.author: wenxyang
ms.search.validFrom: 2023-10-23
---

# Process kit assembly and disassembly orders

[!include [banner](includes/banner.md)]

This article describes how to process kit assembly and disassembly orders for retail product kits in Microsoft Dynamics 365 Commerce.

After you generate assembly or disassembly orders for the different product kit configurations and generate bill of materials (BOM) journals to reserve the product inventory, the next step is to process the assembly and disassembly orders for the kit configurations.

## Process assembly orders

To process an assembly order, a warehouse worker must update the quantities for each kit configuration that's being assembled. After the order is processed, post it to run the inventory process that updates the status of the products from reserved to committed. Inventory for the kit configurations is then increased, and inventory for the individual products that are included in the kit configurations is decreased.

To process assembly orders, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce** \> **Products and categories** \> **Kit orders**.
1. On the **Kit orders** list page, select a product kit that has an order type of **Assembly order**.
1. On the Action Pane, select **Assemble kit**.
1. On the **Kit order** page, in the **Assembled** field, enter the number of kit configurations to assemble for each configuration.
1. Select **Post** to post the assembly order and run the inventory process to update the status of the products.

> [!NOTE]
> After the assembly order is posted, you can't use it to assemble additional kit configurations. To assemble additional kit configurations, you must create a new assembly order for the product kit.

## Process disassembly orders

To process a disassembly order, a warehouse worker must update the quantities for each kit configuration that's being disassembled. After the order is processed, post it to run the inventory process that updates the status of the products from reserved to committed. Inventory for the kit configurations is then decreased, and inventory for the individual products that are included in the kit configurations is increased.

To process disassembly orders, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce** \> **Products and categories** \> **Kit orders**.
1. On the **Kit orders** list page, select a product kit that has an order type of **Disassembly order**.
1. On the Action Pane, select **Disassemble kit**.
1. On the **Kit order** page, in the **Disassembled** field, enter the number of kit configurations to disassemble for each configuration.
1. Select **Post** to post the disassembly order and run the inventory process to update the status of the products.

> [!NOTE]
> After the disassembly order is posted, you can't use it to disassemble additional kit configurations. To disassemble additional kit configurations, you must create a new disassembly order for the product kit.

## Additional resources

[Retail product kit setup overview](retail-product-kit-setup.md)

[Create retail product kits](create-retail-product-kits.md)

[Generate assembly and disassembly orders](generate-assembly-and-disassembly-orders.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
