---
title: Set up tax codes
description: Learn how to set up tax codes in the Tax Calculation, including overviews on simple setup and calculation origin. 
author: liza-golub
ms.date: 07/30/2024
ms.topic: how-to 
ms.custom: 
  - bap-template
ms.search.form: TaxTable, TaxData   
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: egolub
ms.search.validFrom: 2021-10-26 
ms.dyn365.ops.version: Version 10.0.21 
---

# Set up tax codes

[!include [banner](../../includes/banner.md)]

This article explains how to set up tax codes in the Tax Calculation feature of Globalization studio workspace. It includes the setup for a simple scenario to make the tax code work and information about some advanced tax code functionality for complex scenarios.

> [!IMPORTANT]
> The setup of tax codes in the Tax Calculation of Globalization studio workspace is legal entity–agnostic. Tax codes are automatically synced to Sales tax codes when you enable the Enable advanced tax calculation in the Tax calculation parameters for a selected legal entity in Finance.

## Simple setup

Follow these steps to use a tax code in a simple scenario, such as a scenario where there is only one tax rate.

1. Open the **Globalization Studio** workspace, select **Globalization services**, and then select the **Tax Calculation** tile.
2. On the **Tax calculation features** page, select the feature and version that you want to set up, and then select **Edit**.
3. On the **General** tab, select **Configuration version**.
4. On the **Tax codes** tab, select **Add**, and enter the tax code and a description.
5. Select **Calculation origin**. A calculation origin is a group of methods that are defined in the tax configuration version that you selected. For this simple scenario, select **By net amount**.
6. Select **Save**. More fields become available, based on the calculation origin that you selected.
7. On the **Rates** FastTab, select **Add** to add one tax rate for this tax code.
8. Select **Save**.

## Calculation origin

The calculation origin defines how the tax base amount and the tax amount are calculated. The following values are available in the **Calculation origin** field:

- By net amount
- By gross amount
- By quantity
- By margin
- Tax on tax

### By net amount

If you select **By net amount** in the **Calculation origin** field, the tax amount is calculated as a percentage of the purchase or sales amount, excluding any other tax codes.

For example, the tax rate is 25 percent, the invoice line shows a quantity of 10 items at 1.00 each, and the customer is allowed a 10-percent line discount. In this case, amounts are calculated in the following way:

- **Net amount:** (10 × 1.00) – 10 percent = 9.00 
- **Sales tax:** 9.00 × 25 percent = 2.25 
- **Total invoice amount:** 9.00 + 2.25 = 11.25

### By gross amount

If you select **By gross amount** in the **Calculation origin** field, the tax amount is calculated as a percentage of the gross sales amount. The gross amount is the line's net amount plus all taxes and fees for the line except the one tax where the **Calculation origin** field is set to **By gross amount**.

For example, the tax authority has imposed special duties on an item. The duty amounts are added to the net amount before tax is calculated. The following tax codes are used:

- **Duty 1** – The rate is 10 percent, and the **By net amount** calculation method is used.
- **Duty 2** – The rate is 20 percent, and the **By net amount** calculation method is used.
- **Tax rate** – The rate is 25 percent, and the **By gross amount** calculation method is used.

If the net amount is 10.00, the Duty 1 amount is 1.00 (10.00 × 10 percent), and the Duty 2 amount is 2.00 (10.00 × 20 percent). In this case, amounts are calculated in the following way: 

- **Gross amount:** Net amount + Duty 1 amount + Duty 2 amount = 10.00 + 1.00 + 2.00 = 13.00 
- **Tax amount:** 13.00 × 25 percent = 3.25 
- **Total duties and tax:** 1.00 + 2.00 + 3.25 = 6.25 
- **Total invoice amount:** 10.00 + 6.25 = 16.25

### By quantity

If you select **By quantity** in the **Calculation origin** field, the tax amount is calculated as a fixed amount per unit and multiplied by the quantity that is entered on the document line. The amount per unit is specified on the **Rates** FastTab.

For example, the tax code is set up as 1.20 per unit. On a sales invoice line, 25 units of an item are sold. In this case, the tax amount is calculated as 25 × 1.20 = 30.00.

> [!NOTE] 
> If the transaction is entered in a unit other than the unit that's specified on the tax code, the unit is automatically converted based on the unit conversions that are set up on the **Unit conversions** page. This function is available starting from the 10.0.40 update.

#### By quantity, additional option
You can choose whether a tax amount By quantity is calculated before other tax codes and added to the net amount before other tax codes are calculated where **Calculation origin** = **By Net Amount**.

##### Examples
Assume two tax codes are calculated on a transaction:

