---
title: About setting up retail product kits
description: This article describes the overview steps of setting up retail product kits.
author: tonyafehr
ms.date: 10/23/2023
ms.topic: article
audience: Application User
ms.reviewer: josaw
ms.search.region: Global
ms.author: wenxyang
ms.search.validFrom: 2023-10-23
---

# About setting up retail product kits

[!include [banner](includes/banner.md)]

This topic describes the process flow for setting up retail product kits. You use product kits to group and package individual products into one sellable unit. By selling products as a kit, you can reduce costs that are associated with order fulfillment and shipping. A product kit can include multiple products, variants for those products, and product substitutes. Customers can select a product substitute to replace a standard kit product. If the product substitute costs more than the standard kit product, the kit price is adjusted to include the additional cost. The products that are included in a kit are referred to as components. The set of products that make up a product kit are referred to as kit configurations. One product kit can include many components and kit configurations.

The following diagram illustrates the steps that you must complete to create and process retail product kits so that they can be sold in your retail channels. The numbers in the diagram correspond to the sections later in the topic.

![Process flow to set up and maintain product kits](./media/Dn497848.RetailProductKitsProcessFlow(AX.60).gif "Process flow to set up and maintain product kits")

## 1\. Create a product kit

A product kit includes a group of separate products, product variants, and product substitutes. To create a product kit, you create a new product and designate it as a product kit. After you create the product kit, you can add products and product variants to the kit as your kit components, and also add product substitutes for any of the kit components. For more information about how to set up a product kit, see [Create retail product kits](./create-retail-product-kits.md).

## 2\. Add products and product substitutes to the product kit

After you set up the base information for the product kit, the next step is to add the kit components and component substitutes to the kit. The combination of kit components and component substitutes make up the different product configurations for the kit. The product configurations represent every product combination that a product kit might offer. For example, if you set up a product kit that contains three products, and two product substitutes for one of the three products, you can offer three different product kit combinations.

After you set up the kit components and component substitutes, you can also set the kit options, such as allowing disassembly at the point-of-sale (POS) register. Product kits can be disassembled at either the warehouse or at the store. Product kits that can be disassembled at the store enable a store employee to sell one or more components from a product kit separately, instead of selling the entire kit. This option only applies to product kits that are sold in a brick-and-mortar store using the POS register. Product kits that are disassembled at the warehouse are simply broken down, and the individual products are returned to on-hand inventory.

After you have added all of the components and component substitutes to the kit and set the kit options, you must set the kit to an approved status.

## 3\. Release the product kit configurations to your legal entities

Before you can generate assembly orders for the product kit, you must release the product kit configurations to the legal entities in which the kits can be sold. You release kit products by using the same steps that you use to release any product.

## 4\. Set the standard properties for the released product kits

After you release the product kit to your legal entities, you must set up any standard properties for the product kit. This includes assigning the kit to a product category or setting up distribution codes.

## 5\. Define kit pricing and generate trade agreements

After you release the product kit to your legal entities, and you have set up the basic product properties for the kit, the next step is to price the kit. Each component of the product kit is assigned a base price, and the sum of the base prices is equal to the base price of the product kit. The base price for each kit component is the price of the product at the time that it was added to the product kit. If you want to specify a different price for the kit, you can enter a new total kit price for the kit and the new price will be distributed across all of the products in the kit. The price adjustment to each product is based on the percentage that each product’s base price contributes to the total base price for the product kit.

When you add substitute products to a product kit for selected components, you can also specify if there is an additional charge when the customer selects the product substitute instead of the base component. The additional cost is included when the kit price is calculated.

## 6\. Generate assembly orders

After all of the components have been defined and priced, and the kit configurations have been released to your legal entities, the next step is to generate the assembly orders. When you generate assembly orders, you indicate the number of kits to be assembled and the warehouse for which the assembly order is being created.

For more information about how to generate assembly orders for product kits, see [Generate assembly and disassembly orders](./generate-assembly-and-disassembly-orders.md).

## 7\. Assemble kit products

After the assembly orders are generated, the warehouse worker can pick and pack the kit components and package the kit. The warehouse worker updates the assembled quantity for each kit configuration and then, when they have completed assembling all the kits in the order, they can post the BOM journals. When the BOM journals are posted, on-hand inventory for the product kits is increased, and on-hand inventory for the individual components is decreased.

For more information about how to view and maintain assembly orders for product kits, see [Process kit assembly and disassembly orders](./process-kit-assembly-and-disassembly-orders.md).

## See also

[Create retail product kits](./create-retail-product-kits.md)

[Generate assembly and disassembly orders](./generate-assembly-and-disassembly-orders.md)

[Process kit assembly and disassembly orders](./process-kit-assembly-and-disassembly-orders.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
