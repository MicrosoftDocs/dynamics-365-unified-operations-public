---
title: Auto charge compounding and sequencing
description: Advanced auto charges let you apply charge category types of "specific unit" and "specific unit match" to calculate line charges for sales and purchase orders.
author: Henrikan
ms.author: henrikan
ms.topic: how-to
ms.date: 10/31/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form: MarkupAutoSetup, CustParameters, SalesTableListPage, SalesTable, MarkupTrans, SalesTotals
---

# Auto charge compounding and sequencing

[!include [banner](../includes/banner.md)]

Advanced auto charges let you apply specific charges to order headers and order lines, based on the customer that you're working with and/or the items that you're selling. For sales quotations and sales orders, you can also choose to compound header charges.

Header charge compounding affects the value base that's used to calculate an auto charge. All header charges (where the customer is debit or credit) that have a sequence that's equal to or lower than the sequence for a compound charge are added to the sum of line net amounts. This sum is referred to as the *value base*. The value base can be set either to *Sum of line net amounts only* or *Sum including charge amounts*. Compounding is applied only when the charge category is *Percent*.

Compounded header charges require a *charge sequence*. The charge sequence determines the order that header charges are calculated in. Charge sequences can exist only at the header level. They have an impact only when you have one or more charges that are set to compound.

Depending on how you configure the feature, interim header charge totals can be applied on top of either the sum of line net amounts, including all line charges and sales taxes, or the sum of line net amounts only. As the calculation progresses, interim header charges establish a value base that subsequent compound charges are calculated on.

You can define a default header charge sequence for your system. This charge sequence is then automatically applied to new sales quotations and sales orders.

When several header charges that have the same sequence are applied, the position of the header charges controls the order that they're applied in during compounding. The position has an impact only when one or more charges are set to compound.

## Prerequisites

Before you can use this feature, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.38 or later.
- The feature that's named *Sequence and compound for customer charges* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

The *Sequence and compound for customer charges* feature adds new fields to the **Accounts receivable parameters** page to control the compounding. It also adds **Sequence**, **Compound**, and **Position** columns for header charges to sales quotations and sales orders.

## <a name="set-up-comp-seq"></a>Set up auto charge compounding and sequencing

To set up auto charge compounding and sequencing, follow these steps.

1. Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
1. On the **Prices** tab, on the **Prices** FastTab, set the **Find auto charges for header** option to *Yes*.
1. On the **Charges** FastTab, set the following fields:

    - **Re-search on posting** – This option controls whether header auto charges on sales orders and sales quotations are re-searched when documents are confirmed or posted. No other manually added charges are affected during the re-search process. Set this option to *Yes* to ensure that the header charges that are set up in auto charges are always applied.
    - **Combine charges on combined invoices** – The option controls how auto charges are calculated when the *Summary update* function is used to combine multiple sales orders into a single invoice. Set this option to *Yes* to first calculate the grand total of all sales orders that are included in the combined invoice and then apply the auto charge to that total. Set it to *No* to calculate a separate auto charge for each sales order that's included in a combined invoice.
    - **Value base for header charges** – Select one of the following values to specify the value base for calculating percentage-based header charges:

        - *Sum of line net amounts only* – Calculate charges based only on the sum of line amounts. This value ensures compatibility with charge calculations that were done before the *Sequence and compound for customer charges* feature was enabled in your system.
        - *Sum including charge amounts* – Calculate charges based on the sum of line amounts, including line charges. If you select this value, you can also include tax amounts in the value base by specifying tax codes that should be used to determine the tax amount. You can define this behavior for an individual auto charge line by selecting the **Include taxes in value base** button that's added to the toolbar on the **Lines** FastTab of the **Auto charges** page when this value is selected.

The following sections provide example scenarios that show how these settings affect your calculations.

## <a name="scenario1"></a>Example scenario 1: Work with auto charge compounding and sequencing

This section provides an example scenario that shows how auto charge compounding and sequencing works. It's based on the standard demo data.

### Enable demo data

To work through this scenario and the other scenarios in this article by using the demo records and values that are specified here, you must be on a system where the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed. Additionally, you must select the *USMF* legal entity before you begin.

### Create sample auto charges

To apply a charge that's set to compound, you must first set up the auto charge. Use the following procedure to create an example auto charge. (For more information about the settings, see [Automatic application of charges](../procurement/automatic-charges-allocation.md).)

