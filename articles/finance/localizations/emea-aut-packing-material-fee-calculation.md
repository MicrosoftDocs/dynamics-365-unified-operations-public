---
# required metadata

title: Packing material fee calculation for Austria
description: This topic provides information about packing material rates and fees in Austria.
author: EvgenyPopovMBS
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: InventPackagingMaterialTransPurch
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 268034
ms.search.region: Austria
# ms.search.industry: 
ms.author: epopov
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Packing material fee calculation for Austria

[!include [banner](../includes/banner.md)]

This topic provides information about packing material rates and fees in Austria.

In Europe, there are regulations about packaging waste. These regulations work on the principle of "collective producer responsibility." In other words, they enforce the requirement that producers or sellers of packaging take responsibility for the environmental impact of that packaging. According to the regulations, producers are obligated to pay a portion of the cost of recovering and recycling their packaging. This payment is known as a packing material fee<em>,</em> and it's paid periodically to a recycling company. A company should calculate the weight of each type of packing material (paper, plastic, metal, and so on) that was used during a sale or purchase, and multiply that weight by the package material rate. The government provides the package material rate for each type of packing material. In Austria, a more complex formula for is used for packing material fees. Packing materials are divided into various categories (for example, Household and Commercial), and the government provides tax rates for packing materials in each category. The category that packing material belongs to depends on size and the products that the packaging was used for. Packing material fees are calculated and reported, but no ledger transactions are posted automatically, because the fees aren't considered taxes that must be paid to an authority.

## Prerequisites
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Prerequisite</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Category hierarchies</td>
<td>You must create category hierarchies for products. For each category hierarchy, you must create nodes that will be used as product groups for the calculation of packing material fees. You must create a category hierarchy type for packing materials and set the category hierarchy to <strong>Packing</strong>. <strong></strong> <strong>Note:</strong> You can set up a packing category hierarchy for only one category hierarchy type. After you create category hierarchies, follow these steps to associate each product with a category hierarchy.
<ol>
<li>On the <strong>Products</strong> page, select a product in the list.</li>
<li>On the <strong>Product</strong> tab, click <strong>Product categories</strong>.</li>
</ol></td>
</tr>
<tr class="even">
<td>Packing classes</td>
<td>Create or maintain packaging classes for the calculation of packing material fees.</td>
</tr>
<tr class="odd">
<td>Tariff categories</td>
<td>Create or maintain tariff categories for the calculation of packing material fees.</td>
</tr>
<tr class="even">
<td>Packing materials code</td>
<td>Create packing material codes for each type of packing material that is defined.</td>
</tr>
<tr class="odd">
<td>Packing materials fee</td>
<td>Specify packing material fees for each packing material code. For each type of material, define the period of validity, tariff category, price per material, currency, and unit.</td>
</tr>
<tr class="even">
<td>Packaging material allocation</td>
<td>Define which materials are included in a packing unit, so that you can assign weights and view the total number of items that are contained in the packing unit. You can define packing units for individual items, for packaging groups, or for all items. <strong>Note:</strong> When you select the packing unit, you can load the packing unit and have the packing unit quantity calculated automatically on sales order lines. However, the calculation can be done automatically only if the packing unit is the same unit that is specified on the sales order lines.</td>
</tr>
<tr class="odd">
<td>Allocation by tariff categories</td>
<td>Set up rules to define how packing material transactions should be allocated to tariff categories. For each combination of a product group, a packing class, and a packing code, you can set up one or more tariff categories that include quotations (as a percentage). The sum of quotations for each combination should equal 100 percent.</td>
</tr>
</tbody>
</table>

## Manually create packing material transactions
Follow these steps to create packing material transactions for an invoiced sales order or purchase order:

1.  On the **Packing material transactions** page, click **New**, and enter the following information on the **Create packing material transaction** page:
    -   Select an invoice line in the list.
    -   Select a packing material code from the **Packing material code** drop-down list.
    -   Select a packing class from the **Packing class** drop-down list.

2.  Click **OK**.
3.  Select the **Calculate fee** check box to calculate the packing material fee component of the sales order line for reporting.
4.  Optional: Update the **Packing unit**, **Packing unit quantity**, and **Packing unit weight** fields.
5.  Click **Save**.

## Create packing material transactions from sales orders and purchase orders
Packing material weights and fees are calculated for sales order lines and purchase order lines. In the line details for each line, you can specify the packing unit and the packing unit quantity. When a sales order line is invoiced, packing material transactions are created, and the packing material weights are calculated. Packing material fees aren't calculated when the invoice is posted, and they aren't invoiced. **Note:** If a packing unit has been assigned to the item on the selected sales order line, the packing unit and packing unit quantity are loaded automatically. In this case, the quantity is calculated as the ordered quantity (in inventory units) divided by the packing unit factor. When the sales order line is posted, the packing unit and packing unit quantity are taken from the sales order line. However, you can change the values on the **Posting invoice** page on the **Line details** tab. It's relevant when the sales order is partially invoiced.

## Calculate packing material fees
Use the Packing material calculation journal to calculate packing material fees and print the **Packing materials fees** report.

1.  Click **New**, and enter the following information:
    -   **Date from** – Specify the start date of the journal.
    -   **Date to** – Specify the end date of the journal.
    -   **Save details** – Select this check box if you want to review calculation details.

2.  Click **Lines**. The **Journal lines** page appears and shows the aggregated data (grouped by tariff category and packing materials code).
3.  Click **Calculation details** to open the **Calculation details** page, where all data about all transactions for the journal period is allocated to the various tariff categories.

## Print the Packing materials fee calculation report
The **Packing materials fee calculation** report contains information about packing materials fees that were calculated by using Austrian rules. To print this report, on the **Packing material calculation journal** page, select the calculated journal, and then click **Print report**.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]