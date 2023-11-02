---
title: Create retail product kits
description: This article describes how to create retail product kits in Microsoft Dynamics 365 Commerce.
author: rickwyang
ms.date: 11/02/2023
ms.topic: article
audience: Application User
ms.reviewer: josaw
ms.search.region: Global
ms.author: wenxyang
ms.search.validFrom: 2023-10-23
---

# Create retail product kits

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This article describes how to create retail product kits in Microsoft Dynamics 365 Commerce.

By using retail product kits, you can package individual products into one sellable unit and make them available for sale in any retail channel. A product kit consists of kit components and component substitutes. A kit component can be either a distinct product or a product variant. A component substitute can be a distinct product, product master, or product variant. The different combinations of components and component substitutes that are included in a product kit are referred to as kit configurations. One product kit can have one or more configurations.

After you create retail product kits, you release the kits to the legal entities for which you want to offer them, and you define the product properties. After the kits have been released, you define the pricing for them. The kit price can also be adjusted at the time of sale if additional charges apply for products that are substituted for a standard kit component.

The following illustration shows the process flow for setting up a retail product kit.

![Set up retail product kits](./media/Dn497863.SetupProductKits(AX.60).gif)

The following illustration shows how the process of creating retail product kits relates to the overall process flow for retail product kits. For an overview of the process, see [Retail product kit setup overview](retail-product-kit-setup.md).

![The overall kit process flow](./media/Dn497863.KitBiggerProcess(AX.60).gif)

## Prerequisites

The following table lists the prerequisites that must be in place before you start creating retail product kits.

| Category | Prerequisite |
|-------|-------------|
| Set up kit parameters | You must specify the journal name to use to generate trade agreements for products and product variants that are included in a retail product kit. |
| Set up receipt formats for kit products | You must specify whether or not to show the individual kit components on the product receipt. |
| Set up products | Before you can add products, product variants, and product substitutes to a product kit, you must set up your products. For more information about how to set up retail products, see [Set up retail products](set-up-retail-products.md). |

## Create a product kit

First you must create a new product, and designate it as a product kit. After you create the product kit, you can add products and product variants to the kit as your kit components. You can also add product substitutes for any of the kit components.

To create a product kit, follow these steps:

1. In Commerce headquarters, go to **Retail and Commerce \> Products and categories \> Product kits**.
1. On the Action Pane, select **New**.
1. In the **New product** dialog box, enter the following information:
    1. For **Product type**, select **Item**.
    1. Enter a product number, product name, and search name.
    1. Optionally, for **Retail category**, select the retail product category to which you want to assign the product kit. The **Product kit** checkbox is selected by default.
    1. For **Product dimension group**, select the product dimension group that includes the **Configuration** product dimension.
1. Leave all other fields populated with their default values, and then select **OK**.

## Add products and product substitutes to the product kit

Next, you must add the kit components and component substitutes to the kit to define every kit combination that you offer. You must also set up the kit configuration options to indicate whether or not the kit can be disassembled in the point-of-sale (POS) store.

To add products and product substitutes to the product kit, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Products and categories \> Product kits**.
1. On the **Product masters** list page, select the new product kit that you created previously. On the Action Pane, under **Product kit**, select **Configure**.
1. On the **Configure kit** form, select **Edit**.
1. On the **General** FastTab, select the **Disassemble at register** checkbox if you want to allow the kit to be disassembled in the POS store. This allows the kit components to be sold individually.
1. On the **Kit components** FastTab, in the **Components** grid, select **Add** to add the base products to the kit.
1. On the **Add products** form, select the products and product variants you want to add to the product kit, and then select **OK**.
1. In the **Components** grid, you can optionally adjust the quantity and unit of measure for each kit component that you added.
1. On the **Kit components** FastTab, in the **Substitution** grid, select **Add** to add product substitutes for selected base products in the kit.
1. On the **Add products** form, select the products and product variants that you want to add as product substitutes, and then select **OK**.
1. Repeat steps 8 and 9 for each product substitute that you want to add.
1. After you have added all the product components and component substitutes to the kit, select **Approve** to approve the product kit.

> [!NOTE]
> Product kits must have a status of **Approved** before you can release the kit to your legal entities, price the kit, or generate assembly orders.

## Release the product kit to legal entities

Next, you must release the product kit to the legal entities for which the product kits will be sold. You must release the product kit in order to define the pricing for the kit configurations, set up the product properties for the kit, and generate assembly orders for the product kit.

