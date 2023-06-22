---
title: Pricing rules for discounts and margin price adjustments
description: This article explains how to configure pricing rules for margin component price adjustments, simple discounts, quantity discounts, mix-and-match discounts, threshold discounts, and free-item discounts.
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

This article explains how to configure pricing rules for margin component price adjustments, simple discounts, quantity discounts, mix-and-match discounts, threshold discounts, and free-item discounts.

## Create and manage pricing rules

1. Follow one of these steps, depending on the type of pricing rule that you want to work with:

    - To view, edit, and create margin price adjustments, go to **Pricing management \> During-sales pricing \> Price adjustments \> Margin component price adjustments**.
    - To view, edit, and create all types of discounts (including all the other discount types in this list), go to **Pricing management \> During-sales pricing \> Discounts \> All discounts**.
    - To view, edit, and create simple discounts only, go to **Pricing management \> During-sales pricing \> Discounts \> Discounts**.
    - To view, edit, and create quantity discounts only, go to **Pricing management \> During-sales pricing \> Discounts \> Quantity discounts**.
    - To view, edit, and create mix-and-match discounts only, go to **Pricing management \> During-sales pricing \> Discounts \> Mix and match discounts**.
    - To view, edit, and create threshold discounts only, go to **Pricing management \> During-sales pricing \> Discounts \> Threshold discounts**.
    - To view, edit, and create free-item discounts only, go to **Pricing management \> During-sales pricing \> Discounts \> Free item**.