- **Duty**: Calculation origin = By quantity, the value is set to 5.00 per unit = pcs
- **Tax**: Calculation origin = as shown in the examples below, the value is set to 25%

One piece of an item is sold at a unit price of 10.00.

###### Example 1
**Tax**: Calculation origin = By Gross Amount method. The **Calculate before sales tax** option has no effect, because **Tax** is calculated as a percentage of the gross amount. Duty: 1 × 5.00 = 5.00. Gross amount: 10.00 + 5.00 = 15.00. Tax: 15.00 × 25% = 3.75. Total tax: 5.00 + 3.75 = 8.75. Total amount: 10.00 + 8.75 = 18.75.

###### Example 2
**Tax**: Calculation origin = By Net Amount. The **Calculate before sales tax** option isn't selected for the **Duty** calculation. Net amount: 10.00. Duty: 1 × 5.00 = 5.00. Tax: 10.00 × 25% = 2.50. Total tax: 5.00 + 2.50 = 7.50. Total amount: 10.00 + 7.50 = 17.50.

###### Example 3
**Tax**: Calculation origin = By Net Amount. The **Calculate before sales tax option** is selected for the **Duty** calculation. Net amount: 10.00. Duty: 1 × 5.00 = 5.00. Tax: (10.00 + 5.00) × 25% = 3.75. Total tax: 5.00 + 3.75 = 8.75. Total amount: 10.00 + 8.75 = 18.75.

###### Example 4
The results of example 3 and example 1 are the same, because there's only one duty. Assume that you have two duties, and only one of them is included in the net amount for the sales tax calculation: Duty 1: 5.00, using the By Quantity method, and the **Calculate before sales tax** option is selected. Duty 2: 2.50, using the By Quantity method, and the **Calculate before sales tax** option isn't selected. Tax: 25%, using the By Net Amount method. Net amount: 10.00. Duty 1: 1 × 5.00 = 5.00. Duty 2: 1 × 2.50 = 2.50. Net amount subject to tax: 10.00 + 5.00 = 15.00. Tax: 15.00 × 25% = 3.75. Total taxes, including duties: 5.00 + 2.50 + 3.75 = 11.25. Total amount: 10.00 + 11.25 = 21.25. The 25% **Tax** is calculated for the sum of the net amount (10.00) + Duty 1 (5.00) = 15.00. Duty 2 is added to the tax amount after the sales tax is calculated.

### By margin

If you select **By margin** in the **Calculation origin** field, the tax amount is calculated as a percentage of the sales margin. The sales margin is the sales amount minus the cost amount. This calculation method applies only to sales transactions.

For example, the tax rate is 25 percent, the invoice line shows a quantity of 10 items at 10.00 each, and the cost per item is 6. In this case, amounts are calculated in the following way:

- **Sales margin:** 10 × (10.00 – 6.00) = 40.00
- **Tax amount:** 40.00 × 25 percent = 10.00
- **Total invoice amount:** 100.00 + 10.00 = 110.00

### Tax on tax

If you select **Tax on tax** in the **Calculation origin** field, the sales tax is calculated as a percentage of all the other tax amounts on the same document line.

For example, the following tax codes are used:

- **Duty 1** – The rate is 10 percent, and the **By net amount** calculation method is used.
- **Duty 2** – The rate is 20 percent, and the **By net amount** calculation method is used.
- **Tax on duty** – The rate is 25 percent, and the **Tax on tax** calculation method is used.

In this case, amounts are calculated in the following way:

- **Net amount:** 10.00 
- **Duty 1:** 10.00 × 10 percent = 1.00 
- **Duty 2:** 10.00 × 20 percent = 2.00 
- **Tax on duty:** 3.00 × 25 percent = 0.75
- **Total tax:** 1.00 + 2.00 + 0.75 = 3.75 
- **Total invoice amount:** 10.00 + 3.75 = 13.75

## Advanced functionality

This section explains some advanced functionality of the tax code setup for complex scenarios.

### Tax exemption

If you set the **Is Exempt** option to **Yes** on the **General** FastTab, the tax amount will always be overridden to 0 (zero), regardless of the actual tax rate.

You can set the **Exempt Code** field to specify the reason for the exemption. 

You can enable master data lookup for the **Exempt Code** field. In that way, you can select among the exempt code values that are defined in Finance. For information about how to enable master data lookup, see [Enable master data lookup for tax calculation configuration](tax-service-set-up-environment-master-data-lookup.md).

For example, the tax rate is 25 percent, and the **Is Exempt** option is set to **Yes** on the tax code. The invoice line shows a quantity of 10 items at 1.00 each, and the customer is allowed a 10-percent line discount. In this case, amounts are calculated in the following way:

