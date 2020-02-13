---
# required metadata

title: Packing materials and fees
description: Packing material fees are paid to a recycling company at certain intervals. An amount is paid, per unit of weight, for each material that a packing unit consists of. Packing material fees are calculated and reported, but no ledger transactions are posted because the fees are not regarded as taxes to be paid to an authority.
author: MarkusFogelberg
manager: AnnBe
ms.date: 11/02/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: InventPackagingGroup, InventPackagingMaterialCode, InventPackagingMaterialFee, InventPackagingMaterialTrans, InventPackagingMaterialTransPurch, InventPackagingUnit
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 2194
ms.assetid: 040b65dc-43c9-4256-b69f-b2d6e736fbe9
ms.search.region: Global
ms.search.industry: Distribution
ms.author: mafoge
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Packing materials and fees

[!include [banner](../includes/banner.md)]

Packing material fees are paid to a recycling company at certain intervals. An amount is paid, per unit of weight, for each material that a packing unit consists of. Packing material fees are calculated and reported, but no ledger transactions are posted because the fees are not regarded as taxes to be paid to an authority.

Packing material weights and fees are calculated for sales order lines and for purchase order lines.

You can define one or more packing units for an item, for a packing group of items, or for all items. A packing unit consists of the packing materials, their weights, and the number of items that are included in the packing unit. A packing material code is assigned to each type of packing material that is defined. Based on the packing material code, you can specify a price for a specified period. The packing material fee is calculated based on this information.

| **Note**                                                                                                                                             |
|------------------------------------------------------------------------------------------------------------------------------------------------------|
| Even if your company does not pay packing material fees, you can use the functionality to calculate statistics for the weights of packing materials. |

## Setup requirements for packing material fees
Before you calculate packing material weights or packing material fees, or both, you must navigate to **Inventory Management Parameters > General > Packing Materials** and then switch the **Calculate packing material fees** toggle to ‘Yes’.  

Then you must navigate to **Inventory Management > Setup Packing Materials** and create the following base data: 

-   Packing groups – Create packing groups to assign to items.
-   Packing material codes – Create packing material codes for each type of packing material that is defined.
-   Packing units – Specify a packing unit for an item, for a packing group, or for all items. For each packing unit, define which packing materials to include, assign weights, and, in the Packing unit factor field, enter the conversion factor from the inventory unit.
-   Packing material fees – Specify packing material fees per packing material code. For each type of material, define the period of validity, the price per material, the currency, and the unit.

First navigate to **Inventory Management > Setup > Packing Materials > Packing Material Codes.**

Define all the necessary packing materials here. Once you have defined the materials navigate to **Packing Material Fees** to set a fee for your material. 

Once this is done in order to allocate your packing materials go to **Packing material allocation** and create a new allocation and assign it to your Item. You can also assign it to a packing group or all of your items. 

## Packing units on sales order lines
When you create a sales order to ensure that the system checks to see whether packing units are specified for the item you must navigate to **Inventory Management Parameters > General > Packing Materials** and then switch the **Calculate packing material fees** toggle to 'Yes'. 

If packing units are specified, the system updates the sales order line with the specified packing unit and the packing unit quantity. The packing unit quantity is based on the ordered quantity divided by the number of items in the selected packing unit. If a packing unit has not been specified, you can manually enter a packing unit and a packing unit quantity on the sales order line. You can also change the packing unit and the packing unit quantity when you post the sales order line. This is relevant if the sales order line is only partly delivered or partly invoiced. When you invoice the sales order, packing material transactions are created. Packing material transactions contain the weights of the packing materials for the sales line. You can also modify the transactions after you invoice them, and then create new transactions. 

## Packing units on purchase order lines
Packing material transactions for a purchase order line are not created by the system. You create transactions for invoiced purchase order lines manually in the **Packing material transactions** page.

## Set up customer packaging-material-fee license numbers
When you are creating a sales order if you would like to charge your customer for the packing materials go to **Accounts Receivable > Customers > All Customers**

Pick the customer that you would like to charge the packing materials for. Navigate to the **Invoice and Delivery** tab and add the companies license number to the 'Packing duty license number' field under **Sales Tax** as well as the 'License number' field under **Packing Material Fee**

Now when you create and invoice a sales order with the item that you have defined the packing material you will be able to see the packing material fees in the invoice.

If you don't want to charge these remove the license numbers for the customers.
In the scenario that the company pays the fees you will notice that only the weights of the packing materials are displayed on the invoice and not the fees. You will only be able to see the fees in the report navigate to: **Inventory Management > Inquires and Reports > Packing Materials > Calculate Fees**

Here you can specify a range of dates and generate a report with all the packing material fees you owe.

## Print packaging material weights on invoices
You can print the packaging material weights on the invoice and indicate who pays the packaging material fees. The weights are summarized by packaging code. In order to do this navigate to **Accounts Receivable Parameters > Updates > Invoice** and switch the **Print packing material weight toggle** to ‘Yes’. 




