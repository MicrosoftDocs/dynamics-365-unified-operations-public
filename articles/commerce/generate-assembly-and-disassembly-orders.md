---
title: Generate assembly and disassembly orders
description: This article describes how to generate assembly and disassembly orders for retail product kits in Microsoft Dynamics 365 Commerce.
author: rickwyang
ms.date: 10/31/2023
ms.topic: article
audience: Application User
ms.reviewer: josaw
ms.search.region: Global
ms.author: wenxyang
ms.search.validFrom: 2023-10-23
---

# Generate assembly and disassembly orders


[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This article describes how to generate assembly and disassembly orders for retail product kits in Microsoft Dynamics 365 Commerce.

An assembly order tells the warehouse how many kits to assemble. After an assembly order is created, a warehouse worker can use it to assemble each configuration of the product kit.

You can generate assembly orders by using any of the following methods:
  - Generate the assembly order by using the **Configure kit** form after you configure the retail product kit and release the product kit to your legal entities.
  - Manually generate an assembly order for an existing product kit by using the **Kit orders** form.
  - Automatically generate an assembly order from a sales order.

After you generate an assembly order and enter the quantities that you want to assemble, BOM (bill of material) journals are generated to reserve the inventory for the products that are included in the kit configurations.

## Generate an assembly order from a product kit

To generate an assembly order from a product kit, follow these steps.

1. Go to **Retail and Commerce \> Products and categories \> Released product kits**. In the **Released product kits** list, double-click a product kit.
1. In the **Released product details** form, select **Edit**. Then, on the Action Pane, on the **Product** tab, on the **Product kit**, select **Configure**.
1. In the **Configure kit** form, select **Generate assembly order**.
1. In the **Kit order** form, on the **General** FastTab, in the **Warehouse** field, select the warehouse where the product kits will be assembled.
1. On the **Configurations** FastTab, in the **Quantity** field, enter the number of kits that you want the warehouse to assemble for each kit configuration. The total number of kits that will be assembled for this order is displayed in the **Quantity** field in the **General** FastTab.
1. After you have entered the quantity for each configuration, close the form to create the assembly order.

You can view the assembly order that you created and the BOM journal entries that were created in the **Kit orders** form. 

To view the assembly order and BOM journal entries, follow these steps.

1. Go to **Retail and Commerce \> Products and categories \> Kit orders**.
1. In the **Kit orders** list, double-click a kit order to view the details of the assembly order that you just created.
1. To view the BOM journal entries, in the **Kit order** form, on the **Configurations** FastTab, select **View BOM journal**.

## Manually generate assembly and disassembly orders for a product kit

If you need to assemble additional product kits for your stores, you can manually create assembly orders. You can also create disassembly orders for product kits that you are no longer selling. After the product kits are disassembled at the warehouse, the individual kit products can be returned to inventory. Product kits can also be disassembled at the point of sale register if the **Disassemble at register** check box is selected in the **Configure kit** form. For more information about how to set up a product kit, see [Create retail product kits](./create-retail-product-kits.md).

If you want to prevent any more assembly orders from being created for a kit, you can discontinue the kit. To discontinue an existing kit, select the **Discontinue kit** check box for the product kit in the **Configure kit** form. If this check box is selected, no new kits can be assembled for this kit, and only the remaining store inventory for the kit can be sold.

After the assembly and disassembly orders are created, kits can be assembled or disassembled by warehouse workers. For more information about how to process assembly and disassembly orders, see [Process kit assembly and disassembly orders](./process-kit-assembly-and-disassembly-orders.md).

To manually generate assembly and disassembly orders for a product kit, follow these steps.

1. Go to **Retail and Commerce \> Products and categories \> Kit orders**.
1. In the **Kit orders** list, on the Action Pane, select **Order**.
1. In the **Create a new kit order** dialog box, enter information as described in the following table.

    | Field | Description |
    |-------|-------------|
    | **Order type** | Select whether you want to create an assembly order or a disassembly order. |
    | **Product kit** | Select the product kit that you want to assemble or disassemble. |
    | **Company** | Select the legal entity for which the kits are being assembled or disassembled. |
    | **Warehouse** | Select the warehouse that will process the assembly or disassembly order. |

1. Select **OK**.
1. To complete the order, on the **Kit orders** list page, double-click the assembly or disassembly order that you created in the previous step.
1. In the **Kit order** form, on the **Configurations** FastTab, in the **Quantity** field, enter the number of kits that you want the warehouse worker to assemble or disassemble for each kit configuration. The total number of kits that will be assembled or disassembled for this order is displayed in the **Quantity** field on the **General** FastTab.
1. After you enter the quantity for each configuration, close the form to create the order.

You can view the order that you created and the BOM journal entries that were created in the **Kit orders** form. 

To view the order and BOM journal entries, follow these steps.

1. Go to **Retail and Commerce \> Products and categories \> Kit orders**.
1. In the **Kit orders** list, double-click a kit order to view the details of the assembly or disassembly order that you just created.
1. To view the BOM journal entries, in the **Kit order** form, on the **Configurations** FastTab, select **View BOM journal**.

## Generate an assembly order from a sales order

If a product kit or any of its components are out of stock when you add a product kit to a sales order, you can generate an assembly order for the product kit from the sales order. The assembly order is generated when the sales order is processed. When an assembly order is generated from a sales order, the sales order number can be viewed in the description field in the **Kit order** form.

> [!NOTE]
> If the quantities on the sales order line are increased after the assembly order is posted, a separate assembly order must be created.

When product kits are sold in a cash-and-carry scenario, and the product kit is not found in the store’s inventory, the system automatically generates an assembly order for the sale when the store’s transactions are sent to headquarters. The assembly order is then automatically processed and posted.

To generate an assembly order from a sales order, follow these steps:

1. Go to **Sales and marketing \> Sales orders \> All sales orders**. In the **All sales orders** list, on the Action Pane, on the **Sales order** tab, select **Sales order** to create a new sales order.
1. In the **Create sales order** form, in the **Customer account** field, select the customer account to create the sales order for. Enter any addition information such as invoice account, currency, or language, and then select **OK**.
1. In the **Sales order** form, on the **Sales order lines** FastTab, in the **Item number** field, select a product kit to add to the sales order.
1. On the **Line details** FastTab, on the **Product** tab, in the **Configuration** field, select the specific configuration of the product kit that you want to add to the sales order.
1. To view the individual components in the product kit configuration, on the **Sales order lines** FastTab, select **Inventory** \> **Kit components**.
1. Enter any additional information to the sales order, and then process the sales order to automatically generate the assembly order for the kit products.

## Additional resources

[Retail product kit setup overview](retail-product-kit-setup.md)

[Create retail product kits](create-retail-product-kits.md)




[!INCLUDE[footer-include](../includes/footer-banner.md)]
