---
# required metadata

title: Sales tax calculation and rounding
description: This article provides an overview of sales tax calculation and rounding and explains the parameters of the sales tax calculation and rounding setup.
author: wangchen
ms.date: 05/31/2022
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: TaxTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend


# ms.tgt_pltfrm: 
ms.custom: ["13111", "intro-internal"]
ms.assetid: fe5fdc7f-9834-49fb-a611-1dd9c289619d
ms.search.region: Global
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2022-05-31
ms.dyn365.ops.version: AX 10.0.28

---

# Sales tax calculation and rounding

[!include [banner](../includes/banner.md)]

This article provides an overview of the sales tax calculation and rounding in Dynamics 365 Finance. It also explains the parameters of the sales tax calculation and rounding setup, and how they work together.

There are several parameters that control sales tax calculation and rounding. These are:

- **Calculation method** in General ledger parameters - This parameter defines whether the tax base amount is calculated per document or per line. However, if the **Marginal base** parameter is set to **Net amount of invoice balance**, the tax base amount is always calculated per document.
- **Rounding by** in sales tax group - This parameter defines if the tax amount is rounded per sales tax code or per sales tax code combination.
- **Origin** in sales tax code - This parameter defines how the tax amount is calculated. For more information, see [Sales tax calculation methods in the Origin field](sales-tax-calculation-methods-origin-field.md). 
- **Marginal base** in sales tax code - This parameter determines which amount is used to pick the appropriate tax rates from the rates on the **Sales tax code values** page. For more information, see [Sales tax rates based on the Marginal base and Calculation methods](marginal-base-field.md). 
- **Sales tax rounding rule** in sales tax code - This parameter defines how the determined sales tax amount is rounded, including rounding precision and rounding method. 

The following are some frequently used examples of sales tax calculation and rounding using a combination the parameters above.

Scenario:

- There are 2 lines in the taxable document and the tax base amount for each line is 42.42. 
- Each line has two sales tax codes determined, sales tax code 1 and sales tax code 2.
- The tax rate of tax code 1 and tax code 2 is 10%.
- The price is exclusive of tax.
- The rounding precision is 0.01.
- The rounding method is **Round up**.

### Example 1

Parameters value

| Calculation method | Rounding by    | Origin                   | Marginal base       |
| ------------------ | -------------- | ------------------------ | ------------------- |
| Line               | Sales tax code | Percentage of net amount | Net amount per line |

Calculation and rounding behavior

| Line number | Sales tax code | Amount origin | Sales tax amount |
| ------------| ---------------| --------------| -----------------|
| 1           | Code 1         | 42.42         | 4.25             |
| 1           | Code 2         | 42.42         | 4.25             |
| 2           | Code 1         | 42.42         | 4.25             |
| 2           | Code 2         | 42.42         | 4.25             |

**Tax base amount is calculated per line** 

Line 1: 42.42

Line 2: 42.42

**Tax amount is calculated per sales tax code**

Line 1: sales tax code 1 tax amount = 42.42 * 10% = 4.242 

Line 1: sales tax code 2 tax amount = 42.42 * 10% = 4.242 

Line 2: sales tax code 1 tax amount = 42.42 * 10% = 4.242 

Line 2: sales tax code 2 tax amount = 42.42 * 10% = 4.242 

**Tax amount is rounded per sales tax code**

Line 1: rounded sales tax code 1 tax amount = 4.25 

Line 1: rounded sales tax code 2 tax amount = 4.25 

Line 2: rounded sales tax code 1 tax amount = 4.25 

Line 2: rounded sales tax code 2 tax amount = 4.25 

### Example 2

Parameters value

| Calculation method | Rounding by    | Origin                   | Marginal base                 |
| ------------------ | -------------- | ------------------------ | ----------------------------- |
| Line/Total         | Sales tax code | Percentage of net amount | Net amount of invoice balance |

Calculation and rounding behavior

| Line number | Sales tax code | Amount origin | Sales tax amount |
| ----------- | -------------- | ------------- | ---------------- |
| 1           | Code 1         | 42.42         | 4.24             |
| 1           | Code 2         | 42.42         | 4.25             |
| 2           | Code 1         | 42.42         | 4.24             |
| 2           | Code 2         | 42.42         | 4.25             |

**Tax base amount is calculated per document**

Tax base amount = 42.42 + 42.42 = 84.84 

**Tax amount is calculated per sales tax code**

Tax amount for sales tax code 1 = 84.84 * 10% = 8.484

Tax amount for sales tax code 2 = 84.84 * 10% = 8.484

**Tax amount is rounded per sales tax code**

Rounded tax amount for sales tax code 1 = 8.49

Rounded tax amount for sales tax code 2 = 8.49

**Rounded tax amount is allocated to each line per sales tax code**

Allocate rounded sales tax code 1 tax amount 8.49 to Line 1(4.24) and Line 2(4.25)

