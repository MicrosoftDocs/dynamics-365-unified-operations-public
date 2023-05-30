---
# required metadata

title: Sales tax calculation and rounding
description: This article provides an overview of sales tax calculation and rounding and explains the parameters of the sales tax calculation and rounding setup.
author: wangchen
ms.date: 06/01/2022
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
ms.collection: get-started
ms.assetid: fe5fdc7f-9834-49fb-a611-1dd9c289619d
ms.search.region: Global
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2022-05-31
ms.dyn365.ops.version: AX 10.0.28

---

# Sales tax calculation and rounding

[!include [banner](../includes/banner.md)]

This article provides an overview of sales tax calculation and rounding in Microsoft Dynamics 365 Finance. It also explains the parameters that are used in the setup for sales tax calculation and rounding, and how those parameters work together.

## Parameters

Several parameters control sales tax calculation and rounding:

- **Calculation method** – This parameter is set on the **General ledger parameters** page and defines whether the tax base amount is calculated per document or per line. If the **Marginal base** parameter for the sales tax code is set to **Net amount of invoice balance**, the tax base amount is always calculated per document, regardless of the setting of this parameter.
- **Rounding by** – This parameter is set for the sales tax group and defines whether the tax amount is rounded per sales tax code or per sales tax code combination.
- **Origin** – This parameter is set for the sales tax code and defines how the tax amount is calculated. For more information, see [Sales tax calculation methods in the Origin field](sales-tax-calculation-methods-origin-field.md).
- **Marginal base** – This parameter is set for the sales tax code and determines which amount is used to select the appropriate tax rates on the **Sales tax code values** page. For more information, see [Sales tax rates based on the Marginal base and Calculation methods](marginal-base-field.md).
- **Sales tax rounding rule** – This parameter is set for the sales tax code and defines how the determined sales tax amount is rounded, including the rounding precision and the rounding method.

The rest of this article presents some typical examples of sales tax calculation and rounding that use a combination of the preceding parameters.

## Scenario for the examples

- There are two lines in the taxable document, and the tax base amount for each line is 42.42.
- Two sales tax codes are defined for each line: sales tax code 1 and sales tax code 2.
- The tax rate of both tax code 1 and tax code 2 is 10 percent.
- The price excludes tax.
- The rounding precision is 0.01.
- The rounding method is **Round up**.

## Example 1

### Parameter values

| Calculation method | Rounding by    | Origin                   | Marginal base       |
| ------------------ | -------------- | ------------------------ | ------------------- |
| Line               | Sales tax code | Percentage of net amount | Net amount per line |

### Calculation and rounding behavior

| Line number | Sales tax code | Amount origin | Sales tax amount |
| ------------| ---------------| --------------| -----------------|
| 1           | Code 1         | 42.42         | 4.25             |
| 1           | Code 2         | 42.42         | 4.25             |
| 2           | Code 1         | 42.42         | 4.25             |
| 2           | Code 2         | 42.42         | 4.25             |

The tax base amount is calculated per line:

- **Line 1:** 42.42
- **Line 2:** 42.42

The tax amount is calculated per sales tax code:

- **Line 1:**

    - Tax amount for sales tax code 1 = 42.42 &times; 10 percent = 4.242
    - Tax amount for sales tax code 2 = 42.42 &times; 10 percent = 4.242

- **Line 2:**

    - Tax amount for sales tax code 1 = 42.42 &times; 10 percent = 4.242
    - Tax amount for sales tax code 2 = 42.42 &times; 10 percent = 4.242

The tax amount is rounded per sales tax code:

- **Line 1:**

    - Rounded tax amount for sales tax code 1 = 4.25
    - Rounded tax amount for sales tax code 2 = 4.25

- **Line 2:**

    - Rounded tax amount for sales tax code 1 = 4.25
    - Rounded tax amount for sales tax code 2 = 4.25

## Example 2

### Parameter values

