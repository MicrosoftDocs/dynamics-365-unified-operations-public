---
title: Packing material fee calculation for Austria
description: Learn about packing material rates and fees in Austria, including a table that defines various prerequisites and an outline on manually creating transactions.
author: EvgenyPopovMBS
ms.author: evgenypopov
ms.topic: how-to
ms.date: 03/02/2026
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Austria
ms.search.validFrom: 2016-11-30
ms.search.form: InventPackagingMaterialTransPurch
ms.dyn365.ops.version: Version 1611
---

# Packing material fee calculation for Austria

[!include [banner](../../includes/banner.md)]

This article provides information about packing material rates and fees in Austria.

In Europe, regulations govern packaging waste. These regulations work on the principle of "collective producer responsibility." In other words, they enforce the requirement that producers or sellers of packaging take responsibility for the environmental impact of that packaging. According to the regulations, producers must pay a portion of the cost of recovering and recycling their packaging. This payment is known as a packing material fee, and producers pay it periodically to a recycling company. A company should calculate the weight of each type of packing material (paper, plastic, metal, and so on) that it used during a sale or purchase, and multiply that weight by the package material rate. The government provides the package material rate for each type of packing material. In Austria, a more complex formula is used for packing material fees. Packing materials are divided into various categories (for example, Household and Commercial), and the government provides tax rates for packing materials in each category. The category that packing material belongs to depends on size and the products that the packaging was used for. You calculate and report packing material fees, but no ledger transactions are posted automatically, because the fees aren't considered taxes that must be paid to an authority.

## Prerequisites

| Prerequisite | Description |
|---|---|
| Category hierarchies | You must create category hierarchies for products. For each category hierarchy, you must create nodes that you use as product groups for the calculation of packing material fees. You must create a category hierarchy type for packing materials and set the category hierarchy to **Packing**. **Note:** You can set up a packing category hierarchy for only one category hierarchy type. After you create category hierarchies, follow these steps to associate each product with a category hierarchy. 1. On the **Products** page, select a product in the list. 1. On the **Product** tab, select **Product categories**. |
| Packing classes | Create or maintain packaging classes for the calculation of packing material fees. |
| Tariff categories | Create or maintain tariff categories for the calculation of packing material fees. |
| Packing materials code | Create packing material codes for each type of packing material that is defined. |
| Packing materials fee | Specify packing material fees for each packing material code. For each type of material, define the period of validity, tariff category, price per material, currency, and unit. |
| Packaging material allocation | Define which materials are included in a packing unit, so that you can assign weights and view the total number of items that are contained in the packing unit. You can define packing units for individual items, for packaging groups, or for all items. **Note:** When you select the packing unit, you can load the packing unit and have the packing unit quantity calculated automatically on sales order lines. However, the calculation can be done automatically only if the packing unit is the same unit that is specified on the sales order lines. |
| Allocation by tariff categories | Set up rules to define how packing material transactions should be allocated to tariff categories. For each combination of a product group, a packing class, and a packing code, you can set up one or more tariff categories that include quotations (as a percentage). The sum of quotations for each combination should equal 100 percent. |

## Manually create packing material transactions

Follow these steps to create packing material transactions for an invoiced sales order or purchase order:

1. On the **Packing material transactions** page, select **New**, and enter the following information on the **Create packing material transaction** page:
    - Select an invoice line in the list.
    - Select a packing material code from the **Packing material code** drop-down list.
    - Select a packing class from the **Packing class** drop-down list.

1. Select **OK**.
1. Select the **Calculate fee** check box to calculate the packing material fee component of the sales order line for reporting.
1. Optional: Update the **Packing unit**, **Packing unit quantity**, and **Packing unit weight** fields.
1. Select **Save**.

## Create packing material transactions from sales orders and purchase orders

The system calculates packing material weights and fees for sales order lines and purchase order lines. In the line details for each line, you can specify the packing unit and the packing unit quantity. When you invoice a sales order line, the system creates packing material transactions and calculates the packing material weights. The system doesn't calculate packing material fees when you post the invoice, and it doesn't include them on the invoice. **Note:** If you assign a packing unit to the item on the selected sales order line, the system automatically loads the packing unit and packing unit quantity. In this case, the quantity is calculated as the ordered quantity (in inventory units) divided by the packing unit factor. When you post the sales order line, the system takes the packing unit and packing unit quantity from the sales order line. However, you can change the values on the **Posting invoice** page on the **Line details** tab. This change is relevant when the sales order is partially invoiced.

## Calculate packing material fees

Use the Packing material calculation journal to calculate packing material fees and print the **Packing materials fees** report.

1. Select **New**, and enter the following information:
    - **Date from** – Specify the start date of the journal.
    - **Date to** – Specify the end date of the journal.
    - **Save details** – Select this check box if you want to review calculation details.

1. Select **Lines**. The **Journal lines** page appears and shows the aggregated data (grouped by tariff category and packing materials code).
1. Select **Calculation details** to open the **Calculation details** page, where all data about all transactions for the journal period is allocated to the various tariff categories.

## Print the packing materials fee calculation report

The **Packing materials fee calculation** report contains information about packing materials fees that the system calculates by using Austrian rules. To print this report, on the **Packing material calculation journal** page, select the calculated journal, and then select **Print report**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
