---
title: Pricing rules for discounts and margin price adjustments
description: This article explains how to configure all types of pricing rules, including margin component price adjustments, simple discounts, quantity discounts, mix-and-match discounts, threshold discounts and free-item discounts.
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form: RetailPeriodicDiscount, RetailMixAndMatchLineGroups, GUPPriceAdjustPriceAttributeGroupEdit, GUPDiscountPriceComponentGroupExclusionList, GUPFundList, RetailMixAndMatchLineGroupSetup
ms.topic: how-to
ms.date: 04/03/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Pricing rules for discounts and margin price adjustments

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This article explains how to configure pricing rules for component price adjustments, simple discounts, quantity discounts, mix-and-match discounts, threshold discounts and free-item discounts.

## Create and manage your pricing rules

1. Depending on which type of rule you want to make, go to one of the following pages:
    - To view, edit and create margin price adjustments, go to **Pricing management \> During-sales pricing \> Price adjustments \> Margin component price adjustments**
    - To view, edit and create all types of discounts (including all the other discount types in this list), go to **Pricing management \> During-sales pricing \> Discounts \> All discounts**
    - To view, edit and create simple discounts only, go to **Pricing management \> During-sales pricing \> Discounts \> Discounts**
    - To view, edit and create quantity discounts only, go to **Pricing management \> During-sales pricing \> Discounts \> Quantity discounts**
    - To view, edit and create mix-and-match discounts only, go to **Pricing management \> During-sales pricing \> Discounts \> Mix and match discounts**
    - To view, edit and create threshold discounts only, go to **Pricing management \> During-sales pricing \> Discounts \> Threshold discounts**
    - To view, edit and create free-item discounts only, go to **Pricing management \> During-sales pricing \> Discounts \> Free item**
1. Do one of the following steps:
    - To add a new record, on the Action Pane, open the **New** menu and then choose which type of record you want to create.
    - To create a copy of an existing record, select it on the list pane and then select **Copy** on the Action Pane.
    - To edit an existing record, select it on the list pane and then set **Status** to *Disabled* on the **General** FastTab. (All rule records are read-only while enabled)
    - To delete a record, select it on the list pane and then select **Delete** on the Action Pane.
1. Make the following settings in the header of your new or selected rule record:
    - **Discount** or **Margin component adjustment** – Enter a unique identifier for this rule.
    - **Name** – Enter a common name for the rule.
    - **Discount type** – If you're working with a discount rule, then the type of discount is shown here (read-only). This field isn't shown for margin price components.
    - **Publish status** – Initially set to *Draft*. Once you complete the record, you can activate the rule. <!--KFM: How do we activate it? What other values/effects might this have? It seems like this never changes. -->

1. Continue setting up your pricing rule as described in the remaining sections of this article. Many settings are shared by all types of pricing rules, but some are specific to margin component price adjustment, all discounts, or specific types of discounts.

<!-- KFM: Add a step for enabling the rule when done? -->

## Make settings on the General FastTab

The **General** FastTab provides basic settings for your pricing rule. Make the settings described in the following subsections, depending on which type of pricing rule you are setting up.

### General settings that apply to both margin price adjustments and discounts

Make the following settings on the **General** settings tab for all all types of pricing rules.

- **Status** – Set to *Enabled* or *Disabled*. Only *Enabled* records are available for making calculations. New records are set to *Disabled* and can only be enabled after you have finished making all the required settings. All settings are read-only for enabled rules, so you must disable a rule before you can edit it. <!-- KFM: What is the effect of this setting? For coupons, this is always disabled, what does that mean? -->
- **Currency** – Select the currency for which this rule applies. <!--KFM: Does this mean that this record will only apply to orders or order lines that use this currency? -->
- **Price component** – This read-only field shows which type of pricing rule this is (*Discounts* or *Margin component*).
- **Price component code** – Select the [price component code](price-component-code.md) that this rule applies to. Only existing price component codes of the applicable type are listed.
- **Header price attribute group type** – <!-- KFM: Description needed -->
- **Price attribute group** – <!-- KFM: Description needed -->

### General settings that apply to margin price adjustments only

