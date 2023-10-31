---
title: Create retail product kits
description: This article describes the steps of creating retail product kits.
author: rickwyang
ms.date: 10/31/2023
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

This topic describes the tasks that are required to set up retail product kits. By using product kits, you can package individual products into one sellable unit and make them available for sale in any retail channel. A product kit consists of kit components and component substitutes. Kit components can be either a distinct product or a product variant. Component substitutes can be a distinct product, product master, or product variant. The different combinations of components and component substitutes that are included in a product kit are referred to as kit configurations. One product kit can have one or more configurations.

After you create the product kits, you release the kits to the legal entities in which you want to offer them, and you define the product properties. After the kits have been released, you define the pricing for them. The kit price can also be adjusted at the time of sale if additional charges apply for products that are substituted for a standard kit component.

The following illustration shows the process flow for setting up a retail product kit. The numbers correspond to the procedures later in this topic.

![Set up retail product kits](./media/Dn497863.SetupProductKits(AX.60).gif "Set up retail product kits")

## This task is part of a bigger process

The following illustration shows how the process of creating retail product kits relates to the overall process flow for retail product kits. For an overview of the process, see [Retail product kit setup overview](retail-product-kit-setup.md).

![The overall kit process flow](./media/Dn497863.KitBiggerProcess(AX.60).gif "The overall kit process flow")

## Prerequisites

The following table shows the prerequisites that must be in place before you start.

| Category | Prerequisite |
|-------|-------------|
| Set up kit parameters | Specify the journal name to use to generate trade agreements for products and product variants that are included in a retail product kit. |
| Set up receipt formats for kit products | Specify whether to show the individual kit components on the product receipt. |
| Set up products | Before you can add products, product variants, and product substitutes to a product kit, you must set up your products. For more information about how to set up retail products, see [Set up retail products](set-up-retail-products.md). |

## 1\. Create a product kit

Create a new product, and designate it as a product kit. After you create the product kit, you can add products and product variants to the kit as your kit components. You can also add product substitutes for any of the kit components.

To create a product kit, follow these steps:

1.  Click **Retail and Commerce \> Products and categories \> Product kits**.

2.  On the **Action Pane**, click **New**.

3.  In the **New product** dialog box, enter the following information:

      - In the **Product type** field, select **Item**.

      - Enter a product number, product name, and search name.

      - Optional: In the **Retail category** field, select the retail product category that you want to assign the product kit to.

        The **Product kit** check box is selected by default.

      - In the **Product dimension group** field, select the product dimension group that includes the **Configuration** product dimension.

4.  Leave the default values for all other fields, and then click **OK**.

## 2\. Add products and product substitutes to the product kit

Add the kit components and component substitutes to the kit to define every kit combination that you offer. Also, set up the kit configuration options to indicate whether the kit can be disassembled in the point-of-sale (POS) store.

1.  Click **Retail and Commerce \> Products and categories \> Product kits**.

2.  On the **Product masters** list page, select the new product kit that you created in the previous task. On the **Action Pane**, on the **Product kit** tab, click **Configure**.

3.  In the **Configure kit** form, click **Edit**.

4.  On the **General** FastTab, select the **Disassemble at register** check box if you allow the kit to be disassembled in the POS store, so that the kit components can be sold individually.

5.  On the **Kit components** FastTab, in the **Components** grid, click **Add** to add the base products to the kit.

6.  In the **Add products** form, select the products and product variants that you want to add to the product kit, and then click **OK**.

7.  In the **Components** grid, you can adjust the quantity and unit of measure for each kit component that you added.

8.  On the **Kit components** FastTab, in the **Substitution** grid, click **Add** to add product substitutes for selected base products in the kit.

9.  In the **Add products** form, select the products and product variants that you want to add as product substitutes, and then click **OK**.

10. Repeat steps 8 and 9 for each product substitute that you want to add.

11. After you have added all the product components and component substitutes to the kit, click **Approve** to approve the product kit.


    > [!NOTE]
    > <P>Product kits must have a status of <STRONG>Approved</STRONG> before you can release the kit to your legal entities, price the kit, or generate assembly orders.</P>



## 3\. Release the product kit to legal entities

Release the product kit to the legal entities in which the product kits will be sold. You must release the product kit in order to define the pricing for the kit configurations, set up the product properties for the kit, and generate assembly orders for the product kit.

