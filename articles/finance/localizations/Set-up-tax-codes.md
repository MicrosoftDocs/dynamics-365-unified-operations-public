---
# required metadata 

title: Set up tax codes
description: This topic explains how to set up tax codes in the Tax Calculation Service. 
author: wangchen
ms.date: 11/24/2021
ms.topic: business-process 
ms.prod:  
ms.technology:  

# optional metadata 

ms.search.form: TaxTable, TaxData   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2021-10-26 
ms.dyn365.ops.version: Version 10.0.21 
---

# Set up tax codes

[!include [banner](../includes/banner.md)]

This topic explains how to set up tax codes in the Tax Calculation service, including the setup for a simple scenario to make the tax code work, and some advanced functionalities on tax code for complex scenarios.

> [!IMPORTANT]
> Tax code setup in the Tax Calculation Service is legal entity-agnostic. You can complete this setup in the Regulatory Configuration Service (RCS) only once. Tax codes will be synchronized to Dynamics 365 Finance automatically when you enable the Tax Calculation service in Finance for the selected legal entity.


## Simple setup

Complete the steps in this section to use the tax code in a simple scenario, such as only one tax rate.

1. On the **Tax codes** tab, select **Add** and enter the tax code and a description.
2. Select **Calculation origin**. The calculation origin is a group of methods that were defined in the selected tax configuration version. In this simple scenario, select the value **By net amount**.
3. Select **Save**. More fields become available, based on the Calculation origin that you selected.
4. **Add** one tax rate for this tax code.
5. Select **Save**.

## Calculation origin

The Calculation origin defines how the tax base amount and the tax amount are calculated based on what you select. The Calcuation origin is configured in the **Electronic Reporting** workspace by tax configuration. The following values are available in the **Calculation origin** field:

  - **By net amount**
  - **By gross amount**
  - **By quantity**
  - **By margin**
  - **Tax on tax**

### By net amount

When you select **By net amount** in the **Calculation origin** field, the tax amount is calculated as a percentage of the purchase or sales amount, excluding any other tax codes.

For example, the tax rate is 25%. The invoice line will show a quantity of 10 items at 1.00 each. The customer is allowed a 10% line discount. This means the calculation would be:

  Net amount: (10 x 	1.00) -10% = 9.00 Sales tax: 9.00 x 25% = 2.25 Total amount: 9.00 + 2.25 = 11.25

### By gross amount

When you select **By gross amount** in the **Calculation origin** field, the tax amount is calculated as a percentage of the gross sales amount. The gross amount is the line net amount plus all taxes and fees for the line except the one tax with **Calculation origin = By gross amount**.

For example, the tax authority has imposed special duties on an item. The duty amounts are added to the net amount before tax is calculated. Given the following tax codes:

  - Duty 1 = 10%, using the **By net amount** calculation method
  - Duty 2 = 20%, using the **By net amount** calculation method
  - Tax rate = 25%, using the **By gross amount** calculation method

If the net amount is 10.00, then Duty 1 is 1.00 (10.00 x 10%) and Duty 2 = 2.00 (10.00 x 20%). The amounts would be as follows: 

  - Gross amount: Net amount + Duty 1 amount + Duty 2 amount (10.00 + 1.00 + 2.00) = 13.00 
  - Tax amount: 13.00 x 25% = 3.25 
  - Total duties and tax: 1.00 + 2.00 + 3.25 = 6.25 
  - Total amount: 10.00 + 6.25 = 16.25

### By quantity

When you select **By quantity** in the **Calculation origin** field, the tax amount is calculated as a fixed amount per unit and multiplied with the quantity entered on the document line. The amount per unit is specified on the **Rates** FastTab.

For example, the Tax code is set up as: 1.20 per unit. On a sales invoice line, 25 units of an item are sold. The tax amount is calculated as 25 x 1.20 = 30.00

### By margin

When you select **By margin** in the **Calculation origin** field, the tax amount is calculated as a percentage of the sales margin which is the sales amount minus the cost amount. This calculation method only applies to sales transactions.

For example, the tax rate is 25%. The invoice line shows a quantity of 10 items at 10.00 each, and the cost per item is 6. 

  - Sales margin: 10 x ( 10.00 - 6.00) = 40.00
  - Tax amount: 40.00 x 25% = 10.00
  - Total amount: 100.00 + 10.00 = 110.00

### Tax on tax

When you select **Tax on tax** in the **Calculation origin** field, the sales tax is calculated as a percentage of all the other tax amounts in the same document line.

For example, given the following tax codes:

  - Duty 1 = 10%, using the **By net amount** method
  - Duty 2 = 20%, using the **By net amount** method
  - Tax on duty = 25%, using the **Tax on tax** method

The calculations would be:

  - Net amount: 10.00 
  - Duty 1: 10.00 x 10% = 1.00 
  - Duty 2: 10.00 x 20% = 2.00 
  - Tax on duty: 3.00 x 25% = 0.75
  - Total tax: 1.00 + 2.00 + 0.75 = 3.75 
  - Total amount: 10.00 + 3.75 = 13.75

