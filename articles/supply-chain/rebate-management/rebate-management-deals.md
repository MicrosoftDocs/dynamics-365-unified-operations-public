---
# required metadata

title: Rebate management deals
description: This topic describes how to create Rebate management deals. Deals are used to control different methods and bases for calculating rebates and royalties. They include rules for inclusions and exclusions.
author: sherry-zheng
ms.date: 02/19/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: TAMRebateDeal
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: chuzheng
ms.search.validFrom: 2021-02-19
ms.dyn365.ops.version: 10.0.18
---

# Rebate management deals

[!include [banner](../includes/banner.md)]

Rebate management deals are used to control different methods and bases for calculating rebates and royalties. They include rules for inclusions and exclusions. There are three types of Rebate management deals: customer rebates, customer royalties, and vendor rebates. All three types use similar settings. This topic points out differences where they exist.

## Create a deal

1. Go to **Rebate management \> Rebate management deals \> All rebate management deals**. On the **All rebate management deals** list page, you can create and work with deals of all three types.

    Alternatively, follow one of these steps. In each case, the list page that appears provides all the same settings as the **All rebate management deals** list page, but it's filtered to show deals of only one type.

    - Go to **Rebate management \> Rebate management deals \> Customer rebate deals** to create only customer rebate deals.
    - Go to **Rebate management \> Rebate management deals \> Customer royalty deals** to create only customer royalty deals.
    - Go to **Rebate management \> Rebate management deals \> Vendor rebate deals** to create only vendor rebate deals.

1. On the Action Pane, select **New**.
1. In the **Create new deal** dialog box, set the following fields:

    - **Rebate management deal** – If you've [set up a number sequence](rebate-management-parameters.md) for rebate deals, this field is automatically set to a unique, system-generated ID. Otherwise, enter a unique ID.
    - **Description** – Enter a description of the deal.
    - **Module** – Select the type of partner that the deal applies to (*Customer* or *Vendor*). Depending on the page that you started from, this field might be automatically set based on the selected deal type. In this case, the field is read-only.
    - **Type** – Select the type of deal (*Rebate* or *Royalty*). Depending on the page that you started from, this field might be automatically set based on the selected deal type. In this case, the field is read-only.
    - **Reconcile by** – Select how the deal should be calculated and reconciled:

        - *Deal* – A single rebate should be processed for all rebates and deductions in the deal.
        - *Line* – Rebates should be processed for each line in a deal.

    - **Posting profile** – Select the [posting profile](rebate-management-posting.md) to use for transactions where the deal applies. This field is available only when the **Reconcile by** field is set to *Deal*. If it's set to *Line*, you will assign the profile later, for each line that you add to the deal.
    - **Posting profile for guarantee** – Select the [posting profile](rebate-management-posting.md) to use for guarantee transactions. Posting profiles are required for guarantee transactions only if the guarantee applies to a royalty. Otherwise, although a posting profile isn't mandatory, if no posting profile is specified, an error will be shown when guarantees are posted. This field is available only when the **Type** field is set to *Royalty*. 
    - **Rebate output** – Select how the rebate or royalty should be paid:

        - *Financial* – Generate a free text credit note or accounts payable debit note, so that monies can be paid or received later. Note that provisions **can** be used with rebates where this option is selected. This option is the only available option when the **Type** field is set to *Royalty*.
        - *Item* – Generate a sales order for items according to the deal setup. On this sales order, a price of 0 (zero) is assigned to each item. Note that provisions **can't** be used with rebates where this option is selected.

    - **Rebate currency** – Select the currency to use when the rebate, deduction, or royalty is paid.
    - **Document notes** – Enter notes about the deal, as required.
    - **Cumulative guarantee** – You can set this option to *Yes* only if the **Type** field is set to *Royalty*. This option affects the calculation of guaranteed deduction payments. Here is an example:

        - The guarantee of the deal is to sell a value that will lead to a payment of $10,000 per quarter.
        - The organization that is selling the goods sells a value that causes a deduction payment of $12,000 in quarter 1. The result is a $12,000 royalty that is paid, minus the $10,000 guarantee.
        - If the **Cumulative guarantee** option is set to *Yes*, the additional $2,000 of royalties that were paid in quarter 1 apply to quarter 2. Therefore, the customer is guaranteed $8,000 (the $10,000 guarantee minus the $2,000 additional payment).
        - In quarter 2, you register sales that trigger a $5,000 royalty.
        - The system identifies a $3,000 payment (the $8,000 guarantee minus the $5,000 of paid royalties).
        - If the **Cumulative guarantee** option is set to *No*, the full $10,000 are guaranteed each quarter. This guarantee corresponds to a suggested payment of $5,000 payment in quarter 2 (the $10,000 guarantee minus the $5,000 of paid royalties).

