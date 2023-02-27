---
# required metadata

title: Sales tax calculation methods in the Origin field
description: This article explains the options in the Origin field on the Sales tax codes page and how sales tax is calculated based on the selected sales tax code option.
author: kailiang
ms.date: 01/11/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: TaxTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: kailiang
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Sales tax calculation methods in the Origin field

[!include [banner](../includes/banner.md)]

This article explains the options in the **Origin** field on the **Sales tax codes** page and how sales tax is calculated based on the selected option for a sales tax code.

For each sales tax code that you create on the **Sales tax codes** page, you must select the method of calculation to apply to the tax base amount in the **Origin** field.

## Percentage of net amount
**Percentage of net amount calculation** is the default value in the **Origin** field. The sales tax is calculated as a percentage of the purchase or sales amount, excluding any other sales taxes.

### Example
The tax rate is 25%. The invoice line shows a quantity of 10 items at 1.00 each, and the customer is allowed a 10% line discount. Net amount: (10 &times; 1.00) -10% = 9.00. Sales tax: 9.00 &times; 25% = 2.25. Total amount: 9.00 + 2.25 = 11.25.

## Percentage of gross amount
If you select **Percentage of gross amount**, the sales tax is calculated as a percentage of the gross sales amount. The gross amount is the line net amount plus all taxes and fees for the line, except the one tax where **Origin** = **Percentage of gross amount**.

### Example
The tax authority has imposed special duties on an item. The duty amounts are added to the net amount before sales tax is calculated. Given the following sales tax codes:

- DUTY 1 = 10%, using the Percentage of net amount calculation method
- DUTY 2 = 20%, using the Percentage of net amount calculation method
- SALESTAX = 25%, using the Percentage of gross amount calculation method

If the net amount is 10.00, then DUTY 1 is 1.00 (10.00 &times; 10%) and DUTY 2 = 2.00 (10.00 &times; 20%). The amounts would be as follows: Gross amount: Net amount + DUTY 1 amount + DUTY 2 amount (10.00 + 1.00 + 2.00) = 13.00. SALESTAX = 13.00 &times; 25% = 3.25. Total DUTIES and SALESTAX: 1.00 + 2.00 + 3.25 = 6.25. Total amount: 10.00 + 6.25 = 16.25.

> [!NOTE]
> Only one tax code where **Origin** = **Percentage of gross amount** can be used for a transaction. Otherwise, you'll receive an error message that states that the sales tax can't be calculated. 


## Percentage of sales tax
When you select **Percentage of sales tax** in the **Origin** field, sales tax is calculated as a percentage of the sales tax that's selected in the **Sales tax on sales tax** field. The sales tax that's selected in the **Sales tax on sales tax** field is calculated first. The second sales tax is then calculated based on the first sales tax amount.

### Example
Given the following sales tax codes:

- DUTY 1 = 10%, using the Percentage of net amount method.
- DUTY 2 = 20%, using the Percentage of sales tax method, with Duty 1 in the **Sales tax on sales tax** field.
- SALESTAX = 25%, using the Percentage of gross amount method.

Net amount: 10.00. DUTY 1: 10.00 &times; 10% = 1.00. DUTY 2: 1.00 &times; 20% = 0.20. Gross amount: 10.00 + 1.00 + 0.20 = 11.20. SALESTAX: 11.20 &times; 25% = 2.80. Total DUTIES and SALESTAX: 1.00 + 0.20 + 2.80 = 4.00. Total amount: 10.00 + 4.00 = 14.00.

> [!NOTE]
> Multilevel tax-on-tax calculations aren't possible. A tax can't be calculated based on a tax that's already calculated based on another tax. Multiple single-level tax-on-tax codes can be calculated on a transaction. 

## Amount per unit
When you select **Amount per unit** in the **Origin** field, sales tax is calculated as a fixed amount per unit, multiplied by the quantity that's entered on the document line. A unit must be selected in the **Unit** field. The amount per unit is specified on the **Sales tax code values** page.

### Example
The sales tax code is set up as USD 1.20 per unit = box on a sales invoice line. Twenty-five boxes of an item are sold, and the sales tax is calculated as 25 &times; 1.20 = 30.00.

> [!NOTE]
> If the transaction is entered in a unit other than the unit that's specified on the sales tax code, the unit is automatically converted based on the unit conversions that are set up on the **Unit conversions** page. 

### Amount per unit, additional option

