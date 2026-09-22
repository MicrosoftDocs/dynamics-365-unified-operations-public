---
title: Simulate prices based on sales order line attributes
description: Learn how to simulate sales prices in Unified pricing management by assigning price attribute values to individual sales order lines.
author: sherry-zheng
ms.author: chuzheng
ms.topic: how-to
ms.date: 09/21/2026
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form: RetailPricingSimulatorV2, GUPPricingAttributeGroup, SalesQuotationTable
ai-usage: ai-assisted
---

# Simulate prices based on sales order line attributes

[!INCLUDE [banner](../includes/banner.md)]

The same product, sold to the same customer, can command a different price depending on how a line is sold. Package type, warranty type, and fulfillment method are all examples of details that vary from line to line within a single order. Unified pricing management captures these details as *sales order line price attributes*, and your pricing rules can use them as match criteria.

The **Price simulator** page lets you try those rules out before you commit to a sales order. You build a simulated transaction, assign attribute values to each line, and see the prices that the pricing engine returns. You can also use the same attribute values on sales quotation lines, so that a quotation reflects the price a customer would actually be offered.

## Prerequisites

To use the features that are described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.47 or later.
- The **Unified pricing management** module must be turned on. Learn more in [Turn on the Unified pricing management module for your system](upm-pricing-management-enable.md).

## Set up sales order line price attributes

Sales order line price attributes are the details that describe *how* a line is sold, such as its package type, warranty type, or fulfillment method. Unlike attributes that belong to a product or a customer, you choose these values line by line, so two lines for the same product in the same order can carry different values and therefore receive different prices. They're the input that both the price simulator and your pricing rules work from, so you must define them before you can simulate anything.

Define each attribute under **Product information management** and collect them into a single attribute group. Then select that attribute as the **Sales line attribute group** on the **Price attribute** tab of the **Pricing management parameters** page. Your system can have only one such group, and it can't be the same group that you use for sales order header attributes. The attributes in it are limited to the *Decimal*, *Integer*, *Text*, and *TrueFalse* data types.

For the full setup procedure, and for the rules about default values and data types, go to [Price attributes for products, customers, and orders](upm-price-attributes-setup.md).

## Make line attributes available to pricing rules

When you set up an attribute and select it as part of the sales line attribute group, you make its values available on order lines. To let a pricing rule *match* on those values, you must also add each attribute to a price attribute group that has the *Line* scope. A price attribute group defines the set of criteria that a rule can specify values for, so an attribute that isn't in the group can't be used as a condition.

Follow these steps to add your sales order line price attributes to a line-scope price attribute group:

