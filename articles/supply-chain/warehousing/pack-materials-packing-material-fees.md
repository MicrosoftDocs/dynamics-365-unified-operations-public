---
# required metadata

title: Packing materials and fees
description: Packing material fees are paid to a recycling company at certain intervals. An amount is paid, per unit of weight, for each material that a packing unit consists of. Packing material fees are calculated and reported, but no ledger transactions are posted because the fees are not regarded as taxes to be paid to an authority.
author: MarkusFogelberg
manager: AnnBe
ms.date: 02/19/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: InventPackagingGroup, InventPackagingMaterialCode, InventPackagingMaterialFee, InventPackagingMaterialTrans, InventPackagingMaterialTransPurch, InventPackagingUnit
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 2194
ms.assetid: 040b65dc-43c9-4256-b69f-b2d6e736fbe9
ms.search.region: Global
ms.search.industry: Distribution
ms.author: mafoge
ms.search.validFrom: 2020-02-19
ms.dyn365.ops.version: AX 7.0.0

---

# Packing materials and fees

[!include [banner](../includes/banner.md)]

Packing material fees are paid to a recycling company at certain intervals. An amount is paid, per unit of weight, for each material that a packing unit consists of. Packing material fees are calculated and reported, but no ledger transactions are posted because the fees are not regarded as taxes to be paid to an authority.

Packing material weights and fees are calculated for sales order lines and for purchase order lines.

You can define one or more packing units for an item, for a packing group of items, or for all items. A packing unit consists of the packing materials, their weights, and the number of items that are included in the packing unit. A packing material code is assigned to each type of packing material that is defined. Based on the packing material code, you can specify a price for a specified period. The packing material fee is calculated based on this information.

> [!NOTE]
> Even if your company does not pay packing material fees, you can use the functionality to calculate statistics for the weights of packing materials.

<a name="allocations"></a>

## Set up packing material allocation

Before you can calculate packing material weights, packing material fees, or both, you must enable the calculation and establish which materials and fees apply to which items. Do the following:

1. Go to **Inventory management > Setup > Inventory and warehouse management parameters**.
1. On the **General** tab of the **Inventory and warehouse management parameters** page, under **Packing material**, set **Calculate packing material fees** to "Yes". 
1. Go to **Inventory Management > Setup > Packing Materials > Packing groups** and create each of the packing groups that you use. All items in a packing group will use the same packing materials allocation. If you don't use packing groups, you can skip this step.
    > [!TIP]
    > Once you've created your packing groups, can assign a group to each product as needed. To do so, go to **Product information management > Products > Released products**, select a product, expand the **Manage inventory** FastTab, and select the appropriate group in the **Packing group** field.

1. Go to **Inventory management > Setup > Packing materials > Packing material Codes** and define each type of packing material that you use and the unit by which you consume it when preparing a shipment.
1. Go to **Inventory management > Setup > Packing materials > Packing material fees** and set a fee for each type of material that you defined on the **Packing Material Codes** page. Fees are calculated based on the price per unit consumed.
1. To allocate packing materials to items, go to **Inventory management > Setup > Packing material > Packing material allocation**. You can allocate packing materials for all items, groups of items (packing groups), or individual items, depending on how granular you need your allocations to be. You can create as many allocations as needed. For each allocation, make the following settings:
    - **Item code** - Establishes the scope of your allocation. Choose one of the following values:
        - **Table** - Creates an allocation for a single specific item.
        - **Group** - Creates an allocation for all items from a packing group defined on the Packing groups page.
        - **All** - Creates an allocation for all items.
        > [!NOTE]
        > Usually you should make all of your allocations at the same item-code  level (*Table*, *Group*, or *All*). If you use more than one level, then the most specific matching allocation will be used for each item (*Table* beats *Group*, and both of those beat *All*.)
    - **Item relation**: If you are allocating for a single item, then select the item here. If you are allocating for a group, then select the packing group here. If you are allocating for all items, then skip this setting.
    - **Configuration**, **Size**, **Color**, and **Style**: Enter values for these dimensions as needed to further define the item you are allocating.
    - **Packing unit**: Select the unit by which you package your items using your packing material. This may be different from the unit used to purchase and store the item.
    - **Packing unit factor**: Enter the conversion factor for converting from the inventory unit to the packing unit.<br>(*Packing units = Item units * Packing unit factor*)
    - **Packing material**: Add a line here for each piece of packing material needed for the current allocation. Each line specifies a material type (as defined on the  **Packing material codes** page) and the amount of that material that is consumed for each shipped unit of the current item.

## Packing units on sales order lines

Once you've [enabled the packing-materials fee calculation and set up your allocations](#allocations), the system will check whether packing units are specified for each item added to a sales order and then make the fee calculation as needed. On adding an item to a sales order:

- If a packing allocation applies for that item, the system updates the sales order line with the specified packing unit and the packing unit quantity. The packing unit quantity is based on the ordered quantity divided by the number of items in the selected packing unit.

- If no packing allocation applies for that item, you can manually enter a packing unit and a packing unit quantity on the sales order line.

You can also change the packing unit and the packing unit quantity when you post the sales order line. This is relevant if the sales order line is only partly delivered or partly invoiced.

When you invoice the sales order, the system creates packing material transactions. Packing material transactions contain the weights of the packing materials for the sales line. You can also modify transactions after you invoice them, and then create new transactions.

## Packing units on purchase order lines

Packing material transactions for a purchase order line are not created by the system. You create transactions for invoiced purchase order lines manually on the **Packing material transactions** page.

## Set up customer packaging-material-fee license numbers

If sales orders for a given customer should include charges for packing material included with the order, do the following:

1. Go to **Accounts Receivable > Customers > All Customers**

1. Select the customer who should be charged for packing materials.

1. Expand the **Invoice and Delivery** FastTab and make the following settings here:

    - Under the **Sales tax** heading, enter the company's license number in the **Packing duty license number** field.
    - Under the **Packing Material Fee** heading, enter the company's license number in the **License number** field.

Now, when you create and invoice a sales order that includes one or more items with packing materials, you will be able to see the packing material fees on the invoice.

For customers that shouldn't pay packing material fees, delete the license numbers mentioned in the previous procedure. Invoices for customers that don't pay packing material fees show the weights of the materials, but not the fees. To see the fees your company will owe, go to **Inventory Management > Inquires and Reports > Packing material reports > Packing material fee calculation**. Here you can specify a range of dates and generate a report with all the packing material fees you owe for that period.

## Print packaging material weights on invoices

You can print packaging material weights on an invoice and indicate who pays the related fees. The weights are summarized by packaging code. To do this:

1. Go to **Account receivable > Setup > Accounts receivable parameters**.

1. On the **Updates** tab of the **Accounts receivable parameters** page, under **Invoice**, set **Print packing material weight** to "Yes".  