1. Follow one of these steps:

    - To add a new record, select **New** on the Action Pane, and then, on the menu, select the type of record that you want to create.
    - To create a copy of an existing record, select it in the list pane, and then select **Copy** on the Action Pane.
    - To edit an existing record, select it in the list pane, and then, on the **General** FastTab, set the **Status** field to *Disabled*. (All rule records are read-only while they're enabled.)
    - To delete a record, select it in the list pane, and then select **Delete** on the Action Pane.

1. On the header of the new or selected rule record, set the following fields:

    - **Discount** or **Margin component adjustment** – Enter a unique identifier for the rule.
    - **Name** – Enter a common name for the rule.
    - **Discount type** – If you're working with a discount rule, this field shows the type of discount and is read-only. This field isn't shown for margin price components.
    - **Publish status** – This field is initially set to *Draft*. After you complete the record, you can activate the rule.

1. Continue to set up the pricing rule as described in the remaining sections of this article. Many settings are shared by all types of pricing rules. However, some settings are specific to margin component price adjustments, all discounts, or specific types of discounts.

## Enter information on the General FastTab

The **General** FastTab provides basic settings for the pricing rule. Set the fields that are described in the following subsections, depending on the type of pricing rule that you're setting up.

### General settings that apply to both margin price adjustments and discounts

Set the following fields on the **General** FastTab for all types of pricing rules:

- **Status** – Set this field to *Enabled* or *Disabled*. Only enabled records are available for calculations. New records are set to *Disabled* and can be enabled only after you've finished setting all the required fields. All fields are read-only for enabled rules. Therefore, you must disable a rule before you can edit it.
- **Currency** – Select the currency that the rule applies to.
- **Price component** – This read-only field shows the type of pricing rule (*Discounts* or *Margin component*).
- **Price component code** – Select the [price component code](price-component-code.md) that the rule applies to. Only existing price component codes of the applicable type are listed.
- **Header price attribute group type** – This read-only field indicates how customers that the rule applies to are selected. It shows *All* if the rule applies to all customers. It shows *Group* if the rule applies to only a set of customers, as defined by values that are assigned to attributes that are part of an attribute group. You can set the value for the current rule by selecting **Header price attribute group** on the Action Pane. For more information, see the [Set up header price attribute values](#header-attributes) section of this article.
- **Price attribute group** – If the **Header price attribute group type** field is set to *Group*, this read-only field shows the attribute group that's being used to define the set of customers that the current rule applies to. For more information, see the [Set up header price attribute values](#header-attributes) section.

### General settings that apply only to margin price adjustments

If you're setting up a pricing rule for a margin component price adjustment, set the following fields on the **General** FastTab:

- **Concurrency model** – This read-only field indicates how the system will handle situations where more than one price adjustment applies to the same price component code in a price structure. (This type of situation is known as concurrency.) The value *Price component code rank* means that the system will select a price adjustment based on its price attribute combination rank. If multiple price adjustments have the same highest rank, they all apply to the sales order.
- **Quantity tiers** – Set this option to *Yes* to enable the **Quantity tiers** FastTab, where you can define price adjustments that vary based on the quantity on the sales order line.

> [!NOTE]
> Margin component price adjustment quantity tiers differ from quantity discounts. Quantity discounts tiers are based on the item quantity per order. Margin component price adjustment tiers are based on the item quantity per line.

### General settings that apply only to discounts

If you're setting up a pricing rule for a discount, set the following fields on the **General** FastTab. Not all these fields are available for every type of discount.

- **Discount account** – If you want to post the discount amount for the discount record to a separate general ledger account, specify that account. This field overrides the similar field that's available for price structures (**Price component code setup** or **Price tree**). For more information, see [Price component posting](price-component-posting.md).
- **Discount concurrency mode** – Select one of the following values to specify how the system should handle situations where more than one discount rule applies to the same price component code in a price structure. (This type of situation is known as concurrency.)

    - *Exclusive* – The discount is an exclusive discount. Therefore, it can't be combined with other discounts. If there are multiple exclusive discounts, the price engine will apply only the one that gives the largest discount.
    - *Best price* – Discounts of this concurrency mode will compete for the largest discount (lowest price).
    - *Compounded* – The discount will be combined with other discounts according to the pricing sequence that's defined in the price structure. Settings on the **Pricing management parameters** page control whether the compounded discount calculation is based on the original price or the compounded amount. (For more information, see [Resolve concurrency within price component codes](concurrence-within-codes.md).)
    - *Always apply* – The discount will always be applied. Always-apply discounts are applied last. Therefore, they represent universal discounts that apply to all sales orders.
    - *Price attribute combination rank* – Discounts of this concurrency mode don't compete based on price. Instead, they compete based on which discount has the highest price attribute combination rank. If multiple discounts have the same highest rank, they all apply to the sales order.

- **Coupon code required** – Set this option to *Yes* if a coupon code is required to qualify for the discount. The discount must be linked to the coupon. The discount will be triggered only if a valid coupon code is entered together with the order. When this option is enabled, the **Status**, **Effective date** and **Expiration date** fields become unavailable. The settings of those fields will depend on the coupon configuration. To set up coupons, go to **Pricing management \> During-sales pricing \> Coupons**.
- **Claimable** – Set this option to *Yes* to make the discount claimable. (In other words, the discount is sponsored by a vendor and can therefore be charged back to that vendor.)
- **Discount claim group** – If you set the **Claimable** option to *Yes*, select the applicable claim group.
- **Claim offset posting** – If you set the **Claimable** option to *Yes*, select the offset account that you want to post the claim to.
- **Max criteria type** – If a maximum discount per order applies, select the type of limit that you want to apply:

    - *Amount*
    - *Quantity*

- **Max** – If a maximum discount per order applies, select the value of the limit.
- **Max quantity unit** – If a maximum discount per order applies, and the **Max criteria type** field is set to *Quantity*, select the unit that applies to the value that's selected in the **Max** field.

## Enter information on the Details FastTab

The **Details** FastTab lets you enter more information about the pricing rule. It also provides extra information about it. You can set and/or review the following fields:

- **Description** – Enter a description of the pricing rule.
- **Disclaimer** – Enter a disclaimer for the pricing rule.
- **Text for fiscal receipt** – Enter text that will appear on the related fiscal receipt.
- **Header price attribute details** – This read-only field summarizes the header price attribute values for the pricing rule. (You can access the header price attribute values by selecting **Header price attribute group** on the Action Pane.) For more information, see the [Set up header price attribute values](#header-attributes) section of this article.

## Enter information on the Price/discount FastTab

The **Price/discount** FastTab is available only for simple, threshold, and mix-and-match discounts. The settings here are combined with the settings on the **Lines** FastTab to define the discount values for different combinations of customers and items.

### Price/discount settings for simple discounts

If you're setting up a simple discount, set the following fields on the **Price/discount** FastTab:

- **Percentage off** – Enter the default discount percentage for new lines that are added on the **Lines** FastTab. As you add each line to the **Lines** FastTab, you can change the percentage, or change the percentage off to an amount off, as described later in this article.
- **Quantity limit** – Enter the maximum order quantity that the discount applies to. This limit applies to all lines on the **Lines** FastTab. Although the value is repeated for each line on the **Lines** FastTab, you can edit it only on the **Price/discount** FastTab. If you edit the value, all existing lines will be updated. You can't edit the value separately for each line.

### Price/discount settings for mix-and-match discounts

If you're setting up a mix-and-match discount, set the following fields on the **Price/discount** FastTab:

- **Percentage off** – Enter the default discount percentage for new lines that are added on the **Lines** FastTab. As you add each line to the **Lines** FastTab, you can change the percentage, or change the percentage off to an amount off, as described later in this article.
- **Quantity limit** – Enter the maximum order quantity that the discount applies to. This limit applies to all lines on the **Lines** FastTab. Although the value is repeated for each line on the **Lines** FastTab, you can edit it only on the **Price/discount** FastTab. If you edit the value, all existing lines will be updated. You can't edit the value separately for each line.
- **Calculation type** – Select the type of calculation that the current pricing rule will apply. The other fields that are available on the **Price/discount** FastTab vary based on the value that you select.

    - *Deal price* – Use a specific final price instead of a calculated discount. After you select this value, enter the price in the **Deal price** field.
    - *Percentage off* – Calculate the discount as a percentage of the item price. After you select this value, enter the percentage in the **Percentage off** field. For example, the usual price of item A is 40.00, the usual price of item B is 60.00, and a mix-and-match discount of 30 percent applies to these items. If a customer buys item A and item B together, the cost is 70.00 instead of 100.00.
    - *Amount off* – Define the discount as a fixed value. After you select this value, enter the discount in the **Amount off** field.
    - *Least expensive* – After you select this value, enter the discount price in the **Deal price**, **Percentage off**, or **Amount off** field, depending on the method that you want to use to calculate the price. Then, in the **Number of least expensive lines** field, enter the number of least-expensive items that you want to apply the discount to. Finally, set the **Multiple occurrences mode** field to one of the following values:

        - *Favor customer*
        - *Favor retailer*

    - *Line spec* – Use the discount that's specified for each line on the **Lines** FastTab.

- **Count non-discountable products** – Set this option to *Yes* to count non-discountable items toward the quantity.

> [!NOTE]
> For mix-and-match and least-expensive discounts, the number of least-expensive products must be more than one and less than the number of products.

### Price/discount settings for threshold discounts

If you're setting up a threshold discount, set the following field on the **Price/discount** FastTab:

- **Count non-discountable items toward threshold** – Set this option to *Yes* to count non-discountable items toward the quantity.

## Enter information on the Quantity discount configuration FastTab

The **Quantity discount configuration** FastTab is available only for quantity discounts. Use it to set up the discounts that apply to each quantity threshold that you set up.

### Quantity discount settings

On the **Quantity discount** FastTab, set the following fields, which affect how the quantity tiers will work:

- **Calculation type** – Select one of the following options to specify how the discount will be calculated based on the table values:

    - *Percentage off* – The discount will be calculated as a percentage of the price.
    - *Amount off* – A specific value will be subtracted from the price.
    - *Unit price* – A new, specific unit price will be applied.

- **Interval** – This option applies only when the **Calculation type** field is set to *Amount off*. Set it to *Yes* to use a stepped calculation for each quantity tier. See the next section for an example that shows how this setting affects the discount calculation.

The grid on the **Quantity discount configuration** FastTab defines a set of quantity tiers and the discount that applies to each tier. Use the buttons on the toolbar to add and remove rows from the grid. For each row, set the following fields:

- **Minimum quantity** – Enter the minimum quantity of an item that a customer must order to get the discount that's specified on the line.
- **Value** – Enter the value of the discount for the line (based on the selected calculation type).

## View information on the Calculation FastTab

The **Calculation** FastTab provides information about how the price component code that's selected for the pricing rule is set up in your [price structure](price-structure-overview.md).

The following information is shown:

- **Pricing sequence** – This read-only field shows the position of the selected price component code in your price structure.
- **Compound** – This read-only field is shown only for margin price adjustments, not for discounts. It indicates whether the selected price component code is set up to make compound calculations in your price structure.

## Enter information on the Validation period FastTab

Use the fields on the **Validation period** FastTab to control when the pricing rule will apply. The following conditions apply:

- The date range is defined at the header level.
- The date that's used when a pricing rule is validated is based on the value of the **Date type** field on the **General** tab of the **Pricing management parameters** page. You can set the **Date type** field to *Today*, *Requested ship date*, *Requested receipt date*, or *Created date*.

You can set up the validation period by using either standard rules or advanced rules.

### Set up standard date validation rules

Follow these steps to set up the validation period by using the standard validation rules.

1. Set the **Date validation type** field to *Standard* to enable the fields that are required to set up standard date validation.
1. Set the following fields:

    - **Effective date** – Select the first date that the pricing rule should apply.
    - **Expiration date** – Select the last date that the pricing rule should apply.

### Set up advanced date validation rules

Advanced validation rules let you set the validation period by using a discount period record instead of entering simple start and end dates.

Discount period records let you set up detailed date and time limits that can include a start date and time, an end date and time, and specific times of day for each day of the week. You can set up discount period records by going to **Retail and Commerce \> Pricing and discounts \> Discount periods**.

Follow these steps to set up the validation period by using the advanced validation rules.

1. Set the **Date validation type** field to *Advanced* to enable the fields that are required to set up advanced date validation.
1. In the **Discount period number** field, select the discount period record that defines the validation period that you want to use. The read-only **Description**, **Start date**, and **End date** fields are updated to show values from the selected discount period record.

## <a name="items-lines"></a>Enter information on the Lines and Line details FastTabs

Use the **Lines** FastTab to control which discounts and margin price adjustments will apply to each item. All the lines in a pricing rule apply to the same collection of customers. You configure this collection in the [header price attribute group settings](#header-attributes), which you can access by selecting **Header price attribute group** on the Action Pane.

### <a name="add-line"></a>Add a line and configure the set of items that it applies to

Each line assigns calculation rules that apply to a specific collection of items. When you add a line, you'll use a dialog box to set up the items that the line affects and then add the line to the grid. Later, you'll set up the calculation rules for the line by using the columns in the grid. Follow these steps to add a line.

1. On the **Lines** FastTab, select **New** on the toolbar.
1. The **Edit price attributes** dialog box appears. This dialog box lets you set up the logic for finding the items that the current line will apply to. On the **Header price attribute group** FastTab, review the logic that's set up for selecting the customers that the current pricing rule applies to. The values apply to all lines in the current pricing rule and are read-only here. (You can change them in the [header price attribute group settings](#header-attributes).)
1. In the **Price attribute group combination** field, select the combination of price attributes that you'll use to define the items for the current line. The combinations that are available for selection are defined for the [price component code](price-component-code.md) that's selected for the current pricing rule. However, only the right side of the combination name (the [line price attribute group](price-attribute-groups.md) name) is relevant, because the header attributes are common to all lines for the pricing rule, as was mentioned in the previous step. Select the combination where the right side of the name matches the way that you want to define the collection of items that the line applies to.
1. If the selected price attribute group combination considers item (line) attribute values (that is, if it doesn't apply to *all* items), the **Line price attribute group** FastTab is available. In this case, for each row on the **Line price attribute group** FastTab, enter or select one or more values in the **Value** column to define the rules for selecting items. The collection of attributes that's shown comes from the price attribute group combination that you selected. The following rules apply:

    - All rows are combined by using a logical AND operator. Therefore, only those items that have matching values for *all* rows will be included.
    - If you want to create one or more rows that include multiple values, set the **Enable multiple selections** option to *Yes*. You can then add a comma-separated list of values in the **Value** column for each row. These values are combined by using an OR operator. Therefore, the row will find items that match *any* of the values in the list.
    - You can specify values to exclude by adding an exclamation mark (\!) before the value. This exclamation mark is known as an exclusion prefix. For example, to find all items except *A0001*, set the **Value** field to *!A0001* for the attribute where the **Attribute** field is set to *Item number*. You can automatically add the exclusion prefix to the values of any row by selecting the row and then selecting **Exclude values in selected lines**.

1. On the **Preview matching results (Products)** FastTab, view the preview of items that match the conditions that you've set up so far.

    - If the list includes any items that you want to exclude, select the target rows, and then select **Exclude** on the toolbar.
    - The **Line type** column indicates which items you've selected to exclude.
    - To re-include a previously excluded item, select it, and then select **Include** on the toolbar.
    - To view, exclude, and/or re-include specific item variants, select **All variants** on the toolbar. While you're viewing the variants, you can select **Product master** on the toolbar to go back to the standard item list.

1. Select **OK** to add the new line to the grid on the **Lines** FastTab.
1. Set up the calculation rules for the new line by using the columns in the grid, as described in the next section.

If you ever have to return to the **Edit price attributes** dialog box to change the set of items that a line applies to, select the line, and then select **Edit line price attribute** on the toolbar.

### Set line values to define calculation rules and further refine the item selection

The settings for each line on the **Lines** FastTab vary based on the type of pricing rule that you're working with. The following fields and information might be available:

- **Line group type** – This field shows whether the line applies to a specific group of items or to all items.
- **Line price attribute group** – If the **Line group type** field is set to *Group*, this field shows the name of the selected [line price attribute group](price-attribute-groups.md).
- **Price attribute detail** – This field summarizes the values that were set for the line in the **[Edit price attributes](#add-line)** dialog box. To change these values, select **Edit price attribute** on the FastTab toolbar.
- **Combination rank** – This field shows the combination rank that was generated for the price attribute group combination that was selected for the line in the **[Edit price attributes](#add-line)** dialog box. Rankings enable the system to determine which pricing rule is used if an order or order line qualifies for more than one rule. For more information, see [Price component codes](price-component-code.md).
- **Required line quantity** – For free-item discounts where the **Criteria type** field is set to *Quantity*, enter the minimum quantity that must be ordered to qualify for the discount.
- **Required line amount** – For free-item discounts where the **Criteria type** field is set to *Amount*, enter the minimum amount that must be ordered to qualify for the discount.
- **Allow unit conversion** – Select this checkbox to convert the selling unit to the unit that's used for the pricing rule as required.
- **Line type** – Select one of the following values:

    - *Include*
    - *Exclude*

- **Calculation type** – Select one of the following values to specify how the discount or price adjustment for the current line should be calculated:

    - *Percentage off* or *Percent* – Calculate the discount or price adjustment value as a percentage of the price.
    - *Amount off* or *Amount* – Calculate the discount or price adjustment by using a fixed value that's added to or subtracted from the price.
    - *Unit price* – Set a new, fixed unit price.

- **Percent** or **Percentage off** – If you're using a percentage-based calculation type, enter the percentage.
- **Amount** or **Amount off** – If you're using an amount-based calculation type, enter the amount.
- **Unit price** – If you're using the *Unit price* calculation type, enter the new unit price.
- **Quantity limit** – The field shows the maximum order quantity that the discount applies to. This limit applies to all lines on the **Lines** FastTab. You can't edit this separately for each line, but you can edit it for all lines at the same time by using the **Quantity limit** field on the **Price/discount** FastTab.
- **Number of products needed** – This field shows the number of items that the customer must buy in this line group to qualify for the discount. For mix-and-match discounts, the value is read-only and is taken from the group that's selected in the **Line group** field.
- **Line group** – If you're setting up a mix-and-match discount, select the line group that applies to the line. Before you can select a value, you must set up your line groups, add them to the current pricing rule, and configure a color and item threshold for them, as described in [Mix-and-match discounts](discounts.md#mix-match). The line will then be highlighted in the color that was configured for the selected line group (if any color was configured), and the **Number of products needed** value will be updated to match the selected line group configuration.
- *Other dimensions* – The grid might include additional columns that show item, storage, and tracking dimensions (such as **Color**, **Warehouse**, and **Serial number**). To select which dimensions are shown, select **Display dimensions** on the toolbar. Enter values in these columns to limit the line so that it applies only to items that match the specified dimension values.

### Enter information on the Lines details FastTab

If you want to add a note that gives more information about a line on the **Lines** FastTab, select the relevant line, and then enter your note in the **Description** field on the **Line details** FastTab.

## <a name="header-attributes"></a>Set up header price attribute values

Use header price attributes to control which customers the current pricing rule applies to. The limits apply to all lines and items that the rule applies to. (For more information, see the [Enter information on the Lines and Line details FastTabs](#items-lines) section of this article.) Follow these steps to set the header price attributes for the current pricing rule.

> [!NOTE]
> Before you can set header price attributes, you must assign a price component code on the **General** FastTab.

1. On the Action Pane, select **Header price attribute group**.
1. The **Edit price attributes** dialog box appears. This dialog box lets you set up the logic for finding the customers that the current pricing rule will apply to. On the **Header price attribute group** FastTab, review and set the following fields:

    - **Scope of price attributes** – This read-only field indicates the type of attributes that your settings will apply to. It will always show *Header*.
    - **Group type** – Select the type of customer selection that you want to set up. The available values depend on the price attribute combinations that are available for your selected [price component code](price-component-code.md). The following values might be available:

        - *Group* – If you select this value, the dialog box will provide a group of header attributes that you can assign values for, so that you can limit the set of customers that the pricing rule will apply to.
        - *All* – The pricing rule will apply to all customers. If you select this value, no further steps are required. Therefore, you can skip the rest of this procedure and just select **OK** to apply your settings.

    - **Price attribute group** – If you set the **Group type** field to *All*, select a price attribute group. The available values depend on the attribute groups that you've enabled for the selected [price component code](price-component-code.md). The value that you select will affect the set of attributes that you can work with in the dialog box.

1. If you selected a price attribute group, the attributes from it are shown on the **Header price attribute group** FastTab. For each row, enter or select one or more values in the **Value** column to define the rules for selecting customers. The following rules apply:

    - All rows are combined by using a logical AND operator. Therefore, only those customers that have matching values for *all* rows will be included.
    - If you want to create one or more rows that include multiple values, set the **Enable multiple selections** option to *Yes*. You can then add a comma-separated list of values in the **Value** column for each row. These values are combined by using an OR operator. Therefore, the row will find customers that match *any* of the values in the list.
    - You can specify values to exclude by adding an exclamation mark (\!) before the value. This exclamation mark is known as an exclusion prefix. For example, to find all customers except *US-001*, set the **Value** field to *!US-001* for the attribute where the **Attribute** field is set to *Customer account*. You can automatically add the exclusion prefix to the values of any row by selecting the row and then selecting **Exclude values in selected lines**.

1. On the **Preview matching results (Customers)** FastTab, view the preview of customers that match the conditions that you've set up so far.

    - If the list includes any customers that you want to exclude, select the target rows, and then select **Exclude** on the toolbar.
    - The **Line type** column indicates which customers you've selected to exclude.
    - To re-include a previously excluded customer, select it, and then select **Include** on the toolbar.

1. Select **OK** to save your settings and close the dialog box.

## Set up mix-and-match line groups

If you're working with a mix-and-match discount pricing rule, select **Mix and match line groups** to select which mix-and-match line groups can be assigned on the **Lines** FastTab, and specify the number of products that must be bought from each group to qualify for the discount. For information about how to set up mix-and-match line groups, see [Mix-and-match discounts](discounts.md#mix-match).
