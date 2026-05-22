---
title: Generate assembly and disassembly orders
description: Learn how to generate assembly and disassembly orders for retail product kits in Microsoft Dynamics 365 Commerce.
author: rickwyang
ms.date: 01/22/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: wenxyang
ms.search.validFrom: 2023-10-23
---
# Generate assembly and disassembly orders

[!include [banner](includes/banner.md)]

This article describes how to generate assembly and disassembly orders for retail product kits in Microsoft Dynamics 365 Commerce.

An assembly order tells the warehouse how many product kits to assemble. After you create an assembly order, a warehouse worker can use it to assemble each configuration of the product kit.

You can generate assembly orders by using any of the following methods:

- Use the **Configure kit** page after you configure the product kit and release it to your legal entities.
- Use the **Kit orders** page to manually generate an assembly order for an existing product kit.
- Automatically generate an assembly order from a sales order.

After you generate an assembly order and enter the quantities that you want to assemble, the system generates bill of materials (BOM) journals to reserve the inventory for the products that are included in the kit configurations.

## Generate an assembly order from a product kit

To generate an assembly order from a product kit, follow these steps:

1. In Commerce headquarters, go to **Retail and Commerce** \> **Products and categories** \> **Released product kits**.
1. On the **Released product kits** list page, double-tap (or double-click) a product kit.
1. On the **Released product details** page, select **Edit**.
1. On the Action Pane, on the **Product** tab, in the **Product kit** group, select **Configure**.
1. On the **Configure kit** page, select **Generate assembly order**.
1. On the **Kit order** page, on the **General** FastTab, in the **Warehouse** field, select the warehouse where the product kits are assembled.
1. On the **Configurations** FastTab, in the **Quantity** field, enter the number of product kits that you want the warehouse to assemble for each kit configuration. The **Quantity** field on the **General** FastTab shows the total number of kits that are assembled for this order.
1. After you enter the quantity for each kit configuration, close the page to create the assembly order.

On the **Kit orders** page, you can view the assembly order that you created and the BOM journal entries that were created.

To view the assembly order and BOM journal entries, follow these steps:

1. In Commerce headquarters, go to **Retail and Commerce** \> **Products and categories** \> **Kit orders**.
1. On the **Kit orders** list page, double-tap (or double-click) a kit order to view the details of the assembly order that you created.
1. To view the BOM journal entries, on the **Kit order** page, on the **Configurations** FastTab, select **View BOM journal**.

## Manually generate assembly and disassembly orders for a product kit

If you need to assemble more product kits for your stores, you can manually create assembly orders. You can also create disassembly orders for product kits that you're no longer selling. After the product kits are disassembled at the warehouse, the individual kit products can be returned to inventory. Product kits can also be disassembled at the point of sale (POS) register if you select the **Disassemble at register** checkbox on the **Configure kit** page. For more information about how to set up a product kit, see [Create retail product kits](./create-retail-product-kits.md).

If you want to prevent creating any more assembly orders for a product kit, you can discontinue the kit. To discontinue an existing product kit, on the **Configure kit** page, select the **Discontinue kit** checkbox for the kit. If you select this checkbox, you can't assemble new product kits for the kit, and you can only sell the remaining store inventory for the kit.

After you create the assembly and disassembly orders, warehouse workers can assemble or disassemble product kits. For more information about how to process assembly and disassembly orders, see [Process kit assembly and disassembly orders](./process-kit-assembly-and-disassembly-orders.md).

To manually generate assembly and disassembly orders for a product kit, follow these steps:

1. In Commerce headquarters, go to **Retail and Commerce** \> **Products and categories** \> **Kit orders**.
1. On the **Kit orders** list page, on the Action Pane, select **Order**.
1. In the **Create a new kit order** dialog box, set the fields that are described in the following table.

    | Field | Description |
    |-------|-------------|
    | **Order type** | Select whether you want to create an assembly order or a disassembly order. |
    | **Product kit** | Select the product kit that you want to assemble or disassemble. |
    | **Company** | Select the legal entity that you're assembling or disassembling product kits for. |
    | **Warehouse** | Select the warehouse that processes the assembly or disassembly order. |

1. Select **OK**.
1. To complete the order, on the **Kit orders** list page, double-tap (or double-click) the assembly or disassembly order that you created in the previous step.
1. On the **Kit order** page, on the **Configurations** FastTab, in the **Quantity** field, enter the number of product kits that you want the warehouse worker to assemble or disassemble for each kit configuration. The **Quantity** field on the **General** FastTab shows the total number of kits that the order assembles or disassembles.
1. After you enter the quantity for each kit configuration, close the page to create the order.

On the **Kit orders** page, you can view the order that you created and the BOM journal entries that were created.

To view the order and BOM journal entries, follow these steps:

1. In Commerce headquarters, go to **Retail and Commerce** \> **Products and categories** \> **Kit orders**.
1. On the **Kit orders** list page, double-tap (or double-click) a kit order to view the details of the assembly or disassembly order.
1. To view the BOM journal entries, on the **Kit order** page, on the **Configurations** FastTab, select **View BOM journal**.

## Generate an assembly order from a sales order

If a product kit or any of its components are out of stock when you add the kit to a sales order, you can generate an assembly order for the kit from the sales order. The sales order processing generates the assembly order. When you generate an assembly order from a sales order, you can view the sales order number in the description field on the **Kit order** page.

> [!NOTE]
> If you increase the quantities on the sales order line after the assembly order is posted, you must create a separate assembly order.

When you sell product kits in a cash-and-carry scenario, if a kit isn't found in the store's inventory, the system automatically generates an assembly order for the sale when the store's transactions are sent to Commerce headquarters. The system then automatically processes and posts the assembly order.

To generate an assembly order from a sales order, follow these steps:

1. In Commerce headquarters, go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
1. On the **All sales orders** list page, on the Action Pane, on the **Sales order** tab, select **Sales order** to create a new sales order.
1. In the **Create sales order** dialog box, in the **Customer account** field, select the customer account to create the sales order for. Enter any additional information, such as the invoice account, currency, or language, and then select **OK**.
1. On the **Sales order** page, on the **Sales order lines** FastTab, in the **Item number** field, select a product kit to add to the sales order.
1. On the **Line details** FastTab, on the **Product** tab, in the **Configuration** field, select the specific configuration of the product kit that you want to add to the sales order.
1. To view the individual components in the kit configuration, on the **Sales order lines** FastTab, select **Inventory** \> **Kit components**.
1. Enter any additional information for the sales order, and then process the sales order to automatically generate the assembly order for the kit products.

## Additional resources

[Retail product kit setup overview](retail-product-kit-setup.md)

[Create retail product kits](create-retail-product-kits.md)

[Process kit assembly and disassembly orders](process-kit-assembly-and-disassembly-orders.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
