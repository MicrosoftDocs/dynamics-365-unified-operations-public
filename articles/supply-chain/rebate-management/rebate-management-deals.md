---
# required metadata

title: Rebate management deals
description: 
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

Rebate management deals are used to control different methods and bases for calculating rebates and royalties, including rules for inclusions and exclusions. There are three types of rebate management deals, but all types use similar settings. 

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
    - **Posting profile for guarantee** - This setting is only active when **Type** is set to *Royalty*. <!-- KFM: Description needed ("Posting profiles are only required for guarantee transactions if the guarantee applies to a royalty. The posting profile is not mandatory but guarantees will error at posting time if not entered.") -->
    - **Rebate output** - Choose how the rebate or royalty will be paid. Select one of the following:
        - *Financial* – Generate a free text credit note or accounts payable debit note so that subsequently monies will be paid or received. Note that provisions _can_ be used with these types of rebates. This is the only option available when **Type** is set to *Royalty*.
        - *Item* – this will generate a sales order for zero value items as per the setup. Note that provisions _cannot_ be used with these types of rebates. <!-- KFM: Which setup? -->
    - **Rebate currency** - Select the currency to use when paying the rebate, deduction, or royalty.
    - **Document notes** - <!-- KFM: Description needed. -->
    - **Cumulative guarantee** - <!-- KFM: Description needed. -->
1. Select **OK** to create the deal and close the dialog box. This creates the header level of the new deal.

## Add lines to a deal

Once you have created a deal, as described in the previous section, you'll be able to open it from the list page and then add customers, items, and calculation details. Until you add lines to a deal, the deal won't actually do anything.

Lines are added directly to a deal to identify the customers/vendors, items, time frames, basis, and calculation methods for the deal. A deal may have a single or multiple lines. If a deal has multiple lines, the lines are generally of the same type or have the same parameters associated.

1. Go to one of the following pages, depending on which type of deal you want to work with (you can work with all types of deals from the **All rebate management deals** page):

    - **Rebate management \> Rebate management deals \> All rebate management deals**<br>- Go here to work with all types of deals.
    - **Rebate management \> Rebate management deals \> Customer rebate deals** <br>- Provides the same list and settings pages as the **All rebate management deals** page, but filtered to show and create only customer rebate deals.
    - **Rebate management \> Rebate management deals \> Customer royalty deals**<br>- Provides the same list and settings pages as the **All rebate management deals** page, but filtered to show and create only customer royalty deals.
    - **Rebate management \> Rebate management deals \> Vendor rebate deals**<br>-  Provides the same list and settings pages as the **All rebate management deals** page, but filtered to show and create only vendor rebate deals.
1. On the grid, find and open the deal you want to work with.
1. On the **Rebate management** FastTab, select one of the following from the toolbar:
    - **Add line** - Adds a new, blank line to the grid.
    - **Copy line** - If a line already exists and is similar to the line  you are planning to add, then you might choose this option. It will create a copy of the selected line <!-- KFM: Including all details? --> and then let you edit the settings for the new line (typically by updating the item relation and rebates percentage).
1. Make the following settings for the new line:
    - **Rebate management number** - Provided you have [set up a number sequence](rebate-management-parameters.md) for rebate management numbers, an automatically generated and unique ID should already appear here. Otherwise, enter a unique ID.
    - **Type**  - Shows the type of deal the line applies to (*Rebate* or *Royalty*). This is copied from the header and can't be changed.
    - **Description** - Enter a description for the line.
    - **Company** Select the company (legal entity) for which the line applies. During processing, users will only be able to process deal lines assigned to the company they are using at the time. <!--KFM: I'm not sure if the following is important. What is the "Customer rebates form"?: "The Customer rebates form will have a global view, based on the security access of the user." -->
    - **Account code** - Establishes the scope of customers or vendors for which the line applies. Select one of the following:
        - *Table* - To select an individual customer or vendor.
        - *Group* - To select a group of customers or vendors. For more information about how to set up groups, see [Rebate management groups](rebate-management-groups.md).
        - *All* - To set the line to apply to all customers or vendors.
    - **Account relation** - Depending on the **Account code** setting, select the group or specific vendor/customer for which the line applies. This setting is disabled when **Account code** is set to *All*.
    - **Item code** - Establishes the scope of items for which the line applies. Select one of the following:
        - *Table* - To select an individual item.
        - *Group* - To select a group of items. For more information about how to set up groups, see [Rebate management groups](rebate-management-groups.md).
        - *All* - To set the line to apply to all items.
    - **Item relation** - Depending on the **Item code** setting, select the group or specific item for which the line applies. This setting is disabled when **Item code** is set to *All*.
    - Inventory management parameters - Using the remaining fields of the line, specify values for the inventory management parameters that will be used to define the items included in the deal (such as item size, color, style, site, warehouse, and so on). To add or remove the dimensions available, select **Display dimensions** from the Action Pane.
