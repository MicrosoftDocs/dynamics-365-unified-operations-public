---
# required metadata

title: Price simulation
description: This article provides information about price simulation for quotations. Price simulation helps you to evaluate the effect of deductions on the future sales price during the quotation process, before you commit to a specific price.
author: Henrikan
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SalesQuotationPriceSimulation, SalesQuotationsTableLookup
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: 92be7c85-73cf-4f77-833c-d37ce779a031
ms.search.region: Global
# ms.search.industry: 
ms.author: henrikan
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Price simulation

[!include [banner](../includes/banner.md)]

This article provides information about price simulation for quotations. Price simulation helps you to evaluate the effect of deductions on the future sales price during the quotation process, before you commit to a specific price.

A price simulation for a quotation shows a new total amount, based on a proposed new price. A price simulation can also show a new amount for a specific line that is created in an existing quotation. You can enter a price simulation and apply it later. Alternatively, you can use the original quotation without a price simulation and make more changes as you work through the sales process with your customer.  

A price simulation doesn't change the price in the quotation. If the price simulation is applied to a whole quotation, it’s treated as a special discount on the quotation header. If the price simulation is applied to specific items, it’s treated as a special discount on the quotation lines. The unit sales price on a quotation line that is created doesn't change when a price simulation is applied. Instead, a discount percentage that corresponds to the price reduction of the quotation line is applied. When a price simulation is applied, the unit sales price and the discount percentage are transferred to the quotation line or the quotation header.  

>[!NOTE]
>When you run a price simulation, only the current sales currency is used to create the simulation. However, when you view the quotation totals, you see a combination of the company currency and the sales currency.  

Supplementary items that are added to quotation lines might trigger line discounts or multiline discounts. They might also trigger total discounts that change the contribution margins and contribution ratios of the quotation lines and the whole discount.  

You can run multiple price simulations to track the effects of price adjustments on the targets of a quotation. By running these simulations, you can adjust the overall price of the quotation, or the price of one or more specific lines in the quotation, and then apply the price simulation that is most likely to help you close the sale.  

When you create a quotation, you can set up an alert. Here are some of the ways that alerts are used:

-   They can keep you informed about the status of quotations in the organization.
-   They can trigger a review of a specific quotation or inform you when discount limits are exceeded.

## Price simulation and discounts
To guarantee that discounts and prices are calculated correctly, be careful when you run price simulations on quotations that have discounts. Because all price simulations are treated as special discounts on the active quotation line or the whole quotation, you must track the differences in the discounts.

### Types of discounts in trade agreements

Trade agreements in Supply Chain Management can have four types of price discounts. These discounts can be set up for different items, customers, or price groups, and they can be limited by date. To avoid miscalculations, you must consider trade agreements when you run price simulations. Here are the four types of discounts in trade agreements:

-   **Sales price** – Separate sales prices can be specified for items. When quotation lines are created, the program searches for the correct sales price for an item and transfers it to the quotation lines. Therefore, a trade agreement that has this kind of discount doesn't affect the price simulation. The sales price that is used in the quotation line reflects the trade agreement.
-   **Line discount** – Special discounts are specified for items, depending on the quantity that is ordered. Line amounts are typically reduced by the line discount before a price simulation is run. Therefore, a trade agreement that has this kind of discount affects the price simulation.
-   **Multiline discount** – If the combined quantities exceed the limit that you've defined, predefined combinations of ordered items trigger a discount on the whole order. Line amounts are typically reduced by the line discount before a price simulation is run. Therefore, a trade agreement that has this kind of discount affects the price simulation.
-   **Total discount** – If the combined amounts exceed the limit that you've defined, predefined ordered items trigger a discount on the whole order. The total discount is generated by the quotation lines. However, because the total discount is applied to the quotation total as a discount, it reduces the total amount of the quotation. Therefore, a trade agreement that has this kind of discount affects the price simulation.

### Quotation lines and trade agreements

When you create or adjust a quotation line, line discounts are automatically calculated. The relevant sales price is found for the item, based on the trade agreement.

## Price simulation examples
The following examples use price simulation for quotation headers and single line items.

### Price simulation for quotation headers

You create a quotation that has the following lines:

-   10 units of item BR-12 (cost price per unit: USD 9.52, sales price per unit: USD 15.32)
-   12 units of item BR-14 (cost price per unit: USD 7.48, sales price per unit: USD 13.75)

The following table shows the quotation lines.

|    &nbsp;                  | Calculation                          | Result   |
|----------------------------|--------------------------------------|----------|
| Sales quantity             | 10 units + 12 units                  | 22 units |
| Sales value in USD         | (10 × 15.32) + (12 × 13.75)          | 318.20   |
| Cost value in USD          | (10 × 9.52) + (12 × 7.48)            | 184.96   |
| Contribution margin in USD | 318.20 – 184.96                      | 133.24   |
| Contribution ratio         | (\[318.20 – 184.96\] ÷ 318.20) × 100 | 41.87%   |