1. Go to **Accounts receivable** \> **Charges setup** \> **Auto charges**.
1. In the list pane, set the **Level** field to *Header*.
1. On the Action Pane, select **New** to create an auto charges record.
1. On the header of the new record, set the following fields:

    - **Account code** – Select *All*.
    - **Item code** – Select *All*.
    - **Mode of delivery code** – Select *All*.
    - **Charge description** – Enter a name for the charge.

1. On the Action Pane, select **Save**.
1. The **Lines** FastTab should now include a blank line. If it doesn't, select **Add** on the toolbar to add one. Set the following values for this line:

    - **Sequence** – Enter *1*.
    - **Compound** – Clear this option.
    - **Currency** – Select *USD*.
    - **Charges code** – Select *Freight*.
    - **Category** – Select *Fixed*.
    - **Charges value** – Enter *100*.
    - **From amount** – Leave this field blank.
    - **To amount** – Leave this field blank.
    - **GST group** – Leave this field blank.
    - **Keep** – Clear this option.
    - **Site** – Leave this field blank.
    - **Warehouse** – Leave this field blank.

1. On the **Lines** FastTab, select **Add** on the toolbar to add a second charge line. Set the following values for it:

    - **Sequence** – Enter *2*.
    - **Compound** – Select this option.
    - **Currency** – Select *USD*.
    - **Charges code** – Select *Handling*.
    - **Category** – Select *Percent*.
    - **Charges value** – Enter *2*.
    - **From amount** – Leave this field blank.
    - **To amount** – Leave this field blank.
    - **GST group** – Leave this field blank.
    - **Keep** – Clear this option.
    - **Site** – Leave this field blank.
    - **Warehouse** – Leave this field blank.

1. On the Action Pane, select **Save**.

### Create a sample sales order

The charges that you set up can now be automatically applied to a sales quotation or sales order. To apply the charges to a sales order, follow these steps.

1. Go to **Sales and Marketing** \> **Sales orders** \> **All sales orders**.
1. On the Action Pane, select **New** to create a sales order.
1. In the **Create sales order** dialog box, set the **Customer account** field to *US-004*. Then select **OK** to create the order. The selected customer must use the same currency as the auto charges that you set up (*USD*).
1. The new sales order is opened. On the Action Pane, on the **Sell** tab, in the **Charges** group, select **Maintain charges**.
1. The **Maintain charges** page shows the following two lines, which come from the auto charge setup.

    | Position | Sequence | Compound | Charges code | Category | Charges value |
    |---|---|---|---|---|---|
    | 1 | 1 | No | Freight | Fixed | 100 |
    | 2 | 2 | Yes | Handling | Percent | 2 |

    Notice that the **Position** values match the **Sequence** values from the auto charge setup. **Position** values differ from **Sequence** values only in cases where there's an overlap in sequence numbering. The position is used to calculate the value base for charges that are set to compound.

    In this example, a 2 percent charge is applied on top of the 100 USD fixed charge. Therefore, the total header charges equal 102 USD. The 2 percent charge also applies to each order line.

    Users can change the assigned **Position**, **Sequence**, and **Compound** values for a header charge that's applied from auto charges. However, they should be careful, because these types of edits can significantly affect the calculated value base that's used for charges that are set to compound.

    For example, a user changes the preceding automatically created lines so that they have the following values.

    | Position | Sequence | Compound | Charges code | Category | Charges value |
    |---|---|---|---|---|---|
    | 2 | 1 | No | Freight | Fixed | 100 |
    | 1 | 2 | No | Handling | Percent | 2 |

    Because of the updated **Position** values, the 2 percent charge is applied first, while the value base is still zero. However, because 2 percent of zero is zero, the result is no additional charge. The 100 USD fixed charge is then added to give a total header charge of just 100 USD. (The 2 percent charge still applies to each order line.)

    The user then changes the lines so that they have the following values.

    | Position | Sequence | Compound | Charges code | Category | Charges value |
    |---|---|---|---|---|---|
    | 1 | 1 | No | Freight | Fixed | 100 |
    | 2 | 2 | No | Handling | Percent | 2 |

    This time, the **Position** values match the **Sequence** values from the setup. However, the **Compound** option for both charges is set to *No*. In this case, the 100 USD fixed charge is applied first, but the 2 percent handling charge doesn't affect the header charge, because it isn't set to compound, and 2 percent of zero is zero. Therefore, the total sum of header charges is just 100 USD. (The 2 percent charge still applies to each order line.)

