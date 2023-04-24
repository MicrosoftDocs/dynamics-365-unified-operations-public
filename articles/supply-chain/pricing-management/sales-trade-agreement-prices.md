---
title: Sales trade agreement prices
description: This article provides information about sales trade agreement prices.
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form: GUPPricingSetupInquiryResult, GUPParameters, PriceDiscAdmName, PriceDiscAdmTable, PriceDiscAdm
ms.topic: overview
ms.date: 04/03/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Sales trade agreement prices

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

*Sales trade agreement prices* are negotiated prices for specific products that apply to specific customers. For sales where a sales trade agreement applies, this price takes priority over the item base price.

Pricing management uses the standard *Trade agreement price - sales price* side in Microsoft Dynamics 365 Supply Chain Management, but it's enhanced with price attributes.

> [!NOTE]
> Pricing management respects [Supply Chain Management *sales agreements*](../sales-marketing/sales-agreements.md), which differ from the *sales trade agreement prices* that are described in this article. For order lines where a *sales agreement* applies, Pricing management will use the sales agreement. If no sales agreement applies, Pricing management will determine whether an applicable *sales trade agreement price* exists. The discounts that are included in sales trade agreements (line discounts, multiple discounts, and total discounts) are outside the purview of Pricing management. Instead, Pricing management provides a new approach to defining discount rules.

## Configure sales trade agreements, including concurrence rules

Several configuration settings affect the way that sales trade agreements work in Pricing management. Before you start to create any sales trade agreement pricing rules, follow these steps to set up your system.

1. Go to the **Pricing management \> Setup \> Pricing management parameters**.
1. On the **Price and discounts** tab, on the **Trade agreements** FastTab, set the **Enable default find next** option to one of the following values to specify how the system should resolve concurrent sales trade agreement rules:

    - *Yes* – The price engine will check all applicable trade agreement prices and apply the lowest price.
    - *No* – The price engine will use the *price attribute combination rank* to determine the price, by applying the following rules:

        1. Apply the record that has the highest *price attribute combination rank*.
        2. If two or more records have the same highest *price attribute combination rank*, check the *header price attribute*, and apply the highest-ranked record price group.
        3. If two or more records have the same highest *header price attribute*, check the *line price attribute*, and apply the highest-ranked record in the price attribute group.
        4. If multiple price records have the same rank, apply the lowest price.

1. Set the **Apply existing trade agreement** option to *Yes* if the price engine should consider posted sales trade agreement pricing rule records where the **Default relation** field is set to *Price (sales)*. (These records are available at **Sales and Marketing \> Prices and discounts \> Trade agreement journals**.) The price engine will apply the following rules:

    1. Apply the sales trade agreement price that meets the criteria.
    2. If no sales trade agreement price applies, use the qualifying rules that are posted to the trade agreement journals.

1. On the **General** tab, set the **Date type** field to the type of date that you'll use when you set up criteria for matching pricing rule records. The available values are *Today*, *Requested ship date*, *Requested receipt date*, and *Created date*.

### Concurrency example

The following table shows an example of combinations of price component code attributes.

| Price attribute combination | Price attribute combination | Header price attribute | Rank | Line price attribute | Rank |
|---|---|---|---|---|---|
| Target customer segments + Vehicle product | 2003 | Customer account | 4 | Interior Upholstery | 4 |
| Target customer segments + Vehicle product | 2003 | Customer group | 3 | Exterior color | 3 |
| Target customer segments + Vehicle product | 2003 | Price group | 2 | Fuel type | 2 |
| Target customer segments + Vehicle product | 2003 | Sales group | 1 | Drive type | 1 |

The following two records are posted for sales trade agreement price lines that have the same date range. Because the price attribute combinations are the same, the ranks of the price attribute combinations are also the same. Therefore, the price engine applies the RID0002 price.

| ID | Price attribute combination | Header price attribute criteria | Line price attribute criteria | Price | Applicable |
|---|---|---|---|---|---|
| RID0001 | Target customer segments + Product segments | Price group = 01 | Interior Upholstery = Package B | $1,500 | No |
| RID0002 | Target customer segments + Product segments | Customer account = US-003 | Interior Upholstery = Package B | $1,550 | Yes |