| Calculation method | Rounding by    | Origin                   | Marginal base                 |
| ------------------ | -------------- | ------------------------ | ----------------------------- |
| Line/Total         | Sales tax code | Percentage of net amount | Net amount of invoice balance |

### Calculation and rounding behavior

| Line number | Sales tax code | Amount origin | Sales tax amount |
| ----------- | -------------- | ------------- | ---------------- |
| 1           | Code 1         | 42.42         | 4.25             |
| 1           | Code 2         | 42.42         | 4.25             |
| 2           | Code 1         | 42.42         | 4.24             |
| 2           | Code 2         | 42.42         | 4.24             |

The tax base amount is calculated per document:

- Tax base amount = 42.42 + 42.42 = 84.84

The tax amount is calculated per sales tax code:

- Tax amount for sales tax code 1 = 84.84 &times; 10 percent = 8.484
- Tax amount for sales tax code 2 = 84.84 &times; 10 percent = 8.484

The tax amount is rounded per sales tax code:

- Rounded tax amount for sales tax code 1 = 8.49
- Rounded tax amount for sales tax code 2 = 8.49

The rounded tax amount is allocated to each line per sales tax code:

- Allocate the rounded tax amount for sales tax code 1 (8.49) to line 1 (4.25) and line 2 (4.24).
- Allocate the rounded tax amount for sales tax code 2 (8.49) to line 1 (4.25) and line 2 (4.24).

## Example 3

### Parameter values

| Calculation method | Rounding by    | Origin                              | Marginal base       |
| ------------------ | -------------- | ----------------------------------- | ------------------- |
| Line               | Sales tax code | Calculated percentage of net amount | Net amount per line |

### Calculation and rounding behavior

| Line number | Sales tax code | Amount origin | Sales tax amount |
| ----------- | -------------- | ------------- | ---------------- |
| 1           | Code 1         | 42.42         | 4.72             |
| 1           | Code 2         | 42.42         | 4.72             |
| 2           | Code 1         | 42.42         | 4.72             |
| 2           | Code 2         | 42.42         | 4.72             |

The tax base amount is calculated per line:

- **Line 1:** 42.42
- **Line 2:** 42.42

The tax amount is calculated per sales tax code:

- **Line 1:**

    - Tax amount for sales tax code 1 = 42.42 &times; 10 percent &divide; (1 – 10 percent) = 4.7133
    - Tax amount for sales tax code 2 = 42.42 &times; 10 percent &divide; (1 – 10 percent) = 4.7133

- **Line 2:**

    - Tax amount for sales tax code 1 = 42.42 &times; 10 percent &divide; (1 – 10 percent) = 4.7133
    - Tax amount for sales tax code 2 = 42.42 &times; 10 percent &divide; (1 – 10 percent) = 4.7133

The tax amount is rounded per sales tax code:

- **Line 1:**

    - Rounded tax amount for sales tax code 1 = 4.72
    - Rounded tax amount for sales tax code 2 = 4.72

- **Line 2:**

    - Rounded tax amount for sales tax code 1 = 4.72
    - Rounded tax amount for sales tax code 2 = 4.72

## Example 4

### Parameter values

| Calculation method | Rounding by    | Origin                              | Marginal base                 |
| ------------------ | -------------- | ----------------------------------- | ----------------------------- |
| Line/Total         | Sales tax code | Calculated percentage of net amount | Net amount of invoice balance |

### Calculation and rounding behavior

| Line number | Sales tax code | Amount origin | Sales tax amount |
| ----------- | -------------- | ------------- | ---------------- |
| 1           | Code 1         | 42.42         | 4.72             |
| 1           | Code 2         | 42.42         | 4.72             |
| 2           | Code 1         | 42.42         | 4.71             |
| 2           | Code 2         | 42.42         | 4.71             |

The tax base amount is calculated per document:

- Tax base amount = 42.42 + 42.42 = 84.84

The tax amount is calculated per sales tax code:

