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

    - *Unique identifier* – The first field in the header is labeled with the name of the type of rule your are making (such as **Discount** or **Margin component adjustment**). Enter a unique identifier for this rule.
    - **Name** – Enter a common name for the rule.
    - **Discount type** – If you're working with a discount rule, then the type of discount is shown here (read-only). This field isn't shown for margin price components.
    - **Publish status** – Initially set to *Draft*. Once you complete the record, you can activate the rule. <!--KFM: How do we activate it? What value will this show when active? Other values? What other effects does this status have? -->

1. Make the following settings on the **General** FastTab.

    - **Status** – Set to *Enabled* or *Disabled*. Only *Enabled* records are available for making calculations. New records are set to *Disabled* and can only be enabled after you have finished making all the required settings. All settings are read-only for enabled rules, so you must disable a rule before you can edit it.
    - **Currency** – Select the currency for which this rule applies. <!--KFM: Does this mean that this record will only apply to orders or order lines that use this currency? -->
    - **Concurrency model** – This read-only field is only shown for margin component price adjustments. It tells you how the system will handle situations where more than one margin component price adjust applies (concurrence). Its value, *Price component code rank*, means that the system will choose a price adjustment based on the price attribute combination rank. <!--KFM: This doesn't seem quite right. Is it actually about finding the *order* in which adjustments are applied? -->
    - **Discount concurrency mode** – This setting is available for all types of discounts (but not for margin component price adjustments). It tells you how the system will handle situations where more than one discount applies (concurrence). Choose one of the following values:
        - *Exclusive* – The discount is an exclusive discount, which means it can't be combined with other discounts. If there are multiple exclusive discounts, the price engine will only apply the one with the highest discount. <!--KFM: If there are both exclusive and non-exclusive discounts, does the exclusive always win even if a non-exclusive has a higher discount, in which case might multiple non-exclusive discounts then apply? -->
        - *Best price* – Discounts of this concurrency mode will compete for the highest discount (lowest price).
        - *Compounded* – The discount will be combined with other discounts according to the pricing sequence established in the price structure. Settings on the **Pricing management parameters** page control whether the compounded discount calculation basis is the original price or the compounded amount. <!--KFM: Link to topic where this setting is described. -->
        - *Always apply* – The discount will always be applied. Always-apply discounts are applied last and therefore represent represent universal discounts that apply to all.
        - *Price attribute combination rank* – Discount records with this concurrency mode don't compete based on price but on which one has the highest price attribute combination rank. If multiple discounts have the same highest rank, they all apply to the sales order.
    - **Price component** – This read-only field shows which type of price rule this is (*Discounts* or *Margin component*).
    - **Price component code** – Select the [price component code](price-component-code.md) that this rule applies to. Only existing price component codes of the applicable type are listed.
    - **Header price attribute group type** – <!--KFM: Description needed -->
    - **Price attribute group** – <!--KFM: Description needed -->
    - **Quantity tiers** – This setting is only shown for margin component price adjustments. Set to *Yes* to enable the Quantity tiers FastTab, which lets you establish price adjustments that vary based on the sales order line quantity.
    - **Coupon code required** – This setting is available for all types of discounts (but not for margin component price adjustments). Set to *Yes* if a coupon code is required to qualify for the discount. The discount must be linked to the coupon. The discount will only be triggered if a valid coupon code is entered together with the order1. If the Coupon code required option is enabled, the Status field, Effective date and Expiration date fields will not be available. The setting will be pending on the coupon configuration. To create coupons, go to Pricing management > > During-sales pricing > Coupons.









    > [!NOTE]
    > Margin component price adjustment quantity tier is different from Quantity discounts. Quantity discounts tiers are based on the item quantity per order. Margin component price adjustment tiers are based on the item quantity per line.

1. Choose the **Price component code** from the drop-down list. All of the price components codes for the 'Margin component price adjustment' type that you created are available as options.
1. Select Price component code from the drop-down list. The options include all the price component codes of the 'Margin component price adjustment' type that you created.
1. In the Details tab, enter the **Description** of the margin component price adjustments.
1. In the Validation period, set up the rule valid period.

    - You need to be aware of 2 things:
        - For Margin component price adjustments and Discounts, the date range is defined in the header level.
        - The date period will be impacted by the **Date type** in the **Pricing management \> Setup \> Pricing management parameters**.
    - You can define the period in 2 ways:
        - **Standard period** – You can set up the **Effective date** and **Expiration date** for the rule.
        - **Advanced period** – You can define the discount period number for the rule.
1. You need to define the Header price attribute group value to complete the setting of the header level rule. Click **Header price attribute group** and the Edit price attribute slider display for you to define the value criteria.
1. In the Edit price attributes slider, you can select:

    - **Group type** – You select whether you want to define the header price attributes. If you select 'All', you don't specify value for specific header price, and it applies to all customers and orders.
    - **Price attribute group** – Once you select 'Group' in the Group type, you now can select which Header price attribute group you want to use. Once you select the price attribute group, the attributes of the group display in Rank order. You can choose the value for the attributes. If you set **Enable multiple selections** as Yes, you are allowed to multi-select the values.
    - **Exclude values in selected lines** – can be used when you have the criteria that is 'Not equal to'. For example, you choose the 'Customer group = 30', but when you tick Exclude values in select lines, the condition turns to 'Customer group= !30', meaning the Customer group is not 30.
    - **Preview matching results (Customers)** – Gives a preview of current applicable customers that meet the criteria.
    - **Exclude** – in case there are customers that meet the criteria, but you want to rule them out, you can exclude the customers.

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