1. Go to **Pricing management** > **Setup** > **Price attribute groups** > **Price attribute groups**.
1. Select an existing group that has its **Sales order matching scope** field set to *Line*, or create one. Learn more in [Price attribute groups](upm-price-attribute-groups.md).
1. On the **Attributes** FastTab, select **Add** on the toolbar.
1. In the **Add price attribute** dialog box, set the **Price attribute source** field to *SalesLine*. The list then shows only the attributes that come from sales order lines, including the ones in your sales line attribute group. Leave the **Table** field blank unless you want to narrow the list further.
1. Select the checkbox for each attribute that you want the pricing rules to match on, and then select **Update**.
1. Use **Move up** and **Move down** buttons on the toolbar to rank the attributes. The rank decides which rule wins when several rules match a line. Learn more in the [Price attribute ranks](upm-price-attribute-groups.md#price-attribute-ranks) section of the price attribute groups article.
1. On the Action Pane, select **Validation**. The group can be used in pricing rules only after it passes validation and the **Validated** option is set to *Yes*.

You can now configure trade agreement prices, margin price adjustments, and discounts that specify values for these attributes. Define several rules that cover different combinations of attribute values, so that the simulation has something to choose between. Learn more in [Pricing rules for discounts and margin price adjustments](upm-margin-discount-pricing-rules.md) and [Sales trade agreement prices](upm-sales-trade-agreement-prices.md).

## Simulate a price calculation

The price simulator builds a transaction but never saves it as a sales order, so you can experiment freely. Follow these steps to simulate a price calculation that depends on sales order line price attributes:

1. Go to **Pricing management** > **During-sales pricing** > **Price simulator** > **Price simulator**.
1. On the Action Pane, select **New**.
1. In the header, enter a **Name** and **Description** for the simulation.
1. On the **General** FastTab, select the customer, currency, site, and other details that define the scenario you want to test. These values determine which header-scope rules apply.
1. On the **Sales line** FastTab, add a line for each product in the simulated order, and set the quantity and unit for it.
1. Select a line. Then, on the **Sales line** FastTab toolbar, select **Retail attributes**.
1. For each attribute in the list pane, select the **Value** that matches the scenario you want to test. Then, on the Action Pane, select the back button to return to the price simulator.
1. Repeat the previous two steps for every line where the attribute values differ from the defaults.
1. Review the prices on the **Sales line** FastTab. The system recalculates them from your pricing rules and the attribute values that you selected.

Change an attribute value and check the prices again to confirm that the rule you expect is the one that applies.

> [!NOTE]
> Order lines inherit the default value of each attribute. Therefore, you only need to set a value explicitly on the lines where the scenario differs from the default. Learn more in [Price attributes for products, customers, and orders](upm-price-attributes-setup.md).

### Investigate why a price was calculated

A simulation shows more than the final price. The **Transaction summary** FastTab, above the lines, gives the totals for the whole simulated transaction. When you select a line on the **Sales line** FastTab, the FastTabs below it break down the calculation for that line, so you can see which rules the engine considered and which rules it applied:

- **Transaction summary** – Totals for the whole simulated transaction, including the total margin.
- **Applicable price groups** – The price groups that apply to the simulated transaction.
- **Applied periodic discounts** – The discounts that the engine applied.
- **Applied trade agreements** – The sales trade agreement prices that the engine applied, including the price attribute group and the attribute values that each one matched on.
- **Applied base prices** – The base prices that the engine found for the line, before adjustments and discounts.
- **Applied margin component price adjustments** – The margin component price adjustments that the engine applied.
- **Applied flex margin price adjustments** – The flexible margin price adjustments that the engine applied.
- **Applied sales agreements** – The sales agreements that the engine applied.
- **Pricing diagnostics** – Detailed output from the pricing engine for the simulated transaction. This FastTab appears only while the **Enable diagnostics** option is selected on the **General** FastTab.

The trade agreement, discount, and margin component price adjustment FastTabs each show the price attribute group and attribute details for the rule. These columns are the quickest way to confirm that a rule matched for the reason you intended, rather than by coincidence.

### Simulate header attributes as well

Line attributes are only one half of a pricing rule's criteria. Each rule combines one line-scope price attribute group with one header-scope group, so the sales order header attributes matter just as much to the result.

To set them for a simulation, select **Order header price attributes** on the Action Pane, and then assign a value to each attribute in the list. If your rules specify header attribute values and you leave these at their defaults, the rules you're testing might not match at all. Learn more in [Price attributes overview](upm-price-attributes-overview.md).

## Calculate prices on sales quotations

Sales quotations use the same price attributes and pricing rules, so a quotation shows the customer the same price that the simulator predicts. Follow these steps to assign line attribute values to a quotation and calculate its prices:

1. Go to **Sales and marketing** > **Sales quotations** > **All quotations**.
1. Select an existing quotation, or create one. In the **Create quotation** dialog box for a new quotation, or on the **Sales quotation header** FastTab for an existing one, set the header values that match your scenario.
1. On the **Lines** FastTab, add the lines that you want to include in the quotation.
1. Select a line. Then, on the **Lines** FastTab toolbar, select **Retail attributes**.
1. For each attribute in the list pane, select the **Value** that applies to the line. Then, on the Action Pane, select the back button to return to the quotation.
1. Repeat the previous two steps for each line.
1. On the Action Pane, open the **Quotation** tab and, from the **Calculate** group, select **Recalculate**. The system calculates new prices from your attribute values and pricing rules.

## Related information

- [Price attributes overview](upm-price-attributes-overview.md)
- [Price attributes for products, customers, and orders](upm-price-attributes-setup.md)
- [Price attribute groups](upm-price-attribute-groups.md)
- [Pricing rules for discounts and margin price adjustments](upm-margin-discount-pricing-rules.md)
- [Sales trade agreement prices](upm-sales-trade-agreement-prices.md)