## Set up your price component codes and price structures

To use sales trade agreements, you must have the following configurations in your system:

- You must have exactly one price component code where the **Price component** field is set to *Sales trade agreement*. This setting lets you include sales trade agreements as part of your price structures. For more information, see [Price component codes](price-component-code.md).
- Each price structure where you want to consider sales trade agreement prices must include the previously mentioned *Sales trade agreement* price component code. For more information, see [Arrange price component codes into a price structure](price-structure-details.md).

## Manage trade agreement journal names

Follow these steps to create and manage your trade agreement journal names.

1. Go to **Pricing management \> Setup \> Trade agreement prices \> Trade agreement journal names**.
1. Follow one of these steps:

    - To create a new journal name, select **New** on the Action Pane.
    - To edit an existing journal name, select it in the grid, and then select **Edit** on the Action Pane.
    - To delete an existing journal name, select it in the grid, and then select **Delete** on the Action Pane.

1. Set the following fields for the new or selected record:

    - **Name** – Enter a name for the trade agreement journal name.
    - **Description** – Enter a short description of the trade agreement journal name.
    - **Relation** – This read-only field always shows a value of *Price (sales)*.
    - **Enable price attributes** – Select this checkbox to create sales trade agreement journals that have the price attributes.

1. On the Action Pane, select **Save**.
1. To view and manage all the trade agreement journals that use a selected trade agreement journal name, select **Trade agreement journals** on the Action Pane.

## Manage sales trade agreement journals

Follow these steps to create and manage your sales trade agreement journals.

1. Go to **Pricing management \> During-sales pricing \> Sales trade agreement price \> Trade agreement journals**.
1. Follow one of these steps:

    - To create a new journal, make sure that the **Show** field is set to *All* or *Not posted*, and then select **New** on the Action Pane.
    - To edit an existing journal, select it in the grid.
    - To delete an existing journal, select it in the grid, and then select **Delete** on the Action Pane.

    > [!TIP]
    > If you're looking for an existing journal to edit or delete, you can use the filter and/or the **Show** field to find it.

1. Set the following fields for the new or selected journal:

    - **Name** – Select an existing trade agreement journal name. For the name that you select, the **Enable price attributes** option must be set to *Yes* and the **Relation** field must be set to *Price (sales)* on the **Trade agreement journal names** page.
    - **Price/discount journal number** – A value is automatically generated the first time that you save a new journal. The field then becomes read-only. 
    - **Description** – Enter a short description of the journal. For new journals, this field takes its default value from the selected trade agreement journal name.
    - **Posted** – This read-only field shows whether the journal has been posted.
    - **Posted on** – If the journal has been posted, this read-only field shows the date when it was posted.
    - **Enable price attributes** – This read-only field takes its default value from the selected trade agreement journal name.

1. On the Action Pane, select **Save**.

## Manage pricing rules for a sales trade agreement journal

Sales trade agreement journal pricing rules control which prices apply to which combinations of customers and products. Each rule exists as a *line* that belongs to the relevant sales trade agreement journal.

Follow these steps to add, view, and manage pricing rules for a sales trade agreement journal.