- **Net amount:** (10 × 1.00) – 10 percent = 9.00 
- **Sales tax:** 0.00 
- **Total invoice amount:** 9.00 + 0.00 = 9.00

### Use tax

If you set the **Is Use Tax** option to **Yes** on the **General** FastTab, the tax amount will be posted to the **Use tax payable** account instead of the **Vendor summary** account.

For example, the tax rate is 25 percent, and the **Is Use Tax** option is set to **Yes** on the tax code. The invoice line shows a quantity of 10 items at 1.00 each, and the customer is allowed a 10-percent line discount. In this case, amounts are calculated in the following way:

- **Net amount:** (10 × 1.00) – 10 percent = 9.00 
- **Use tax:** 9.00 × 25 percent = 2.25
- **Total invoice amount:** 9.00 + 0.00 = 9.00

> [!IMPORTANT]
> If both the **Is Exempt** option and the **Is Use Tax** option are set to **Yes** on a tax code, the code will be recognized as tax-exempt for sales transactions and use tax for purchase transactions.

### Reverse charges

If you set the **Is Reverse Charge** option to **Yes** on the **General** FastTab, the tax rate can be configured as negative. For a reverse charge scenario, we recommend that you set up two tax codes: one that has a positive tax rate and one that has a negative tax rate. Both tax codes should have the same rate value, and the **Is Reverse Charge** option should be set to **Yes** on the tax code that has a negative tax rate. For more information about the reverse charge solution in Finance, see [Reverse charge mechanism for VAT/GST scheme](emea-reverse-charge.md).

For example, two tax codes are determined on one invoice line. One tax rate is 25 percent. The other tax rate is -25 percent, and the **Is Reverse Charge** option is set to **Yes** on the second tax code. The invoice line shows a quantity of 10 items at 1.00 each. In this case, the amounts are calculated in the following way:

- **Net amount:** (10 × 1.00) = 10.00 
- **Tax code 1:** 10.00 × 25 percent = 2.50
- **Tax code 2:** 10 × -25 percent = -2.50
- **Total invoice amount:** 10.00 + 2.50 -2.50 = 10.00

### Exclusion from base amount calculations

If you set the **Exclude from base amount calculation** option to **Yes** on the **General** FastTab, the calculated tax amount of the tax code is excluded from the tax base amount for other tax code calculations in the price-inclusive scenario.

For more information, see [Calculate tax on prices when Prices include taxes is enabled](global-exclude-from-tax-base-amount-calculation.md).

### Rates

On the **Rate** FastTab, you can define different tax rates for different ranges of tax base amounts. To calculate the tax amount, the Tax Calculation service always uses the rate that matches the tax base amount.

For example, tax rates might be configured as shown in the following table.

| Minimum amount | Maximum amount | Tax rate   |
| -------------- | -------------- | ---------- |
| 0              | 1,000          | 10 percent |
| 1,000          | 5,000          | 15 percent |
| 5,000          | 10,000         | 20 percent |
| 10,000         | 0              | 30 percent |

In this case, the tax amount is calculated in the following way:

- If the tax base amount is 300.00, the tax rate is 10 percent, and the tax amount is 300.00 × 10 percent = 30.00.
- If the tax base amount is 3,000.00, the tax rate is 15 percent, and the tax amount is 3,000.00 × 15 percent = 450.00.
- If the tax base amount is 6,000.00, the tax rate is 20 percent, and the tax amount is 6,000.00 × 10 percent = 1,200.00.
- If the tax base amount is 20,000.00, the tax rate is 30 percent, and the tax amount is 20,000.00 × 30 percent = 6,000.00.

> [!NOTE]
> If the tax base amount can match both the maximum amount on one line and the minimum amount on the other line, the base will use the tax rate that matches the minimum base amount. For example, if the tax base amount is 1000.00, the tax rate is 15 percent, and the tax amount is 1,000.00 × 15 percent = 150.00.

### Limits

On the **Limits** FastTab, you can define tax limits to override the calculated tax amount if the tax amount falls into the minimum/maximum range.

- If the calculated tax amount is more than or equal to the maximum tax amount that is configured on the **Limits** FastTab, the final tax amount equals the maximum tax amount.
- If the calculated tax amount is less than the minimum tax amount that is configured on the **Limits** FastTab, the final tax amount is 0 (zero).

For example, the tax limits are configured in the following way:

- **Minimum tax amount:** 100 
- **Maximum tax amount:** 1,000

If the calculated tax amount is 2,000, the final tax amount is 1,000.

If the calculated tax amount is 500, the final tax amount is 500.

If the calculated tax amount is 80, the final tax amount is 0 (zero).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
