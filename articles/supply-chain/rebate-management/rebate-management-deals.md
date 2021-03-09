---
# required metadata

title: Rebate management deals
description: This topic describes how to create Rebate management deals, which are used to control different methods and bases for calculating rebates and royalties, including rules for inclusions and exclusions.
author: sherry-zheng
manager: tfehr
ms.date: 02/19/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: TAMRebateDeal
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: chuzheng
ms.search.validFrom: 2021-02-19
ms.dyn365.ops.version: Release 10.0.18
---

# Rebate management deals

[!include [banner](../includes/banner.md)]

Rebate management deals are used to control different methods and bases for calculating rebates and royalties, including rules for inclusions and exclusions. There are three types of rebate management deals (customer rebates, customer royalties, and vendor rebates) but all types use similar settings. This topic points out differences where they exist.

## Create a new deal

Do the following steps to create a new deal:

1. Go to one of the following pages, depending on which type of deal you want to create (you can create all types of deals from the **All rebate management deals** page):

    - **Rebate management \> Rebate management deals \> All rebate management deals**<br>- Go here to work with all types of deals.
    - **Rebate management \> Rebate management deals \> Customer rebate deals** <br>- Provides the same list and settings pages as the **All rebate management deals** page, but filtered to show and create only customer rebate deals.
    - **Rebate management \> Rebate management deals \> Customer royalty deals**<br>- Provides the same list and settings pages as the **All rebate management deals** page, but filtered to show and create only customer royalty deals.
    - **Rebate management \> Rebate management deals \> Vendor rebate deals**<br>-  Provides the same list and settings pages as the **All rebate management deals** page, but filtered to show and create only vendor rebate deals.

1. On the Action Pane, select **New**.
1. The **Create new deal** dialog box opens. Make the following settings:
    - **Rebate management deal** - Provided you have [set up a number sequence](rebate-management-parameters.md) for rebate deals, an automatically generated and unique ID should already appear here. Otherwise, enter a unique ID.
    - **Description** - Enter a description of the deal.
    - **Module** - Set to the type of partner the deal will apply to (*Customer* or *Vendor*). Depending on which page you started on, this may be pre-filled and read-only to match your selected deal type.
    - **Type**  - Set to the type of deal you want to create (*Rebate* or *Royalty*). Depending on which page you started on, this may be pre-filled and read-only to match your selected deal type.
    - **Reconcile by** - This affects how the deal will be calculated and reconciled. Choose one of the following:
        - *Deal* - A single rebate will be processed for all rebates and deductions within the deal.
        - *Line* - Rebates will be processed for each line within a deal.
    - **Posting profile** - Select the [posting profile](rebate-management-posting.md) that should apply to transactions where this deal will apply. This setting is only active when **Reconcile by** is set to *Deal*. When you reconcile by line, you will assign the profile later, for each line you add to the deal.
    - **Posting profile for guarantee** - This setting is only active when **Type** is set to *Royalty*. [Posting profiles](rebate-management-posting.md) are only required for guarantee transactions if the guarantee applies to a royalty. The posting profile is not mandatory but guarantees will error at posting time if not entered.
    - **Rebate output** - Choose how the rebate or royalty will be paid. Select one of the following:
        - *Financial* – Generate a free text credit note or accounts payable debit note so that subsequently monies will be paid or received. Note that provisions _can_ be used with these types of rebates. This is the only option available when **Type** is set to *Royalty*.
        - *Item* – Generate a sales order for items as per the deal setup, with each item assigned a price of zero. Note that provisions _cannot_ be used with these types of rebates.
    - **Rebate currency** - Select the currency to use when paying the rebate, deduction, or royalty.
    - **Document notes** - Enter some notes about the deal, as needed.
    - **Cumulative guarantee** - You can only set this to *Yes* for deals where **Type** is *Royalty*. This setting affects the calculation of guaranteed deductions payments. For example:
        - The guarantee of the deal is to sell a value that will result in a $10,000 payment per quarter.
        - The organization selling the goods sells a value which results in a deductions payment of $12,000 in the first quarter. This results in a $12,000 royalty paid minus the $10,000 guarantee.
        - If **Cumulative guarantee** is set to *Yes*, the additional $2,000 of royalties paid in the first period applies to the second, so the customer is guaranteed $8,000 ($10,000 guarantee minus $2,000 additional payment).
        - In the second quarter, you register sales that would trigger a $5,000 royalty.
        - The system then identifies that the $8,000 guarantee minus the $5,000 royalties paid results in a $3,000 payment.
        - If **Cumulative guarantee** is set to *No*, the full $10,000 would be guaranteed each period, which would then equate to a suggested $5,000 payment in period 2 ($10,000 guarantee minus $5,000 royalties equals $5,000 suggested payment).

