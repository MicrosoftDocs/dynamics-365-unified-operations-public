---
# required metadata

title: Inventory on-hand list
description: This article describes how to use the On-hand list page to inspect on-hand inventory details. It shows a few of the ways that the various filtering and sorting options work together, and how those options can sometimes produce unexpected results when they are combined.
author: yufeihuang
ms.date: 07/07/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: InventOnhandItem, InventOnHandItemListPage, WHSOnHand
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for articles migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: yufeihuang
ms.search.validFrom: 2020-07-07
ms.dyn365.ops.version: 10.0.12
---

# Inventory on-hand list

[!include [banner](../includes/banner.md)]

This article describes how to use the **On-hand list** page to inspect on-hand inventory details. It shows a few of the ways that the various filtering and sorting options work together, and how those options can sometimes produce unexpected results when they are combined.

## Query your on-hand inventory

To check the availability of inventory, go to **Inventory management \> Inquiries and reports \> On-hand list**.

The **On-hand list** page is automatically updated when transactions are made in inventory. Those transactions might be forecasted, physical, or financial transactions.

Use the following tools to find the set of products that you're looking for:

- On the Action Pane, select [**Dimensions**](#dimensions) to open a dialog box where you can add or remove columns that are shown in the **On-hand** grid.
- In the [**Filters** pane](#filters-pane), enter values for specific fields to show only records that match those values. Note that filters that you define here apply to source tables that might be aggregated later, according to the dimensions that you've selected to show. For information about how this behavior can affect your results, see the [examples](#examples) later in this article.
- In the **Filters** pane, select **Apply** to generate the list of matching on-hand inventory in the **On-hand** grid.
- In the **On-hand** grid, select any column heading to sort or filter by values in that column. A QuickFilter at the top of the grid provides additional filtering options. These filters apply to the results, not to the source tables. For information about how this behavior can affect your results, see the [examples](#examples) later in this article.

For each matching item, the **On-hand** grid provides the following columns of inventory information.

| Column | Description |
|---|---|
| Physical inventory | The physical quantity that is available in inventory. |
| Physical reserved | The total quantity that was physically reserved. |
| Available physical | The available (not reserved) quantity that is available in physical inventory.<p>**Available physical** is a calculated field. The value equals the **Physical inventory** value minus the **Physical reserved** value.</p> |
| Available physical on exact dimensions | The available physical quantity for all the dimensions that are shown in the grid. |
| Ordered in total | The total quantity that is included on inbound orders or that has a positive quantity in various inventory journals. |
| On order | The total quantity that is included on outbound orders or that has a negative quantity in various inventory journals. |
| Ordered reserved | The total quantity that is reserved on ordered receipts. The value in this field represents the total quantity of items in outbound transactions that have a status of _Ordered reserved_. Items that are reserved as ordered aren't physically available in inventory. Therefore, they can't be directly picked and delivered. |
| Available for reservation | The total quantity of on-hand inventory that can be reserved.<p>**Note:** If the **Reserve ordered items** check box is selected on the **Inventory and warehouse management parameters** page, the value in this field includes expected receipts. If the check box is cleared, the value excludes expected receipts.</p> |
| Total available | The total available quantity.<p>**Total available** is a calculated field. The value equals the **Available physical** value plus the **Ordered in total** value minus the **On order** value.</p> |

## <a name="filters-pane"></a>Apply filters to find the records that you're looking for

Use the **Filters** pane to filter the on-hand inventory list so that it includes only records where the field values match the filtering criteria. To define a filter, follow these steps.

1. In the **Filters** pane, find the field that you want to filter on.
2. In the field below the name of the target field, select a logical operator (for example, *starts with*, *equal to*, or *greater than*).
3. Enter or select the value to look for.

> [!IMPORTANT]
> The **On-hand list** page is assembled from a detailed on-hand inventory table that includes all available dimensions. However, the list on this page is a summary. Therefore, it might combine rows from the source table by aggregating values according to the dimensions that are shown.
>
> The filters that you define in the **Filters** pane apply to the source table, not to the aggregated list. This behavior can sometimes produce unexpected results. For information about how this behavior can affect your results, see the [examples](#examples) later in this article.
> 
> However, the [filters that are provided in the grid](#grid-filters) *do* apply to the aggregated list. These filters include both the QuickFilter at the top of the grid and the filter for each column heading.

You can modify the set of filters that is available in the **Filters** pane by following these steps.

- To remove a filter from the pane, select its **Close** button (**X**).
- To add a filter, select **Add** at the top of the **Filters** pane. The **Add filter fields** dialog box that appears shows a list of the available fields. It also shows information about the data type and table for each field. Use the column headings to filter and sort the list as you require, and then select the check box for each field that you want to add to the **Filter** pane. When you've finished, select **Insert** to apply your changes.

## <a name="dimensions"></a>Select which dimensions to show

Dimensions tell you more about each item in the on-hand inventory list, and give you more ways to sort and filter the list. The dimensions that you select to show also affect how rows are aggregated on the **On-hand list** page. This aggregation, in turn, can affect how rows from the source tables are combined in the results that you see. For information about how this behavior can affect your results, see the [examples](#examples) later in this article.

To customize the selection of inventory dimensions that is shown, follow these steps.

1. On the Action Pane, select **Dimensions**.

    The **Dimension display** dialog box that appears shows every dimension.

2. Select the check box for each dimension that you want to include in the grid.
3. If you want your selection to be used by default the next time that you open the **On-hand list** page, set the **Save setup** option to **Yes**. If you set this option to **No**, your selection will be used only during the current session. Therefore, the next time that you open the page, the current default selection will be used.
4. Select **OK** to close the dialog box and apply your changes.

## <a name="grid-filters"></a>Filter on the output of the inventory on-hand list

You can select any column heading in the **On-hand** grid to sort or filter by values in that column. A QuickFilter at the top of the grid provides additional filtering options. These filters apply to the results, not to the source tables. For information about how this behavior can affect your results, see the [examples](#examples) later in this article.

> [!NOTE]
> You can't filter and sort by all columns. Most of the quantity columns don't include sorting and filtering controls, because they are calculated fields. The **On order** column is an exception.

## <a name="examples"></a>Examples

Your system includes a detailed (non-aggregated) inventory table that shows the following on-hand inventory.

| Item Number | Site | Warehouse | Physical Inventory | Available Physical |
|---|---|---|---|---|
| IA0001 | 1 | 1 | 1 | 1 |
| IA0001 | 1 | 2 | 2 | 2 |
| IA0001 | 1 | 3 | 1 | 1 |

### Scenario 1

The **On-hand list** page is set up to show the following final dimensions:

- Item number
- Site
- Warehouse

In the **Filters** pane, the following filtering criteria are set up:

- **Item Number** \| **is exactly** \| _IA0001_
- **Available Physical** \| **less than or equal** \| _1_

Here is the resulting output.

| Item Number | Site | Warehouse | Physical Inventory | Available Physical |
|---|---|---|---|---|
| IA0001 | 1 | 1 | 1 | 1 |
| IA0001 | 1 | 3 | 1 | 1 |

### Scenario 2

The **On-hand list** page is set up to show the following final dimensions:

- Item number
- Site

In the **Filters** pane, the following filtering criteria are set up:

- **Item Number** \| **is exactly** \| _IA0001_
- **Available Physical** \| **less than or equal** \| _1_

Here is the resulting output.

| Item Number | Site | Physical Inventory | Available Physical |
|---|---|---|---|
| IA0001 | 1 | 2 | 2 |

Note that the settings in the **Filters** pane apply to the detailed (non-aggregated) inventory table that is shown at the beginning of this section. Therefore, the criterion **Available Physical** \| **less than or equal** \| _1_ finds two rows from that table (the first and third rows, each of which shows an **Available Physical** value of _1_). However, in this scenario, the **On-hand list** page isn't set up to show the **Warehouse** dimension. Therefore, it aggregates the two original rows into a single resulting row, because both rows have identical values in all the dimensions that are shown. This row appears to violate the filtering criterion, because the **Available Physical** value is shown as _2_. However, the result is correct, because the settings in the **Filters** pane apply to the source table, not to the aggregated table that is shown on the **On-hand list** page.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]