1. Select **OK** to create the deal and close the dialog box.

This procedure creates the header level of the new deal. Next, you will add lines to the deal.

## Add lines to a deal

After you've created a deal as described in the previous section, you can open it from the list page. You can then add lines to identify the customers or vendors, items, time frames, a basis, and calculation methods for the deal. A deal can have one or multiple lines. If a deal has multiple lines, they are generally of the same type, or the same parameters are associated with them. Until you add lines to a deal, the deal won't actually do anything.

1. Open the appropriate rebate deals list page, as described in the previous section.
1. Find and open the deal that you want to work with.
1. On the **Rebate management** FastTab, select one of the following buttons to add a deal line to the grid:

    - **Add line** – Add a new, blank deal line.
    - **Copy line** – If an existing deal line resembles the deal line that you want to add, you can select this button to copy add a copy of it. The new deal line will include all the settings from the related Rebate management details. You can then edit the settings. For example, you will typically update the item relation and the rebate percentage.

1. On the new deal line, set the following fields:

    - **Rebate management number** – If you've [set up a number sequence](rebate-management-parameters.md) for Rebate management numbers, this field is automatically set to a unique, system-generated ID. Otherwise, enter a unique ID.
    - **Type** – The type of deal that the line applies to (*Rebate* or *Royalty*). The value is copied from the header and can't be changed.
    - **Description** – Enter a description of the deal line.
    - **Company** – Select the company (legal entity) that the deal line applies to. During processing, users can process only deal lines that are assigned to the company that they are currently using. The **Customer rebates deals** list page provides a multi-company view, based on the security access of the user. However, you can edit and process rebates only for the company that you're currently using.
    - **Account code** – Select the scope of customers or vendors that the deal line applies to:

        - *Table* – The deal line applies to a specific customer or vendor.
        - *Group* – The deal line applies to a group of customers or vendors. For more information about how to set up groups, see [Rebate management groups](rebate-management-groups.md).
        - *All* – The deal line applies to all customers or vendors.

    - **Account relation** – If you selected *Table* in the **Account code** field, select the customer or vendor that the deal applies to. If you selected *Group*, select the customer or vendor group. If you selected *All*, this field is unavailable.
    - **Item code** – Select the scope of items that the deal line applies to:

        - *Table* – The deal line applies to a specific item.
        - *Group* – The deal line applies to a group of items. For more information about how to set up groups, see [Rebate management groups](rebate-management-groups.md).
        - *All* – The deal line applies to all items.

    - **Item relation** – If you selected *Table* in the **Item code** field, select the item that the deal line applies to. If you selected *Group*, select the item group. If you selected *All*, this field is unavailable.
    - **Unit type** – Select the unit type that applies to the deal line (*Inventory unit* or *Catch weight unit*). Note that this field might be blank for older records. In this case, the *Inventory unit* value is assumed.
    - **(Inventory management parameters)** – In the remaining fields on the deal line, specify values for the inventory management parameters that will be used to define the items that are included in the deal (such as the item size, color, style, site, and warehouse). To add or remove the dimensions, select **Display dimensions** on the Action Pane.