Allocate rounded sales tax code 2 tax amount 8.49 to Line 1(4.24) and Line 2(4.25)

### Example 3

Parameters value

| Calculation method | Rounding by    | Origin                              | Marginal base       |
| ------------------ | -------------- | ----------------------------------- | ------------------- |
| Line               | Sales tax code | Calculated percentage of net amount | Net amount per line |

Calculation and rounding behavior

| Line number | Sales tax code | Amount origin | Sales tax amount |
| ----------- | -------------- | ------------- | ---------------- |
| 1           | Code 1         | 42.42         | 4.72             |
| 1           | Code 2         | 42.42         | 4.72             |
| 2           | Code 1         | 42.42         | 4.72             |
| 2           | Code 2         | 42.42         | 4.72             |

**Tax base amount is calculated per line** 

Line 1: 42.42

Line 2: 42.42

**Tax amount is calculated per sales tax code**

Line 1: sales tax code 1 tax amount = 42.42 * 10% / (1 - 10%) = 4.7133 

Line 1: sales tax code 2 tax amount = 42.42 * 10% / (1 - 10%) = 4.7133 

Line 2: sales tax code 1 tax amount = 42.42 * 10% / (1 - 10%) = 4.7133 

Line 2: sales tax code 2 tax amount = 42.42 * 10% / (1 - 10%) = 4.7133 

**Tax amount is rounded per sales tax code**

Line 1: rounded sales tax code 1 tax amount = 4.72 

Line 1: rounded sales tax code 2 tax amount = 4.72 

Line 2: rounded sales tax code 1 tax amount = 4.72 

Line 2: rounded sales tax code 2 tax amount = 4.72 

### Example 4

Parameters value

| Calculation method | Rounding by    | Origin                              | Marginal base                 |
| ------------------ | -------------- | ----------------------------------- | ----------------------------- |
| Line/Total         | Sales tax code | Calculated percentage of net amount | Net amount of invoice balance |

Calculation and rounding behavior

| Line number | Sales tax code | Amount origin | Sales tax amount |
| ----------- | -------------- | ------------- | ---------------- |
| 1           | Code 1         | 42.42         | 4.71             |
| 1           | Code 2         | 42.42         | 4.72             |
| 2           | Code 1         | 42.42         | 4.71             |
| 2           | Code 2         | 42.42         | 4.72             |

**Tax base amount is calculated per document**

Tax base amount = 42.42 + 42.42 = 84.84  

**Tax amount is calculated per sales tax code**

Tax amount for sales tax code 1 = 84.84 * 10% / (1 - 10%) = 9.4267

Tax amount for sales tax code 2 = 84.84 * 10% / (1 - 10%) = 9.4267

**Tax amount is rounded per sales tax code**

Rounded tax amount for sales tax code 1 = 9.43

Rounded tax amount for sales tax code 2 = 9.43

**Rounded tax amount is allocated to each line per sales tax code**

Allocate sales tax code 1 tax amount 9.43 to Line 1(4.71) and Line 2(4.72)

Allocate sales tax code 2 tax amount 9.43 to Line 1(4.71) and Line 2(4.72)

### Example 5

Parameters value

| Calculation method | Rounding by                | Origin                   | Marginal base       |
| ------------------ | -------------------------- | ------------------------ | ------------------- |
| Line               | Sales tax code combination | Percentage of net amount | Net amount per line |

Calculation and rounding behavior

| Line number | Sales tax code | Amount origin | Sales tax amount |
| ----------- | -------------- | ------------- | ---------------- |
| 1           | Code 1         | 42.42         | 4.25             |
| 1           | Code 2         | 42.42         | 4.24             |
| 2           | Code 1         | 42.42         | 4.24             |
| 2           | Code 2         | 42.42         | 4.24             |

**Tax base amount is calculated per line** 

Line 1: 42.42

Line 2: 42.42

**Tax amount is calculated per sales tax code**

Line 1: sales tax code 1 tax amount = 42.42 * 10% = 4.242 

Line 1: sales tax code 2 tax amount = 42.42 * 10% = 4.242 

Line 2: sales tax code 1 tax amount = 42.42 * 10% = 4.242 

Line 2: sales tax code 2 tax amount = 42.42 * 10% = 4.242 

**Tax amount is rounded per sales tax code combination**

Total sales tax amount = 4.242 + 4.242 + 4.242 + 4.242 = 16.968 rounded up to 16.97

**Rounded tax amount is allocated to each line per sales tax code**

Allocate sales tax amount 16.97 to Line 1 and Line 2

Line 1: sales tax code 1 tax amount = 4.25

Line 1: sales tax code 2 tax amount = 4.24

Line 2: sales tax code 1 tax amount = 4.24

Line 2: sales tax code 2 tax amount = 4.24

### Example 6

Parameters value

| Calculation method | Rounding by                | Origin                   | Marginal base                 |
| ------------------ | -------------------------- | ------------------------ | ----------------------------- |
| Line/Total         | Sales tax code combination | Percentage of net amount | Net amount of invoice balance |