1. Close the **Maintain charges** page by selecting the back button on the Action Pane.
1. If necessary, you can revert the edits that you made on the **Maintain charges** page to return to the default setup lines. On the Action Pane, on the **Sell** tab, in the **Calculate** group, select **Header auto charges**. This action restores only those lines that were automatically added from auto charges. It doesn't affect charge lines that were manually added to the sales order header. This action also doesn't restore any order line charges.

## Position, Sequence, and Compound fields on header charges

As you saw in [example scenario 1](#scenario1), the **Maintain charges** page includes the following fields for charge settings:

- **Position** – Use this field to prioritize the calculation of each charge line. Lines are calculated in sequence, starting with the line that has the lowest **Position** value (because the lowest position has the highest priority). This value is automatically generated for all auto charge lines, based on each line's **Sequence** value on the **Auto charges** page. However, it's still editable and can be manually updated. Each **Position** value must be unique for each order. There can be no overlaps.
- **Sequence** – This field indicates the intended position of the charge as it's set up on the **Auto charges** page. For default charge lines, the value is copied from the auto charge setup. For custom charge lines that are manually added to the **Maintain charges** page, the value is set to *0* (zero). Sequence numbers don't have to be unique and might therefore overlap. If the auto charge setup includes overlapping sequence numbers, the system assigns unique **Position** values, starting with the most specific (customer) record. Although the **Sequence** field is editable and can be manually updated, we recommend that you keep it aligned with the **Position** value.
- **Compound** – Use this option to specify whether the line should be compounded with other header charges that have been added so far. This option applies only to charges that have a **Category** value of *Percent*. Compounding applies only to charges that are added by the auto charge setup. Although the system allows you to select the **Compound** option for manually added charge lines, compounding isn't actually performed for those lines.

> [!NOTE]
> Although the system usually prevents you from entering duplicate **Position** values, duplicates can still occur. For example, they might occur if you delete an auto charge line, add new manual charges, and then restore auto charges by selecting the **Header auto charges** action. In these cases, the system uses the record ID of each charge record to resolve the relative positions of the charges when it calculates the value base. We recommend that you avoid this scenario, because you won't be able to see how the value base was calculated.

## Example scenario 2: Value base for header charges options

When the system calculates the value of a charge that has a **Category** value of *Percent*, it applies the defined percentage to the value base that it has calculated so far at that position of the calculation. The value base can consist of the net amount across all order lines or the net amount across all order lines that include line changes, both with and without sales taxes.

The following examples show how the **Value base for header charges** field that's set on the **Accounts receivable parameters** page can affect your calculations. This field is also described in the [Set up auto charge compounding and sequencing](#set-up-comp-seq) section.

### Sum of line amounts only

The following example shows how a value of *Sum of line amounts only* in the **Value base for header charges** field can affect header charge calculations.

1. If you haven't already done so, [set up the auto charges that are specified for example scenario 1](#scenario1).
1. Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
1. On the **Prices** tab, on the **Charges** FastTab, set the **Value base for header charges** field to *Sum of line net amounts only*.
1. Go to **Sales and Marketing** \> **Sales orders** \> **All sales orders**.
1. On the Action Pane, select **New** to create a sales order.
1. In the **Create sales order** dialog box, set the **Customer account** field to *US-004*. Then select **OK** to create the order. The selected customer must use the same currency as the auto charges that you set up (*USD*).
1. The new sales order is opened. On the **Sales order lines** FastTab, add an order line for any item, and edit the **Quantity** and **Unit price** fields to ensure that the **Net amount** value for the line is 100 USD.
1. While the new order line is still selected on the **Sales order lines** FastTab, select **Financials** \> **Maintain charges** on the toolbar.
1. On the **Maintain charges** page, on the Action Pane, select **New** to add a charge line. Then set the following values for it:

    - **Charge code** – Select *Freight*.
    - **Category** – Select *Fixed*.
    - **Charges value** – Enter *10*.
    - **Currency** – Select *USD*.

1. On the Action Pane, select **Save**.
1. On the Action Pane, select the back button to return to the sales order.
1. On Action Pane, on the **Sales order** tab, in the **View** group, select **Totals**.
1. The **Totals** dialog box shows the different calculation results that apply to the current order. Notice the value that's shown for **Total Charges** is 114 USD. This value is calculated in the following way:

    *Line charge fixed* &plus; *Header charge fixed* &plus; *Header charge percentage and compound* (= 2% of *Line amount* &plus; 2% of *Header charge with lower position*)

    10 USD &plus; 100 USD &plus; (2 USD \[= 2% of 100 USD\] &plus; 2 USD \[= 2% of 100 USD\]) = 114 USD

### Sum including charge amounts

The following example shows how a value of *Sum including charge amounts* in the **Value base for header charges** field can affect header charge calculations. This setting affects header charges that have a **Category** value of *Percent*, regardless of whether the **Compound** option is enabled.

1. Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
1. On the **Prices** tab, on the **Charges** FastTab, change the value of the **Value base for header charges** field to *Sum including charge amounts*.
1. Open the sales order that you created in the previous example.
1. On Action Pane, on the **Sales order** tab, in the **View** group, select **Totals**.
1. In the **Totals** dialog box, notice that the value that's shown for **Total Charges** is now 114.20 USD. This value is calculated in the following way:

    *Line charge fixed* &plus; *Header charge fixed* &plus; *Header charge percentage and compound* (= 2% of *Header charge with lower position* &plus; 2% of *Line amount* &plus; 2% of *Line charge*)

    10 USD &plus; 100 USD &plus; (2 USD \[= 2% of 100 USD\] &plus; 2 USD \[= 2% of 100 USD\] &plus; 0.20 USD \[= 2% of 10 USD\]) = 114.20 USD

When the **Value base for header charges** field is set to *Sum including charge amounts*, you can include selected sales taxes in the value base calculation. To set up this functionality, following these steps.

1. Go to **Accounts receivable** \> **Charges setup** \> **Auto charges**.
1. In the list pane, set the **Level** field to *Header*.
1. Select the auto charge that you want to set up, or create a new one.
1. On the **Lines** FastTab, select the line that you want to set up, or add a new one.
1. On the toolbar, select **Include taxes in value base**. (This toolbar button is available only when the **Value base for header charges** field is set to *Sum including charge amounts* on the **Accounts receivable parameters** page.)
1. On the **Sales tax codes in value base for auto charge** page, add a line for each sales tax code that you want to include in value base calculations for the selected auto charge line.
1. On the Action Pane, select **Save**.

## Example scenario 3: Re-search on posting options

The **Re-search on posting** option ensures that header charges are assessed against the header charge setup when posting occurs. Auto charges that are set up as tiered charges are automatically assessed. The assessment compares automatically applied header charges against the auto charge setup. It ensures that all the header charges that are automatically applied to sales orders and quotations at the time of creation resemble the auto charge setup. All automatically applied header charges that were manually changed or deleted are restored. All manually added header charges are left unchanged. In other words, the option ensures that the auto charge setup is always applied.

> [!NOTE]
> Tiered charges are supported only for sales orders. Therefore, they're included in the re-search only for sales orders.

The following example shows the effect of the **Re-search on posting** option.

1. If you haven't already done so, [set up the auto charges that are specified for example scenario 1](#scenario1).
1. Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
1. On the **Prices** tab, on the **Charges** FastTab, set the following values:

    - **Re-search on posting** – Set this option to *Yes*.
    - **Value base for header charges** – Select *Sum of line net amounts only*.

1. Go to **Sales and Marketing** \> **Sales orders** \> **All sales orders**.
1. On the Action Pane, select **New** to create a sales order.
1. In the **Create sales order** dialog box, set the **Customer account** field to *US-004*. Then select **OK** to create the order. The selected customer must use the same currency as the auto charges that you set up (*USD*).
1. The new sales order is opened. On the Action Pane, on the **Sell** tab, in the **Charges** group, select **Maintain charges**.
1. The **Maintain charges** page shows lines that came from the auto charge setup. Use the **Delete** button on the Action Pane to delete each auto charge line, so that no charges are listed on the page.
1. On the Action Pane, select **New** to add a charge line. Then set the following values for it:

    - **Position** – Enter *3*.
    - **Sequence** – Enter *3*.
    - **Charges code** – Select *Freight*.
    - **Category** – Select *Fixed*.
    - **Charges value** – Enter *10*.
    - **Currency** – Select *USD*.

1. On the Action Pane, select **Save**.
1. On the Action Pane, select the back button to return to the sales order.
1. On the Action Pane, on the **Sales order** tab, in the **View** group, select **Totals**.
1. In the **Totals** dialog box, notice that **Total charges** shows the value of the fixed header charge that you just added (10 USD). Close the dialog box.
1. On the **Sales order lines** FastTab, add an order line for any item, and edit the **Quantity** and **Unit price** fields to ensure that the **Net amount** value for the line is 100 USD.
1. On the Action Pane, select **Save**.
1. On the Action Pane, on the **Sell** tab, in the **Generate** group, select **Confirm sales order**.
1. In the **Confirm sales order** dialog box, select **OK** to confirm the order.
1. You're returned to the sales order. On the Action Pane, on the **Sell** tab, in the **Charges** group, select **Maintain charges**.
1. On the **Maintain charges** page, notice that the two auto charges that you deleted have been reapplied on the sales order header, and that the custom line that you added is still included. This behavior occurs because the **Re-search on posting** option is enabled, and you confirmed (posted) the order. The following three lines should be shown.

    | Position | Sequence | Compound | Charges code | Category | Charges value |
    |---|---|---|---|---|---|
    | 1 | 1 | No | Freight | Fixed | 100 |
    | 2 | 2 | Yes | Handling | Percent | 2 |
    | 3 | 3 | No | Freight | Fixed | 10 |

1. On the Action Pane, select the back button to return to the sales order.
1. On the Action Pane, on the **Sales order** tab, in the **View** group, select **Totals**.
1. In the **Totals** dialog box, notice that **Total charges** now shows the calculated value of all three header charges (114 USD). This value is calculated in the following way:

    *Line charge fixed* &plus; *Header charge fixed* &plus; *Header charge percentage and compound* (= 2% of *Line amount* &plus; 2% of *Header charge with lower position*)

    10 USD &plus; 100 USD &plus; (2 USD \[= 2% of 100 USD\] &plus; 2 USD \[= 2% of 100 USD\]) = 114 USD

## Example scenario 4: Combine charges on combined invoices options

The setting of the **Combine charges on combined invoices** option on the **Accounts receivable parameters** page controls how header charges are calculated when multiple sales orders are combined into a single invoice by using the *Summary update* function.

- *Yes* – First calculate the grand total of all sales orders that are included in the combined invoice. Then apply the auto charges to that total.
- *No* – Calculate header charges individually for each sales order that's included in the summary invoice. In scenarios where header charges are set up to represent per-invoice charges instead of per-sales order charges, this setting can lead to over-charging.

The following example shows the effects of the **Combine charges on combined invoices** option.

1. If you haven't already done so, [set up the auto charges that are specified for example scenario 1](#scenario1).
1. Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
1. On the **Prices** tab, on the **Charges** FastTab, set the following values:

    - **Re-search on posting** – Set this option to *Yes*.
    - **Combine charges on combined invoices** – Set this option to *No*.
    - **Value base for header charges** – Select *Sum of line net amounts only*.

1. Go to **Sales and Marketing** \> **Sales orders** \> **All sales orders**.
1. Follow these steps to create a sales order that has one sales line:

    1. On the Action Pane, select **New** to create a sales order.
    1. In the **Create sales order** dialog box, set the **Customer account** field to *US-004*. Then select **OK** to create the order. The selected customer must use the same currency as the auto charges that you set up (*USD*).
    1. On the **Sales order lines** FastTab, add an order line for any item, and edit the **Quantity** and **Unit price** fields to ensure that the **Net amount** value for the line is 100 USD.
    1. On the Action Pane, select **Save**.

1. Repeat the previous step to create a second, identical sales order.

    In a real warehouse, warehouse workers would now pick and pack both sales orders and register their work by using the Warehouse Management mobile app. However, these steps aren't required to continue this example scenario.

1. Go back to **Sales and Marketing** \> **Sales orders** \> **All sales orders**.
1. Find and select the two new sales orders. Then, on the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
1. In the **Posting invoice** dialog box, on the **Parameters** FastTab, set the **Summary update for** field to *Invoice account*.
1. On the toolbar, select **Arrange**.
1. Select **OK**.
1. Select one of the two sales orders. Then, on the Action Pane, on the **Invoice** tab, in the **Journals** group, select **Invoice**.
1. The invoice is opened. On the Action Pane, select **Charges**.
1. Notice that the header charges have been calculated for each sales order. For each sales order, a header charge of 104 USD is applied. This value is calculated as 100 USD &plus; 2% compound (2% of the line amount \[100 USD\] &plus; 2% of the fixed charge \[100 USD\]). Therefore, the total charges for the invoice are 2 &times; 104 USD = 208 USD.
1. Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
1. On the **Prices** tab, on the **Charges** FastTab, change the setting of the **Combine charges on combined invoices** option from *No* to *Yes*.
1. As you did before, go to **Sales and Marketing** \> **Sales orders** \> **All sales orders**, and create new sales orders for the same account that have identical sales lines. Then pick and pack both sales orders.
1. Go back to **Sales and Marketing** \> **Sales orders** \> **All sales orders**.
1. Find and select the two new sales orders. Then, on the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
1. In the **Posting invoice** dialog box, set the **Summary update for** field to *Invoice account*.
1. On the toolbar, select **Arrange**.
1. Select **OK**.
1. Select one of the two sales orders. Then, on the Action Pane, on the **Invoice** tab, in the **Journals** group, select **Invoice**.
1. The invoice is opened. On the Action Pane, select **Charges**.
1. Notice that the header auto charges have been re-searched and reapplied per invoice. The customer will be debited just one instance of the fixed auto charge of 100 USD instead of two instances, because the charge is now applied per invoice instead of per sales order. The total calculated charges for the invoice are 106 USD. This value is calculated as one header fixed charge of 100 USD + 2% compound (2% of the total line amounts \[100 USD &plus; 100 USD\] &plus; 2% of the fixed charge \[100 USD\]).

    In this setup, the fixed auto charge is applied only once (per invoice), and the percentage-based charge that's set to compound is calculated from a value base that's 100 USD less than the header charges that are calculated per sales order.

1. Go back to **Sales and Marketing** \> **Sales orders** \> **All sales orders**.
1. Select the first of the two new sales orders. Then, on the Action Pane, on the **Sell** tab, in the **Charges** group, select **Maintain charges**. Make a note of the charges that are shown, and then repeat this step for the second new sales order.

    Notice that, as part of combining charges on combined invoices, the auto charges are now present only on the first sales order. This behavior is by design. It ensures that the combination of charges on combined invoices provides the correct charge calculation.

> [!NOTE]
> Auto charges are applied based on the customer accounts on sales orders, not the invoice accounts on invoices. In cases where a summary update is done for sales orders for different customer accounts that have the same invoice account, and where different header charges are set up for the different customer accounts, the customer account for the *last* sales order for the summary update is the customer account that the header charges are re-searched and re-applied for when invoicing occurs.

## Pricing management

The features that are described in this article work together with the [Pricing management module](../pricing-management/pricing-management-overview.md). Pricing management introduces changes to the setup and search for auto charges. Therefore, it also changes some of the behavior that's described in this article. When the Unified pricing management module is [enabled](../unified-pricing-management/upm-pricing-management-enable.md), charges that are set up at **Accounts receivable** \> **Charges setup** don't apply. Instead, only charges that are set up on the auto charges page that's specific to the **Pricing management** module apply to sales orders and sales quotations. To set up auto charges in Pricing management, go to **Pricing management** \> **During-sales pricing** \> **Charges setup** \> **Auto charges**.

## Limitations

The capabilities for compounding charges and defining a value base that the compounding is applied to are available for sales quotations and sales orders, not purchase orders. This feature also introduces some new capabilities that don't support all scenarios. The following subsections describe the most important limitations.

### Intercompany trade

The lack of compounding and sequencing support for purchase orders affects intercompany scenarios, because sales order and purchase order charges would be calculated differently. To prevent intercompany scenarios from being blocked, header charges for any sales order that fulfills a local purchase order are applied and calculated without using the compounding and sequencing features that are described in this article. Therefore, compounding and sequencing are either applied or not applied, based on context. In intercompany scenarios, compounding and sequencing aren't applied. However, they're applied in non-intercompany scenarios.

### Prorate and summary updates

Header charges can be assigned a charges code that's set to *prorate*. The ability to re-search when posting occurs, and to combine charges on combined invoices, prevents the duplication of fixed charges from auto charges. The combination of charges on combined invoices isn't supported for header charges that are set to *prorate*. Therefore, prorated header charges that are applied in a summary update scenario are always re-searched and calculated based on the individual sales orders. They aren't combined.

### Tiered charge and summary updates

A header charge can be set to use **From amount** and **To amount** tiers. The tiers are evaluated based on the net amount of a sales order. When you use sequencing and compounding, tiers are always assessed against the net amount of a sales order. If the net amount of a sales order is within a tier, and if a tiered charge is calculated as a percentage, the charge is calculated based on the current value base, even though the tier was assessed based on the net amount. If you make a summary update, such as a summary invoice, when the system is configured to re-search when posting occurs, the tiers are assessed against the net amount only for the *first* sales order that's included in the summary update. The tiers aren't assessed against the net amount across *all* order lines in the summary update.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