1. On the Action Pane, select **Save**.
1. If you want to further limit the set of items that a deal line applies to, select the line, and then, on the **Rebate management** FastTab, select **Filter** to open a standard **Inquiry** dialog box.
1. For each deal line that you add, set up the calculation details and other details on the **Rebate management details** FastTab, as described in the next section.

## Add Rebate management details to a deal line

For each line in your deal, you must set up details on the **Rebate management details** FastTab. First select the deal line on the **Rebate management** FastTab. Then set values for that deal line by using the various tabs on the **Rebate management details** FastTab. The following subsections describe how to use each tab.

### Settings on the General tab

The **General** tab on the **Rebate management details** FastTab lets you set up the calculation method and basis for the selected deal line. This setup controls whether a minimum purchase is required, the posting profiles that are associated with the deal line, and the details of the calculation. The following table describes the fields that are available.

| Field | Description |
|---|---|
| Calculation method | Select the method to use when the selected deal line is combined with other deal lines (*Stepped*, *Cumulative*, *Rolling*, or *Total*). The value of this field can dramatically affect the outcome of your rebate calculations. For a full description of each method and examples that show how it affects the rebate calculation, see the [Calculation methods for deal lines](#calc-methods) section later in this topic. |
| Basis | Select whether the rebate is applied based on quantity (that is, the total number of units that are purchased or sold) or value (that is, the total price of goods that are purchased or sold). |
| Transaction type | <p>Select the point in the process when the calculation should occur:</p><ul><li>*Order* – Use the ordered quantity or value as the basis for the calculation.</li><li>*Delivered* – Use the delivered quantity or value as the basis for the calculation.</li><li>*Invoice* – Use the invoiced quantity or value as the basis for the calculation.</li></ul> |
| Unit | If you selected *Quantity* in the **Basis** field, select the unit that the quantity must be specified in. |
| Minimum amount | Enter the minimum amount that must be paid per period. You can enter a negative value to allow for negative rebate amounts if credit notes exceed sales for the period. |
| Rebate reduction principle | Select the [rebate reduction principle](rebate-reduction-principle.md) that applies to the deal line. |
| Variant number | If the deal line applies to an item that has variants, select the variant that the deal line applies to. |
| Vendor rebate basis | <p>This field is shown only for vendor rebates (that is, deals where the **Module** field is set to *Vendor*). Select the basis for the vendor rebate:</p><ul><li>*Purchase order* – The rebate that the vendor receives is based on the quantity or value on the purchase order.</li><li>*Sales order* – The vendor receives a rebate only after the goods have been sold. The rebate is based on the quantity or value on the sales order.</li></ul> |
| Price basis | <p>This field is shown only for vendor rebates (deals where the **Module** field is set to *Vendor*). If you selected *Sales order* in the **Vendor rebate basis** field, select the applicable price basis:</p><ul><li><p>*FIFO* – The **Calculate FIFO purchase price** periodic task must be run to calculate the rebate. (To run the task, go to **Rebates management \> Periodic tasks \> Calculate FIFO purchase price**.) A first in, first out (FIFO) rule will be used to calculate the value of the stock that is sold. This value will then be used to calculate the vendor rebates. Here is an example:</p><ul><li>**Stock sold:** 1,000 units at $3.00 each = $3,000</li><li>**Current purchase price, based on FIFO:** $2.00</li><li>**Working calculation:** *Units sold* × *Current purchase price* = 1,000 × $2.00 = $2,000</li></ul></li><li><p>*Latest Purchase Price* – The value from the last purchase transaction will be used to calculate the vendor rebates. Here is an example:</p><ul><li>**Stock sold:** 1,000 units at $3.00 each = $3,000</li><li>**Latest purchase price:** $2.00</li><li>**Working calculation:** *Units sold* × *Latest purchase price* = 1,000 × $2.00 = $2,000</li></ul></li><li><p>*Average Purchase Price* – The weighted average value for the last *X* months will be used to calculate the vendor rebates. If you select this option, you must enter the number of months in the **Number of months** field (which is available only when the **Price basis** field is set to *Average Purchase Price*). Here is an example:</p><ul><li>**Stock sold:** 1,000 units at $3.00 each = $3,000</li><li>**Average purchase price:** $2.00</li><li>**Working calculation:** *Units sold* × *Average purchase price* = 1,000 × $2.00 = $2,000</li></ul></li><li><p>*Sales Price* – The sales price will be used to calculate the vendor rebates. Here is an example:</p><ul><li>**Stock sold:** 1,000 units at $3.00 each = $3,000</li><li>**Average purchase price:** $2.00</li><li>**Working calculation:** *Units sold* × *Sales price* = 1,000 × $3.00 = $3,000</li></ul></li></ul> |
| Number of months | This field is shown only for vendor rebates (deals where the **Module** field is set to *Vendor*). If you selected *Average Purchase Price* in the **Price basis** field, enter the number of months that should be used. |
| Posting profile | Select the [posting profile](rebate-management-posting.md) that applies to the selected deal line. This profile is used only when the **Reconcile by** field on the deal header is set to *Line*. If the **Reconcile by** field is set to *Deal*, the posting profile that is set on the deal header is always used. If no posting profile is set on the deal line, the posting profile that is set on the deal header is used. |
| Posting profile for guarantee | This field works like the **Posting profile** field, but it applies only to royalties. |
| Payment type | The payment type for the posting profile that is selected for the deal. |
| Sales tax inclusive | Select whether the transaction is tax-inclusive. Tax inclusiveness is relevant only when the **Basis** field is set to *Value*. The invoice amount will be used as the tax-inclusive amount. If the rebate calculation is based on a percentage, the system will multiply the rebate percentage by the tax-inclusive amount. Note that the calculation uses the sales tax value from the deal line. |
| Include credit notes | <p>Set this option to *Yes* to include credit notes in the rebate calculation.</p><p>If you set this option to *Yes*, the effect varies, depending on the value of the **Transaction type** field:</p><ul><li>If the **Transaction type** field is set to *Invoice*, the calculation will factor in credit notes. This configuration is the usual configuration.</li><li>If the **Transaction type** field is set to *Order*, the calculation will factor in both sales orders that have negative values and open returned orders.</li></ul> |
| Discounted amount | Set this option to *Yes* to base the calculation on the discounted amount of the item or items in cases where deal line discounts are given. |
| Paid invoices only | Set this option to *Yes* if the calculation should consider only fully paid invoices. (In other words, rebates won't be calculated for partially paid invoices.) This option is available only when the **Transaction type** field is set to *Invoice*. |
| Include free text | Set this option to *Yes* to include free text invoices in the calculation. Free text invoices can be included only for deal lines where the **Item code** field is set to *All*. |
| Include settlement discount | Set this option to *Yes* to reduce the rebate by the first settlement discount. It's assumed that the organization will take the first settlement discount. Set this option to *No* to enable the settlement discount to be used later. |
| Document notes | Enter notes that should be used as transaction text on rebate transaction journal lines. |

### Settings on the Dates tab

The settings on the **Dates** tab on the **Rebate management details** FastTab define the frequency and timing of the calculations that are specified on the **General** tab. They determine how calculations occur at processing time.

This tab lets you specify the range of dates that the selected deal line is valid for and the calculation frequency. You can also specify whether the guarantee should be posted, and when.

You can use the buttons on the toolbar to add date lines to the grid or remove them. If multiple date lines exist, the valid date ranges must not overlap. Otherwise, you will receive an error message when you try to save the deal.

The following table describes the fields that are available for each date line.

| Field | Description |
|---|---|
| From date | Enter the first date that the date line applies to. If "from" and "to" dates are specified on the header of the deal, they are used as default values for every new date line. |
| To date | Enter the last date that the date line applies to. If "from" and "to" dates are specified on the header of the deal, they are used as default values for every new date line. |
| Per | Specify how often the deal line should be calculated. Enter an integer here, and then select a unit in the **Cumulate by** field. For example, to calculate every other week, set the **Per** field to *2* and the **Cumulate by** field to *Weeks*. |
| Cumulate by | Select the unit that applies to the **Per** setting. Select *Lifetime* to calculate over the whole lifetime of the deal line. Select *Customized period* to select a period that is defined in the general ledger. In this case, you must also set the **Period type** field. |
| Period type | This field is available only when the **Cumulate by** field is set to *Customized period*. The values that are available for selection come from the period types that are defined in the general ledger. |
| First day of the week | Specify how the weeks are identified for the period. This field is available only when the **Cumulate by** field is set to *Weeks*. |
| Claim per | Specify how often rebate monies can be claimed for the deal line. Enter an integer here, and then select a unit in the **Claim by** field. |
| Claim by | Select the unit that applies to the **Claim per** setting. Select *Lifetime* to allow claims just once during the whole lifetime of the deal line. Select *Customized period* to select a period that is defined in the general ledger. In this case, you must also set the **Claim period type** field. |
| Claim period type | This field is available only when the **Claim by** field is set to *Customized period*. The values that are available for selection come from the period types that are defined in the general ledger. |
| Process at posting | Select this check box if the claim line should be processed at posting time. This option is available only for deal lines where the **Transaction type** field on the **General** tab is set to *Delivered* or *Invoice*. For provisions, the provision will be posted when the delivery note or invoice is generated. |
| Guarantee per | This field applies only to royalty deals. Specify how often the guarantee of the royalty should be calculated during the period that is defined by the **Cumulate by** setting. Enter an integer here, and then select a payment time in the **Guarantee paid** field. |
| Guarantee paid | <p>This field applies only to royalty deals. It works in conjunction with the **Guarantee per** field to define the frequency of the guarantee calculation. Select one of the following values:</p><ul><li><p>*Beginning of period* – The guarantee is paid at the beginning of the agreement period that is defined for the date line. The full guarantee is processed first. Only the value of royalties that exceed the guaranteed amount is posted as a royalty. Here is an example:</p><ul><li>**Guarantee minimum:** $10,000 over two months.</li><li>**Month 1:** $10,000 were posted as a guarantee, and $0 in royalties were posted.</li><li>**Month 2:** $2,000 were posted to royalties, and $0 in guarantees were posted.</li><li>**Working calculation:** *Remaining guarantee* – *Royalties posted* = $0 – $2,000 = -$2,000.</li></ul><p>Because a royalty payment of $2,000 is required, a journal is created for $2,000.</p><p>**Note:** The guarantee should be calculated and posted together with the deductions provision for the first period.</p></li><li><p>*End of period* – The guarantee isn't paid until the end of the deductions agreement, as defined on the date line. Here is an example:</p><ul><li>**Guarantee minimum:** $10,000 over two months.</li><li>**Month 1:** $5,000 were posted as a royalty, and a journal was created.</li><li>**Month 2:** $7,000 were posted as a royalty, and a journal was created.</li><li>**Working calculation:** Because the royalties exceed the guarantee amount, $0 are posted to the guarantee.</li></ul><p>**Note:** The guarantee should be calculated and posted only together with the deductions and rebates transaction for the final period.</p></li></ul> |
| Guarantee minimum | This field applies only to royalty deals. Enter the minimum amount of the guarantee for a royalty, in the currency that is defined on the deal header. |

### Settings on the Lines tab

The **Lines** tab of the **Rebate management details** FastTab lets you define calculation lines for the selected deal line. Each calculation line establishes a quantity or value threshold, and a related compensation amount or items. The **Basis** field on the **General** specifies whether each calculation line is based on a quantity or a value.

You can use the buttons on the toolbar to add calculation lines to the grid or remove them. You can have any number of calculation lines. However, if multiple calculation lines exist, the "to" and "from" quantity or value ranges must not overlap.

The following table describes the fields that are available for each calculation line.

| Field | Description |
|---|---|
| From qty/value | Enter the minimum quantity or value that the calculation line applies to. |
| To qty/value | Enter the maximum quantity or value that the calculation line applies to. |
| Rebate management method | <p>This field is available only for deals where the **Rebate output** field on the header is set to *Financial*. Select the method to use to calculate the rebate:</p><ul><li>*Fixed* – A fixed price amount is used for the line.</li><li>*Percent* – A percentage of the sale amount is used.</li><li>*Rate* – A fixed price amount per order is used.</li></ul><p>**Important:** We strongly recommend that you use the same method for every calculation line on the **Lines** tab. If a new method is required, create a new deal line. Remember that you can use the **Copy line** button on the **Rebate management** FastTab to create a new deal line from an existing deal line.</p><p>**Note:** If the **Rebate output** field is set to *Item*, this field is always set to *Fixed*. For more information about how to specify the items, see the text that follows this table. |
| Rebate management amount | This field is available only for deals where the **Rebate output** on the header is set to *Financial*. Enter the amount that should be used to calculate the rebate, based on the method that you selected in the **Rebate management method** field. |

As was mentioned in the previous table, for deals where the **Rebate output** field on the header is set to *Item*, you must specify the items that will be provided for every calculation line on the **Lines** tab. To specify the items, follow these steps.

1. On the **Lines** tab, create the required calculation line if it doesn't exist, and select it.
1. If the deal hasn't been saved since you created the calculation line, select **Save** on the Action Pane.
1. On the **Lines** tab, select **Items**.
1. On the **Items** page, use the buttons on the Action Pane to add items to the grid, or remove items, as required. For each row, set the following fields:

    - **Item number** – Select the item that will be provided.
    - **(Other dimensions)** – If you must use more dimensions to define the item (for example, item configuration, size, color, style, site, or warehouse), specify them. To add or remove available dimensions, select **Display dimensions** on the Action Pane.
    - **Quantity** – Enter the quantity that will be provided after the threshold for the selected calculation line is met.
    - **Unit** – Select the unit that the **Quantity** value is specified in.
    - **Multiple** – This field works in conjunction with the **Quantity** field. For example, on an item line, you set the **Quantity** field to *2* and the **Multiple** field of *100*. If you then have a total sales order quantity of 150, two of the items will be free (two per 100).

### Settings on the Inventory dimensions tab

The **Inventory dimensions** tab on the **Rebate management details** FastTab shows all the available dimension values for the product that is specified for the selected deal line. It includes dimensions that aren't shown on the **Rebate management** FastTab. You can edit values only for those dimensions that apply to the selected product.

You can add more dimensions to the grid on the **Rebate management** FastTab by selecting **Display dimensions** on the Action Pane.

## <a name="calc-methods"></a>Calculation methods for deal lines

Every time that you set up details for one of your deal lines, as described in the previous section, you must select the calculation method for that line. This section explains each calculation method and provides examples that show how each method calculates the total rebate for orders and deal lines. In these examples, the orders and deal lines are identical. Only the calculation methods differ.

### Stepped calculation method

The stepped calculation method calculates on a step-by-step basis, where each deal line incrementally contributes to the rebate until the sales quantity or value is reached. The steps can be based on either the quantity or the value of the goods that are sold, depending on the setting of the **Basis** field on the **General** tab of the **Rebate management details** FastTab.

For example, a deal line is set up so that the **Calculation method** field is set to *Stepped* and the **Basis** field is set to *Value*. It includes calculation lines that provide the following rebates:

- **Line A:** 10 percent up to $1,000
- **Line B:** 25 percent up to $2,500

If the value of the goods that were purchased or sold is $2,000, the resulting rebate of $350 is calculated in the following way:

- **Rebate (A):** *Threshold (A)* × *Percentage (A)* = $1,000 × 10 percent = $100
- **Rebate (B):** (*Value sold* – *Threshold (A)*) × *Percentage (B)* = ($2,000 – $1,000) × 25 percent = $250
- **Total rebate:** *Rebate (A)* + *Rebate (B)* = $100 + $250 = $350

If the **Basis** field is set to *Quantity* instead of *Value*, the stepped calculation method works in a similar way. The first step is used for the identified quantity until the second step is reached. The second step is then used for all quantity above the first step, until the third step is reached. This process then continues through all subsequent steps.

### Cumulative calculation method

The cumulative calculation method uses just one calculation line to calculate the rebate. If multiple calculation lines are available for the deal line, the highest-value or highest-quantity calculation line that is reached is used for the whole quantity or value. Like the other calculation methods, the cumulative method uses the setting of the **Basis** field on the **General** tab of the **Rebate management details** FastTab to determine whether the sales quantity or the sales value is used to calculate the rebates.

For example, a deal line is set up so that the **Calculation method** field is set to *Cumulative* and the **Basis** field is set to *Value*. It includes calculation lines that provide the following rebates:

- **Line A:** 10 percent up to $1,000
- **Line B:** 25 percent up to $2,500

If the value of the goods that were purchased or sold is $2,000, the calculation uses only line B. The resulting rebate of $500 is calculated in the following way:

- **Total rebate:** *Value sold* × *Rebate (B)* = $2,000 × 25 percent = $500

### Rolling calculation method

The rolling calculation method calculates all possible calculation lines for the deal. If there are multiple calculation lines, and more than one of them is reached, all the calculation lines that are reached will be used, but upper thresholds apply to each percentage. Like the other calculation methods, the rolling method uses the setting of the **Basis** field on the **General** tab of the **Rebate management details** FastTab to determine whether the sales quantity or the sales value is used to calculate the rebates.

For example, a deal line is set up so that the **Calculation method** field is set to *Rolling* and the **Basis** field is set to *Value*. It includes calculation lines that provide the following rebates:

- **Line A:** 10 percent up to $1,000
- **Line B:** 25 percent up to $2,500

If the value of the goods that were purchased or sold is $2,000, the resulting rebate of $600 is calculated in the following way:

- **Rebate (A):** *Threshold (A)* × *Percentage (A)* = $1,000 × 10 percent = $100
- **Rebate (B):** *Value sold* × *Percentage (B)* = $2,000 × 25 percent = $500
- **Total rebate:** *Rebate (A)* + *Rebate (B)* = $100 + $500 = $600

### Total calculation method

The total calculation method uses all calculation lines to calculate the rebate. It applies the total quantity to calculate the rebate for each calculation line that is reached, and each calculation line applies its percentage to the full amount. Like the other calculation methods, the total method uses the setting of the **Basis** field on the **General** tab of the **Rebate management details** FastTab to determine whether the sales quantity or the sales value is used to calculate the rebates.

For example, a deal line is set up so that the **Calculation method** field is set to *Total* and the **Basis** field is set to *Value*. It includes calculation lines that provide the following rebates:

- **Line A:** 10 percent up to $1,000
- **Line B:** 25 percent up to $2,500

If the value of the goods that were purchased or sold is $2,000, the resulting rebate of $700 is calculated in the following way:

- **Rebate (A):** *Value sold* × *Percentage (A)* = $2,000 × 10 percent = $200
- **Rebate (B):** *Value sold* × *Percentage (B)* = $2,000 × 25 percent = $500
- **Total rebate:** *Rebate (A)* + *Rebate (B)* = $200 + $500 = $700
