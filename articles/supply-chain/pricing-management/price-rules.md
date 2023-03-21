## Create and manage your pricing rules

1. Depending on which type of rule you want to make, go to one of the following pages:

    - **Pricing management \> During-sales pricing \> Price adjustments \> Margin component price adjustments**
    - **Pricing management \> During-sales pricing \> Discounts \> All discounts**
    - **Pricing management \> During-sales pricing \> Discounts \> Discounts**
    - **Pricing management \> During-sales pricing \> Discounts \> Quantity discounts**
    - **Pricing management \> During-sales pricing \> Discounts \> Mix and match discounts**
    - **Pricing management \> During-sales pricing \> Discounts \> Threshold discounts**
    - **Pricing management \> During-sales pricing \> Discounts \> Free item**

1. Do one of the following steps:
    - To add a new record, on the Action Pane, open the **New** menu and then choose which type of record you want to create.
    - To create a copy of an existing record, select it on the list pane and then select **Copy** on the Action Pane.
    - To edit an existing record, select it on the list pane and then set **Status** to *Disabled* on the **General** FastTab. (All rule records are read-only while enabled)
    - To delete a record, select it on the list pane and then select **Delete** on the Action Pane.
1. Make the following settings in the header of your new or selected rule record:

    - **Discount** or **Margin component adjustment** – Enter a unique identifier for this rule.
    - **Name** – Enter a common name for the rule.
    - **Discount type** – If you're working with a discount rule, then the type of discount is shown here (read-only). This field isn't shown for margin price components.
    - **Publish status** – Initially set to *Draft*. Once you complete the record, you can activate the rule. <!--KFM: How do we activate it? What value will this show when active? Other values? What other effects does this status have? -->

1. Continue setting up your price rule as described in the remaining sections of this article. Many settings are shared by all types of price rules, but some are specific to margin component price adjustment, all discounts, or specific types of discounts.

<!-- KFM: Add a step for enabling the rule when done? -->

## Make settings on the General FastTab

The **General** FastTab provides basic settings for your pricing rule. Make the settings described in the following subsections, depending on which type of pricing rule you are setting up.

### General settings that apply to both margin price adjustments and discounts

Make the following settings on the **General** settings tab for all all types of price rules.

- **Status** – Set to *Enabled* or *Disabled*. Only *Enabled* records are available for making calculations. New records are set to *Disabled* and can only be enabled after you have finished making all the required settings. All settings are read-only for enabled rules, so you must disable a rule before you can edit it. <!-- KFM: What is the effect of this setting? For coupons, this is always disabled, what does that mean? -->
- **Currency** – Select the currency for which this rule applies. <!--KFM: Does this mean that this record will only apply to orders or order lines that use this currency? -->
- **Price component** – This read-only field shows which type of price rule this is (*Discounts* or *Margin component*).
- **Price component code** – Select the [price component code](price-component-code.md) that this rule applies to. Only existing price component codes of the applicable type are listed.
- **Header price attribute group type** – <!-- KFM: Description needed -->
- **Price attribute group** – <!-- KFM: Description needed -->

### General settings that apply to margin price adjustments only

Make the following settings on the **General** settings tab if you are setting up a price rule for a margin component price adjustment.

- **Concurrency model** – This read-only field tells you how the system will handle situations where more than one margin component price adjust applies (concurrence). Its value, *Price component code rank*, means that the system will choose a price adjustment based on the price attribute combination rank. <!--KFM: This doesn't seem quite right. Is it actually about finding the *order* in which adjustments are applied? -->
- **Quantity tiers** – Set to *Yes* to enable the Quantity tiers FastTab, which lets you establish price adjustments that vary based on the sales order line quantity.

> [!NOTE]
> Margin component price adjustment quantity tier is different from Quantity discounts. Quantity discounts tiers are based on the item quantity per order. Margin component price adjustment tiers are based on the item quantity per line.

### General settings that apply to discounts only

Make the following settings on the **General** settings tab if you are setting up a price rule for a discount. Not all types of discounts include all of these settings.

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

The **Details** FastTab lets you enter more information about your price rule, and also provides extra information about it. You can enter and/or inspect the following details here.