1. Select **OK** to create the deal and close the dialog box. This creates the header level of the new deal.

## Add lines to a deal

Once you have created a deal, as described in the previous section, you'll be able to open it from the list page and then add customers, items, and calculation details. Until you add lines to a deal, the deal won't actually do anything.

Lines are added directly to a deal to identify the customers/vendors, items, time frames, basis, and calculation methods for the deal. A deal may have a single or multiple lines. If a deal has multiple lines, the lines are generally of the same type or have the same parameters associated.

1. Open the appropriate rebate deals page, as described in the previous section, and then find and open the deal you want to work with.

1. On the **Rebate management** FastTab, select one of the following from the toolbar:
    - **Add line** - Adds a new, blank deal line to the grid.
    - **Copy line** - If a deal line already exists and is similar to the deal line you are planning to add, then you might choose this option. It will create a copy of the selected deal line (including all settings from the related **Rebate management details**) and then let you edit the settings for the new deal line (typically by updating the item relation and rebates percentage).
1. Make the following settings for the new deal line:
    - **Rebate management number** - Provided you have [set up a number sequence](rebate-management-parameters.md) for rebate management numbers, an automatically generated and unique ID should already appear here. Otherwise, enter a unique ID.
    - **Type**  - Shows the type of deal the line applies to (*Rebate* or *Royalty*). This is copied from the header and can't be changed.
    - **Description** - Enter a description for the deal line.
    - **Company** Select the company (legal entity) for which the deal line applies. During processing, users will only be able to process deal lines assigned to the company they are using at the time. The **Customer rebates deals** page provides a multi-company view, based on the security access of the user. However, you can only edit and process rebates for the company you are currently using.
    - **Account code** - Establishes the scope of customers or vendors for which the deal line applies. Select one of the following:
        - *Table* - To select an individual customer or vendor.
        - *Group* - To select a group of customers or vendors. For more information about how to set up groups, see [Rebate management groups](rebate-management-groups.md).
        - *All* - To set the deal line to apply to all customers or vendors.
    - **Account relation** - Depending on the **Account code** setting, select the group or specific vendor/customer for which the deal line applies. This setting is disabled when **Account code** is set to *All*.
    - **Item code** - Establishes the scope of items for which the deal line applies. Select one of the following:
        - *Table* - To select an individual item.
        - *Group* - To select a group of items. For more information about how to set up groups, see [Rebate management groups](rebate-management-groups.md).
        - *All* - To set the deal line to apply to all items.
    - **Item relation** - Depending on the **Item code** setting, select the group or specific item for which the deal line applies. This setting is disabled when **Item code** is set to *All*.
    - Inventory management parameters - Using the remaining fields of the deal line, specify values for the inventory management parameters that will be used to define the items included in the deal (such as item size, color, style, site, warehouse, and so on). To add or remove the dimensions available, select **Display dimensions** from the Action Pane.
1. Select **Save** on the Action Pane.
1. If you'd like to further restrict the set of items a deal line applies to, select the line and then select the **Filter** button on the **Rebate management** FastTab toolbar to open a standard **Inquiry** dialog box.
1. For each deal line that you add, set up the calculation and other details using the **Rebate management details** FastTab, as described in the next section.

## Add rebate management details to a deal line

For each line in your deal, you must set up details using the **Rebate management details** FastTab. First select the deal line on the **Rebate management** FastTab, then make settings for that deal line using the various tabs of the **Rebate management details** FastTab. The following subsections describe how to use each of the tabs available here.

### Settings on the General tab

The **General** tab of the the **Rebate management details** FastTab lets you set up the calculation method and basis for the selected deal line. This controls whether a minimum purchase is required, the posting profiles associated with the deal line, and the details of the calculation. The following table describes the settings available here.