Make the following settings on the **General** settings tab if you are setting up a pricing rule for a margin component price adjustment.

- **Concurrency model** – This read-only field tells you how the system will handle situations where more than one margin component price adjust applies (concurrence). Its value, *Price component code rank*, means that the system will choose a price adjustment based on the price attribute combination rank. <!--KFM: This doesn't seem quite right. Is it actually about finding the *order* in which adjustments are applied? -->
- **Quantity tiers** – Set to *Yes* to enable the Quantity tiers FastTab, which lets you establish price adjustments that vary based on the sales order line quantity.

> [!NOTE]
> Margin component price adjustment quantity tier is different from Quantity discounts. Quantity discounts tiers are based on the item quantity per order. Margin component price adjustment tiers are based on the item quantity per line.

### General settings that apply to discounts only

Make the following settings on the **General** settings tab if you are setting up a pricing rule for a discount. Not all types of discounts include all of these settings.

- **Discount account** – If you'd like to post the discount amount for this discount record to a separate general ledger account, then specify that account here. This setting overrides the similar setting available for price structures (**Price component code setup** or **Price tree**). For more information, see [Price component posting](price-component-posting.md).
- **Discount concurrency mode** – Choose how the system should handle situations where more than one discount applies for the same price component code within a price structure (concurrence). Choose one of the following values:
    - *Exclusive* – The discount is an exclusive discount, which means it can't be combined with other discounts. If there are multiple exclusive discounts, the price engine will only apply the one with the highest discount. <!--KFM: If there are both exclusive and non-exclusive discounts, does the exclusive always win even if a non-exclusive has a higher discount, in which case might multiple non-exclusive discounts then apply? -->
    - *Best price* – Discounts of this concurrency mode will compete for the highest discount (lowest price).
    - *Compounded* – The discount will be combined with other discounts according to the pricing sequence established in the price structure. Settings on the **Pricing management parameters** page control whether the compounded discount calculation basis is the original price or the compounded amount. <!--KFM: Link to topic where this setting is described. -->
    - *Always apply* – The discount will always be applied. Always-apply discounts are applied last and therefore represent represent universal discounts that apply to all.
    - *Price attribute combination rank* – Discounts with this concurrency mode don't compete based on price but on which one has the highest price attribute combination rank. If multiple discounts have the same highest rank, they all apply to the sales order.
- **Coupon code required** – Set to *Yes* if a coupon code is required to qualify for the discount. The discount must be linked to the coupon <!--KFM: How do we do this? -->. When ordering, the discount will only be triggered if a valid coupon code is entered together with the order. When this option is enabled, the **Status**, **Effective date** and **Expiration date** fields are made inactive. The setting will be pending on the coupon configuration <!-- KFM: Do we mean that the  **Status**, **Effective date** and **Expiration date** settings now come from the coupon setup? -->. To set up your coupons, go to **Pricing management \> During-sales pricing \> Coupons**. <!--KFM: It looks like we need a bar code too; set up on **Pricing management parameters** page? We probably need a full topic dedicated to setting up coupons, add a link here when available. -->
- **Claimable** – Set this to *Yes* to make the discount claimable, which means that the discount is sponsored by a vendors and can therefore be charged back to the vendor. <!-- KFM: More details of the discount claim will be covered by the Discount claim documents. Add link when available. -->
- **Discount claim group** – If you set **Claimable** to *Yes*, then select the applicable claim group here.  <!-- KFM: What is a claim group? -->
- **Claim offset posting** – If you set **Claimable** to *Yes*, then select the offset account that you want to post the claim to here.
- **Max criteria type** – If a maxim discount per order applies, then select the type of limit you want to apply. Choose one of the following values:
    - *Amount* – <!-- KFM: Description needed -->
    - *Quantity* – <!-- KFM: Description needed -->
- **Max** – If a maxim discount per order applies, then select the value of the limit here.
- **Max quantity unit** – If a maxim discount per order applies, and **Max criteria type** is *Quantity*, then select the unit that applies for the value selected in the **Max** field.

## Make settings on the Details FastTab

The **Details** FastTab lets you enter more information about your pricing rule, and also provides extra information about it. You can enter and/or inspect the following details here.

