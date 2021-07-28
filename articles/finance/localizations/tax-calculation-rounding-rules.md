---
# required metadata

title: Tax calculation rounding rules
description: This topic provides information about how the rounding rules in the tax calculation parameter of the tax calculation service works.
author: kailiang
ms.date: 07/28/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:
audience: Application user
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: kailiang
ms.search.validFrom: 2021-08-02
ms.dyn365.ops.version: 10.0.21

---
# Tax calculation rounding rules

This topic provides information about how the rounding rules in the tax calculation parameter of the tax calculation service works.
> [!Note] When tax calculation service is enabled, the rounding rules on the Sales tax code and Sales tax group pages will not be effective.

The rounding rules configuration for tax calculation service are under **Tax > Setup > Tax configuration > Tax calculation parameters**.
[![Tax calculation parameters](./media/tax-calculation-parameters-calculation-1.png)](./media/tax-calculation-parameters-calculation-1.png)

The calculated amounts in the payload from the tax calculation service are rounded according to the configuration in **Rounding precision** and **Rounding method**.

##### Rounding precision 

The rounding precision is supported up to 6 decimal places. Set the rounding precision to “0.000000”, the amount results are rounded to 6 decimal places and then sent to Dynamics 365 Finance. For example: Amount **987.1234567** will be rounded to **987.123457** (via the normal rounding method). 

>   [!Note] **Dynamics 365 Finance** will further round the amount according to the currency rounding rules. Hence, tax amounts displayed and recorded in the transactions are impacted by both rounding rules.  

##### Rounding method

The rounding method for tax calculation can be configured per legal entity. The following options are available: **Normal, Downward** and **Rounding-up**.

##### Example 1

For amount **987.345**.

| Rounding method option | Rounding precision = 0.00 | Rounding precision = 0.01 | Rounding precision = 0.10 | Rounding precision = 1.00 | Rounding precision = 10.00 |
| :--------------------- | :------------------------ | :------------------------ | :------------------------ | :------------------------ | :------------------------- |
| Normal                 | 987.35                    | 987.35                    | 987.30                    | 987.00                    | 990.00                     |
| Downward               | 987.00                    | 987.34                    | 987.30                    | 987.00                    | 980.00                     |
| Rounding-up            | 988.00                    | 987.35                    | 987.40                    | 988.00                    | 990.00                     |


| Rounding method option | Rounding precision = 0.02 | Rounding precision = 0.05 | Rounding precision = 0.25 |
| :--------------------- | :------------------------ | :------------------------ | :------------------------ |
| Normal                 | 987.34                    | 987.35                    | 987.25                    |
| Downward               | 987.34                    | 987.30                    | 987.25                    |
| Rounding-up            | 987.36                    | 987.35                    | 987.50                    |

The calculation and rounding logic of tax amounts can further be configured according to taxation rules.

##### Rounding by 

Select the rounding principle that applies to the taxes. The following options are available:

  - **Tax codes**
    “Rounding per tax code” means tax amount will be rounded inside each tax code. 
  - **Tax code combinations**
    “Rounding per tax code combination” means tax amount will be rounded inside tax code combination within the line. 

##### Calculation method 

 Select whether taxes on invoices are calculated for each line or for all lines. The following options are available: 

-  **Line** 
“Rounding by line” means tax amount will be calculated line by line. Each line's tax amount will not impact others.  
-  **Total** 
 “Rounding by total” means tax amount will be calculated within one document across lines. 

##### Example 2

When calculating 1 invoice with 4 lines. 

- 2 tax codes: VAT1 (10%) and VAT2 (10%). 
- Rounding method = Rounding-up. 
- Rounding Precision = 0.01. 

1. Rounding by **Tax codes** and **Line**.

| Line no. | Line net amount | Determined tax codes | Tax amount (before rounding) | Tax amount (rounded) |
| :------- | :-------------- | :------------------- | :--------------------------- | :------------------- |
| 1        | 11.11           | VAT1                 | 1.111                        | 1.12                 |
| 2        | 22.22           | VAT1; VAT2           | 2.222; 2.222                 | 2.23; 2.23           |
| 3        | 33.33           | VAT1                 | 3.333                        | 3.34                 |
| 4        | 44.44           | VAT1; VAT2           | 4.444; 4;444                 | 4.45; 4.45           |

2. Rounding by **Tax code combinations** and **Line**.

| Line no. | Line net amount | Determined tax codes | Tax amount (before rounding) | Tax amount (rounded) |
| :------- | :-------------- | :------------------- | :--------------------------- | :------------------- |
| 1        | 11.11           | VAT1                 | 1.111                        | 1.12                 |
| 2*       | 22.22           | VAT1; VAT2           | 2.222; 2.222                 | 2.23; 2.22           |
| 3        | 33.33           | VAT1                 | 3.333                        | 3.34                 |
| 4**      | 44.44           | VAT1; VAT2           | 4.444; 4;444                 | 4.45; 4.44           |

```
*Line2 = Round[22.22 * (10% + 10%)] = 2.23 + 2.22
**Line4 = Round[44.44 * (10% + 10%)] = 4.45 + 4.44
```

3. Rounding by **Tax codes** and **Total**.

| Line no. | Line net amount | Determined tax codes | Tax amount (before rounding) | Tax amount (rounded) |
| :------- | :-------------- | :------------------- | :--------------------------- | :------------------- |
| 1        | 11.11           | VAT1*                | 1.111                        | 1.12                 |
| 2        | 22.22           | VAT1*; VAT2**        | 2.222; 2.222                 | 2.22; 2.23           |
| 3        | 33.33           | VAT1*                | 3.333                        | 3.33                 |
| 4        | 44.44           | VAT1*; VAT2**        | 4.444; 4;444                 | 4.44; 4.44           |

```
*VAT1(Line1, Line2, Line3, Line4) = Round[(11.11 + 22.22 + 33.33 + 44.44) * 10%] = 1.12 + 2.22 + 3.33 + 4.44
**VAT2(Line2, Line4) = Round[(22.22 + 44.44) * 10%] = 2.23 + 4.44
```

4. Rounding by **Tax code combinations** and **Total**.

| Line no. | Line net amount | Determined tax codes | Tax amount (before rounding) | Tax amount (rounded) |
| :------- | :-------------- | :------------------- | :--------------------------- | :------------------- |
| 1*       | 11.11           | VAT1                 | 1.111                        | 1.12                 |
| 2**      | 22.22           | VAT1; VAT2           | 2.222; 2.222                 | 2.23; 2.22           |
| 3*       | 33.33           | VAT1                 | 3.333                        | 3.33                 |
| 4**      | 44.44           | VAT1; VAT2           | 4.444; 4;444                 | 4.44; 4.45           |
```
*Line1, Line3 = Round[(11.11 + 33.33) % 10%] = 1.12 + 3.33
**Line2, Line4 = Round[(22.22 + 44.44) * (10% + 10%)] = 2.23 + 2.22 + 4.44 + 4.45
```