1.  Click **Retail and Commerce \> Products and categories \> Product kits**.

2.  On the **Product masters** list page, select the new product kit that you configured in the previous task, and then, on the **Action Pane**, click **Release products**.

3.  In the **Release products** form, on the **Select products to release** tab, select the kit configurations that you want to release. By default, all configurations for the selected product kit are selected.

4.  On the **Select companies to release to** tab, select the legal entities to which the kit should be released, and then click **Next**.

5.  In the **Confirm selection** tab, click **Finish** to run the process and release the products to the selected legal entities.

6.  To verify that the product kit has been released to the selected legal entities, follow these steps:

    1.  Click **Retail and Commerce \> Products and categories \> Released product kits**.

    2.  On the **Released product kits** list page, view your product kit.

## 4\. Set the standard properties for the product kit

After you release the product kits to the legal entities, you can set the standard properties that apply to the products in the kit. These properties can include inventory dimensions, product categories, and product attributes. For general information about how to set up product properties, see [Key tasks: Define products](/dynamicsax-2012/appuser-itpro/key-tasks-define-products). For information about how to set up retail products, see [Set up retail products](set-up-retail-products.md).

1.  Click **Retail and Commerce \> Products and categories \> Released product kits**. On the **Released product kits** list page, double-click the product kit that you released in the previous task.

2.  In the **Released product details** form, click **Edit**. Then, on the **Action Pane**, on the **Product** tab, on the **Set up**, click **Dimension groups**, and select the inventory dimension groups for the product kit.

3.  On the **General** FastTab, in the **Administration** group, select the item model group for the kit, so that the kit can be assembled.

4.  On the **Purchase** FastTab, in the **Unit** field, select the unit of measure to use for the purchase of the product kit.

5.  On the **Sell** FastTab, in the **Unit** field, select the unit of measure to use for the sale of the product kit.

6.  On the **Manage inventory** FastTab, in the **Inventory** group, in the **Unit** field, select the unit of measure in which the product kit is stored in inventory.

7.  On the **Retail** FastTab, enter any additional information that is required for the product kit. This information includes configuration data for any product variants that are included in the kit.

## 5\. Define kit pricing and generate trade agreements

You can price product kits as a whole product or as a sum of the individual components. The base price for each kit component is the price of the product at the time that it was added to the product kit.

If you define a price for the overall kit, the new price is distributed across all the products in the kit. The price adjustment to each product is based on the percentage that each product’s base price contributes to the total base price for the product kit. You can also specify whether there is an additional charge for product substitutes when the customer selects the product substitute instead of the base component. The additional cost is included when the kit price is calculated.

1.  Click **Retail and Commerce \> Products and categories \> Released product kits**. On the **Released product kits** list page, double-click a released product kit in the list.

2.  In the **Released product details** form, click **Edit**. Then, on the **Action Pane**, on the **Product** tab, on the **Product kit**, click **Configure**.

3.  In the **Configure kit** form, on the **Kit components** FastTab, in the **Components** grid, follow one of these steps:

      - In the **Kit price** column, enter the kit price for each component in the product kit.

      - Click **Specify kit price** to enter a price for the overall product kit.

4.  On the **Kit components** FastTab, in the **Substitution** grid, in the **Charge** field, enter the amount to add to the kit price if the substitute product is selected to replace the base product component. Repeat this step for each substitute product in the grid.

    For example, a customer selects a kit that includes a standard bicycle tire set, but the customer wants to upgrade to a premium bicycle tire set. If the cost to upgrade the tire set is 50.00 USD, enter **50.00** in the **Charge** field.

5.  Repeat steps 3 and 4 for each component and component substitute that is included in the product kit.


    > [!NOTE]
    > <P>If you select an overall kit price for the base components in the product kit, you only have to follow step 3 one time.</P>



## Next step

After you set up the kit and define your kit configuration, the next steps are to generate the assembly orders and assemble the orders. For more information, see Create and view kit assembly and disassembly orders and Process kit assembly and disassembly orders.

## Related tasks

[Retail product kit setup overview](retail-product-kit-setup.md)

## Technical information for system administrators

If you don't have access to the pages that are used to complete this task, contact your system administrator and provide the information that is shown in the following table.

| Category | Prerequisite |
|-------|-------------|
| Configuration keys | Retail |
| Security roles | Merchandising manager |

[!INCLUDE[footer-include](../includes/footer-banner.md)]
