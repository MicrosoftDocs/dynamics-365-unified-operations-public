---
title: Sales tax calculation and rounding
description: Access an overview of sales tax calculation and rounding and explains the parameters of the sales tax calculation and rounding setup.
author: EricWangChen
ms.author: wangchen
ms.topic: overview
ms.date: 09/08/2026
ms.reviewer: twheeloc
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2022-05-31
ms.search.form: TaxTable
ms.dyn365.ops.version: AX 10.0.28
ms.assetid: fe5fdc7f-9834-49fb-a611-1dd9c289619d
---

# Sales tax calculation and rounding

[!INCLUDE [banner](../includes/banner.md)]

This article provides an overview of sales tax calculation and rounding in Microsoft Dynamics 365 Finance. It also explains the parameters that are used in the setup for sales tax calculation and rounding, and how those parameters work together.

## Parameters

Several parameters control sales tax calculation and rounding:

- **Calculation method** – Set on the **General ledger parameters** page. It defines whether the system calculates the tax base amount per document or per line. If you set the **Marginal base** parameter for the sales tax code to **Net amount of invoice balance**, the system always calculates the tax base amount per document, regardless of the setting of this parameter.
- **Rounding by** – Set for the sales tax group. It defines whether the system rounds the tax amount per sales tax code or per sales tax code combination.
- **Origin** – Set for the sales tax code. It defines how the system calculates the tax amount. Learn more in [Sales tax calculation methods in the Origin field](sales-tax-calculation-methods-origin-field.md).
- **Marginal base** – This parameter is set for the sales tax code and determines which amount is used to select the appropriate tax rates on the **Sales tax code values** page. Learn more in [Sales tax rates based on the Marginal base and Calculation methods](marginal-base-field.md).
- **Sales tax rounding rule** – This parameter is set for the sales tax code and defines how the determined sales tax amount is rounded, including the rounding precision and the rounding method.
- **Sales tax amount per invoice line** – This option determines whether the calculated sales tax amount is stored on each individual document line. Learn more in [Store the sales tax amount on each invoice line](#store-the-sales-tax-amount-on-each-invoice-line).

The rest of this article presents some typical examples of sales tax calculation and rounding that use a combination of the preceding parameters.

## Store the sales tax amount on each invoice line

The **Sales tax amount per invoice line** option determines whether the sales tax amount that you calculate for a document is also stored on each individual line of the document, such as a purchase order line or a sales order line.

To set this option, go to **Tax** > **Setup** > **Parameters** > **General ledger parameters**. On the **Sales tax** tab, expand **Tax options** and then set **Sales tax amount per invoice line**.

- When **Sales tax amount per invoice line** is set to *Yes*, the system stores the calculated sales tax amount on each line during confirmation or posting, and it populates the per-line **Sales tax amount** field.
- When **Sales tax amount per invoice line** is set to *No*, the system still calculates sales tax for the document and keeps it visible on the sales tax transactions (for example, on **Purchase** > **Tax** > **Sales tax**), but the per-line **Sales tax amount** field remains blank or zero.

This option applies prospectively to processing that occurs after you save the change. It doesn't retroactively populate the per-line amount on documents that were already processed. An existing document can receive the stored per-line amount only through a supported confirmation or posting action, and only when its current state makes that action available. Review this legal-entity tax setting with your tax and accounting administrators before you change it because it affects how tax amounts are stored and displayed across sales and purchase documents.

## Scenario for the examples

- The taxable document contains two lines, and the tax base amount for each line is 42.42.
- You define two sales tax codes for each line: sales tax code 1 and sales tax code 2.
- The tax rate for both tax code 1 and tax code 2 is 10 percent.
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

Calculate the tax base amount per line:

- **Line 1:** 42.42
- **Line 2:** 42.42

Calculate the tax amount per sales tax code:

- **Line 1:**

  - Tax amount for sales tax code 1 = 42.42 &times; 10 percent = 4.242
  - Tax amount for sales tax code 2 = 42.42 &times; 10 percent = 4.242

- **Line 2:**

  - Tax amount for sales tax code 1 = 42.42 &times; 10 percent = 4.242
  - Tax amount for sales tax code 2 = 42.42 &times; 10 percent = 4.242

Round the tax amount for each sales tax code:

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

Calculate the tax base amount per document:

- Tax base amount = 42.42 + 42.42 = 84.84

Calculate the tax amount per sales tax code:

- Tax amount for sales tax code 1 = 84.84 &times; 10 percent = 8.484
- Tax amount for sales tax code 2 = 84.84 &times; 10 percent = 8.484

Round the tax amount for each sales tax code:

- Rounded tax amount for sales tax code 1 = 8.49
- Rounded tax amount for sales tax code 2 = 8.49

Allocate the rounded tax amount to each line per sales tax code:

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

Calculate the tax base amount per line:

- **Line 1:** 42.42
- **Line 2:** 42.42

Calculate the tax amount per sales tax code:

- **Line 1:**

  - Tax amount for sales tax code 1 = 42.42 &times; 10 percent &divide; (1 – 10 percent) = 4.7133
  - Tax amount for sales tax code 2 = 42.42 &times; 10 percent &divide; (1 – 10 percent) = 4.7133

- **Line 2:**

  - Tax amount for sales tax code 1 = 42.42 &times; 10 percent &divide; (1 – 10 percent) = 4.7133
  - Tax amount for sales tax code 2 = 42.42 &times; 10 percent &divide; (1 – 10 percent) = 4.7133

Round the tax amount for each sales tax code:

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

Calculate the tax base amount per document:

- Tax base amount = 42.42 + 42.42 = 84.84

Calculate the tax amount per sales tax code:

- Tax amount for sales tax code 1 = 84.84 &times; 10 percent &divide; (1 – 10 percent) = 9.4267
- Tax amount for sales tax code 2 = 84.84 &times; 10 percent &divide; (1 – 10 percent) = 9.4267

Round the tax amount for each sales tax code:

- Rounded tax amount for sales tax code 1 = 9.43
- Rounded tax amount for sales tax code 2 = 9.43

Allocate the rounded tax amount to each line per sales tax code:

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

Calculate the tax base amount per line:

- **Line 1:** 42.42
- **Line 2:** 42.42

Calculate the tax amount per sales tax code:

- **Line 1:**

  - Tax amount for sales tax code 1 = 42.42 &times; 10 percent = 4.242
  - Tax amount for sales tax code 2 = 42.42 &times; 10 percent = 4.242

- **Line 2:**

  - Tax amount for sales tax code 1 = 42.42 &times; 10 percent = 4.242
  - Tax amount for sales tax code 2 = 42.42 &times; 10 percent = 4.242

Round the tax amount per sales tax code combination:

- Total sales tax amount = 4.242 + 4.242 + 4.242 + 4.242 = 16.968, which rounds up to 16.97

Allocate the rounded tax amount to each line per sales tax code:

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

Calculate the tax base amount per document:

- Tax base amount = 42.42 + 42.42 = 84.84

Calculate the tax amount per sales tax code:

- Tax amount for sales tax code 1 = 84.84 &times; 10 percent = 8.484
- Tax amount for sales tax code 2 = 84.84 &times; 10 percent = 8.484

Round the tax amount per sales tax code combination:

- Total sales tax amount = 8.484 + 8.484 = 16.968, which rounds up to 16.97

Allocate the rounded tax amount to each line per sales tax code:

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

Calculate the tax base amount per line:

- **Line 1:** 42.42
- **Line 2:** 42.42

Calculate the tax amount per sales tax code:

- **Line 1:**

  - Tax amount for sales tax code 1 = 42.42 &times; 10 percent &divide; (1 – 10 percent) = 4.7133
  - Tax amount for sales tax code 2 = 42.42 &times; 10 percent &divide; (1 – 10 percent) = 4.7133

- **Line 2:**

  - Tax amount for sales tax code 1 = 42.42 &times; 10 percent &divide; (1 – 10 percent) = 4.7133
  - Tax amount for sales tax code 2 = 42.42 &times; 10 percent &divide; (1 – 10 percent) = 4.7133

Round the tax amount per sales tax code combination:

- Total sales tax amount = 4.7133 + 4.7133 + 4.7133 + 4.7133 = 18.8532, which rounds up to 18.86

Allocate the rounded tax amount to each line per sales tax code:

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

Calculate the tax base amount per document:

- Tax base amount = 42.42 + 42.42 = 84.84

Calculate the tax amount per sales tax code:

- Tax amount for sales tax code 1 = 84.84 &times; 10 percent &divide; (1 – 10 percent) = 9.4267
- Tax amount for sales tax code 2 = 84.84 &times; 10 percent &divide; (1 – 10 percent) = 9.4267

Round the tax amount per sales tax code combination:

- Total sales tax amount = 9.4267 + 9.4267 = 18.8534, which rounds up to 18.86

Allocate the rounded tax amount to each line per sales tax code:

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