- **Description** – Enter a description of the price rule. <!-- KFM: Where is this used, just here? -->
- **Disclaimer** – Enter a disclaimer for the price rule. <!-- KFM: Where is this used, just here? -->
- **Text for fiscal receipt** – Enter a text to be displayed on the related fiscal receipt. <!-- KFM: What is this? Can we give a link or little more info? -->
- **Header price attribute details** – This read-only field summarizes the header price attribute values for this price rule (available by selecting **Header price attribute group** on the Action Pane). For more information, see [Set up header price attribute values](#header-attributes).

## Make settings on the Price/discount FastTab

The **Price/discount** FastTab is only provided for standard and mix-and-match discounts. The settings here combine with those on the Lines FastTab to establish the discount values for various combinations of customers and products. <!-- KFM: Will this also work if we don't have any lines? -->

### Price/discount settings for both standard and mix-and-match discounts

Make the following settings for both standard and mix-and-match discounts:

- **Percentage off** – Enter the default discount percentage to new lines added to the **Lines** FastTab. You can change the percentage, or change the percentage off to an amount off, for each line as you add it to **Lines** Fast Tab, as described later in this article.
- **Quantity limit** – Enter the maximum order quantity for which this discount applies. This limit applies to all lines on the **Lines** FastTab. You can't edit this separately for each line. This value is repeated for each line on the **Lines** FastTab, but you can only edit the value here. All existing lines will update if you change this value.

### Price/discount settings for mix-and-match discounts only

If you're setting up a mix-and-match discount, then also make the following settings in addition to those mentioned in the previous section:

- **Calculation type** – Select which type of calculation the current price rule will apply. The selection you make here will affect which other fields of this FastTab will be active. Select one of the following options:
    - *Deal price* – Specify a specific final price rather than a calculated discount. After selecting this option, enter the price in the **Deal price** field.
    - *Percentage off* – Calculate the discount as a percentage of the item price. After selecting this option, enter the percentage in the **Percentage off** field. For example, suppose the usual price of product A is 40.00, the usual price of product B is 60.00, and a mix-and-match discount of 30 percent applies to these products. Then, if a customer buys product A and product B together, the cost is 70.00 instead of 100.00.
    - *Amount off* – Define the discount as a fixed value. After selecting this option, enter the discount in the **Amount off** field.
    - *Least expensive* – <!-- KFM: A general description of what this setting means is needed here. --> After selecting this option, enter
    - *Line spec*
- **Deal price**
- **Percentage off**
- **Amount off**
- **Number of least expensive lines**
- **Multiple occurrences mode**
    - *Favor customer*
    - *Favor retailer*
- **Count non-discountable products**
- **Generate bundle ID**




## Make settings on the Quantity discount configuration FastTab

The **Quantity discount configuration** FastTab is only provided for quantity discounts. Use it to set up the discounts that apply for each quantity threshold that you want to set up.

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

<!-- KFM: Introduce the following table. What is this? -->

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

| Sales order line | Product | Quantity | Discount per unit | Discount for line |
|---|---|---|---|---|
| Line 1 | EV003 | 10 | $3 | $30 |
| Line 2 | EV002 | 2 | $3 | $6 |

When **Interval** is set to *Yes*, the quantity discount for an example order is calculated as shown in the following table. <!-- KFM: We should explain more about where these numbers are coming from. I don't get it. -->

| Sales order line | Product | Quantity | Discount per unit | Discount for line |
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
- **Compound** – This read-only field is only shown for margin price adjustments (not for discounts). It shows whether the selected **Price component code** is set to use compound calculations within your pricing structure.
















## Make settings on the Validation period FastTab


1. In the Validation period, set up the rule valid period.

    - You need to be aware of 2 things:
        - For Margin component price adjustments and Discounts, the date range is defined in the header level.
        - The date period will be impacted by the **Date type** in the **Pricing management \> Setup \> Pricing management parameters**.
    - You can define the period in 2 ways:
        - **Standard period** – You can set up the **Effective date** and **Expiration date** for the rule.
        - **Advanced period** – You can define the discount period number for the rule.

## Make settings on the Lines FastTab

1. You can now edit the rule line in the Line fast tab. Click **+Add** to add a new record. The Edit price attribute display for you to define the line attributes.

    - **Price attribute group combination** – select the combination which includes the Line price attribute group. The price attribute of the Line price attribute group will display for you to select the value. You can choose the value for the attributes. If you set **Enable multiple selections** as Yes, you are allowed to multi-select the values.
    - **Exclude values in selected lines** – can be used when you have the criteria that is 'Not equal to'.
    - **Preview matching results (Products)** – Gives a preview of current applicable products that meet the criteria.
    - **Exclude** – in case there are products that meet the criteria, but you want to rule them out, you can exclude the products.
    - Click **OK** to close the slider. Use the **Edit line price attribute** to adjust the value of the line price attributes.

1. Enter the **Site, Warehouse** if applicable for the rule criteria for matching the sales order line.
1. Enter the **Unit** as the rule criteria for matching the sales order line.
1. **Allow unit conversion** – enable the conversion of the selling unit to match the rule.
1. Specify the **calculation method** and **calculation value** (percent\\amount). Margin component price adjustment allows you to set up the price up (positive) and price down (negative) in percentage or amount.
1. Provide more information in the **Description** in the Line details fast tab.
1. Use the Edit line price attribute to adjust the value of the line price attributes.
1. Click **Save** to save the rule.
1. You can activate the rule once you change the status from **Disable** to **Enabled**.

## Make settings on the Lines details FastTab

## <a name="header-attributes"></a>Set up header price attribute values

1. You need to define the Header price attribute group value to complete the setting of the header level rule. Click **Header price attribute group** and the Edit price attribute slider display for you to define the value criteria.
1. In the Edit price attributes slider, you can select:

    - **Group type** – You select whether you want to define the header price attributes. If you select 'All', you don't specify value for specific header price, and it applies to all customers and orders.
    - **Price attribute group** – Once you select 'Group' in the Group type, you now can select which Header price attribute group you want to use. Once you select the price attribute group, the attributes of the group display in Rank order. You can choose the value for the attributes. If you set **Enable multiple selections** as Yes, you are allowed to multi-select the values.
    - **Exclude values in selected lines** – can be used when you have the criteria that is 'Not equal to'. For example, you choose the 'Customer group = 30', but when you tick Exclude values in select lines, the condition turns to 'Customer group= !30', meaning the Customer group is not 30.
    - **Preview matching results (Customers)** – Gives a preview of current applicable customers that meet the criteria.
    - **Exclude** – in case there are customers that meet the criteria, but you want to rule them out, you can exclude the customers.

## Set up Mix and match line groups

## Set up a discount exclusion list