---
title: Sales trade agreement prices
description:
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form: GUPPricingSetupInquiryResult, GUPParameters, PriceDiscAdmName, PriceDiscAdmTable, PriceDiscAdm
ms.topic: overview
ms.date: 03/24/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Sales trade agreement prices

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

*Sales trade agreement prices* are negotiated prices for specific products that apply for specific customers. For sales where a sales trade agreement applies, this price will take priority over the item base price.

Pricing management leverages the standard Supply Chain Management *Trade agreement price - sales price* side and enhanced with the price attributes. <!-- KFM: This sentence is unclear. What do we mean by "side"? Please revise. -->

> [!NOTE]
> Pricing management respects [Supply Chain Management sales agreements](../sales-marketing/sales-agreements.md), which are different from the *sales trade agreement prices* described in this article <!-- KFM: I think this is what we mean here. Please confirm. -->. For order lines where a *sales agreement* applies, Pricing management will use that price. If no sales agreement applies, then Pricing management will check whether an applicable *sales trade agreement price* exists. The discounts included in sales trade agreements (line discounts, multiple discounts, and total discounts) fall outside the purview of Pricing management<!-- KFM: I don't understand the point we are making here. Please revise. -->. Pricing management provides a new approach to defining discount rules.

## Configure sales trade agreement price control

Several configuration settings affect the way sales trade agreements work in Pricing management. Follow these steps to set up your system before you start creating any sales trade agreement price rules.

1. Go to the **Pricing management \> Setup \> Pricing management parameters**
1. Open the **Price and discounts** tab.
1. Expand the **Trade agreements** FastTab.
1. Set **Enable default find next** to one of the following values:
    - *Yes* – The price engine will check all applicable trade agreement prices and apply the *cheapest* price.
    - *No* – The price engine will use the *price attribute combination rank* to determine the price by applying the following rules: <!-- KFM: It isn't clear where the various ranks in this table come from or what "records" we are referring to. -->
        - Apply the record with the highest *price attribute combination rank*.
        - If two or more records have an equal and highest *price attribute combination rank*, the price engine will check the *header price attribute* and apply the highest ranked record price group.
        - If two or more records have an equal and highest *header price attribute*, the price engine will check the *line price attribute* and apply the highest ranked record in the price attribute group.
        - In case there are multiple price records found with the same rank, Price engine will apply the cheapest price.
1. Set **Apply existing trade agreement** to one of the following values:
    - *Yes* – The price engine will consider posted sales trade agreement price rule records that have a **Default relation** of *Price (sales)* (available at **Sales and Marketing \> Prices and discounts \> Trade agreement journals**). The price engine will apply the following rules:
        - First apply the sales trade agreement price that meets the criteria. <!-- KFM: What criteria do we mean here? -->
        - If no sales trade agreement price applies, then use the qualifying rules posted to the **Trade agreement journals**.
    - *No* – <!-- KFM: Description needed -->
1. Open the **General** tab.
1. Set **Date type** to the type of date (*Today*, *Requested ship date*, *Requested receipt date*, or *Created date*) you will use when setting up criteria for matching price rule records <!-- KFM: Matching to what? Sales orders? Which rules? -->.
1. Go to **Pricing management \> Setup \> Trade agreement prices \> Trade agreement journal names**. Select the **Enable price attribute** check box <!-- Which row do we mean? Are we supposed to be creating a new name here? Why do I want to select this checkbox, and what if I don't? Maybe this should be in another section. --> to allow you to create sales trade agreement journals with the price attributes.

## Set up your price component codes and pricing structures

To use sales trade agreements, you must have the following configurations available in your system:

- You must have exactly one price component code where **Price component** is set to *Sales trade agreement*. This will allow you to include sales trade agreements as part of your price structures. For more information, see [Price component codes](price-component-code.md).
- Each price structure where you want to consider sales trade agreement prices must include the *Sales trade agreement* price component code just mentioned. For more information, see [Price structure overview](price-tree-overview.md).

## Create a new sales trade agreement journal

<!-- KFM: Intro should tell us what a sales trade agreement journal is, what it is for, why we are doing this, and when we should do this. Are we actually creating the sales trade agreement rule here? -->

Follow these steps to create a new sales trade agreement journal:

