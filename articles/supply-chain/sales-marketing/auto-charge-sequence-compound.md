---
title: Autocharge compounding and sequencing (preview)
description: Advanced auto charges enable you to compound header charges for sales quotations and sales orders. They also let you apply charge category types of "specific unit" and "specific unit match" to calculate line charges for sales and purchase orders. 
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: MarkupAutoSetup, CustParameters, SalesTableListPage, SalesTable, MarkupTrans, SalesTotals
ms.topic: how-to
ms.date: 10/31/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Autocharge compounding and sequencing (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!--KFM: Preview until 10.0.38 GA -->

Advanced auto charges let you apply specific charges to order headers and order lines based on which customer you're working with and/or which items you're selling. For sales quotations and sales orders, you can also choose to compound header charges.

Header charge compounding affects the value base used to calculate an auto charge. All header charges (where the customer is debit or credit) with a sequence equal to or lower than the sequence for a compound charge are added to the sum of line net amounts. This sum is referred to as  the *value base*. The value base can be set either to *sum of line net amounts only* or *sum including charge amounts*. Compounding is only applied when the charge category is percentage.  

Compounded header charges require a *charge sequence*, which determines the order in which header charges are calculated. Charge sequences can only exist at the header level. Depending on how you configure the feature, interim header charge totals can be applied on top of the sum of line net amounts (including all line charges and sales taxes) or the sum of line net amounts only. As the calculation progress, interim header charges establish a value base upon which subsequent compound charges are calculated. You can define a default header-charge sequence for your system, which automatically applies to new sales quotations and sales orders. Sequences only have an impact when you have one or more charges set to compound.

When several header charges with the same sequence are applied, the position of the header charges controls the order in which they're applied when compounding. The position only has an impact when one or more charges are set to compound.

[!INCLUDE [preview-note](../includes/preview-note.md)]

## Prerequisites

To use this feature, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.38 or later.
- The feature that is named *Sequence and compound for customer charges* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

The *Sequence and compound for customer charges* adds new settings to the **Accounts receivable parameters** page to control the compounding. It also adds the columns **Sequence**, **Compound**, and **Position** for header charges on sales quotations and sales orders.  

## <a name="set-up-comp-seq"></a>Set up autocharge compounding and sequencing

To set up autocharge compounding and sequencing, follow these steps:

1. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. Open the **Prices** tab.
1. On the **Prices** FastTab, set **Find auto charges for header** to *Yes*.
1. On the **Charges** FastTab, make the following settings:
    - **Re-search on posting** – Specify whether header auto charges on sales orders and sales quotations should be re-searched when documents are confirmed or posted. Other manually added charges won't be affected during the re-search process. Set this to *Yes* to ensure that the header charges set up in auto charges are always applied.
    - **Combine charges on combined invoices** – The parameter controls how auto charges are calculated when multiple sales orders are combined into a single invoice using the *summary update* function. Set this parameter to *Yes* to first calculate the grand total of all sales orders included in the combined invoice and then apply the auto charge to that total. Set this parameter to *No* to calculate a separate auto charge for each sales order included in a combined invoice.
    - **value base for header charges** – This parameter determines the value base for calculating percentage-based header charges. Choose one of the following options:
        - *Sum of line net amounts only* – Calculate charges based on the sum of line amounts only. This option ensures compatibility with charge calculations made before the *Sequence and compound for customer charges* feature was enabled for your system.
        - *Sum including charge amounts* – Calculate charges based on the sum of line amounts, including line charges. This option also lets you choose to include tax amounts in the value base by specifying tax codes that should be used to determine the tax amount. You can define this for an individual auto charge line by selecting **Include taxes in value base**, which is shown when this option is enabled.

Examples of how these settings affect your calculations are given in the various example scenarios provided later in this article.

## <a name="scenario1"></a>Example scenario 1: Work with autocharge compounding and sequencing

This section provides an example scenario (based on the standard demo data) that shows how autocharge compounding and sequencing works.

### Enable demo data

To work through this and the other scenarios in this article using the demo records and values that are specified here, you must be on a system where the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed. Additionally, you must select the *USMF* legal entity before you begin.

### Create sample auto charges

To apply a charge set as compound, you must first set up the auto charge. Use the following procedure to crate an example auto charge (for more information about these settings, see [Automatic application of charges](automatic-charges-allocation.md)).

1. Go to **Accounts receivable \> Charges setup \> Auto charges**.
1. On the list pane, set **Level** to *Header*.
1. On the Action Pane, select **New** to create a new auto charges record.
1. In the header of the new record, set the following fields:
    - **Account code** – Select *All*.
    - **Item code** – Select *All*.
    - **Mode of delivery code** – Select *All*.
    - **Charge description** – Enter a name for the charge.

1. On the Action Pane, select **Save**.
1. On the **Lines** FastTab, you should now see an empty line (select **Add** from the toolbar to add one if you don't). Make the following settings for the new line:

    - **Sequence** – Enter *1*.
    - **Compound** – Unselect.
    - **Currency** – Select *USD*.
    - **Charges code** – Select *Freight*.
    - **Category** – Select *Fixed*.
    - **Charges value** – Enter *100*.
    - **From amount** – Leave blank.
    - **To amount** – Leave blank.
    - **GST group** – Leave blank.
    - **Keep** – Unselect.
    - **Site** – Leave blank.
    - **Warehouse** – Leave blank.

1. On the **Lines** FastTab, select **Add** to add a second charge line. Make the following settings for the new line:

    - **Sequence** – Enter *2*.
    - **Compound** – Select.
    - **Currency** – Select *USD*.
    - **Charges code** – Select *Handling*.
    - **Category** – Select *Percent*.
    - **Charges value** – Enter *2*.
    - **From amount** – Leave blank.
    - **To amount** – Leave blank.
    - **GST group** – Leave blank.
    - **Keep** – Unselect.
    - **Site** – Leave blank.
    - **Warehouse** – Leave blank.

1. On the Action Pane, select **Save**.

### Create a sample sales order

The charges you set up can now be applied automatically to a sales quotation or sales order. To apply the charges to a sales order, follow these steps:

1. Go to **Sales and Marketing \> Sales orders \> All sales orders**.
1. On the Action Pane, select **New** to create a new sales order.
1. The **Create sales order** dialog opens. Set **Customer account** *US-004* and then select **OK** to create the order. The selected customer must use the same currency as the auto charges you set up (*USD*).
1. The new sales order opens. On the Action Pane, open the **Sell** tab and, from the **Charges** group, select **Maintain charges**.
1. The **Maintain charges** page opens, showing the following two lines, which came from your autocharges setup:

    | Position | Sequence | Compound | Charges code | Category | Charges value |
    | --- | --- | --- | --- | --- | --- |
    | 1 | 1 | No | Freight | Fixed | 100 |
    | 2 | 2 | Yes | Handling | Percent | 2 |

    Note that the **Position** matches the **Sequence** from the auto charges setup. The position differs from sequence in cases where there's an overlap in sequence numbering. The position is used to calculate the value base for charges set to compound.

    In this example, a 2% charge is applied on top of the 100 USD fixed charge equaling 102 USD as total header charges. The 2% charge also applies to each order line.

    Users can change the assigned position, sequence, and compound values for a header charge applied from auto charges. But care should be taken because edits such as these can significantly impact the calculated value base used for charges set to compound.

    For example, a user might change the autocreated lines listed previously to the settings shown in the following table:

    | Position | Sequence | Compound | Charges code | Category | Charges value |
    | --- | --- | --- | --- | --- | --- |
    | 2 | 1 | No | Freight | Fixed | 100 |
    | 1 | 2 | No | Handling | Percent | 2 |

    Because of the updated the **Position** settings, the 2% charge is applied first, when the value base is still zero, so 2% or zero results in zero additional charge. Then the 100 USD fixed charge is added to give a total header charge of just 100 USD. The 2% charge still applies to each order line.

    Now, suppose the user changes the charges to the values shown in the following table:

    | Position | Sequence | Compound | Charges code | Category | Charges value |
    | --- | --- | --- | --- | --- | --- |
    | 1 | 1 | No | Freight | Fixed | 100 |
    | 2 | 2 | No | Handling | Percent | 2 |

    This time, the **Position** values match the **Sequence** from the setup, but both charges have **Compound** set to *No*. Therefore, the 100 USD fixed charge is applied first, but the 2% handling charge isn't set to compound, so it doesn't affect header charge because 2% of zero is zero (though it still adds a 2% charge to each order line). The total sum of header charges is therefore just 100 USD.

1. Close the **Maintain charges** page by selecting the back button on the Action Pane.
1. If necessary, you can revert edits made on **Maintain charges** page to the default setup lines. To do so, on the Action Pane, open the **Sell** tab and, from the **Calculate** group, select **Header auto charges**. This action only restores those lines that were automatically added from auto charges. Any charge lines that were added manually to the sales order header aren't affected by this action. This action also doesn't restore any order line charges.

## Position, Sequence, and Compound fields on header charges

As we saw in [Example scenario 1](#scenario1), charge settings on the **Maintain charges** page include the following fields:

- **Position** – Use this field to prioritize the calculation of each charge line. Lines are calculated in sequence starting with the lowest **Position** value (lowest **Position** has highest priority). This value is auto generated for all autocharge lines (based on each line's **Sequence** setting on the **Auto charges** page), but it's still editable and can be manually updated. Each **Position** value must be unique for each order (no overlaps).
- **Sequence** – This value indicates the intended position of the charge as set up on the **Auto charges** page. The value is copied from the **Auto charges** setup for each default charge line. For custom charge lines (added manually to the **Maintain charges** page), this value is set to zero. Sequence numbers don't need to be unique and therefore might overlap. If your autocharge setup includes overlapping **Sequence** numbers, the system assigns unique **Position** values starting with the most specific (customer) record. **Sequence** is an editable field and can be manually updated, but we recommend keeping it aligned with the **Position** value.
- **Compound** – Indicates whether the line should be compounded with other header charges added so far. This only applies to charges with a **Category** of *Percent*. Compounding only applies for charges added by the **Auto charges** setup.  Although the system allows you to select **Compound** for manually added charge lines, compounding isn't actually performed for such a line.

> [!NOTE]
> Though the system normally prevents you from entering duplicate **Position** values, duplicates can still occur, for example, if you delete an auto-charge line, add new manual charges, and then restore auto charges by selecting the **Header auto charges** action. In such a case, the system will use the record ID of each charge record to resolve their relative positions when calculating the value base. We recommend that you avoid this scenario because you won't be able to see how the value base was calculated.

## Example scenario 2: Value base for header charges options

When the system calculates the value of a charge with a **Category** of *Percent*, it applies the defined percentage to the *value base* calculated so far at that position of the calculation. The value base can consist of the net amount across all order lines or the net amount across all order lines including line changes, both with or without sales taxes.

The following examples show how the **Value base for header charges** option set on the **Accounts receivable parameters** page can impact your calculations. This setting is also described in the [Set up autocharge compounding and sequencing](#set-up-comp-seq) section.

### Sum of line amounts only

The following example illustrates how setting **Value base for header charges** to *Sum of line amounts only* can affect header charge calculations.

1. If you haven't already done so, [set up the auto charges specified for example scenario 1](#scenario1).
1. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. Open the **Prices** tab.
1. On the **Charges** FastTab, set **Value base for header charges** to *Sum of line net amounts only*.
1. Go to **Sales and Marketing \> Sales orders \> All sales orders**.
1. On the Action Pane, select **New** to create a new sales order
1. The **Create sales order** dialog opens. Set **Customer account** *US-004* and then select **OK** to create the order. The selected customer must use the same currency as the auto charges you set up (*USD*).
1. Your new order opens. On the **Sales order lines** FastTab, add an order line for any item and edit the **Quantity** and **Unit price** fields to make sure the line **Net amount** is 100 USD.
1. With your new order line still selected, select **Financials \> Maintain charges** from the **Sales order lines** FastTab toolbar.
1. The **Maintain charges** page opens. On the Action Pane, select **New** to add a new line charge. Then enter the following values for the new line:
    - **Charge code** – Select *Freight*.
    - **Category** – Select *Fixed*.
    - **Charges value** – Enter *10*.
    - **Currency** – Select *USD*.
1. On the Action Pane, select **Save**.
1. On the Action Pane, select the back button to return to your sales order.
1. On Action Pane, open the **Sales order** tab and, from the **View** group, select **Totals**.
1. The **Totals** dialog opens, showing the various calculation results that apply to the current order. Notice the value shown for **Total Charges**. It's calculated as follows:

    **Total Charges** = [*Line charge fixed* (10 USD)] &plus; [*Header charge fixed* (100 USD)] &plus; [*Header charge percentage and compound* (2% of line amount (2% of 100 USD = 2 USD) &plus; 2% of header charge with lower position (2% of 100 USD = 2 USD))] = 114 USD.

### Sum including charge amounts

The following example illustrates how setting **Value base for header charges** to *Sum including charge amounts* can affect header charge calculations. This setting affects header charges that have a **Category** of *Percentage*, both with or without **Compound** enabled.  

1. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. Open the **Prices** tab.
1. On the **Charges** FastTab, change **Value base for header charges** to *Sum including charge amounts*.
1. Open the sales order that you created in the previous example.
1. On Action Pane, open the **Sales order** tab and, from the **View** group, select **Totals**.
1. The **Totals** dialog opens. This time, the value shown for **Total Charges** is 114.20 USD. It's calculated as follows:

    **Total Charges** = [*Line charge fixed* (10 USD)] &plus; [*Header charge fixed* (100 USD)] &plus; [*Header charge percentage and compound* (2% of header charge with lower position (2% of 100 USD = 2 USD) &plus; 2% of line amount (2% of 100 USD = 2 USD)  &plus; 2% of line charge (2% of 10 USD = 0.20 USD))] = 114.20 USD.

When **Value base for header charges** is set to *Sum including charge amounts*, you can choose to included selected sales taxes in the value base calculation. To set up this functionality, following these steps:

1. Go to **Accounts receivable \> Charges setup \> Auto charges**.
1. On the list pane, set **Level** to *Header*.
1. On the list pane, select the auto charge that you want to set up (or create a new one).
1. On the **Lines** FastTab, select the line that you want to set up (or add a new one).
1. From the **Lines** FastTab toolbar, select **Include taxes in value base**. (This toolbar button is only shown when **Value base for header charges** is set to *Sum including charge amounts* on the **Accounts receivable parameters** page.)
1. The **Sales tax codes in value base for auto charge** page opens. Add a line for each sales tax code that you want to include in your value base calculations for the selected autocharge line.
1. On the Action Pane, select **Save**.

## Example scenario 3: Re-search on posting options

The **Re-searching on posting** option ensures that header charges are assessed against the header-charge setup upon posting. Auto charges set up as tiered charges are automatically assessed. The assessment compares automatically applied header charges against the autocharges setup. It ensures that all the header charges automatically applied to sales orders and quotations on creation are similar to the autocharges setup. All automatically added header charges that were manually changed or deleted are restored. All manually added header charges are left unchanged. The setting ensures that the autocharge setup is always applied.

> [!NOTE]
> Tiered charges are only supported for sales orders, and are therefore only included in the re-search for sales orders.

The following procedure illustrates the effect of the **Re-search on posting** option.

1. If you haven't already done so, [set up the auto charges specified for example scenario 1](#scenario1).
1. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. Open the **Prices** tab.
1. On the **Charges** FastTab, make the following settings:
    - **Re-search on posting** – Set to *Yes*.
    - **value base for header charges** – Set to *Sum of line net amounts only*.
1. Go to **Sales and Marketing \> Sales orders \> All sales orders**.
1. On the Action Pane, select **New** to create a new sales order
1. The **Create sales order** dialog opens. Set **Customer account** *US-004* and then select **OK** to create the order. The selected customer must use the same currency as the auto charges you set up (*USD*).
1. The new sales order opens. On the Action Pane, open the **Sell** tab and, from the **Charges** group, select **Maintain charges**.
1. The **Maintain charges** page opens, showing lines that came from your autocharges setup.
1. Use the **Delete** button on the Action Pane to delete each of the autocharge lines so that there are no charges listed.
1. Select **New** on the Action Pane to add a new charge line. Then make the following settings for the new line:
    - **Position** – Enter *3*.
    - **Sequence** – Enter *3*.
    - **Charges code** – Select *Freight*.
    - **Category** – Select *Fixed*.
    - **Charges value** – Enter *10*.
    - **Currency** – Select *USD*.
1. On the Action Pane, select **Save**.
1. On the Action Pane, select the back button to return to your sales order.
1. On the Action Pane, open the **Sales order** tab and, from the **View** group, select **Totals**.
1. On the **Totals** dialog, notice that **Total charges** shows the value of the fixed header charge that you just added (10 USD). Then close the dialog.
1. On the **Sales order lines** FastTab, add an order line for any item and edit the **Quantity** and **Unit price** fields to make sure the line **Net amount** is 100 USD.
1. On the Action Pane, select **Save**.
1. On the Action Pane, open the **Sell** tab and, from the **Generate** group, select **Confirm sales order**.
1. The **Confirm sales order** dialog opens. Select **OK** to confirm the order.
1. You return to the sales order. On the Action Pane, open the **Sell** tab and, from the **Charges** group, select **Maintain charges**.
1. Notice that the two auto charges you deleted have been reapplied on the sales order header while your custom line is still included. This happened because the **Re-search on posting** option is enabled and you confirmed (posted) the order. As a result, the following three lines should now be shown:

    | Position | Sequence | Compound | Charges code | Category | Charges value |
    | --- | --- | --- | --- | --- | --- |
    | 1 | 1 | No | Freight | Fixed | 100 |
    | 2 | 2 | Yes | Handling | Percent | 2 |
    | 3 | 3 | No | Freight | Fixed | 10 |

1. On the Action Pane, select the back button to return to your sales order.
1. On the Action Pane, open the **Sales order** tab and, from the **View** group, select **Totals**.
1. On the **Totals** dialog, notice that **Total charges** now shows the calculated value of all three header charges.

    **Total Charges** = [*Line charge fixed* (10 USD)] &plus; [*Header charge fixed* (100 USD)] &plus; [*Header charge percentage and compound* (2% of line amount (2% of 100 USD = 2 USD) &plus; 2% of header charge with lower position (2% of 100 USD = 2 USD))] = 114 USD.

## Example scenario 4: Combine charges on combined invoices options

The **Combine charges on combined invoices** setting on the **Accounts receivable parameters** page controls how header charges are calculated when multiple sales orders are combined into a single invoice using the *Summary update* function.

- Set **Combine charges on combined invoices** to *Yes* to first calculate the grand total of all sales orders included in the combined invoice and then apply the auto charges to that total.
- Set **Combine charges on combined invoices** to *No* to calculate header charges individually for each sales order included in the summary invoice. In scenarios where header charges are set up with the intent of representing per-invoice charges rather than a per-sales order charges, this setting can result in over charging.

The following scenario illustrates the effects of this setting:

1. If you haven't already done so, [set up the auto charges specified for example scenario 1](#scenario1).
1. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. Open the **Prices** tab and, on the **Charges** FastTab, make the following settings:
    - **Re-search on posting** – Set to *Yes*.
    - **Combine charges on combined invoices** – Set to *No*.
    - **value base for header charges** – set to *Sum of line net amounts only*.

1. Go to **Sales and Marketing \> Sales orders \> All sales orders**.
1. Follow these steps to create a new sales order with one sales line:
    1. On the Action Pane, select **New** to create a new sales order.
    1. The **Create sales order** dialog opens. Set **Customer account** *US-004* and then select **OK** to create the order. The selected customer must use the same currency as the auto charges you set up (*USD*).
    1. On the **Sales order lines** FastTab, add an order line for any item and edit the **Quantity** and **Unit price** fields to make sure the line **Net amount** is 100 USD.
    1. On the Action Pane, select **Save**.
1. Repeat the previous step to create a second, identical sales order.
1. If this were a real warehouse, warehouse workers would now pick and pack both sales orders and register their work using the Warehouse Management mobile app. However, these steps aren't necessary to continue working through this example scenario.
1. Go back to **Sales and Marketing \> Sales orders \> All sales orders**. Find and select the two new sales orders.
1. On the Action Pane, open the **Invoice** tab and, from the **Generate** group, select **Invoice**.
1. In the **Posting invoice** dialog, expand the **Parameters** FastTab and set **Summary update for** to *Invoice account*.
1. On the dialog toolbar, select **Arrange**.
1. Select **OK**.
1. Select one of the two sales orders. On the Action Pane open the **Invoice** tab and, from the **Journals** group, select **Invoice**.
1. The invoice opens. On the Action Pane, select **Charges**.

    The header charges have been calculated for each sales order. For each sales order, a header charge of 100 USD + 2% compound (2% of the line amount (100 USD) &plus; 2% of the fixed charge (100 USD)) is applied, resulting in 2 &times; 104 = 208 USD in total charges for the invoice.

1. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. Open the **Prices** tab and, on the **Charges** FastTab, make the following settings:
    - **Combine charges on combined invoices** – Change from *No* to *Yes*.

1. As you did previously, go to **Sales and Marketing \> Sales orders \> All sales orders** and create two new sales orders for the same account with identical sales lines. Then pick and pack both sales orders.
1. Go back to **Sales and Marketing \> Sales orders \> All sales orders**. Find and select the two new sales orders.
1. On the Action Pane, open the **Invoice** tab and, from the **Generate** group, select **Invoice**.
1. In the **Posting invoice** dialog, set **Summary update for** to *Invoice account*.
1. On the dialog toolbar, select **Arrange**.
1. Select **OK**.
1. Select one of the two sales orders. On the Action Pane open the **Invoice** tab and, from the **Journals** group, select **Invoice**.
1. The invoice opens. On the Action Pane, select **Charges**.

    The header auto charges have been re-searched and reapplied per invoice. The customer will be debited just one instance of the fixed auto charge of 100 USD instead of two instances because the charge is now applied per invoice instead of per sales order. The total calculated charge for the invoice is one header fixed charge of 100 USD + 2% compound (2% of the total line amounts (100 USD &plus; 100 USD) &plus; 2% of the fixed charge (100 USD)) = 106 USD in total charges.

    With this setup, the fixed auto charge is only applied once (per invoice) and the percentage-based charge set to compound is calculated from a value base that is 100 USD lower compared to header charges calculated per sales order.

1. Go back to **Sales and Marketing \> Sales orders \> All sales orders**.
1. Select the first of your two new sales orders. On the Action Pane, open the **Sell** tab and, from the **Charges** group, select **Maintain charges**. Note the charges shown and then do the same for the second new sales order.

    Notice that, as part the combining charges on combined invoices, the auto charges are now only present on the first sales order. This is by intent to ensure that the combining of charges on combined invoices provides the correct charge calculation.

> [!NOTE]
> Auto charges are applied based on customer accounts on the sales orders, not invoice accounts for the invoice. In cases where a summary update is done for sales orders for different customer accounts with the same invoice account, and where different header charges are set up for the various customer accounts, the customer account for the *last* sales order for the summary update is the customer account for which the header charges are re-searched and re-applied on invoicing.

## Pricing management

The features described in this article work together with the [Pricing management module](../pricing-management/pricing-management-overview.md). Pricing management introduces changes to the setup and search of auto charges and therefore also changes some of the behavior described in this article. When the Pricing management module is [enabled](../pricing-management/pricing-management-enable.md), then charges set up under **Accounts receivable \> Charges setup** don't apply. Instead, only those charges set up on the auto charges page specific to the Pricing management module apply for sales orders and sales quotations. To set up auto charges in Pricing management, go to **Pricing management \> During-sales pricing \> Charges setup \> Auto charges**.

## Limitations

The abilities to compound charges and define a value base upon which the compounding is applied is available for sales quotations and sales orders, not for purchase orders. This feature also introduces as few new capabilities that don't support all scenarios. The following subsections describe the most important limitations.

### Intercompany trade

The lack of compounding and sequencing support for purchase orders affects intercompany scenarios because it means that sales-order and purchase-order charges would be calculated differently. To prevent intercompany scenarios from being blocked, header charges for any sales order that fulfills a local purchase order are applied and calculated without using the compounding and sequencing features described in this article. This means that whether compounding and sequencing are applied is contextual. In intercompany scenarios, compounding and sequencing aren't applied; in non-intercompany scenarios, they are.

### Prorate and summary updates

Header charges can be assigned a charges code that is set to *prorate*. The ability to re-search on posting and to combine charges on combined invoices prevents fixed charges from auto charges from being duplicated. Combining charges on combined invoices isn't supported for header charges set to prorate. That means that prorate header charges that are applied in a summary-update scenario will always be re-searched and calculated based on the individual sales orders, not combined.

### Tiered charge and summary updates

A header charge can be set to use **From amount** and **To amount** tiers. The tiers are evaluated based on the net amount for a sales order. When you're using sequencing and compounding, tiers are always assessed against the net amount for a sales order. If the net amount for a sales order is within a tier, and a tiered charge is calculated as a percentage, then the charge will be calculated based on the current value base even though the tier was assessed based on the net amount. If you make a summary update, such as summary invoice, when the system is configured to re-search on posting, then the tiers are assessed against the net amount for the *first* sales order included in the summary update only. The tiers aren't assessed against the net amount across all order lines in the summary update.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