You run a price simulation and apply a 15-percent total discount for the whole quotation, or the quotation header. The following table shows the new totals of the quotation after the price simulation is run.

|     &nbsp;                                           | Calculation                               | Result   |
|------------------------------------------------------|-------------------------------------------|----------|
| Sales quantity                                       | 10 units + 12 units                       | 22 units |
| Old sales value in USD                               | (10 × 15.32) + (12 × 13.75)               | 318.20   |
| Old cost value in USD                                | (10 × 9.52) + (12 × 7.48)                 | 184.96   |
| Old contribution margin in USD                       | 318.20 – 184.96                           | 133.24   |
| Old contribution ratio                               | (\[318.20 – (10 × 9.52)\] ÷ 318.20) × 100 | 41.87%   |
| Price simulation of 15-percent total discount in USD | (15 × 318.2) ÷ 100                        | 47.73    |
| New sales value in USD                               | 318.20 – 47.73                            | 270.47   |
| New contribution margin in USD                       | 270.47 – 184.96                           | 85.51    |
| New contribution ratio                               | \[(270.47 – 184.96) ÷ 270.47\] × 100      | 31.61%   |

### Price simulation for single line items

You create a quotation that has the following lines:

-   10 units of item BR-12 (cost price per unit: USD 9.52, sales price per unit: USD 15.32)
-   12 units of item BR-14 (cost price per unit: USD 7.48, sales price per unit: USD 13.75)

The following table shows the quotation lines.

|      &nbsp;                          | Calculation                          | Result   |
|--------------------------------------|--------------------------------------|----------|
| Sales quantity                       | 10 units + 12 units                  | 22 units |
| Sales value in USD for BR-12         | 10 × 15.32                           | 153.20   |
| Sales value in USD for BR-14         | 12 × 13.75                           | 165.00   |
| Cost value in USD for BR-12          | 10 × 9.52                            | 95.20    |
| Cost value in USD for BR-14          | 12 × 7.48                            | 89.76    |
| Contribution margin in USD for BR-12 | 153.20 – 95.20                       | 58.00    |
| Contribution margin in USD for BR-14 | 165.00 – 89.76                       | 75.24    |
| Contribution ratio in USD for BR-12  | \[(153.20 – 95.20) ÷ 153.20\] × 100  | 37.86    |
| Contribution ratio in USD for BR-14  | \[(165.00 – 89.76) ÷ 165.00\] × 100  | 45.60    |
| Total sales value in USD             | (10 × 15.32) + (12 × 13.75)          | 318.20   |
| Total cost value in USD              | (10 × 9.52) + (12 × 7.48)            | 184.96   |
| Total contribution margin in USD     | 318.20 – 184.96                      | 133.24   |
| Total contribution ratio             | \[(318.20 – 184.96) ÷ 318.20\] × 100 | 41.87%   |

You run a price simulation and apply a 10-percent total discount to the BR-12 units. The following table shows the new totals of the quotation after the price simulation is run for the single line item.

|    &nbsp;                                         | Calculation                             | Result   |
|---------------------------------------------------|-----------------------------------------|----------|
| Sales quantity                                    | 10 units + 12 units                     | 22 units |
| Old sales value in USD for BR-12                  | 10 × 15.32                              | 153.20   |
| Price simulation of 10-percent discount for BR-12 | (10 × 153.2) ÷ 100                      | 15.32    |
| New sales value in USD for BR-12                  | (10 × 15.32) – 15.32                    | 137.88   |
| Sales value in USD for BR-14                      | 12 × 13.75                              | 165.00   |
| Cost value in USD for BR-12                       | 10 × 9.52                               | 95.20    |
| Cost value in USD for BR-14                       | 12 × 7.48                               | 89.76    |
| New contribution margin in USD for BR-12          | 137.88 – 95.20                          | 42.68    |
| Contribution margin in USD for BR-14              | 165.00 – 89.76                          | 75.24    |
| New contribution ratio in USD for BR-12           | \[(137.88 – 95.20) ÷ 137.88\] × 100     | 30.95    |
| Contribution ratio in USD for BR-14               | \[(165.00 – 89.76) ÷ 165.00\] × 100     | 45.60    |
| New total sales value in USD                      | \[(10 × 15.32) – 15.32\] + (12 × 13.75) | 302.88   |
| Total cost value in USD                           | (10 × 9.52) + (12 × 7.48)               | 184.96   |
| New total contribution margin in USD              | 302.88 – 184.96                         | 117.92   |
| New total contribution ratio                      | \[(302.88 – 184.96) ÷ 302.88\] × 100    | 38.93%   |

The price simulation affects only the line that it's applied to and reduces the total for that line.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]