- Tax amount for sales tax code 1 = 84.84 &times; 10 percent &divide; (1 – 10 percent) = 9.4267
- Tax amount for sales tax code 2 = 84.84 &times; 10 percent &divide; (1 – 10 percent) = 9.4267

The tax amount is rounded per sales tax code:

- Rounded tax amount for sales tax code 1 = 9.43
- Rounded tax amount for sales tax code 2 = 9.43

The rounded tax amount is allocated to each line per sales tax code:

- Allocate the tax amount for sales tax code 1 (9.43) to line 1 (4.72) and line 2 (4.71).
- Allocate the tax amount for sales tax code 2 (9.43) to line 1 (4.72) and line 2 (4.71).

## Example 5

### Parameter values

| Calculation method | Rounding by                | Origin                   | Marginal base       |
| ------------------ | -------------------------- | ------------------------ | ------------------- |
| Line               | Sales tax code combination | Percentage of net amount | Net amount per line |

### Calculation and rounding behavior

| Line number | Sales tax code | Amount origin | Sales tax amount |
| ----------- | -------------- | ------------- | ---------------- |
| 1           | Code 1         | 42.42         | 4.25             |
| 1           | Code 2         | 42.42         | 4.24             |
| 2           | Code 1         | 42.42         | 4.24             |
| 2           | Code 2         | 42.42         | 4.24             |

The tax base amount is calculated per line:

- **Line 1:** 42.42
- **Line 2:** 42.42

The tax amount is calculated per sales tax code:

- **Line 1:**

    - Tax amount for sales tax code 1 = 42.42 &times; 10 percent = 4.242
    - tax amount for sales tax code 2 = 42.42 &times; 10 percent = 4.242

- **Line 2:**

    - Tax amount for sales tax code 1 = 42.42 &times; 10 percent = 4.242
    - Tax amount for sales tax code 2 = 42.42 &times; 10 percent = 4.242

The tax amount is rounded per sales tax code combination:

- Total sales tax amount = 4.242 + 4.242 + 4.242 + 4.242 = 16.968, which is rounded up to 16.97

The rounded tax amount is allocated to each line per sales tax code:

- Allocate the sales tax amount (16.97) to line 1 and line 2:

    - **Line 1:**

        - Tax amount for sales tax code 1 = 4.25
        - Tax amount for sales tax code 2 = 4.24

    - **Line 2:**

        - Tax amount for sales tax code 1 = 4.24
        - Tax amount for sales tax code 2 = 4.24

## Example 6

### Parameter values

| Calculation method | Rounding by                | Origin                   | Marginal base                 |
| ------------------ | -------------------------- | ------------------------ | ----------------------------- |
| Line/Total         | Sales tax code combination | Percentage of net amount | Net amount of invoice balance |

### Calculation and rounding behavior

| Line number | Sales tax code | Amount origin | Sales tax amount |
| ----------- | -------------- | ------------- | ---------------- |
| 1           | Code 1         | 42.42         | 4.25             |
| 1           | Code 2         | 42.42         | 4.24             |
| 2           | Code 1         | 42.42         | 4.24             |
| 2           | Code 2         | 42.42         | 4.24             |

The tax base amount is calculated per document:

- Tax base amount = 42.42 + 42.42 = 84.84

The tax amount is calculated per sales tax code:

- Tax amount for sales tax code 1 = 84.84 &times; 10 percent = 8.484
- Tax amount for sales tax code 2 = 84.84 &times; 10 percent = 8.484

The tax amount is rounded per sales tax code combination:

- Total sales tax amount = 8.484 + 8.484 = 16.968, which is rounded up to 16.97

The rounded tax amount is allocated to each line per sales tax code:

- Allocate the sales tax amount (16.97) to line 1 and line 2:

    - **Line 1:**

        - Tax amount for sales tax code 1 = 4.25
        - Tax amount for sales tax code 2 = 4.24

    - **Line 2:**

        - Tax amount for sales tax code 1 = 4.24
        - Tax amount for sales tax code 2 = 4.24