Calculation and rounding behavior

| Line number | Sales tax code | Amount origin | Sales tax amount |
| ----------- | -------------- | ------------- | ---------------- |
| 1           | Code 1         | 42.42         | 4.25             |
| 1           | Code 2         | 42.42         | 4.24             |
| 2           | Code 1         | 42.42         | 4.24             |
| 2           | Code 2         | 42.42         | 4.24             |

**Tax base amount is calculated per document**

Tax base amount = 42.42 + 42.42 = 84.84 

**Tax amount is calculated per sales tax code**

Tax amount for sales tax code 1 = 84.84 * 10% = 8.484

Tax amount for sales tax code 2 = 84.84 * 10% = 8.484

**Tax amount is rounded per sales tax code combination**

Total sales tax amount = 8.484 + 8.484 = 16.968 rounded up to 16.97

**Rounded tax amount is allocated to each line per sales tax code**

Allocate sales tax amount 16.97 to Line 1 and Line 2

Line 1: sales tax code 1 tax amount = 4.25

Line 1: sales tax code 2 tax amount = 4.24

Line 2: sales tax code 1 tax amount = 4.24

Line 2: sales tax code 2 tax amount = 4.24

### Example 7

Parameters value

| Calculation method | Rounding by                | Origin                              | Marginal base       |
| ------------------ | -------------------------- | ----------------------------------- | ------------------- |
| Line               | Sales tax code combination | Calculated percentage of net amount | Net amount per line |

Calculation and rounding behavior

| Line number | Sales tax code | Amount origin | Sales tax amount |
| ----------- | -------------- | ------------- | ---------------- |
| 1           | Code 1         | 42.42         | 4.72             |
| 1           | Code 2         | 42.42         | 4.71             |
| 2           | Code 1         | 42.42         | 4.71             |
| 2           | Code 2         | 42.42         | 4.72             |

**Tax base amount is calculated per line** 

Line 1: 42.42

Line 2: 42.42

**Tax amount is calculated per sales tax code**

Line 1: sales tax code 1 tax amount =  42.42 * 10% / (1 - 10%) = 4.7133 

Line 1: sales tax code 2 tax amount =  42.42 * 10% / (1 - 10%) = 4.7133 

Line 2: sales tax code 1 tax amount =  42.42 * 10% / (1 - 10%) = 4.7133 

Line 2: sales tax code 2 tax amount =  42.42 * 10% / (1 - 10%) = 4.7133 

**Tax amount is rounded per sales tax code combination**

Total sales tax amount = 4.7133 + 4.7133 + 4.7133 + 4.7133 = 18.8532 rounded up to 18.86

**Rounded tax amount is allocated to each line per sales tax code**

Allocate sales tax amount 18.86 to Line 1 and Line 2

Line 1: sales tax code 1 tax amount = 4.72

Line 1: sales tax code 2 tax amount = 4.71

Line 2: sales tax code 1 tax amount = 4.71

Line 2: sales tax code 2 tax amount = 4.72

### Example 8

Parameters value

| Calculation method | Rounding by                | Origin                              | Marginal base                 |
| ------------------ | -------------------------- | ----------------------------------- | ----------------------------- |
| Line/Total         | Sales tax code combination | Calculated percentage of net amount | Net amount of invoice balance |

Calculation and rounding behavior

| Line number | Sales tax code | Amount origin | Sales tax amount |
| ----------- | -------------- | ------------- | ---------------- |
| 1           | Code 1         | 42.42         | 4.72             |
| 1           | Code 2         | 42.42         | 4.71             |
| 2           | Code 1         | 42.42         | 4.71             |
| 2           | Code 2         | 42.42         | 4.72             |

**Tax base amount is calculated per document**

Tax base amount = 42.42 + 42.42 = 84.84 

**Tax amount is calculated per sales tax code**

Tax amount for sales tax code 1 = 84.84 * 10% / (1 - 10%) = 9.4267

Tax amount for sales tax code 2 = 84.84 * 10% / (1 - 10%) = 9.4267

**Tax amount is rounded per sales tax code combination**

Total sales tax amount = 9.4267 + 9.4267 = 18.8534 rounded up to 18.86

**Rounded tax amount is allocated to each line per sales tax code**

Allocate sales tax amount 18.86 to Line 1 and Line 2

Line 1: sales tax code 1 tax amount = 4.72

Line 1: sales tax code 2 tax amount = 4.71

Line 2: sales tax code 1 tax amount = 4.71

Line 2: sales tax code 2 tax amount = 4.72



## Additional resources

- [Sales tax calculation methods in the Origin field](sales-tax-calculation-methods-origin-field.md)
- [Sales tax rates based on the Marginal base and Calculation methods](marginal-base-field.md)
- [Whole amount and Interval calculation options for sales tax codes](whole-amount-interval-options-sales-tax-codes.md)
