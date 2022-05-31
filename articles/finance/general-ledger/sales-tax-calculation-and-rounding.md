---
# required metadata

title: Sales tax calculation and rounding
description: This topic provides an overview of the sales tax calculation and rounding in Dynamics 365 Finance. It explains the parameters of the sales tax calculation and rounding setup, and how they work together.
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
ms.dyn365.ops.version: AX 10.0.29

---

# Sales tax calculation and rounding

[!include [banner](../includes/banner.md)]

This topic provides an overview of the sales tax calculation and rounding in Dynamics 365 Finance. It explains the parameters of the sales tax calculation and rounding setup, and how they work together.

## Overview

There are several parameters controlling the sales tax calculation and rounding in Dynamics 365 Finance:

1. **Calculation method** in General ledger parameters: This parameter defines whether tax base amount is calculated per document or per line. There is a special case the tax base amount is always calculated per document if **Marginal base** parameter = Net amount of invoice balance
2. **Rounding by** in sales tax group: This parameter defines whether tax amount is rounded per sales tax code or per sales tax code combination.
3. **Origin** in sales tax code: This parameter defines how tax amount is calculated. For more information, see this article [Sales tax calculation methods in the Origin field - Finance | Dynamics 365 | Microsoft Docs](https://docs.microsoft.com/en-us/dynamics365/finance/general-ledger/sales-tax-calculation-methods-origin-field) 
4. **Marginal base** in sales tax code: This parameter determines which amount is used to pick the appropriate tax rate(s) from the rates in the Sales tax code values page. For more information, see this article [Sales tax rates based on the Marginal base and Calculation methods - Finance | Dynamics 365 | Microsoft Docs](https://docs.microsoft.com/en-us/dynamics365/finance/general-ledger/marginal-base-field) 
5. **Sales tax rounding rule** in sales tax code: This parameter defines how the determined sales tax amount is rounded, including rounding precision and rounding method. 

Following are some frequently used examples of sales tax calculation and rounding per the combination of above parameters:

Scenario:

- There are 2 lines in the taxable document. Tax base amount for each line is the same 42.42. 
- Each line has two sales tax codes determined, sales tax code 1 and sales tax code 2.
- Tax rate of tax code 1 and tax code 2 is 10%
- Price exclusive tax
- Rounding precision is 0.01
- Rounding method is Round up

### **Example 1**

Parameters value

| Calculation method | Rounding by    | Origin                   | Marginal base       |
| ------------------ | -------------- | ------------------------ | ------------------- |
| Line               | Sales tax code | Percentage of net amount | Net amount per line |

Calculation and Rounding behavior

| Line No. | Sales tax code | Amount origin | Sales tax amount |
| -------- | -------------- | ------------- | ---------------- |
| 1        | Code 1         | 42.42         | 4.25             |
| 1        | Code 2         | 42.42         | 4.25             |
| 2        | Code 1         | 42.42         | 4.25             |
| 2        | Code 2         | 42.42         | 4.25             |

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

### **Example 2**

Parameters value

| Calculation method | Rounding by    | Origin                   | Marginal base                 |
| ------------------ | -------------- | ------------------------ | ----------------------------- |
| Line/Total         | Sales tax code | Percentage of net amount | Net amount of invoice balance |

Calculation and Rounding behavior

| Line No. | Sales tax code | Amount origin | Sales tax amount |
| -------- | -------------- | ------------- | ---------------- |
| 1        | Code 1         | 42.42         | 4.24             |
| 1        | Code 2         | 42.42         | 4.25             |
| 2        | Code 1         | 42.42         | 4.24             |
| 2        | Code 2         | 42.42         | 4.25             |

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

### **Example 3**

Parameters value

| Calculation method | Rounding by    | Origin                              | Marginal base       |
| ------------------ | -------------- | ----------------------------------- | ------------------- |
| Line               | Sales tax code | Calculated percentage of net amount | Net amount per line |

Calculation and Rounding behavior

| Line No. | Sales tax code | Amount origin | Sales tax amount |
| -------- | -------------- | ------------- | ---------------- |
| 1        | Code 1         | 42.42         | 4.72             |
| 1        | Code 2         | 42.42         | 4.72             |
| 2        | Code 1         | 42.42         | 4.72             |
| 2        | Code 2         | 42.42         | 4.72             |

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

### **Example 4**

Parameters value

| Calculation method | Rounding by    | Origin                              | Marginal base                 |
| ------------------ | -------------- | ----------------------------------- | ----------------------------- |
| Line/Total         | Sales tax code | Calculated percentage of net amount | Net amount of invoice balance |

Calculation and Rounding behavior

| Line No. | Sales tax code | Amount origin | Sales tax amount |
| -------- | -------------- | ------------- | ---------------- |
| 1        | Code 1         | 42.42         | 4.71             |
| 1        | Code 2         | 42.42         | 4.72             |
| 2        | Code 1         | 42.42         | 4.71             |
| 2        | Code 2         | 42.42         | 4.72             |

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

### **Example 5**

Parameters value

| Calculation method | Rounding by                | Origin                   | Marginal base       |
| ------------------ | -------------------------- | ------------------------ | ------------------- |
| Line               | Sales tax code combination | Percentage of net amount | Net amount per line |

Calculation and Rounding behavior

| Line No. | Sales tax code | Amount origin | Sales tax amount |
| -------- | -------------- | ------------- | ---------------- |
| 1        | Code 1         | 42.42         | 4.25             |
| 1        | Code 2         | 42.42         | 4.24             |
| 2        | Code 1         | 42.42         | 4.24             |
| 2        | Code 2         | 42.42         | 4.24             |

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

### **Example 6**

Parameters value

| Calculation method | Rounding by                | Origin                   | Marginal base                 |
| ------------------ | -------------------------- | ------------------------ | ----------------------------- |
| Line/Total         | Sales tax code combination | Percentage of net amount | Net amount of invoice balance |

Calculation and Rounding behavior

| Line No. | Sales tax code | Amount origin | Sales tax amount |
| -------- | -------------- | ------------- | ---------------- |
| 1        | Code 1         | 42.42         | 4.25             |
| 1        | Code 2         | 42.42         | 4.24             |
| 2        | Code 1         | 42.42         | 4.24             |
| 2        | Code 2         | 42.42         | 4.24             |

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

### **Example 7**

Parameters value

| Calculation method | Rounding by                | Origin                              | Marginal base       |
| ------------------ | -------------------------- | ----------------------------------- | ------------------- |
| Line               | Sales tax code combination | Calculated percentage of net amount | Net amount per line |

Calculation and Rounding behavior

| Line No. | Sales tax code | Amount origin | Sales tax amount |
| -------- | -------------- | ------------- | ---------------- |
| 1        | Code 1         | 42.42         | 4.72             |
| 1        | Code 2         | 42.42         | 4.71             |
| 2        | Code 1         | 42.42         | 4.71             |
| 2        | Code 2         | 42.42         | 4.72             |

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

### **Example 8**

Parameters value

| Calculation method | Rounding by                | Origin                              | Marginal base                 |
| ------------------ | -------------------------- | ----------------------------------- | ----------------------------- |
| Line/Total         | Sales tax code combination | Calculated percentage of net amount | Net amount of invoice balance |

Calculation and Rounding behavior

| Line No. | Sales tax code | Amount origin | Sales tax amount |
| -------- | -------------- | ------------- | ---------------- |
| 1        | Code 1         | 42.42         | 4.72             |
| 1        | Code 2         | 42.42         | 4.71             |
| 2        | Code 1         | 42.42         | 4.71             |
| 2        | Code 2         | 42.42         | 4.72             |

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

[Sales tax calculation methods in the Origin field - Finance | Dynamics 365 | Microsoft Docs](https://docs.microsoft.com/en-us/dynamics365/finance/general-ledger/sales-tax-calculation-methods-origin-field)

[Sales tax rates based on the Marginal base and Calculation methods](https://docs.microsoft.com/en-us/dynamics365/finance/general-ledger/marginal-base-field)

[Whole amount and Interval calculation options for sales tax codes](https://docs.microsoft.com/en-us/dynamics365/finance/general-ledger/whole-amount-interval-options-sales-tax-codes)