1. For each line that you add, set up the calculation and other details using the **Rebate management details** FastTab, as described in the next section.

## Add rebate management details to a line

For each line in your deal, you must set up details using the **Rebate management details** FastTab. First select the deal line on the **Rebate management** FastTab, then make settings for that line using the various tabs of the **Rebate management details** FastTab. The following subsections describe how to use each of the tabs available here.

### Settings on the General tab

The **General** tab lets you set up the calculation method and basis for the selected deal line. This controls whether a minimum purchase is required, the posting profiles associated with the line, and the details of the calculation. The following table describes the settings available here.

| Field | Description |
|---|---|
| Calculation method | Choose the method to use when combining the selected line with other deal lines. This can dramatically affect the outcome of your rebate calculations. The available methods are *Stepped*, *Cumulative*, *Rolling*, and *Total*. For a complete description of each method and examples of how they affect the rebate calculation, see [Calculation methods for deal lines](#calc-methods). |
| Basis | Choose whether the rebate applies based on *Quantity* (the total number of units purchased/sold) or *Value* (the total price of goods purchased/sold). |
| Transaction type | Select point in the process when the calculation will occur. Choose one of the following:<ul><li>*Order* - Use the ordered quantity or value as the basis of the calculation.</li><li>*Delivered* - Use the delivered quantity or value as the basis of the calculation.</li><li>*Invoice* - Use the invoiced quantity or value as the basis of the calculation.</li> |
| Unit | When **Basis** is set to *Quantity* field, select the unit in which the quantity is to be specified. |
| Minimum amount | Enter the minimum amount that must be paid per period. You can enter a negative value, if needed, to allow negative rebate amounts if credit notes are greater than sales for the period. <!-- KFM: A bit more explanation is needed here. --> |
| Rebate reduction principle | Select the [rebate reduction principle](rebate-reduction-principle.md) that applies for the line. <!-- KFM: A bit more explanation is needed here. --> |
| Variant number | If the deal line applies to an item that has variants, select the variant for which the line applies. <!-- KFM: Original was unclear. Please confirm. --> |
| Posting profile | Select the [posting profile](rebate-management-posting.md) that applies for the selected line. This profile is only used when **Reconcile by** is set to *Line* in the deal header. If the **Reconcile by** is set to *Deal*, the posting profile set in the deal header is always used. If no posting profile is set at the line, the header posting profile is used. <!-- KFM: Is this last part true? Seems like we can't set a profile in the header when set to use LINE. --> |
| Posting profile for guarantee | <!-- KFM: Description needed. --> |
| Payment type | <!-- KFM: Description needed. --> |
| Sales tax inclusive | Choose whether the transaction is tax inclusive, which is only relevant when **Basis** is set to *Value*. The invoice amount will be used as the tax inclusive amount. If the rebate calculation based on a percentage, the system will multiply the rebate percentage by the tax inclusive amount. Note that the calculation uses the sales tax value from the line. |
| Include credit notes | Choose whether to include credit notes in the rebate calculation. The effect varies based on the **Transaction type** setting as follows:<ul><li>If the **Transaction type** is *Invoice* and this option is set to *Yes*, then the calculation will factor in credit notes. This is the usual configuration.</li><li>If the **Transaction type** is *Order* and this option is set to *Yes*, the calculation will factor in both sales orders with negative values and open returned orders</li></ul> |
| Discounted amount | Set this to *Yes* to base the calculation on the discounted amount of the item or items in cases where line discounts are given. |
| Paid invoices only | Set this to *Yes* if the calculation should only check for fully paid invoices (rebates won't be calculated for partially paid invoices). This option is only available when **Transaction type** is set to *Invoice*. |
| Include free text | Set this to *Yes* to include free text invoices in the calculation. Free text invoices can only be included for deal lines where **Item code** is set to *All*. |
| Include settlement discount | Set this to *Yes* to reduce the rebate by the first settlement discount. It is assumed that the organization will take the first settlement discount. <!-- KFM: I'm not sure what this means. More info may be needed. --> |
| Document notes | Enter notes to be used as transaction text in rebate transaction journal lines. |

### Settings on the Dates tab

The **Dates** tab specifies the dates for which the selected deal line is valid. It specifies the valid date range, the calculation frequency, whether the guarantee is posted, and when. These settings determine how calculations occur at processing time. If multiple date lines exist, the valid date ranges must not overlap. If the dates overlap, you will see an error message when you try to save the deal. These setting determine the frequency and timing of the calculations identified on the **General** tab.

<!-- KFM: Continue here. -->

1. To add a new date line, select **add line** in the dates FastTab section.
2. Enter a **from date** , this identifies that the deal line will include all transactions from this date forward. If from and to dates have been entered on the header of the rebate deal, the from and to dates will automatically fill into each of the lines.
3. Enter a **to date** , this identifies the end date that will include all transactions to this date. If from and to dates have been entered on the header of the rebate deal, the from and to dates will automatically fill into each of the lines.
4. Enter a number in the **Per** field. The per field identifies how often, or the frequency of the calculation of the deal. This field will work in conjunction with the **cumulate by** field and helps determine the next selection. For example. If bi-monthly periods are required enter 2 here.
5. Select the **cumulate by** field that will be utilized for the frequency of the deal calculation. The options include:

- **Days**
- **Weeks**
- **Months**
- **Quarters**
- **Years**.
- **Period**
- **Customized period**
- **Fiscal year**
- **Invoice**
- **Lifetime** – over the lifetime of the deal identified.
The cumulate by field along with the per field determines the frequency at which the rebate deals are calculated for the deal line. For example, if bi-monthly periods are required select Months in the cumulate by field and 2 in the **Per** field.
1. Select the **period type**. The period type field is only available for selection if the cumulate by field is set to **customized period**. The period type is a drop-down field that will come from the period types defined in the General ledger module and is further defined there.
2. Select the **starting day of the week**. This identifies how the weeks are identified for the period. This field is only available if the cumulate by field is set to weeks.
3. **Claim per**. The **claim per** field identifies how often the rebate monies can be claimed for the deal line. The **claim per** line works in conjunction with the **claim by** field and helps determine the next selection.
4. Select the **claim by** field that will be utilized for the frequency of the deal claim. The options include:

- **Invoice**
- **Days**
- **Weeks**
- **Months**
- **Quarters**
- **Years**.
- **Period**
- **Customized period**
- **Fiscal year**
- **Lifetime** – over the lifetime of the deal identified.
The claim by field along with the claim per field determines how the rebates are claimed for the rebate line.
1. Select the **claim period type**. The **claim period type** is only available for selection if the claim by field is set to **customized period**. The **claim period type** is a drop-down field that will come from the period types defined in the General ledger module and is further defined there.
2. Select **process at posting**. When this is selected, the claim line is processed at posting time. This option is only available when the transaction type is delivery note or invoice. If it is a provision, it will be posted at the time of delivery note/invoicing.
3. **Guarantee per** field is only applicable to a royalty deal. This field works in conjunction with the **guarantee paid** field to identify the frequency of the guarantee of the royalty.
4. **Guarantee Paid** is only applicable to a royalty deal. This field works in conjunction with the guarantee per field to determine the frequency of the guarantee calculation. The two options available are beginning of the period or end of the period.
5. **Guarantee minimum** is only applicable to a royalty deal. This identifies the minimum amount of the guarantee for a royalty.

### Settings on the Lines tab

The Lines FastTab is where each deal line quantity/value rebate is identified. On the lines FastTab, the user will define the details as to levels or lines of a quantity or value split of the rebate, along with the rebate percentage or rate.
- Select Add line to create a new record line for the value/quantity identification line. There may be a single line or multiple lines defined on this tab, depending on the parameters set for the rebate. The value/quantity cannot overlap if there are multiple lines on this tab.
- Enter a **from quantity/value** figure; this is the minimum value or quantity that calculation will be based on. The determination as to whether this is value or quantity based is defined on the Dates FastTab.
- Enter a **to quantity/value** figure. This is the maximum value or quantity that the rebate calculation will be based on. The determination as to whether this is value or quantity based is defined on the Dates FastTab.
- For rebates with a **rebate output** method of **financial** , set on the header of the rebate deal, specify the **method** , or the type of value that will be calculated. The options for the method are:
  - **Fixed**
  - **Percent**
  - **Rate**
The selection of the method field works in conjunction of the next field, the value field. These two fields will determine the value of the rebate as it is calculated.
- Enter a **value** in rebates and deductions amount field. This is determined from the previous field; if percent was set then the value entered here will be a percentage figure. If the fixed method was set, then the value entered here will be a fixed figure. If the rate method was set, the rate for calculation should be entered.
_Note: It is not advisable to have mixed methods for one deal line. If new calculation method is needed, a new deal line should be created. Remember you can use copy to create a similar rebate._
- For rebates with a **rebate output** method of **item** you will need to click the **items** button, located on the lines FastTab. The items button will only be available once the Lines FastTab has been saved. Once the line has saved, the user may add item lines to the deal line.
  - Select the **item** in the item number field.
  - If applicable select the **product dimensions**
  - Select the **quantity** that will be rebated once the threshold is met.
  - Select the **unit.**
  - Select the **multiple** that this quantity will be given for. The multiple line works in conjunction with the quantity line for rebates processing. For example, on a rebate deal line we set the quantity to 2 and a multiple of 100. We then have a total sales order quantity of 150. In this scenario, 2 of the items would be free (2 per/100).
When an item is selected in the rebate output, a particular quantity of items will be rebated based on the deal line calculation, and the rebate item parameters are set here. The items button is per each line&#39;s threshold of from and to quantity/value. As many lines as required for the deal line.

### Settings on the inventory dimensions tab


<a name="calc-methods"></a>

## Calculation methods for deal lines

Each time you set up details for one of your deal lines, as described in the previous section, you must choose the calculation method for that line. This section explains each calculation method and provides examples of how the total rebate is calculated in each case for otherwise identical orders and deal lines.

### The stepped calculation method

The stepped calculation method calculates on a step basis, with each line contributing to the rebate until the sales quantity or value is reached. The step can be set based on either the quantity of the goods sold or the value of the goods sold. The method uses the **Basis** setting to choose whether to use sales quantity or sales value to calculate the rebates.

For example, suppose each line uses a **Calculation method** of *Stepped* and a **Basis** of *Value*, and the deal includes lines that provide the following rebates:

- Line (A): 10% up to $1,000
- Line (B): 25% up to $2,500

If $2,000 was purchased/sold, then the resulting rebate would be $350, which is calculated as follows:

- Rebate (A) = Threshold (A) \* Percentage (A) = $1,000 \* 10% = $100
- Rebate (B) = (Value Sold – Threshold (A)) \* Percentage (B) = ($2,000 - $1,000) \* 25% = $250
- Total Rebate = Rebate (A) + Rebate (B) = $100 + $250 = $350

The quantity basis is based on the quantity of goods sold, rather than the value, and works similarly. In the stepped method, the first step is used for the identified quantity until the second step is reached. From there, the second step will be used for all quantity above the first step until the third or subsequent step. This will continue on through all subsequent steps.

### The cumulative calculation method

The cumulative method calculation method uses just one line to calculate the rebate. If there are multiple calculation lines available for the deal, the highest value or quantity line that is reached is the one used for the entire quantity or value. As with the other calculation methods, the cumulative method uses the **Basis** setting to choose whether to use sales quantity or sales value to calculate the rebates.

For example, suppose each line uses a **Calculation method** of *Cumulative* and a **Basis** of *Value*, and the deal includes lines that provide the following rebates:

- Line (A): 10% up to $1,000
- Line (B): 25% up to $2,500

If $2,000 was purchased/sold, then the resulting rebate would be $500 because it uses only line (B). The calculation is as follows:

- Total Rebate = Value Sold \* Rebate (B) = $2000 \* 25% = $500

### The rolling calculation method

The rolling method calculates all possible lines for the deal. If there are multiple lines and more than on is reached, all of the lines reached will be used, but upper thresholds apply for each percentage. As with the other calculation methods, the rolling method uses the **Basis** setting to choose whether to use sales quantity or sales value to calculate the rebates.

For example, suppose each line uses a **Calculation method** of *Rolling* and a **Basis** of *Value*, and the deal includes lines that provide the following rebates:

- Line (A): 10% up to $1,000
- Line (B): 25% up to $2,500

If $2,000 was purchased/sold, then the resulting rebate would be $600. The calculation is as follows:

- Rebate (A) = Threshold (A) \* Percentage (A) = $1,000 \* 10% = $100
- Rebate (B) = Value Sold \* Percentage (B) = $2,000 \* 25% = $500
- Total Rebate = Rebate (A) + Rebate (B) = $100 + $500 = $600

### The total calculation method

The total total calculation method uses all lines to calculate the rebate, and applies the total quantity to calculate the rebate for each reached line and each line applies its percentage to the full amount. As with the other calculation methods, the rolling method uses the **Basis** setting to choose whether to use sales quantity or sales value to calculate the rebates.

For example, suppose each line uses a **Calculation method** of *Total* and a **Basis** of *Value*, and the deal includes lines that provide the following rebates:

- Line (A): 10% up to $1,000
- Line (B): 25% up to $2,500

If $2,000 was purchased/sold, then the resulting rebate would be $700. The calculation is as follows:

- Rebate (A) = Value Sold \* Percentage (A) = $2,000 \* 10% = $200
- Rebate (B) = Value Sold \* Percentage (B) = $2,000 \* 25% = $500
- Total Rebate = Rebate (A) + Rebate (B) = $200 + $500 = $700