- **Description** – Enter a description of the pricing rule. <!-- KFM: Where is this used, just here? -->
- **Disclaimer** – Enter a disclaimer for the pricing rule. <!-- KFM: Where is this used, just here? -->
- **Text for fiscal receipt** – Enter a text to be displayed on the related fiscal receipt. <!-- KFM: What is this? Can we give a link or little more info? -->
- **Header price attribute details** – This read-only field summarizes the header price attribute values for this pricing rule (available by selecting **Header price attribute group** on the Action Pane). For more information, see [Set up header price attribute values](#header-attributes).

## Make settings on the Price/discount FastTab

The **Price/discount** FastTab is only provided for simple, threshold, and mix-and-match discounts. The settings here combine with those on the **Lines** FastTab to establish the discount values for various combinations of customers and items.

### Price/discount settings for simple discounts

If you're setting up a simple discount, make the following settings on the **Price/discount** FastTab:

- **Percentage off** – Enter the default discount percentage to new lines added to the **Lines** FastTab. You can change the percentage, or change the percentage off to an amount off, for each line as you add it to **Lines** Fast Tab, as described later in this article.
- **Quantity limit** – Enter the maximum order quantity for which this discount applies. This limit applies to all lines on the **Lines** FastTab. You can't edit this separately for each line. This value is repeated for each line on the **Lines** FastTab, but you can only edit the value here. All existing lines will update if you change this value.

### Price/discount settings for mix-and-match discounts

If you're setting up a mix-and-match discount, make the following settings on the **Price/discount** FastTab:

- **Percentage off** – Enter the default discount percentage to new lines added to the **Lines** FastTab. You can change the percentage, or change the percentage off to an amount off, for each line as you add it to **Lines** Fast Tab, as described later in this article.
- **Quantity limit** – Enter the maximum order quantity for which this discount applies. This limit applies to all lines on the **Lines** FastTab. You can't edit this separately for each line. This value is repeated for each line on the **Lines** FastTab, but you can only edit the value here. All existing lines will update if you change this value.
- **Calculation type** – Select which type of calculation the current pricing rule will apply. The selection you make here will affect which other fields of this FastTab will be active. Select one of the following options:
    - *Deal price* – Specify a specific final price rather than a calculated discount. After selecting this option, enter the price in the **Deal price** field.
    - *Percentage off* – Calculate the discount as a percentage of the item price. After selecting this option, enter the percentage in the **Percentage off** field. For example, suppose the usual price of item A is 40.00, the usual price of item B is 60.00, and a mix-and-match discount of 30 percent applies to these items. Then, if a customer buys item A and item B together, the cost is 70.00 instead of 100.00.
    - *Amount off* – Define the discount as a fixed value. After selecting this option, enter the discount in the **Amount off** field.
    - *Least expensive* – <!-- KFM: A general description of what this setting means is needed here. --> After selecting this option, enter the discount price in the **Deal price**, **Percentage off**, or **Amount off** field (depending on which method you want to use to calculate the price). Then, in the **Number of least expensive lines** field, enter the number of least-expensive items that you want to apply the discount to. Finally, set **Multiple occurrences mode** to one of the following values:
        - *Favor customer* – <!-- KFM: Description needed. -->
        - *Favor retailer* – <!-- KFM: Description needed. -->
    - *Line spec* – Use the discount specified for each line on the **Lines** FastTab.
- **Count non-discountable products** – Set to *Yes* to count non-discountable items towards the quantity. <!-- KFM: What quantity and for what purpose? What if we set to No? -->
- **Generate bundle ID** – <!-- KFM: Description needed. -->

> [!NOTE]
> For mix-and-match, least-expensive discounts, the number of least-expensive products must be more than one and less than the number of products. <!-- KFM: This isn't clear, please revise. Is this referring to the **Number of products needed** setting? -->

### Price/discount settings for threshold discounts

If you're setting up a threshold discount, then make the following setting on **Price/discount** FastTab:

- **Count non-discountable items toward threshold** – <!-- KFM: Description needed. -->

## Make settings on the Free item setup FastTab

The **Free item setup** FastTab is only provided for free item discounts. Make the following settings here:

- **Criteria type** – <!-- KFM: Description needed. -->
    - *Quantity* – <!-- KFM: Description needed. -->
    - *Amount* – <!-- KFM: Description needed. -->
- **Calculation type** – <!-- KFM: Description needed. -->
    - *Stepped* – <!-- KFM: Description needed. -->
    - *Normal* – <!-- KFM: Description needed. -->
- **Repeatable** – <!-- KFM: Description needed. -->
    - *No* – <!-- KFM: Description needed. -->
    - *Repeatable by header* – <!-- KFM: Description needed. -->
    - *Repeatable by line* – <!-- KFM: Description needed. -->

To finish setting up the free item discount, use the grid on the **Free item setup** FastTab to <!-- KFM: Description needed. -->. Use the toolbar buttons to add or remove lines in the grid. For each line, make the following settings:

- **Required header quantity/amount** – <!-- KFM: Description needed. -->
- **Supplementary quantity** – <!-- KFM: Description needed. -->

## Make settings on the Quantity discount configuration FastTab

The **Quantity discount configuration** FastTab is only provided for quantity discounts. Use it to set up the discounts that apply for each quantity threshold that you set up.

### Quantity discount settings

On the **Quantity discount** FastTab, make the following settings, which affect how the quantity tiers will work: <!-- KFM: I've assumed these settings apply to the whole table, not to each individual row. Correct? -->

- **Calculation type** – Choose how the discount will be calculated based on the table values. Choose one of the following values:
    - *Percentage off* – The discount will be calculated as a percentage of the price.
    - *Amount off* – A specific value will be subtracted from the price.
    - *Unit price* – A new, specific unit price will be applied. <!-- KFM: How is this combine with other discounts and adjustments? -->
- **Interval** – This setting only applies when the **Calculation type** is *Amount off*. Set it to *Yes* to use a stepped calculation for each quantity tier. See the next section for an example of how this setting affects the discount calculation. <!-- KFM: What does this mean? More info needed. What happens when this is *No*? -->

The table on this FastTab establishes a set of quantity tiers and the discount that applies for each of them. <!-- KFM: How do these combine? Does only one row apply, or does each lower value row also apply? --> Use the buttons on the FastTab toolbar to add and remove rows from the table. For each row, make the following settings:

- **Minimum quantity** – Enter the minimum quantity of an item that a customer must order to get the discount specified on the line.
- **Value** – Enter the value of the discount for the line (based on the selected **Calculation type**).

### Example of how the Interval setting affects the discount calculation

<!-- KFM: Introduce this section with a general description of what this setting means. -->

<!-- KFM: Introduce the following table. What is this, how does it affect this example? -->

| Attribute group | Attributes | Value | Include |
|---|---|---|---|
| Header price attribute group | Customer 10 | 10 | US-020, US-021 |
| Line price attribute group | Interior Upholstery | Package B | EV002, EV003 |

You have a quantity discount with the following settings in the table on the **Quantity discount** FastTab.

| Minimum Quantity | Value |
|---|---|
| 1 | 2 |
| 10 | 3 |
| 20 | 4 |

When **Interval** is set to *No*, the quantity discount for an example order is calculated as shown in the following table. <!-- KFM: We should explain more about where these numbers are coming from. I don't get it. -->

| Sales order line | Item | Quantity | Discount per unit | Discount for line |
|---|---|---|---|---|
| Line 1 | EV003 | 10 | $3 | $30 |
| Line 2 | EV002 | 2 | $3 | $6 |

When **Interval** is set to *Yes*, the quantity discount for an example order is calculated as shown in the following table. <!-- KFM: We should explain more about where these numbers are coming from. I don't get it. -->

| Sales order line | Item | Quantity | Discount per unit | Discount for line |
|---|---|---|---|---|
| Line 1 | EV003 | 10 | $2.25 | $22.50 |
| Line 2 | EV002 | 2 | $2.25 | $4.50 |

The calculation logic is shown in the following table. <!-- KFM: The meaning of this table isn't clear. More explanation needed. -->

| Tier | Quantity | Discount per unit | Discount |
|---|---|---|---|
| &lt;10 | 9 | $2 | $18 |
| &lt;20 | 3 | $3 | $9 |

## View information on the Calculation FastTab

The **Calculation** FastTab provides information about how the **Price component code** selected for the pricing rule is set up within your [pricing structure](price-structure-overview.md). <!-- KFM: What if there are multiple structures -->

The following information is shown here:

- **Pricing sequence** – This read-only field displays the position of the selected **Price component code** within your pricing structure.
- **Compound** – This read-only field is only shown for margin price adjustments (not for discounts). It shows whether the selected **Price component code** is set to make compound calculations within your pricing structure.

## Make settings on the Validation period FastTab

Use the settings on the **Validation period** FastTab to control when the pricing rule will apply.  The following conditions apply:

- The date range is defined at the header level. <!-- KFM: Please clarify. -->
- The date used when validating a pricing rule is based on the **Date type** setting on the **General** tab of the  **Pricing management parameters** page,. You can set the **Date type** to *Today*, *Requested ship date*, *Requested receipt date*, or *Created date*. <!-- KFM: Is this for margin price adjustments only, or also for discounts? We should give a link. Currently, this is explained in [Sales trade agreement prices](sales-trade-agreement-prices.md), but should maybe be moved. -->

You can choose to set up the validation period using either standard or advanced settings.

### Set up standard date validation rules

To set up the validation period using the standard validation rules, follow these steps:

1. Set **Date validation type** to *Standard* to enable the fields needed for setting up standard date validation.
1. Make the following settings:
    - **Effective date** – Select the first date on which the pricing rule should apply.
    - **Expiration date** – Select the last date on which the pricing rule should apply.

### Set up advanced date validation rules

Advanced validation rules let you set the validation period using a discount period record rather than entering simple start and end dates.

Discount period records let you set up detailed date and time limits, which can include a start date and time, end date and time, plus specific times of day for each day of the week. You can set up discount period records by going to **Retail and Commerce \> Pricing and discounts \> Discount periods**.

To set up the validation period using the advanced validation rules, follow these steps:

1. Set **Date validation type** to *Advanced* to enable the fields needed for setting up advanced date validation.
1. In the **Discount period number** field, select the discount period record that defines the validation period you want to use.
1. The read-only **Description**, **Start date**, and **End date** fields update to show values from your selected discount period record.

## <a name="items-lines"></a>Make settings on the Lines and Line details FastTabs

Use the **Lines** FastTab to control which discounts and margin price adjustments will apply for which items. All the lines in a pricing rule apply to the same collection of customers, which you can configure using the [**Header price attribute group**](#header-attributes) settings.

### <a name="add-line"></a>Add a line and configure the set of items that it will apply for

Each line assigns calculation rules that apply for a specified collection of items. When you add a line, you'll use a dialog to set up the items it affects and then add the line to the grid. Later, you'll set up the calculation rules for it using the columns in the grid. Follow these steps to add a line.

1. From the **Lines** FastTab toolbar, select **New**.
1. The **Edit price attributes** dialog opens. This dialog lets you set up the logic for finding the items the current line will apply for.
1. Expand the **Header price attribute group** FastTab to see the logic set up for selecting the customers for whom the current pricing rule applies. These settings apply for all lines in the current pricing rule and are read-only here (you can change them using the [**Header price attribute group**](#header-attributes) settings, which are available from the Action Pane).
1. From the **Price attribute group combination** drop-down list, select the combination of price attributes that you will use to define the items for the current line. These combinations are the ones defined for the [price component code](price-component-code.md) selected for the current pricing rule, but only the right side (the [line price attribute group](price-attribute-groups.md) name) of the combination name is relevant because the header attributes are common for all lines for the pricing rule (as mentioned in the previous step). Choose the combination where the right-side of the name matches the way you want to define the collection of items that the line applies for.
1. If your selected **Price attribute group combination** considers item (line) attribute values (rather than applying to *all* items), then the **Line price attribute group** FastTab is available. In this case, for each row on the **Line price attribute group** FastTab, enter or select one or more values in the **Value** column to establish the rules for selecting items. The collection of attributes shown here come from the **Price attribute group combination** you selected. The following rules apply:
    - All rows are combined using a logical AND operator, which means that only those items that have matching values for *all* rows will be included.
    - If you want to create one or more rows that include multiple values, set **Enable multiple selections** to *Yes*. This will allow you to add a comma-separated list of values in the **Value** column for each row. These values are combined using an OR operator, which means that the row will find items that match *any* of the values in the list.
    - You can specify values to exclude by adding an "!" before the value. For example, to find all items other than *A0001*, you could set the attribute with **Attribute** *Item number* to have **Value** *!A0001*. You can add the exclusion prefix to the values of any row automatically by selecting it and then selecting the **Exclude values in selected lines** button.
1. The **Preview matching results (Products)** FastTab shows a preview of items that match the conditions you've set up so far.
    - If the list includes any items that you'd like to exclude, select the target rows and select **Exclude** from the toolbar.
    - The **Line type** column indicates which items you have chosen to exclude using the toolbar button.
    - To re-include an excluded item, select it and then select **Include** from the toolbar.
    - To view, exclude, and/or re-include specific item variants, select **All variants** from the toolbar. While viewing the variants, you can select **Product master** from the toolbar to go back to the standard item list.
1. Select **OK** to add the new line to the **Lines** FastTab grid.
1. Set up the calculation rules for the new line using the columns in the grid, as described in the next section.

If you ever need to return to the **Edit price attributes** dialog to change the the set of items a line applies to, select the line and then select **Edit line price attribute** from the toolbar.

### Set line values to establish calculation rules and further refine the item selection

The settings for each line on the **Lines** FastTab vary based on which kind of pricing rule you are working with. The following settings and information may be available here:

- **Line group type** – Shows whether the line applies to a specific *Group* of items or to *All* items.
- **Line price attribute group** – If the **Line group type** is *Group*, then this column shows the name of the selected [line price attribute group](price-attribute-groups.md).
- **Price attribute detail** – Summarizes the settings made for this line using the **[Edit price attributes](#add-line)** dialog. To change these settings, select **Edit price attribute** from the FastTab toolbar.
- **Combination rank** – Shows the combination rank generated for the **Price attribute group combination** selected for this line using the **[Edit price attributes](#add-line)** dialog. Rankings let the system decide which pricing rule to use when an order or order line qualifies for more than one rule. See also [Price component codes](price-component-code.md).
- **Free item group** – <!-- KFM: Description needed -->
- **Mandatory** – <!-- KFM: Description needed -->
- **Required line quantity** – For free-item discounts using a **Criteria type** of *Quantity*, enter the minimum quantity that must be ordered to quality for the discount.
- **Required line amount** – For free-item discounts using a **Criteria type** of *Amount*, enter the minimum amount that must be ordered to quality for the discount.
- **Name** – <!-- KFM: Description needed -->
- **Unit** – <!-- KFM: Description needed -->
- **Allow unit conversion** – Select this check box to convert the selling unit to the unit used for the pricing rule when needed.
- **Line type** – <!-- KFM: Description needed --> Select one of the following values:
    - *Include* – <!-- KFM: Description needed -->
    - *Exclude* – <!-- KFM: Description needed -->
- **Calculation type** – Choose how the discount or price adjustment for the current line should be calculated. Select one of the following values:
    - *Percentage off* or *Percent* – Calculate the discount or price adjustment value as a percentage of the price.
    - *Amount off* of *Amount* – Calculate the discount or price adjustment using a fixed value added or subtracted from the price.
    - *Unit price* – Set a new, fixed unit price.
- **Percent** or **Percentage off** – If you are using a percentage-based **Calculation type**, then enter the percentage here.
- **Amount** or **Amount off** – If you are using an amount-based **Calculation type**, then enter the amount here.
- **Unit price** – If you are using the *Unit price* **Calculation type**, enter the new unit price here.
- **Quantity limit** – Shows the maximum order quantity for which this discount applies. This limit applies to all lines on the **Lines** FastTab. You can't edit this separately for each line, but you can edit it for all lines at once using the **Quantity limit** field on the **Price/discount** FastTab.
- **Number of products needed** – The number of items that the customer needs to buy in this line group before the discount applies. This is read-only for mix-and-match discounts, which take this value from the group selected in the **Line group** column.
- **Line group** – If you are setting up a mix-and-match discount, then select the line group that applies to the line here. Before you can make a selection here, you must first set up your line groups, add them to the current pricing rule, and configure them with a color and item threshold, as described in [Mix and match discounts](discounts.md#mix-match). The line will then be highlighted using the color chosen for the selected line group (if any), and the **Number of products needed** will update to match the selected line group configuration.
- *Other dimensions* – Columns showing item, storage, and tracking dimensions may also be included in the grid (such as **Color**, **Warehouse**, **Serial number**, and so on). To choose which dimensions are shown, select **Display dimensions** from the toolbar. Enter values in these columns to restrict the line to only apply to items that match your specified dimension values.

### Make settings on the Lines details FastTab

If you'd like to add more information about a line on the **Lines** FastTab, then select the relevant line and enter your note in the **Description** field of the **Line details** FastTab.

## <a name="header-attributes"></a>Set up header price attribute values

Use header price attributes to control which customers the current pricing rule applies to. These limits apply to all lines and items the rule applies for (see also [Make settings on the Lines and Line details FastTabs](#items-lines)). Follow these step to set the header price attributes for the current pricing rule:

1. Before you can set header price attributes, you must already have assigned a **Price component code** on the General FastTab.
1. From the Action Pane, select **Header price attribute** group.
1. The **Edit price attributes** dialog opens. This dialog lets you set up the logic for finding the customers the current pricing rule will apply for.
1. Expand the **Header price attribute group** FastTab. Review and set the following settings:
    - **Scope of price attributes** – This read-only field tells you which type of attributes your settings here will apply to. It will always show *Header*. <!-- KFM: Please confirm -->
    - **Group type** – Choose the type of customer selection you want to set up. The options here will depend on which price attribute combinations are available for your selected [price component code](price-component-code.md). The following options may appear here:
        - *Group* – The dialog will provide you with a group of header attributes for which you can assign values to limit the set of customers to whom this pricing rule will apply.
        - *All* – This pricing rule will apply for all customers. If you choose this option, then no further steps are needed, so you can skip the rest of this procedure and just select **OK** to apply your settings.
    - **Price attribute group** – If **Group type** is *All*, then select a price attribute group here. The available options will depend on the attribute groups enabled for your selected [price component code](price-component-code.md). The choice you make here will affect the set of attributes you'll be able to work with on this dialog.
1. If you selected a **Price attribute group**, then the attributes from your selected group are now shown on the **Header price attribute group** FastTab. For each row, enter or select one or more values in the **Value** column to establish the rules for selecting customers. The following rules apply:
    - All rows are combined using a logical AND operator, which means that only those customers that have matching values for *all* rows will be included.
    - If you want to create one or more rows that include multiple values, set **Enable multiple selections** to *Yes*. This will allow you to add a comma-separated list of values in the **Value** column for each row. These values are combined using an OR operator, which means that the row will find customers that match *any* of the values in the list.
    - You can specify values to exclude by adding an "!" before the value. For example, to find all customers other than *US-001*, you could set the attribute with **Attribute** *Customer account* to have **Value** *!US-001*. You can add the exclusion prefix to the values of any row automatically by selecting it and then selecting the **Exclude values in selected lines** button.
1. The **Preview matching results (Customers)** FastTab shows a preview of customers that match the conditions you've set up so far.
    - If the list includes any customers that you'd like to exclude, select the target rows and select **Exclude** from the toolbar.
    - The **Line type** column indicates which customers you have chosen to exclude using the toolbar button.
    - To re-include an excluded customer, select it and then select **Include** from the toolbar.
1. Select **OK** to save your settings and close the dialog.

## Set up Mix and match line groups

If you are working with a mix-and-match discount pricing rule, then select **Mix and match line groups** to choose which mix-and-match line groups can be assigned on **Lines** FastTab, and set the number of products needed from each group to quality for the discount. For details about how to set up your mix-and-match line groups, see [Mix and match discounts](discounts.md#mix-match).

## Set up a discount exclusion list

<!--KFM: Description needed. -->

## Set up a fund list

<!--KFM: Description needed. -->