On the **Calculation** tab, you can select whether an amount per unit calculated tax is calculated before other tax codes and added to the net amount before other tax codes where **Origin** = **Percentage of net amount** are calculated.

### Examples

Assume two tax codes are calculated on a transaction:

- DUTY: Origin = Amount per unit and a sales tax, the value is set to 5.00 per unit = pcs
- SALESTAX: Origin = as shown in the examples below, the value is set to 25%

One piece of an item is sold at a unit price of 10.00.

#### Example 1
SALESTAX: Origin = Percentage of gross amount method. The **Calculate before sales tax** option has no effect, because SALESTAX is calculated as a percentage of the gross amount. DUTY: 1 &times; 5.00 = 5.00. Gross amount: 10.00 + 5.00 = 15.00. SALESTAX: 15.00 &times; 25% = 3.75. Total sales tax: 5.00 + 3.75 = 8.75. Total amount: 10.00 + 8.75 = 18.75.

#### Example 2
SALESTAX: Origin = Percentage of net amount. The **Calculate before sales tax** option isn't selected for the DUTY calculation. Net amount: 10.00. DUTY: 1 &times; 5.00 = 5.00. SALESTAX: 10.00 &times; 25% = 2.50. Total sales tax: 5.00 + 2.50 = 7.50. Total amount: 10.00 + 7.50 = 17.50.

#### Example 3
SALESTAX: Origin = Percentage of net amount. The **Calculate before sales tax** option is selected for the DUTY calculation. Net amount: 10.00. DUTY: 1 &times; 5.00 = 5.00. SALESTAX: (10.00 + 5.00) &times; 25% = 3.75. Total sales tax: 5.00 + 3.75 = 8.75. Total amount: 10.00 + 8.75 = 18.75.

#### Example 4
The results of example 3 and example 1 are the same, because there's only one duty. Assume that you have two duties, and only one of them is included in the net amount for the sales tax calculation: DUTY 1: 5.00, using the **Amount per unit** method, and the **Calculate before sales tax** option is selected. DUTY 2: 2.50, using the **Amount per unit** method, and the **Calculate before sales tax** option isn't selected. Sales tax: 25%, using the **Percentage of net amount** method. Net amount: 10.00. DUTY 1: 1 &times; 5.00 = 5.00. DUTY 2: 1 &times; 2.50 = 2.50. Net amount subject to sales tax: 10.00 + 5.00 = 15.00. SALESTAX: 15.00 &times; 25% = 3.75. Total sales taxes, including duties: 5.00 + 2.50 + 3.75 = 11.25. Total amount: 10.00 + 11.25 = 21.25. The 25% SALESTAX is calculated for the sum of the net amount (10.00) + DUTY 1 (5.00) = 15.00. DUTY 2 is added to the tax amount after the sales tax is calculated.

## Calculated percentage of net amount
The **Calculated percentage of net amount** handles tax calculation differently, depending on the setting of the **Amounts include sales tax** parameter for the document or journal.

### Example 1

Document/journal is set to **Amounts include sales tax** = **Yes**. Transaction line amount: 10.00. Tax rate: 25%. Sales tax: Transaction line amount &times; tax rate (10.00 &times; 25%) = 2.50. Tax base amount (origin amount): Transaction line amount – Sales tax (10.00 – 2.50) = 7.50.

### Example 2

Document/journal is set to **Amounts include sales tax** = **No**. Transaction line amount: 10.00. Tax rate: 25%. Sales tax: (Transaction line amount &times; tax rate) &divide; (100 – tax rate) (10.00 &times; 25%) &divide; (100% – 25%) = 3.33. Tax base amount (origin amount): Transaction line amount = 10.00.

## Percentage of margin
The **Percentage of margin calculation** method is introduced by the [tax calculation service](../localizations/global-tax-calcuation-service-overview.md) and is effective only in the tax calculation service. The sales tax is calculated as a percentage of the difference between the sales price and the return cost price.

### Example
The tax rate is 20%. The invoice line shows a quantity of two items at 329.00 each. The return cost price of each item is 318.00. Net amount: (2 &times; 329.00) = 658.00. Sales tax: (658.00 – \[2 &times; 318.00\]) &times; 20% = 4.40.

## Additional resources

[Sales tax rates based on the Marginal base and Calculation methods](marginal-base-field.md)

[Whole amount and Interval calculation options for sales tax codes](whole-amount-interval-options-sales-tax-codes.md)



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
