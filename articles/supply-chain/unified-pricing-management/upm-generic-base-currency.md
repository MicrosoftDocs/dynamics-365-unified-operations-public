---
title: Manage pricing rules using a generic base currency
description: Learn how to define pricing rules in a single generic base currency and let Unified pricing management convert prices to each transaction currency.
author: sherry-zheng
ms.author: chuzheng
ms.topic: how-to
ms.date: 09/21/2026
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form: GUPParameters, PriceDiscAdm, RetailPeriodicDiscount
ai-usage: ai-assisted
---

# Manage pricing rules using a generic base currency

[!INCLUDE [banner](../includes/banner.md)]

Global enterprises and multi-entity organizations often sell the same products in many transaction currencies. Without a generic base currency, you must duplicate every trade agreement price, price adjustment, and discount for each of those currencies. Unified pricing management lets you define each rule once, in a currency that you nominate as your *generic currency*, and then converts the result to the transaction currency when a price is calculated. This approach reduces duplication and keeps prices anchored to a single reference currency across markets.

## How generic currency pricing works

After you turn on generic currency, the currency code becomes a matching criterion for pricing rules. When the pricing engine evaluates an order, it considers only two kinds of rules:

- Rules where the **Currency** field matches the transaction currency.
- Rules that are defined in the generic currency and have the **Include generic currency** setting turned on.

The pricing engine ignores rules that are defined in any other currency.

Generic-currency rules don't act as a fallback. They're evaluated together with the rules that are defined in the transaction currency, and they compete and compound according to your price structure in the usual way. For example, if the generic currency is euros (EUR) and a sales order uses US dollars (USD), both a USD trade agreement price and a generic EUR trade agreement price are candidates for the base price. The pricing engine converts the EUR price to USD and then applies your concurrency rules to determine which price wins.

Conversion uses the exchange rate type that you select on the **Pricing management parameters** page, and the exchange rate that applies on the pricing date. The **Date type** field on the **General** tab of the **Pricing management parameters** page controls which date is used. Therefore, a quotation that's priced for a past date uses the exchange rate for that date, not today's rate. Learn more in [Pricing rules for discounts and margin price adjustments](upm-margin-discount-pricing-rules.md).

If you turn on smart rounding for currency conversion, the converted amount is then rounded according to the smart rounding rules that are set up for the transaction currency. In other words, rounding is applied to the converted price, not to the price in the generic currency.

Generic currency applies to sales trade agreement prices, margin component price adjustments, and all discount types, including shipping threshold discounts. It applies to prices that are calculated for sales orders, sales quotations, and point of sale (POS) transactions.

## Prerequisites

To use the features that are described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management or Dynamics 365 Commerce version 10.0.47 or later.
- The **Unified pricing management** module must be turned on. Learn more in [Turn on the Unified pricing management module for your system](upm-pricing-management-enable.md).

## Choose the generic currency and conversion options

Before you can flag any pricing rule as a generic-currency rule, you must nominate the currency to use and specify how the system converts prices out of it. Follow these steps.

1. Go to **Pricing management** > **Setup** > **Pricing management parameters**.
1. Open the **General** tab.
1. Expand the **Generic currency and smart rounding** FastTab and set the following fields:

    - **Enable generic currency** – Turn on this setting to make the currency code a matching criterion for pricing rules, as described in the [How generic currency pricing works](#how-generic-currency-pricing-works) section. Until you turn it on, the **Include generic currency** setting is hidden on every pricing rule page.
    - **Generic currency** – Select the currency to define your centralized prices in. This is the currency that you want to use for the pricing rules that apply across markets.
    - **Exchange rate type** – Select the exchange rate type that the system uses to convert generic-currency prices into each transaction currency. Exchange rate types let you keep several sets of rates (for example, a daily rate and a budget rate) and choose which set applies to pricing.
    - **Apply smart rounding after currency conversion** – Turn on this setting if converted prices should be rounded according to your smart rounding rules. Leave it turned off to use the converted amount as-is.

1. Select **Save**.

> [!NOTE]
> The **Generic currency** and **Exchange rate type** fields must be set together. If you set one of them but leave the other blank, the system reports the following message: *You must select both Generic currency and Exchange rate type, or none of them.* These two fields are shared with the **Accounts receivable parameters** page, so a value that you set in one place also appears in the other.

## Set up exchange rates

The pricing engine can convert a generic-currency price only if an exchange rate exists for the currency pair and the exchange rate type that you selected. Therefore, set up a rate between the generic currency and every transaction currency that you sell in.

1. Go to **General ledger** > **Currencies** > **Currency exchange rates**.
1. Select the exchange rate type that you chose on the **Pricing management parameters** page.
1. For each transaction currency that you support, add a currency pair that converts from the generic currency, and enter the rates that apply for each period.

## Define pricing rules in the generic currency

Pricing rules aren't automatically treated as generic-currency rules. You must set the rule's currency to the generic currency and then select **Include generic currency** on the rule itself. You do this while you create or edit the rule, before you activate or post it.

### Sales trade agreement prices

For trade agreement prices, set the option on the journal lines that you post to create the agreements. Follow these steps to define a trade agreement price in the generic currency.

1. Go to **Pricing management** > **During-sales pricing** > **Sales trade agreement price** > **Trade agreement journals**.
1. Create a journal, or select an existing one, and then select **Lines**.
1. Add a line, and set the **Currency** field to your generic currency. The **Include generic currency** checkbox becomes available only when the line currency matches the generic currency that you define on the **Pricing management parameters** page. For lines in any other currency, the checkbox stays unavailable.
1. Select the **Include generic currency** checkbox. The **Currency** field then becomes read-only for that line.
1. Finish defining the line, and then post the journal in the usual way. Learn more in [Sales trade agreement prices](upm-sales-trade-agreement-prices.md).

The setting carries over to the resulting agreement, where you can review it in the **Include generic currency** column on the active trade agreement pages.

### Discounts and margin price adjustments

For margin component price adjustments and all discount types, set the option on the rule record itself. Follow these steps.

1. Open the page for the type of pricing rule that you want to create, as described in [Pricing rules for discounts and margin price adjustments](upm-margin-discount-pricing-rules.md).
1. Create the rule, or select an existing disabled rule.
1. On the **General** FastTab, set the **Currency** field to your generic currency.
1. Select the **Include generic currency** checkbox, which appears directly below the **Currency** field.
1. Finish setting up the rule, and then set its status to *Enabled*.

## Related information

- [Unified pricing management module overview](upm-pricing-management-overview.md)
- [Turn on the Unified pricing management module for your system](upm-pricing-management-enable.md)
- [Sales trade agreement prices](upm-sales-trade-agreement-prices.md)
- [Pricing rules for discounts and margin price adjustments](upm-margin-discount-pricing-rules.md)
- [Discount types](upm-discounts.md)