| Field | Description |
|---|---|
| Calculation method | Choose the method to use when combining the selected deal line with other deal lines. This can dramatically affect the outcome of your rebate calculations. The available methods are *Stepped*, *Cumulative*, *Rolling*, and *Total*. For a complete description of each method and examples of how they affect the rebate calculation, see [Calculation methods for deal lines](#calc-methods). |
| Basis | Choose whether the rebate applies based on *Quantity* (the total number of units purchased/sold) or *Value* (the total price of goods purchased/sold). |
| Transaction type | Select point in the process when the calculation will occur. Choose one of the following:<ul><li>*Order* - Use the ordered quantity or value as the basis of the calculation.</li><li>*Delivered* - Use the delivered quantity or value as the basis of the calculation.</li><li>*Invoice* - Use the invoiced quantity or value as the basis of the calculation.</li> |
| Unit | When **Basis** is set to *Quantity* field, select the unit in which the quantity is to be specified. |
| Minimum amount | Enter the minimum amount that must be paid per period. You can enter a negative value, if needed, to allow negative rebate amounts if credit notes are greater than sales for the period. |
| Rebate reduction principle | Select the [rebate reduction principle](rebate-reduction-principle.md) that applies for the deal line. |
| Variant number | If the deal line applies to an item that has variants, select the variant for which the deal line applies. |
| Vendor rebate basis | This field is only shown for vendor rebates (deals where **Module** is *Vendor*). Select one of the following to establish the vendor rebate basis:<ul><li>*Purchase order* - The vendor receives a rebate based on the purchase order quantity/values.</li><li>*Sales order* - The vendor receives a rebate only after the goods have been sold. This is based on the sales order quantity/value</li></ul> |
| Price basis | This field is only shown for vendor rebates (deals where **Module** is *Vendor*). If the **Vendor rebates basis** is set to *Sales order*, select the applicable price basis. Choose one of the following:<ul><li>*FIFO* - The **Calculate FIFO purchase price** periodic task must run to calculate the rebate (available at **Rebates management > Periodic tasks > Calculate FIFO purchase price**). Based on a FIFO rule, the system will calculate the value of the sold stock. This value will then be used to calculate the vendor rebates.<br><br>For example:<br>1,000 (a) units sold @ $3.00 (b) = $3,000<br>Current purchase price based on FIFO is $2.00 (c)<br><br>Working calculation:<br>1,000 (a) \* $2.00 (c) = $2,000<br><br></li><li>*Latest Purchase Price* - The value from the last purchased transaction will be used to calculate the vendor rebate.<br><br>For example:<br>1,000 (a) units sold @ $3.00 (b) = $3,000<br>Latest Purchase Price is $2.00 (c)<br><br>Working calculation:<br>1,000 (a) \* $2.00 (c) = $2,000<br><br></li><li>*Average Purchase Price* - The weighted average value for the last X months will be used to calculate the value of the vendor rebates. The number of months must be entered into the **Number of months** field. This option is only available when **Price basis** is set to *Average purchase price*.<br><br>For example:<br>1,000 (a) units sold @ $3.00 (b) = $3,000<br>Average purchase price is $2.00 (c)<br><br>Working calculation:<br>1,000 (a) \* $2.00 (c) = $2,000<br><br></li><li>*Sales Price* - The sales price will be used to calculate the rebates.<br><br>For example:<br>1,000 (a) units sold @ $3.00 (b) = $3,000<br>Average purchase price is $2.00 (c)<br><br>Working Calculation:<br>1,000 (a) * $3.00 (b) = $3,000 |
| Number of months | This field is only shown for vendor rebates (deals where **Module** is *Vendor*). Select the number of months to be used when the **Price basis** is *Average purchase price*. |
| Posting profile | Select the [posting profile](rebate-management-posting.md) that applies for the selected deal line. This profile is only used when **Reconcile by** is set to *Line* in the deal header. If the **Reconcile by** is set to *Deal*, the posting profile set in the deal header is always used. If no posting profile is set at the deal line, the header posting profile is used. |
| Posting profile for guarantee | This setting only applies for royalties. It works similarly to the **Posting profile** setting, but applies to royalties. |
| Payment type | Displays the payment type for the selected **Posting profile** for this deal. |
| Sales tax inclusive | Choose whether the transaction is tax inclusive, which is only relevant when **Basis** is set to *Value*. The invoice amount will be used as the tax inclusive amount. If the rebate calculation based on a percentage, the system will multiply the rebate percentage by the tax inclusive amount. Note that the calculation uses the sales tax value from the deal line. |
| Include credit notes | Choose whether to include credit notes in the rebate calculation. The effect varies based on the **Transaction type** setting as follows:<ul><li>If the **Transaction type** is *Invoice* and this option is set to *Yes*, then the calculation will factor in credit notes. This is the usual configuration.</li><li>If the **Transaction type** is *Order* and this option is set to *Yes*, the calculation will factor in both sales orders with negative values and open returned orders</li></ul> |
| Discounted amount | Set this to *Yes* to base the calculation on the discounted amount of the item or items in cases where deal line discounts are given. |
| Paid invoices only | Set this to *Yes* if the calculation should only check for fully paid invoices (rebates won't be calculated for partially paid invoices). This option is only available when **Transaction type** is set to *Invoice*. |
| Include free text | Set this to *Yes* to include free text invoices in the calculation. Free text invoices can only be included for deal lines where **Item code** is set to *All*. |
| Include settlement discount | Set this to *Yes* to reduce the rebate by the first settlement discount. It is assumed that the organization will take the first settlement discount. Set this to *No* to allow the settlement discount to be used at a later time. |
| Document notes | Enter notes to be used as transaction text in rebate transaction journal lines. |

### Settings on the Dates tab

The **Dates** tab of the the **Rebate management details** FastTab specifies the dates for which the selected deal line is valid. It specifies the valid date range, the calculation frequency, whether the guarantee is posted, and when. These settings determine how calculations occur at processing time. If multiple date lines exist, the valid date ranges must not overlap. If the dates overlap, you will see an error message when you try to save the deal. These setting determine the frequency and timing of the calculations identified on the **General** tab.

Use the buttons in the toolbar of this tab to add or remove date lines from the grid. The following table describes the settings available for each date line.

| Field | Description |
|---|---|
| From date | Enter the first date for which the date line applies. If from and to dates are specified on the header of the deal, those values are used as defaults for each new date line. |
| To date | Enter the last date on which the deal applies. If from and to dates are specified on the header of the deal, those values are used as defaults for each new date line. |
| Per | Specify how often the deal line is to be calculated. Enter an integer here and then specify a unit in the **Cumulate by** field. For example, to calculate every other week, set **Per** to *2* and **Cumulate by** to *Weeks*. |
| Cumulate by | Specify the unit that applies to the **Per** setting. Set this to *Lifetime* to calculate over the entire lifetime of the deal line. Select *Customized period* to choose a period defined in the general ledger, in which case you must also make a selection for the **Period type** field. |
| Period type | This field is only active when **Cumulate by** is set to *Customized period*. The values available here come from the period types defined in the general ledger. |
| First day of the week | Specify how the weeks are identified for the period. This field is only active when **Cumulate by** is set to *Weeks*.  |
| Claim per | Specify how often rebate monies can be claimed for the deal line. Enter an integer here and then specify a unit in the **Claim by** field. |
| Claim by | Specify the unit that applies to the **Claim per** setting. Set this to *Lifetime* to allow claims just once over the entire lifetime of the deal line. Select *Customized period* to choose a period defined in the general ledger, in which case you must also make a selection for the **Period type** field. |
| Claim period type | The claim period type is only available for selection if the **Claim by** field is set to *Customized period*. The values available here come from the period types defined in the general ledger. |
| Process at posting | When this is selected, the claim line is processed at posting time. This option is only available for deal lines where the **Transaction type** (on the **General** tab) is *Delivery* or *Invoice*. If it is a provision, it will be posted at the time when the delivery note or invoice is generated. |
| Guarantee per | This setting only applies to royalty deals. Specify how often the guarantee of the royalty is to be calculated during the period established by the **Cumulate by** setting. Enter an integer here and then select a payment time from the **Guarantee paid** field. |
| Guarantee paid | This setting only applies to royalty deals. It works in conjunction with the **Guarantee per** field to determine the frequency of the guarantee calculation. Choose one of the following:<ul><li>*Beginning of period* - The guarantee is paid up front, at the beginning of the agreement period, as defined for the date line. The full guarantee is processed first. Only the value of the royalties over the guaranteed amount are posted as a royalty.<br><br>For example:<br>Guarantee minimum: $10,000 over 2 months<br>Month 1: $10,000 was posted as guarantee and $0 in royalties posted.<br>Month 2: $2,000 was posted to royalties and $0 in guarantee.<br><br>Working calculation:<br>$0,00 guarantee remaining – $2,000 royalties posted = -$2,000, a royalties payment of $2,000 is required, therefore a journal is created for $2,000<br><br>**Note**: The guarantee should be calculated and posted along with the deductions provision for the first period.<br><br></li><li>*End of period* - The guarantee is not paid until the end of the deductions agreement as defined for the date line.<br><br>For example:<br>Guarantee minimum: $10,000 over 2 months<br>Month 1: $5000 posted as royalty and journal created<br>Month 2: $7000 posted as royalty and journal created<br><br>Working calculation:<br>As the royalties exceed the guarantee amount, $0 will be posted to the guarantee.<br><br>**Note**: The guarantee should only be calculated and posted along with the deductions and rebates transaction for the final period. |
| Guarantee minimum | This setting only applies to royalty deals. Enter the minimum amount of the guarantee for a royalty using the currency defined on the deal header. |

### Settings on the Lines tab

Use the **Lines** tab of the the **Rebate management details** FastTab to specify calculation lines for the selected deal line. Each calculation line establishes a quantity/value threshold and a related compensation amount/items. The denomination of each calculation line here (quantity or value) is established by the **Basis** setting on the **General** tab. You can have any number of calculation lines here, but if you have more than one, then the to/from ranges must not overlap.

Use the buttons in the toolbar of this tab to add or remove calculation lines from the grid. The following table describes the settings available for each calculation line.

| Field | Description |
|---|---|
| From qty/value | Enter the minimum quantity or value for which this calculation line applies. |
| To qty/value | Enter the maximum quantity or value for which this calculation line applies. |
| Rebate management method | This field is only active for deals where **Rebate output** is set to *Financial* in the header. It establishes method used to calculate the rebate. (When **Rebate output** is set to *Item*, this field is always set to *Fixed*; see the text after this table for more information about how to specify the items.) Choose one of the following values:</p><ul><li>*Fixed* - Establishes a fixed price amount for the line. </li><li>*Percent* - Establishes a percentage of the sale amount.</li><li>*Rate* - Establishes a fixed price amount per order.</li></ul><p>**Important**: We strongly recommend that you use the same rebate management method for each of the calculation lines defined on this tab. If a new method is needed, then create a new deal line. Remember you can use copy to create a similar deal line.  |
| Rebate management amount | This field is only active for deals where **Rebate output** is set to *Financial* in the header. Enter the amount used to calculate the rebate based on the selected **Rebate management method**. |

As mentioned in the table, for deals where **Rebate output** method is set to *item*, you must specify the items that will be provided for each of the calculation lines specified on the **Lines** tab of the the **Rebate management details** FastTab. To do this:

1. Create the required calculation line on the **Lines** tab (if needed) and select it.
1. If the deal hasn't been saved since you created the calculation line, select **Save** on the Action Pane.
1. Select **Items** from the toolbar on the **Lines** tab.
1. The **Items** page opens. Use buttons in the Action Pane to add or remove items in the grid as needed. For each row, make the following settings:
    - **Item number** - Select the item that will be provided.
    - Other dimensions - If you need to use more dimensions to specify the item (such as item configuration, size, color, style, site, warehouse, and so on), then specify them as needed. To add or remove the dimensions available, select **Display dimensions** from the Action Pane.
    - **Quantity** - Enter the quantity that will be provided once the threshold for the selected calculation line is met.
    - **Unit** - Select the unit in which the **Quantity** is defined.
    - **Multiple** - This setting works in conjunction with the **Quantity** value. For example, on an item line, we set the **Quantity** to 2 and set a **Multiple** value of *100*. We then have a total sales order quantity of 150. In this scenario, 2 of the items would be free (2 per/100).

### Settings on the Inventory dimensions tab

The **Inventory dimensions** tab of the the **Rebate management details** FastTab shows all the available dimension values for the product specified for the selected deal line, including dimensions not shown on the **Rebate management** FastTab. You can only edit values for those dimensions that apply to the selected product. You can also add more of these dimensions to the grid on the **Rebate management** FastTab by selecting **Display dimensions** from the Action Pane.

<a name="calc-methods"></a>

## Calculation methods for deal lines

Each time you set up details for one of your deal lines, as described in the previous section, you must choose the calculation method for that line. This section explains each calculation method and provides examples of how the total rebate is calculated in each case for otherwise identical orders and deal lines.

### The stepped calculation method

The stepped calculation method calculates on a step basis, with each deal line contributing to the rebate until the sales quantity or value is reached. The step can be set based on either the quantity of the goods sold or the value of the goods sold. The method uses the **Basis** setting to choose whether to use sales quantity or sales value to calculate the rebates.

For example, suppose a deal line uses a **Calculation method** of *Stepped* and a **Basis** of *Value*, and includes calculation lines that provide the following rebates:

- Line (A): 10% up to $1,000
- Line (B): 25% up to $2,500

If $2,000 was purchased/sold, then the resulting rebate would be $350, which is calculated as follows:

- Rebate (A) = Threshold (A) \* Percentage (A) = $1,000 \* 10% = $100
- Rebate (B) = (Value Sold – Threshold (A)) \* Percentage (B) = ($2,000 - $1,000) \* 25% = $250
- Total Rebate = Rebate (A) + Rebate (B) = $100 + $250 = $350

The quantity basis is based on the quantity of goods sold, rather than the value, and works similarly. In the stepped method, the first step is used for the identified quantity until the second step is reached. From there, the second step will be used for all quantity above the first step until the third or subsequent step. This will continue on through all subsequent steps.

### The cumulative calculation method

The cumulative method calculation method uses just one calculation line to calculate the rebate. If there are multiple calculation lines available for the deal line, the highest value or quantity calculation line that is reached is the one used for the entire quantity or value. As with the other calculation methods, the cumulative method uses the **Basis** setting to choose whether to use sales quantity or sales value to calculate the rebates.

For example, suppose a deal line uses a **Calculation method** of *Cumulative* and a **Basis** of *Value*, and includes calculation lines that provide the following rebates:

- Line (A): 10% up to $1,000
- Line (B): 25% up to $2,500

If $2,000 was purchased/sold, then the resulting rebate would be $500 because it uses only line (B). The calculation is as follows:

- Total Rebate = Value Sold \* Rebate (B) = $2000 \* 25% = $500

### The rolling calculation method

The rolling method calculates all possible calculation lines for the deal. If there are multiple calculation lines and more than on is reached, all of the calculation lines reached will be used, but upper thresholds apply for each percentage. As with the other calculation methods, the rolling method uses the **Basis** setting to choose whether to use sales quantity or sales value to calculate the rebates.

For example, suppose a deal line uses a **Calculation method** of *Rolling* and a **Basis** of *Value*, and includes calculation lines that provide the following rebates:

- Line (A): 10% up to $1,000
- Line (B): 25% up to $2,500

If $2,000 was purchased/sold, then the resulting rebate would be $600. The calculation is as follows:

- Rebate (A) = Threshold (A) \* Percentage (A) = $1,000 \* 10% = $100
- Rebate (B) = Value Sold \* Percentage (B) = $2,000 \* 25% = $500
- Total Rebate = Rebate (A) + Rebate (B) = $100 + $500 = $600

### The total calculation method

The total total calculation method uses all calculation lines to calculate the rebate, and applies the total quantity to calculate the rebate for each reached calculation line and each calculation line applies its percentage to the full amount. As with the other calculation methods, the rolling method uses the **Basis** setting to choose whether to use sales quantity or sales value to calculate the rebates.

For example, suppose a deal line uses a **Calculation method** of *Total* and a **Basis** of *Value*, and includes calculation lines that provide the following rebates:

- Line (A): 10% up to $1,000
- Line (B): 25% up to $2,500

If $2,000 was purchased/sold, then the resulting rebate would be $700. The calculation is as follows:

- Rebate (A) = Value Sold \* Percentage (A) = $2,000 \* 10% = $200
- Rebate (B) = Value Sold \* Percentage (B) = $2,000 \* 25% = $500
- Total Rebate = Rebate (A) + Rebate (B) = $200 + $500 = $700