1. Go to **Pricing management \> During-sales pricing \> Sales trade agreement price \> Trade agreement journals**.
1. On the Action Pane, select **New**.
1. In the **Name** field, select a trade agreement journal name. The name you choose must be configured on the **Trade agreement journal names** page with  **Enable price attributes** set to *Yes* and Relation set to *Price (sales)*.
1. With your new row still selected, select **Lines** on the Action Pane.
1. The **Journal lines, trade agreement** page opens On the Action Pane, select **New** to create a new line. <!-- KFM: We should explain what these lines mean and why we are adding them. -->
1. The **Edit price attribute** dialog opens, where you can enter the attribute value as rule condition. <!-- KFM: The second part of this sentence isn't clear. Please revise. --> 
1. Expand the **General** FastTab and make the following settings:
    - **Price attribute group combination** – Select one of the price attribute combinations that is associated with your *Sales trade agreement price* [price component code](price-component-code.md). <!-- KFM: What affect will this have? Can we give some advice? Other settings in the dialog disappear depending on what we select here.  -->
    - **Header price attribute group** – <!-- KFM: Description needed -->
    - **Line price attribute group** – <!-- KFM: Description needed -->
1. If your selected **Price attribute group combination** considers header values (rather than applying to *all* customers), then the **Header price attribute group** FastTab is available. In this case, for each row on the **Header price attribute group** FastTab, enter or select one or more values in the **Condition** column to establish the rules for selecting customers. <!-- KFM: What are we doing here? Finding orders for specific customers? --> The following rules apply.
    - All rows are combined using a logical AND operator, which means that only those customers that have matching values for *all* rows will be included.
    - If you want to create one or more rows that include multiple values, set **Enable multiple selections** to *Yes*. This will allow you to add a comma-separated list of values in the **Values** column for each row. The values are combined using an OR operator, which means that the row will find customers that match *any* of the values in the list.
    - You can specify values to exclude by adding an "!" before the value. For example, to find all customer accounts other than *DE-001*, you could set the attribute with **Attribute** *Customer account* to have **Condition** *!DE-001*. You can add the exclusion prefix to the values of any row automatically by selecting it and then selecting the **Exclude values in selected lines** button.
1. To preview the results of your settings on the **Header price attribute group** FastTab, select the **Preview matching results** button. A dialog opens, showing a preview of customers that match the conditions you've set up so far.
    - If the list includes any customers that you'd like to exclude, select the target rows and select **Exclude** from the toolbar.
    - The **Line type** column indicates which customers you have chosen to exclude using the toolbar button.
    - To re-include an excluded customer, select it and then select **Include** from the toolbar.
1. If your selected **Price attribute group combination** considers line values (rather than applying to *all* products), then the **Line price attribute group** FastTab is available. In this case, use this FastTab to establish rules for selecting products. The settings and preview options here work the same way as they do for the **Header price attribute group** FastTab.
1. Select **OK** to add the new line to the **Overview** FastTab grid on the **Journal lines, trade agreement** page.
1. Make the following settings for each line in the **Overview** FastTab grid, as needed:
    - **From** – Enter a minimum quantity for the line. This value establishes a minimum quantity that a customer must order before they can qualify for the agreement price.
    - **To** – Enter a maximum quantity for the line. This value establishes the maximum quantity above which the agreement price no longer applies. 
    - **Amount in currency** – Enter the price that applies for the line.
    - **Currency** – Select the currency you used to specify the price in the **Amount in currency** field.
    - **Unit** – Select the unit for which the price you specified applies.
    - **Allow unit conversion** – Select this check box to allow the price you specified for the selected **Unit** to be converted proportionately for sales lines that specify other units based on the available unit conversion factors. This feature allows you to maintain a single record that can apply to sales made in different units.
    - **Allow price adjustment** – Select this check box if your sales trade agreement price is not your final unit price (additional margin component price adjustments will be permitted). See the table after this procedure for an example of how this setting could affect the final unit price.
    - **Flat tier amount** – <!-- KFM: Description needed. -->
    - *Inventory dimensions* – Use columns showing inventory dimensions (such as **Color**, **Warehouse**, **Serial number**, and so on.) to further refine the conditions for a line. To choose which dimensions to show in the grid, select **Inventory \> Dimensions** from the toolbar.

    > [!TIP]
    > If you offer prices based on multiple quantity breaks, then specify each quantity bracket as a row with the relevant **From** and **To** values. For the sales trade agreement price, the tiered quantity range is per sales order line. This differs from discounts, where quantity discount tiers are per sales order line <!-- KFM: How is this different? -->.

