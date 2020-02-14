---
# required metadata

title: Packing materials and fees
description: Packing material fees are paid to a recycling company at certain intervals. An amount is paid, per unit of weight, for each material that a packing unit consists of. Packing material fees are calculated and reported, but no ledger transactions are posted because the fees are not regarded as taxes to be paid to an authority.
author: MarkusFogelberg
manager: AnnBe
ms.date: 02/14/2020
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
ms.search.validFrom: 2020-02-14
ms.dyn365.ops.version: AX 7.0.0

---

# Packing materials and fees

[!include [banner](../includes/banner.md)]

Packing material fees are paid to a recycling company at certain intervals. An amount is paid, per unit of weight, for each material that a packing unit consists of. Packing material fees are calculated and reported, but no ledger transactions are posted because the fees are not regarded as taxes to be paid to an authority.

Packing material weights and fees are calculated for sales order lines and for purchase order lines.

You can define one or more packing units for an item, for a packing group of items, or for all items. A packing unit consists of the packing materials, their weights, and the number of items that are included in the packing unit. A packing material code is assigned to each type of packing material that is defined. Based on the packing material code, you can specify a price for a specified period. The packing material fee is calculated based on this information.

> [!NOTE]
> Even if your company does not pay packing material fees, you can use the functionality to calculate statistics for the weights of packing materials. |

## Set up packing material fees

Before you can calculate packing material weights, packing material fees, or both, you must do the following:

1. Go to **Inventory Management > Setup > Inventory and warehouse management parameters**.

1. On the **General** tab of the **Inventory and warehouse management parameters** page, under **Packing Material**, set **Calculate packing material fees** to "Yes".  

1. Use the various pages listed under **Inventory Management > Setup > Packing Material** in the navigator to create the following base data:

    - **Packing groups** – Create packing groups to assign to items.
    - **Packing material codes** – Create packing material codes for each type of packing material that is defined.
    - **Packing units** – Specify a packing unit for an item, for a packing group, or for all items. For each packing unit, define which packing materials to include, and assign weights. In the **Packing unit factor** field, enter the conversion factor from the inventory unit. <!-- KFM: I don't see "Packing units" here. Do we mean "Packing material allocation"? We mention that later in this procedure, so maybe we should remove this bullet? -->
    - **Packing material fees** – Specify packing material fees per packing material code. For each type of material, define the period of validity, the price per material, the currency, and the unit.

1. Go to **Inventory Management > Setup > Packing Materials > Packing Material Codes** and define all the necessary packing materials here

1. Go to **Packing Material Fees** and set a fee for your material.

1. To allocate your packing materials, go to **Inventory Management > Setup > Packing Material > Packing material allocation**. Create a new allocation and assign it to your item. You can also assign it to a packing group or to all of your items.

## Packing units on sales order lines

To ensure that the system checks whether packing units are specified for each item added to a sales order, do the following:

1. Go to **Inventory Management > Setup > Inventory and warehouse management parameters**.

1. On the **General** tab of the **Inventory and warehouse management parameters** page, under **Packing Material**, set **Calculate packing material fees** to "Yes".  

If packing units are specified, the system updates each sales order line with the specified packing unit and the packing unit quantity. The packing unit quantity is based on the ordered quantity divided by the number of items in the selected packing unit.

If no packing unit is specified, you can manually enter a packing unit and a packing unit quantity on the sales order line.

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
    - Under the **Packing Material Fee** heading, enter the company's license number in the **License number** field. <!-- KFM: Are we entering the same license number in both fields? Or can we provide a more specific name for each of these licenses? -->

Now when you create and invoice a sales order that includes one or more items with packing materials, you will be able to see the packing material fees on the invoice.

For customers that shouldn't pay packing material fees, delete the license numbers mentioned in the previous procedure.

Invoices for customers that don't pay packing material fees show the weights of the materials, but not the fees. To see the fees your company will owe, go to **Inventory Management > Inquires and Reports > Packing material reports > Packing material fee calculation**. Here you can specify a range of dates and generate a report with all the packing material fees you owe for that period. <!-- KFM: It was hard to figure out who was paying for what and when in this paragraph. I think I got it right, but please confirm. -->

## Print packaging material weights on invoices

You can print packaging material weights on an invoice and indicate who pays the related fees. The weights are summarized by packaging code. To do this:

1. Go to **Account receivable > Setup > Accounts receivable parameters**.

1. On the **Updates** tab of the **Accounts receivable parameters** page, under **Invoice**, set **Print packing material weight** to "Yes".  