## Example 7

### Parameter values

| Calculation method | Rounding by                | Origin                              | Marginal base       |
| ------------------ | -------------------------- | ----------------------------------- | ------------------- |
| Line               | Sales tax code combination | Calculated percentage of net amount | Net amount per line |

### Calculation and rounding behavior

| Line number | Sales tax code | Amount origin | Sales tax amount |
| ----------- | -------------- | ------------- | ---------------- |
| 1           | Code 1         | 42.42         | 4.72             |
| 1           | Code 2         | 42.42         | 4.71             |
| 2           | Code 1         | 42.42         | 4.71             |
| 2           | Code 2         | 42.42         | 4.72             |

The tax base amount is calculated per line:

- **Line 1:** 42.42
- **Line 2:** 42.42

The tax amount is calculated per sales tax code:

- **Line 1:**

    - Tax amount for sales tax code 1 = 42.42 &times; 10 percent &divide; (1 – 10 percent) = 4.7133
    - Tax amount for sales tax code 2 = 42.42 &times; 10 percent &divide; (1 – 10 percent) = 4.7133

- **Line 2:**

    - Tax amount for sales tax code 1 = 42.42 &times; 10 percent &divide; (1 – 10 percent) = 4.7133
    - Tax amount for sales tax code 2 = 42.42 &times; 10 percent &divide; (1 – 10 percent) = 4.7133

The tax amount is rounded per sales tax code combination:

- Total sales tax amount = 4.7133 + 4.7133 + 4.7133 + 4.7133 = 18.8532, which is rounded up to 18.86

The rounded tax amount is allocated to each line per sales tax code:

- Allocate the sales tax amount (18.86) to line 1 and line 2:

    - **Line 1:**

        - Tax amount for sales tax code 1 = 4.72
        - Tax amount for sales tax code 2 = 4.71

    - **Line 2:**

        - Tax amount for sales tax code 1 = 4.71
        - Tax amount for sales tax code 2 = 4.72

## Example 8

### Parameter values

| Calculation method | Rounding by                | Origin                              | Marginal base                 |
| ------------------ | -------------------------- | ----------------------------------- | ----------------------------- |
| Line/Total         | Sales tax code combination | Calculated percentage of net amount | Net amount of invoice balance |

### Calculation and rounding behavior

| Line number | Sales tax code | Amount origin | Sales tax amount |
| ----------- | -------------- | ------------- | ---------------- |
| 1           | Code 1         | 42.42         | 4.72             |
| 1           | Code 2         | 42.42         | 4.71             |
| 2           | Code 1         | 42.42         | 4.71             |
| 2           | Code 2         | 42.42         | 4.72             |

The tax base amount is calculated per document:

- Tax base amount = 42.42 + 42.42 = 84.84

The tax amount is calculated per sales tax code:

- Tax amount for sales tax code 1 = 84.84 &times; 10 percent &divide; (1 – 10 percent) = 9.4267
- Tax amount for sales tax code 2 = 84.84 &times; 10 percent &divide; (1 – 10 percent) = 9.4267

The tax amount is rounded per sales tax code combination:

- Total sales tax amount = 9.4267 + 9.4267 = 18.8534, which is rounded up to 18.86

The rounded tax amount is allocated to each line per sales tax code:

- Allocate the sales tax amount (18.86) to line 1 and line 2:

    - **Line 1:**

        - Tax amount for sales tax code 1 = 4.72
        - Tax amount for sales tax code 2 = 4.71

    - **Line 2:**

        - Tax amount for sales tax code 1 = 4.71
        - Tax amount for sales tax code 2 = 4.72

## Additional resources

- [Sales tax calculation methods in the Origin field](sales-tax-calculation-methods-origin-field.md)
- [Sales tax rates based on the Marginal base and Calculation methods](marginal-base-field.md)
- [Whole amount and Interval calculation options for sales tax codes](whole-amount-interval-options-sales-tax-codes.md)