To release the product kit to legal entities, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Products and categories \> Product kits**.
1. On the **Product masters** list page, select the new product kit that you configured previously, and then on the Action Pane, select **Release products**.
1. On the **Release products** form, on the **Select products to release** tab, select the kit configurations that you want to release. By default, all configurations for the selected product kit are selected.
1. On the **Select companies to release to** tab, select the legal entities for which the kit should be released, and then select **Next**.
1. On the **Confirm selection** tab, select **Finish** to run the process and release the products to the selected legal entities.
1. To verify that the product kit has been released to the selected legal entities, follow these steps:
    1. Go to **Retail and Commerce \> Products and categories \> Released product kits**.
    1. On the **Released product kits** list page, view your product kit.

## Set the standard properties for the product kit

After you release the product kits to the legal entities, you can then set the standard properties that apply to the products in the kit. These properties can include inventory dimensions, product categories, and product attributes. For general information about how to set up product properties, see [Key tasks: Define products](/dynamicsax-2012/appuser-itpro/key-tasks-define-products). For information about how to set up retail products, see [Set up retail products](set-up-retail-products.md).

To set the standard properties for the product kit, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Products and categories \> Released product kits**.
1. On the **Released product kits** list page, double-click the product kit that you released previously.
1. On the **Released product details** form, select **Edit**.
1. On the Action Pane, under **Product /> Set up**, select **Dimension groups**, and then select the inventory dimension groups for the product kit.
1. On the **General** FastTab, in the **Administration** group, select the item model group for the kit. This allows the kit can be assembled.
1. On the **Purchase** FastTab, for **Unit**, select the unit of measure to use for the purchase of the product kit.
1. On the **Sell** FastTab, for **Unit**, select the unit of measure to use for the sale of the product kit.
1. On the **Manage inventory** FastTab, in the **Inventory** group, for **Unit**, select the unit of measure for which the product kit is stored in inventory.
1. On the **Retail** FastTab, enter any additional information that is required for the product kit. This information includes configuration data for any product variants that are included in the kit.

## Define kit pricing and generate trade agreements

You can price product kits as a whole product, or as a sum of the individual components. The base price for each kit component is the price of the product at the time it was added to the product kit.

If you define a price for the overall kit, the new price is distributed across all the products in the kit. The price adjustment to each product is based on the percentage that each product's base price contributes to the total base price for the product kit. You can also specify whether there is an additional charge for product substitutes when the customer selects the product substitute instead of the base component. The additional cost is included when the kit price is calculated.

To define kit pricing and generate trade agreements, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Products and categories \> Released product kits**.
1. On the **Released product kits** list page, double-click a released product kit in the list.
1. On the **Released product details** form, select **Edit**.
1. On the Action Pane, under **Product \> Product kit**, select **Configure**.
1. On the **Configure kit** form, on the **Kit components** FastTab, in the **Components** grid, follow one of these steps:
    - In the **Kit price** column, enter the kit price for each component in the product kit.
    - Select **Specify kit price** to enter a price for the overall product kit.
1. On the **Kit components** FastTab, in the **Substitution** grid, for **Charge**, enter the amount to add to the kit price if the substitute product is selected to replace the base product component. Repeat this step for each substitute product in the grid. For example, a customer selects a kit that includes a standard bicycle tire set, but the customer wants to upgrade to a premium bicycle tire set. If the cost to upgrade the tire set is $50.00 USD, for **Charge**, enter **50.00**.
1. Repeat steps 5 and 6 for each component and component substitute that is included in the product kit.

> [!NOTE]
> If you select an overall kit price for the base components in the product kit, you only have to implement step 5 once.

## Technical information for system administrators

If you don't have access to the pages that are used to complete this task, contact your system administrator and provide the information shown in the following table.

| Category | Prerequisite |
|-------|-------------|
| Configuration keys | Retail |
| Security roles | Merchandising manager |

## Next steps

After you set up the kit and define your kit configuration, the next steps are to generate the assembly orders and assemble the orders. For more information, see [Generate assembly and disassembly orders](generate-assembly-and-disassembly-orders.md) and [Process kit assembly and disassembly orders](process-kit-assembly-and-disassembly-orders.md).

## Additional resources

[Retail product kit setup overview](retail-product-kit-setup.md)

[Generate assembly and disassembly orders](generate-assembly-and-disassembly-orders.md)

[Process kit assembly and disassembly orders](process-kit-assembly-and-disassembly-orders.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
