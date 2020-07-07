---
# required metadata

title: Inventory on-hand list
description: This topic describes how to use the On-hand list page to inspect on-hand inventory details. It points out a few of the ways that the various filtering and sorting options work together, and how they can sometimes combine to produce unexpected results.
author: sherry-zheng
manager: tfehr
ms.date: 07/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: chuzheng
ms.search.validFrom: 2020-07-07
ms.dyn365.ops.version: Release 10.0.12
---

# Inventory on-hand list

[!include [banner](../includes/banner.md)]

This topic describes how to use the **On-hand list** page to inspect on-hand inventory details. It points out a few of the ways that the various filtering and sorting options work together, and how they can sometimes combine to produce unexpected results.

## Inquire on-hand inventory

To check the inventory availability, go to **Inventory management \> Inquiries and reports \> On-hand list**.

The inventory **On-hand list** pageupdates automatically when transactions are made in the inventory, whether they are forecasted, physical, or financial transactions.

Use the following tools to find the set of products you are looking for:

- Select [**Dimensions**](#_Dimensions_Display) on the Action Pane to open a dialog box where you can add or remove columns displayed in the **On-hand** grid.
- On the [**Filters** pane](#_Apply_filters_in), enter value for specific fields to only show records that match those values. Note that the filters here apply to source tables that may be aggregated later according to the dimensions you&#39;ve chosen to display. See the [examples provided later](#examples) to learn how this can affect your results.
- Select **Apply** on the **Filters** pane to generate the list of matching on-hand inventory in the **On-hand** grid.
- Select any column heading in the **On-hand** grid to sort or filter by values in that column. A quick filter at the top of the grid also gives additional filtering options. These filters apply to the results (not the source tables). See the [examples provided later](#examples) to learn how this can affect your results.

The **On-hand** grid provides the following columns of inventory information for each matching item:

| **Column** | **Description** |
| --- | --- |
| **Physical inventory** | The physical quantity available in inventory. |
| **Physical reserved** | The total quantity that was physically reserved. |
| **Available physical** | The available (not reserved) quantity available in physical inventory.<br><br>**Available physical** is a calculated field that equals **Physical inventory** minus **Physical reserved**. |
| **Available physical on extra dimensions** | The available physical quantity for all the dimensions displayed on the grid. |
| **Ordered in total** | The total quantity that are on inbound orders or have a positive quantity on various inventory journals. |
| **On Order** | The total quantity that are on outbound orders or have a negative quantity on various inventory journals. |
| **Ordered reserved** | The total quantity that are reserved on ordered receipts. The value shown here represents the total of items in outbound transactions with the status _Ordered reserved_. Items that are reserved as ordered are not physically available in inventory and therefore can&#39;t be directly picked and delivered. |
| **Available for reservation** | The total quantity on-hand inventory that can be reserved.<br><br>**Note**: If the **Reserve ordered items** check box is selected on the **Inventory and warehouse management parameters** page, the quantity in this field includes expected receipts. If the check box is not selected, the quantity does not include expected receipts. |
| **Total available** | The total available quantity.<br><br>**Total available** is a calculated field that equals **Available Physical** plus **Ordered in Total** minus **On**  **Order**. |

## Apply filters to find the records you are looking for

Use the **Filters** pane to filter the on-hand inventory list to include only records with fields that match the filtering criteria. To use the filter:

1. On the **Filters** pane, find the field you want to filter on.
2. Select a logical operator (starts with, equal to, greater than, and so on) using the drop-down list below the target field name.
3. Enter or select a value to look for.

> [!IMPORTANT]
> The **On-hand list** page is assembled from a detailed on-hand inventory table, which includes all available dimensions. However, the list shown here is a summary, so it may combine rows from the source table by aggregating according to dimensions displayed. The filters apply to the source table, not to the aggregate list, which can sometimes produce unexpected results. See the [examples provided later](#examples) to learn how this can affect your results.
> 
> However, the [filters provided on the grid](#grid-filters), including the quick filter at the top and for each column heading, do apply to the post-aggregated results.

You can modify the set of filters available on the **Filters** pane by doing the following:

- To remove a filter from the pane, select its close button ( **X** ).
- To add a filter, select **+Add** at the top of the **Filters** pane. This opens the **Add filter fields** dialog box, which shows a list of the available fields together with data type and table information for each of them. Use the column headings to filter and sort the list as needed. Mark the check box for each filed you&#39;d like to add and select **Insert** to apply your setting.

## Choose which dimensions to display

Dimensions tell you more about each item in the on-hand list and give you more ways to sort and filter the list. The selection of dimensions that you choose to show also affects the way rows are aggregated in the **On-hand list** page, which can affect how rows from the source tables are combined in the results you see (see the [examples provided later](#examples) to learn how this can affect your results).

To customize the selection of inventory dimensions displays:

1. Select **Dimensions** on the Action Pane.
2. The **Dimension display** dialog box opens, showing each of the dimensions.
3. Mark the check box for each dimension that you want to include in your grid.
4. Set **Save setup** to **Yes** if you&#39;d like your current selection to become the default next time you open the **On-hand list** page. Set it to **No** to use your new dimensions only during the current session and return to the current default selection next time.
5. Select **OK** to close the dialog box and apply your settings.

<a name="grid-filters"></a>
## Filter on the inventory on-hand list output

Select any column heading in the **On-hand** grid to sort or filter by values in that column. A quick filter at the top of the grid also gives additional filtering options. These filters apply to the results (not the source tables). See the [examples provided later](#examples) to learn how this can affect your results.

> [!NOTE]
> You can&#39;t filter and sort by all columns. Most of the quantity columns, other than **On order** , do not include sorting and filtering controls. This is because most quantity columns are calculated fields.

<a name="examples"></a>
## Examples

Your system includes a detailed inventory (non-aggregated) table that shows the following on-hand inventory:

| **Item number** | **Site** | **Warehouse** | **Physical inventory** | **Available physical** |
| --- | --- | --- | --- | --- |
| IA0001 | 1 | 1 | 1 | 1 |
| IA0001 | 1 | 2 | 2 | 2 |
| IA0001 | 1 | 3 | 1 | 1 |

### Scenario 1

The **On-hand list** page is set to show the final dimensions:

- **Item number**
- **Site**
- **Warehouse**

The **Filters** list is set with the following values:

- **Item Number** | **is exactly** | _IA0001_
- **Available Physical** | **less than or equal** | _1_

Therefore, the output looks like this:

| **Item Number** | **Site** | **Warehouse** | **Physical Inventory** | **Available Physical** |
| --- | --- | --- | --- | --- |
| IA0001 | 1 | 1 | 1 | 1 |
| IA0001 | 1 | 3 | 1 | 1 |

### Scenario 2

The **On-hand list** page is set to show the final dimensions:

- **Item number**
- **Site**

The **Filters** list is set with the following values:

- **Item Number** | **is exactly** | _IA0001_
- **Available Physical** | **less than or equal** | _1_

Note that the **Filters** apply to the detailed table shown at the start of this section. That means that the criterion **Available Physical** | **less than or equal** | _1_ will find two rows from that table (the first and third rows, each of which show a value **Available physical** of _1_). However, because the **On-hand list** page is not showing the **Warehouse** dimension, it aggregates the two original rows into a single resulting row (because both have identical values in all displayed dimensions), so here we see a single row that appears to violate the filter because **Available Physical** is now shown as 2. However, the result is correct because the **Filters** settings apply to the source table, not the aggregated table shown on the page.

Therefore, the output looks like this:

| **Item Number** | **Site** | **Physical Inventory** | **Available Physical** |
| --- | --- | --- | --- |
| IA0001 | 1 | 2 | 2 |