1. Go to **Pricing management \> During-sales pricing \> Sales trade agreement price \> Trade agreement journals**.
1. Create or select the journal that you want to work with, as described in the previous section.
1. On the Action Pane, select **Lines**.
1. The **Journal lines, trade agreement** page appears. If you want to add a new pricing rule, select **New** on the Action Pane. If you want to work with existing rules only, skip ahead to step 10.
1. In the **Edit price attributes** dialog box, you'll set up the logic for selecting the customers and products that the line will apply to. On the **General** FastTab, in the **Price attribute group combination** field, select one of the price attribute combinations that's associated with your *Sales trade agreement price* [price component code](price-component-code.md). The value that you select controls which attributes will be available to define the customer and/or products that the line applies to.
1. If the selected price attribute group combination considers header values (that is, if it doesn't apply to *all* customers), the **Header price attribute group** FastTab is available. In this case, for each row on the **Header price attribute group** FastTab, enter or select one or more values in the **Condition** column to define the rules for selecting customers. The following rules apply:

    - All rows are combined by using a logical AND operator. Therefore, only those customers that have matching values for *all* rows will be included.
    - If you want to create one or more rows that include multiple values, set the **Enable multiple selections** option to *Yes*. You can then add a comma-separated list of values in the **Values** column for each row. These values are combined by using an OR operator. Therefore, the row will find customers that have *any* of the values in the list.
    - You can specify values to exclude by adding an exclamation mark (\!) before the value. This exclamation mark is known as an exclusion prefix. For example, to find all customer accounts except *DE-001*, set the **Condition** field to *\!DE-001* for the attribute where the **Attribute** field is set to *Customer account*. You can automatically add the exclusion prefix to the values of any row by selecting the row and then selecting **Exclude values in selected lines**.

1. To preview the results of your settings on the **Header price attribute group** FastTab, select **Preview matching results**. A dialog box shows a preview of customers that match the conditions that you've set up so far.

    - If the list includes any customers that you want to exclude, select the target rows, and then select **Exclude** on the toolbar.
    - The **Line type** column indicates which customers you've selected to exclude.
    - To re-include a previously excluded customer, select it, and then select **Include** on the toolbar.

1. If the selected price attribute group combination considers line values (that is, if it doesn't apply to *all* products), the **Line price attribute group** FastTab is available. Use this FastTab to define rules for selecting products. The fields and preview options work just as they do on the **Header price attribute group** FastTab.
1. Select **OK** to add the new line to the grid on the **Overview** FastTab of the **Journal lines, trade agreement** page.
1. On the **Overview** FastTab, for each line in the grid, set the following fields as required:

    - **Header price attribute group** – This field shows which header price attribute group was selected for the line. For lines that apply to all customers, this field is blank. To change the value, select **Edit price attribute** on the toolbar of the FastTab.
    - **Price attribute detail** – This field summarizes the header attribute values that identify the customers that the line applies to. For lines that apply to all customers, this field is blank. To change the values, select **Edit price attribute** on the toolbar.
    - **Line price attribute group** – This field shows which line price attribute group was selected for this line. For lines that apply to all products, this field is blank. To change the value, select **Edit price attribute** on the toolbar.
    - **Price attribute detail** – This field summarizes the line attribute values that identify the products that the line applies to. For lines that apply to all products, this field is blank. To change the values, select **Edit price attribute** on the toolbar.
    - **Price attribute combination rank** – This field shows the rank that's assigned to the price attribute group combination that was selected for the current line in the **Edit price attribute** dialog box. The value affects how concurrent rules are resolved when more than one rule can apply to the same order line.
    - **Allow price adjustment** – Select this checkbox if your sales trade agreement price isn't your final unit price, but additional margin component price adjustments will be permitted. For an example that shows how this setting can affect the final unit price, see the table after this procedure.
    - **Allow unit conversion** – Select this checkbox to allow the price that you specified for the selected unit to be converted proportionately for sales lines that specify other units. The conversion is based on the available unit conversion factors. This feature lets you maintain a single record that can apply to sales in different units.
    - **From** – Enter a minimum quantity for the line. This value defines the minimum quantity that a customer must order to qualify for the agreement price.
    - **To** – Enter a maximum quantity for the line. This value defines the maximum quantity that a customer can order and still qualify for the agreement price.
    - **Unit** – Select the unit that the specified price applies to.
    - **Amount in currency** – Enter the price that applies to the line.
    - **Currency** – Select the currency that you used to specify the price in the **Amount in currency** field.
    - *Inventory dimensions* – Use columns that show inventory dimensions (such as **Color**, **Warehouse**, and **Serial number**) to further refine the conditions for a line. To select which dimensions are shown in the grid, select **Inventory \> Dimensions** on the toolbar.

    > [!TIP]
    > If you offer prices based on multiple quantity breaks, specify each quantity bracket as a row that has the relevant **From** and **To** values. For the sales trade agreement price, the tiered quantity range is per sales order line. This behavior differs from the behavior for discounts, where quantity discount tiers are per sales order line.

1. Select each line that you added, and then, on the **Details** tab, set the following fields for it:

    - **From date** – Enter the first date that the selected line will be valid.
    - **To date** – Enter the last date that the selected line will be valid.

1. Continue to add lines as required. Use the following buttons on the toolbar to modify or copy existing lines:

    - **Select** – Copy existing lines from posted journals to the current journal. For information about how to use this button, see the [Create a new journal based on posted journal lines](#select-command) section of this article.
    - **Edit price attributes** – Open the **Edit price attributes** dialog box for the selected line, so that you can edit its settings as described earlier in this procedure.
    - **Copy and revise** – Create a copy of the selected line, and open a dialog box where you can pre-edit settings for the new line.
    - **Copy line** – Create a copy of the selected line.
    - **Clear journal** – Delete *all* the lines in the journal. (To delete a single existing line, select the line, and select **Delete** on the Action Pane.)

1. On the Action Pane, select **Save**.
1. To validate all the lines, select **Validate \> Validate all lines** on the Action Pane. To validate only the selected lines, select **Validate \> Validate selected lines**.
1. In the **Price/discount Journal posting** dialog box, select **OK** to run the validation.

The following table shows an example of a price structure that will be affected by the **Allow price adjustment** setting for a sales trade agreement.

| Price component code | Price component | Price sequence | Value |
|---|---|---|---|
| TAM01 | Sales trade agreement price | 10 | $200 |
| MAC01 | Price adjustment 01 | 20 | $10 |
| MAC02 | Price adjustment 02 | 30 | $20 |

The final price will be affected in the following way:

- If the **Allow price adjustment** checkbox is selected, the final unit price will be $230.
- If the **Allow price adjustment** checkbox isn't selected, the final unit price will be $200.

## Post a sales trade agreement journal

Follow these steps to post a sales trade agreement journal.

1. Go to **Pricing management \> During-sales pricing \> Sales trade agreement price \> Trade agreement journals**.
1. Select the journal that you want to post, and then select **Lines** on the Action Pane.
1. On the **Journal lines, trade agreement** page, on the Action Pane, select **Post**.
1. In the **Price/discount Journal posting** dialog box, select **OK** to post the journal.

## <a name=select-command></a>Create a new journal based on posted journal lines

If you must create a new journal that includes lines that are similar to the lines in a previously posted journal, you can start by adding copies of the posted journal lines to your new journal.

1. Go to **Pricing management \> During-sales pricing \> Sales trade agreement price \> Trade agreement journals**.
1. On the Action Pane, select **New**.
1. On the Action Pane, select **Lines**.
1. On the **Overview** FastTab, select **Select** on the toolbar.
1. The **Select** dialog box appears. Use the fields to build a query that will find the matching lines from posted journals that you want to copy to your new journal.
1. Set the **Match value only** option to control how the system filters the records. For example, you're looking for a journal line that matches price attribute **Customer group** = *A*, and you have customer *US-001* that belongs to customer group A. In this case, the **Match value only** settings work in the following way:

    - *Yes* – When you select customer account *US-001*, the system won't match the line, because there's no record that specifies the customer account, even though the rule applies to customer account US-001.
    - *No* – When you select customer account *US-001*, the system will match the line, because the rule applies to customer account US-001.

1. After your query is set up, select **Select** to copy the matching posted trade agreement lines to a new journal.
1. Edit the copied lines as required.
1. Validate and post the journal.

## View posted sales trade agreement prices for products and customers

Follow these steps to view posted sales trade agreement prices that apply to a selected product or customer.

1. Follow one of these steps:

    - To find trade agreement prices for products, go to **Product information management \> Products \> Released products**.
    - To find trade agreement prices for customers, go to **Sales and marketing \> Customers \> All customers**.

1. Select the product or customer that you want to inspect.
1. On the Action Pane, on the **Price** tab, select **Trade agreements**.
1. The **Trade agreements** dialog box appears. Criteria for finding lines for the selected product or customer are already included. Set the **Posted** option to *Yes* to find only posted lines.
1. Set the **Match value only** option to *No*.
1. Select **OK**. The trade agreement lines that are found are shown.