## Advanced functionality

The following sections explain some advanced functionality on tax codes setup for complex scenarios.

### Exempt tax

When you set the **Is exempt** field to **Yes** on the **General** FastTab, the tax amount will always be overriden as zero regardless of the actual tax rate.

You can specify Exempt code field here for the specific exempt reason. 

Master selection can be enabled for this field to select the defined exempt code values from Dynamics 365 Finance. To enable the master selection, see this article for detail information.

For example, the tax rate is 25% and the **Is exempt** field is **Yes** on the tax code. The invoice line shows a quantity of 10 items at 1.00 each, and the customer is allowed a 10% line discount. 

  - Net amount: (10 x 	1.00) -10% = 9.00 
  - Sales tax: 0.00 
  - Total amount: 9.00 + 0.00 = 9.00

### Use tax

When you set the **Is exempt**  field to **Yes** on the **General** FastTab, the tax amount will always be overriden as zero regardless of the actual tax rate.

You can specify Exempt code field here for the specific exempt reason. 

Master selection can be enabled for this field to select the defined exempt code values from Dynamics 365 Finance. To enable the master selection, see this article for detail information.

For example, the tax rate is 25% and the **Is exempt** field is set to **Yes** on the tax code. The invoice line shows a quantity of 10 items at 1.00 each, and the customer is allowed a 10% line discount. 

  - Net amount: (10 x 1.00) -10% = 9.00 
  - Sales tax: 0.00 
  - Total amount: 9.00 + 0.00 = 9.00


> [!IMPORTANT]
> If a tax code is marked as **exempt** and **use tax**, the code will be recognized as exempt tax for sales transactions and use tax for purchase transactions.

#### Reverse charge

When you set the **Is reverse charge** field to **Yes** on the **General** FastTab, the tax rate can be configured as negative. For a reverse charge scenario, we recommend that you set up two tax codes, one with a positive tax rate, and the other with a negative tax rate. Both tax codes should have the same rate value, with the **Is reverse charge** field set to **Yes**. For more information about the reverse charge solution in Finance, see [Reverse charge mechanism for VAT/GST scheme](emea-reverse-charge.md).

For example, two tax codes are determined in one invoice line. One tax rate is 25% and the other is -25% with the **Is reverse charge** field marked as **Yes** on the tax code. The invoice line shows a quantity of 10 items at 1.00 each. 

  - Net amount: (10 x 	1.00)  = 10.00 
  - Tax code 1 10.00 X 25% = 2.50
  - Tax code 2 10 X -25% = -2.50
  - Total amount: 10.00 + 2.50 -2.50 = 10.00

### Exclude from base amount calculation

When you set the **Exclude from base amount calculation** field to **Yes**, the calculated tax amount of this tax code is excluded from tax base amount for other tax codes calculation in the price inclusive scenario.

For more information, see [Calculate tax on prices when Prices include taxes is enabled](global-exclude-from-tax-base-amount-calculation.md)

### Rate

You can define different tax rates for different tax base amount ranges. The Tax Calculation service always uses the rate that matches the tax base amount to calculate the tax amount.

The following table provides an example of how tax rates are configured.

| Minimum amount | Maximum amount | Tax rate |
| -------------- | -------------- | -------- |
| 0              | 1000           | 10%      |
| 1000           | 5000           | 15%      |
| 5000           | 10000          | 20%      |
| 10000          | 0              | 30%      |

- If the tax base amount = 300.00, then tax rate = 10%, tax amount = 300.00 X 10% = 30.00
- If the tax base amount = 3000.00, then tax rate = 15%, tax amount = 3000.00 X 15% = 450.00
- If the tax base amount = 6000.00, then tax rate = 20%, tax amount = 6000.00 X 10% = 1200.00
- If the tax base amount = 20000.00, then tax rate = 30%, tax amount = 20000.00 X 30% = 6000.00

> [!NOTE]
> If the tax base amount can match both the maximum amount in one line, and the minimum amount in the other line, then the base will use the tax rate that matches the minimum base amount. For example, if the tax base amount = 1000.00, then the tax rate = 15%, and the tax amount = 1000.00 X 15% = 150.00

### Limits

You can define tax limits to override the calculated tax amount if the amount falls into the minimum/maximum range.

- If the calculated tax amount is greater than or equal to the maximum tax amount configured on the **Limits** FastTab, the final tax amount = the maximum tax amount.
- If the calculated tax amount is less than the minimum tax amount configured on the **Limits** FastTab, the final tax amount = 0.

For example, if the tax limits are configured as:

- Minimum tax amount = 100 
- Maximum tax amount = 1000


If the calculated tax amount is 2000, the final tax mount = 1000

If the calculated tax amount is 500, the final tax mount = 500

If the calculated tax amount is 80, the final tax mount = 0


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