1. For each line you added to the **Overview** FastTab, select the line and make the following settings on the **Details** tab:
    - **From date** – Enter the first date on which the selected line will be valid. <!-- KFM: Can we leave blank to include all dates? -->
    - **To date** – Enter the last date on which the selected line will be valid. <!-- KFM: Can we leave blank to include all dates? -->
    - **Price charges** – <!-- KFM: Description needed. -->
    - **Price unit** – <!-- KFM: Description needed. -->
    - **Lead time** – <!-- KFM: Description needed. -->
    - **Working days** – <!-- KFM: Description needed. -->
    - **Disregard lead time** – <!-- KFM: Description needed. -->

<!-- KFM: What is the **Error log** FastTab for? -->
1. Continue adding lines as needed. Use the following buttons on the toolbar to modify or copy existing lines:
    - **Select** – Lets you copy existing lines from posted journals to the current journal. See [Create a new journal based on posted journal lines](#select-command) for details about how to use this function.
    - **Edit price attributes** – Opens the **Edit price attributes** dialog for the selected line, so you can edit its settings as described previously in the procedure.
    - **Copy and revise** – Creates a copy of the selected line and provides a dialog where you can pre-edit settings for the newly created line.
    - **Copy line** – Creates a copy of the selected line.
    - **Clear journal** – Deletes all the lines in the journal.
    - **Select all agreements to be deleted** – <!-- KFM: Description needed. -->
    - **Restore trade agreements** – <!-- KFM: Description needed. -->

    To delete a single existing line, select it and select **Delete** from the Action Pane.

1. On the Action Pane, select **Save**.
1. On the Action Pane, select **Validate \> Validate all lines** (or validate just the selected lines by selecting **Validate \> Validate selected lines**). <!-- KFM: Why are we doing this? What affect will this have? Indicated by the **Trade agreement validation** column? -->
1. The **Price/discount Journal posting** dialog opens. Select **OK** to run the validation. <!-- KFM: Are any of these other settings relevant? -->
1. On the Action Pane, select **Post**. <!-- KFM: What does this do? WHy are we doing this now? -->
1. The **Price/discount Journal posting** dialog opens. Select **OK** to post. <!-- KFM: Are any of these other settings relevant? -->

The following tables shows an example of a pricing structure that would be affected by the **Allow price adjustment** setting for a sales trade agreement.

| Price component code | Price component | Price sequence | Value |
|---|---|---|---|
| TAM01 | Sales trade agreement price | 10 | $200 |
| MAC01 | Price adjustment 01 | 20 | $10 |
| MAC02 | Price adjustment 02 | 30 | $20 |

The final price would be affected as follows:

- If **Allow price adjustment** is *Yes*, the final unit price would be $230
- If **Allow price adjustment** is *No*, the final unit price would be $200

## <a name=select-command></a>Create a new journal based on posted journal lines

If you need to create a new journal that includes lines that are similar to a previously posted journal lines, then you can start by adding copies of the posted journal lines to your new journa;.

1. Go to **Pricing management \> During-sales pricing \> Sales trade agreement price \> Trade agreement journals**.
1. Select **New** on the Action Pane.
1. On the Action Pane, select **Lines**.
1. On the **Overview** FastTab toolbar, select **Select**.
1. The **Select** dialog opens. Use these settings to build a query that will find the matching lines from posted journals that you would like to copy to your new journal.
1. Set **Match value only** to control how the system filters the records. For example, suppose you are looking for a journal line that matches price attribute **Customer group** = *A* and you have customer *US-001* that to customer group A. Then the **Match value only** settings work as follows:
    - *Yes* – When you select customer account US-001, system won't match the line because there is no record that specifies the customer account, even though the rule applies to US-001.
    - *No* – When you select customer account US-001, system will match the line because the rule applies to US-001.
1. Once your query is set up, select **Select** to copy the matching posted trade agreement lines to a new journal.
1. Edit the copied lines as needed.
1. Validate and post the journal.

## View posted sales trade agreement prices for products and customers

Follow these steps to view posted sales trade agreement prices that apply for a selected product or customer.

1. Do one of the following steps:
    - To find trade agreement prices for products, go to **Product information management \> Products \> Released products**.
    - To find trade agreement prices for customers, go to **Sales and marketing \> Customers \> All customers**.
1. Select the product or customer you want to inspect.
1. On the Action Pane, open the **Price** tab and select **Trade agreements**.
1. The **Trade agreements** dialog opens. Criteria for finding lines for your selected product or customer are already included.
1. Set **Posted** to *Yes* to find only posted lines.
1. Set **Match value only** to *No*.
1. Select **OK**.
1. The found trade agreement lines are now shown.
