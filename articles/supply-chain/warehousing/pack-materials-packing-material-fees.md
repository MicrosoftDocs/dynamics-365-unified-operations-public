---
# required metadata

title: Packing materials and fees
description: This topic provides information about packing material fees that are paid to recycling companies at specific intervals.
author: Mirzaab
ms.date: 02/19/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: InventPackagingGroup, InventPackagingMaterialCode, InventPackagingMaterialFee, InventPackagingMaterialTrans, InventPackagingMaterialTransPurch, InventPackagingUnit
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 2194
ms.assetid: 040b65dc-43c9-4256-b69f-b2d6e736fbe9
ms.search.region: Global
ms.search.industry: Distribution
ms.author: mirzaab
ms.search.validFrom: 2020-02-19
ms.dyn365.ops.version: AX 7.0.0

---

# Packing materials and fees

[!include [banner](../includes/banner.md)]

Packing material fees are paid to a recycling company at specific intervals. An amount is paid, per unit of weight, for each material that a packing unit consists of. Although packing material fees are calculated and reported, no ledger transactions are posted, because the fees aren't considered taxes that must be paid to an authority.

Packing material weights and fees are calculated for sales order lines and purchase order lines.

You can define one or more packing units for a single item, a group of items (packing group), or all items. A packing unit consists of the packing materials, their weights, and the number of items that are included in the packing unit. A packing material code is assigned to each type of packing material that is defined. Based on the packing material code, you can specify a price for a specific period. The packing material fee is calculated based on this information.

> [!NOTE]
> Even if your company doesn't pay packing material fees, you can use the functionality to calculate statistics for the weights of packing materials.

## <a name="allocations"></a>Set up packing material allocation

Before you can calculate packing material weights, packing material fees, or both, you must turn on the calculation and define which materials and fees apply to which items.

1. Go to **Inventory management \> Setup \> Inventory and warehouse management parameters**.
1. On the **General** tab, in the **Packing material** section, set the **Calculate packing material fees** option to **Yes**.
1. Go to **Inventory management \> Setup \> Packing material \> Packing groups**, and create all the packing groups that you use. All the items in a packing group will use the same packing material allocation. If you don't use packing groups, you can skip this step.

    > [!TIP]
    > After you've created your packing groups, can assign a group to each product as you require. Go to **Product information management \> Products \> Released products**, select a product, and then, on the **Manage inventory** FastTab, in the **Packing group** field, select the appropriate packing group.

1. Go to **Inventory management \> Setup \> Packing material \> Packing material codes**, define each type of packing material that you use, and specify the unit that the packing material is consumed in when you prepare shipments.
1. Go to **Inventory management \> Setup \> Packing material \> Packing material fees**, and set a fee for each type of packing material that you just defined. Fees are calculated based on the price per unit that is consumed.
1. To allocate packing materials to items, go to **Inventory management \> Setup \> Packing material \> Packaging material allocation**, and create allocations. You can create as many allocations as you require. You can allocate packing materials for individual items, groups of items (packing groups), or all items, depending on how detailed your allocations should be.

    For each allocation that you create, follow these steps.

    1. On the **General** FastTab, set the following fields:

        - **Item code** – Select the scope of the allocation:

            - **Table** – Create an allocation for a single specific item.
            - **Group** – Create an allocation for all the items the belong to a packing group that is defined on the **Packing groups** page.
            - **All** – Create an allocation for all items.

            > [!NOTE]
            > Usually, you should make all your allocations at the same level (**Table**, **Group**, or **All**). If you use more than one level, the most specific matching allocation will be used for each item. (The **Table** level takes precedence over the **Group** level, and both those levels take precedence over the **All** level.)

        - **Item relation** – If you're allocating for a single item, select the item. If you're allocating for a group of items, select the packing group. If you're allocating for all items, leave this field blank.
        - **Configuration**, **Size**, **Color**, and **Style** – Enter values for these dimensions as you require, to further define the item that you're allocating for.
        - **Packing unit** – Select the unit that the item is packaged in when the packing material is used. This unit might differ from the unit that the item is purchased and stored in.
        - **Packing unit factor** – Enter the conversion factor that is used to convert from the inventory unit to the packing unit. (The conversion uses the formula *Packing units* = *Item units* × *Packing unit factor*.)

    1. On the **Packing material** FastTab, add a line for each piece of packing material that is required for the current allocation. On each line, specify the type of material (as defined on the **Packing material codes** page) and the amount of it that is consumed for each shipped unit of the current item.

## Packing units on sales order lines

After you've [turned on the calculation for packing material fees and set up your allocations](#allocations), the system verifies that packing units are specified for each item that is added to a sales order. It then calculates any fees that are required. When an item is added to a sales order, one of the following steps occurs:

- **If a packing allocation applies to the item:** The system updates the sales order line with the specified packing unit and the packing unit quantity. (The packing unit quantity is calculated by using the formula *Packing unit quantity* = *Ordered quantity* ÷ *Number of items in the selected packing unit*.)
- **If no packing allocation applies to the item:** You can manually enter a packing unit and a packing unit quantity on the sales order line.

You can also change the packing unit and the packing unit quantity when you post the sales order line. This capability is relevant if the sales order line is only partly delivered or partly invoiced.

When you invoice the sales order, the system creates packing material transactions. Packing material transactions contain the weights of the packing materials for the sales line. You can modify the transactions after you invoice them. You can then create new transactions.

## Packing units on purchase order lines

The system doesn't create packing material transactions for purchase order lines. Instead, you manually create transactions for invoiced purchase order lines on the **Packing material transactions** page.

## Set up license numbers for customers that are charged packing material fees

If the sales orders for a specific customer should include charges for the packing materials that are used for each order, follow these steps.

1. Go to **Accounts receivable \> Customers \> All customers**.
1. Select the customer that should be charged for packing materials.
1. On the **Invoice and delivery** FastTab, set the following fields:

    - In the **Sales tax** section, in the **Packing duty license number** field, enter the company's license number.
    - In the **Packing material fee** section, in the **License number** field, enter the company's license number.

Now, when you create and invoice a sales order that includes one or more items that use packing materials, the invoice will show the packing material fees.

For customers that should not pay packing material fees, follow these same steps, but clear the license numbers from the **Packing duty license number** and **License number** fields. Invoices for customers that don't pay packing material fees show the weights of the packing materials, but they don't show the fees.

To generate a report that shows all the packing material fees that your company will owe for a specific period, go to **Inventory management \> Inquiries and reports \> Packing material reports \> Packing material fee calculation**, specify a range of dates, and then select **OK**.

## Print packing material weights on invoices

You can print packing material weights on an invoice and indicate who pays the related fees. The weights are summarized by packaging code.

1. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. On the **Updates** tab, on the **Invoice** FastTab, set the **Print packing material weight** option to **Yes**.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]