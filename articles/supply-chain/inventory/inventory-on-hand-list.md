---
title: Inventory on-hand list
description: Learn how to use the On-hand list page to inspect on-hand inventory details, including an outline on querying your on-hand inventory.
author: Weijiesa
ms.author: weijiesa
ms.topic: how-to
ms.date: 01/27/2025
ms.custom:
  - bap-template
ms.reviewer: kamaybac
ms.search.form: InventOnhandItem, InventOnHandItemListPage, WHSOnHand
---

# Inventory on-hand list

[!include [banner](../includes/banner.md)]

This article describes how to use the **On-hand list** page to inspect on-hand inventory details. Use this page to understand where the goods are, what's available, what's expected, and what's reserved for use.

The on-hand inventory list provides a summarized view of all inventory and warehouse transactions in your system. On the **On-hand list** page, you can filter by dimension values (product, storage, and/or tracking dimensions) and break down output values by dimension values. The values that are shown on the page change based on the filter and display dimensions that you set. This article shows a few of the ways that the various filtering and output options work together, and how they affect the results that are presented.

In addition, you can inquire about the inventory and warehouse transactions to get an explanation of the values in the list, change the on-hand values, and find related information.

:::image type="content" source="media/on-hand-page.png" alt-text="Screenshot of the On-hand list page." lightbox="media/on-hand-page.png":::

## Query your on-hand inventory

The **On-hand list** page is automatically updated when transactions are made in inventory. Those transactions might be forecasted, physical, or financial transactions.

To check the availability of inventory, follow these steps.

1. Go to **Inventory management** \> **Inquiries and reports** \> **On-hand list**.
1. In the [**Filters** pane](#filters-pane), specify the product and locations that you want to view on-hand information for. You can add filters as you require by using the **Add** button. In addition, you can remove filters by using the **Remove** (**X**) button. Select **Apply** to view the results. The more filters you specify, the more specific the on-hand results are. Therefore, fewer rows and/or lower on-hand values are shown.
1. On the Action Pane, select [**Dimensions**](#dimensions) to open the **Dimensions display** dialog box, where you can specify the dimensions that are used to present your on-hand inventory. The more dimensions you specify, the more granular the results are. For example, if you add the **Location** storage dimension, a **Location** column is added to the grid, and the results are expanded. Instead of showing one row per warehouse, they now show one row per warehouse location.

    > [!TIP]
    > - You can save the set of dimensions that you use most often. The **On-hand list** page then automatically shows those dimensions each time that you open it. To save a dimension set, set the **Save setup** option to *Yes* in the **Dimensions display** dialog box before you close it.
    > - The on-hand information is easiest to understand when the dimensions that are shown are aligned with filters that you're using. Use the [examples](#examples) later in this article to understand how different combinations of filters and dimensions lead to different results.
    > - You can further filter the results by using the **Filter** field at the top of the grid and the dropdown lists in the column headers. Unlike the **Filters** pane, these filters apply only to the presentation of results. They don't change the result values.

The **On-hand** grid provides the following columns of inventory information.

| Column | Description |
|---|---|
| Physical inventory | The physical quantity that is available in inventory. |
| Physical reserved | The total quantity that was physically reserved. |
| Available physical | The available (not reserved) quantity that is available in physical inventory.<p>**Available physical** is a calculated field. The value equals the **Physical inventory** value minus the **Physical reserved** value.</p> |
| Available physical on exact dimensions | The available physical quantity for all the dimensions that are shown in the grid. |
| Ordered in total | The total quantity that is included on inbound orders or that has a positive quantity in various inventory journals. |
| On order | The total quantity that is included on outbound orders or that has a negative quantity in various inventory journals. |
| Ordered reserved | The total quantity that is reserved on ordered receipts. The value in this field represents the total quantity of items in outbound transactions that have a status of *Ordered reserved*. Items that are reserved as ordered aren't physically available in inventory. Therefore, they can't be directly picked and delivered. |
| Available for reservation | The total quantity of on-hand inventory that can be reserved.<p>**Note:** If the **Reserve ordered items** checkbox is selected on the **Inventory and warehouse management parameters** page, the value in this field includes expected receipts. If the checkbox is cleared, the value excludes expected receipts.</p> |
| Total available | The total available quantity.<p>**Total available** is a calculated field. The value equals the **Available physical** value plus the **Ordered in total** value minus the **On order** value.</p> |

## <a name="filters-pane"></a>Apply filters to scope on-hand calculations to items and dimensions you're looking for

Use the **Filters** pane to filter the on-hand inventory list so that it includes only records where the field values match the filtering criteria. To define a filter, follow these steps.

1. In the **Filters** pane, find the field that you want to filter on.
1. In the field below the name of the target field, select a logical operator (for example, *starts with*, *equal to*, or *greater than*).
1. Enter or select the value to look for.

> [!IMPORTANT]
> The **On-hand list** page is assembled from a detailed on-hand inventory table that includes all available dimensions. However, the list on this page is a summary. Therefore, it might combine rows from the source table by aggregating values according to the dimensions that are shown.
>
> The filters that you define in the **Filters** pane apply to the source table, not to the aggregated list. This behavior can sometimes produce unexpected results. Use the [examples](#examples) later in this article to understand how this behavior can affect your results.
>
> However, the [filters that are provided in the grid](#grid-filters) *do* apply to the aggregated list. These filters include both the QuickFilter at the top of the grid and the filter for each column heading.

You can modify the set of filters that is available in the **Filters** pane by following these steps.

- To remove a filter from the pane, select its **Close** button (**X**).
- To add a filter, select **Add** at the top of the **Filters** pane. The **Add filter fields** dialog box that appears shows a list of the available fields. It also shows information about the data type and table for each field. Use the column headings to filter and sort the list as you require, and then select the checkbox for each field that you want to add to the **Filter** pane. When you've finished, select **Insert** to apply your changes.

## <a name="dimensions"></a>Select the dimensions you want on-hand results for

Dimensions tell you more about each item in the on-hand inventory list. They also give you more ways to sort and filter the list. The dimensions that you select to show affect how rows are aggregated on the **On-hand list** page. This aggregation, in turn, can affect how rows from the source tables are combined in the results that are shown. Use the [examples](#examples) later in this article to understand how this behavior can affect your results.

To customize the selection of inventory dimensions that is shown, follow these steps.

1. On the Action Pane, select **Dimensions**.

    The **Dimension display** dialog box that appears shows every dimension.

1. Select the checkbox for each dimension that you want to include in the grid.
1. If you want your selection to be used by default the next time that you open the **On-hand list** page, set the **Save setup** option to *Yes*. If you set this option to *No*, your selection is used only during the current session. Therefore, the next time that you open the page, the current default selection will be used.
1. Select **OK** to close the dialog box and apply your changes.

## Investigate and act on the on-hand information

The on-hand information on the **On-hand list** page is aggregated based on the filters and dimensions that you specified. In SQL terms, filters control the `WHERE` clause of the on-hand calculation, and dimensions control the `GROUP BY` clause. These clauses, in turn, control how many records and columns are shown in the on-hand list. Nevertheless, you might still have to further inspect a specific value in the on-hand information.

To learn more about the transactions that participated in the on-hand calculation, follow these steps.

1. On the Action Pane, select **Transactions**. The [**Inventory transactions**](inventory-transactions-details.md) page appears. The same filters and dimensions that you used in the on-hand list are applied to this page.
1. On the Action Pane, select **Warehouse transactions**. The [**Warehouse transactions**](../warehousing/warehouse-transactions.md) page appears. The same filters and dimensions that you used in the on-hand list are applied to this page.

Inspect the Action Pane to find useful actions that are related to your on-hand inventory. For example, you can perform the following actions:

- Update your on-hand quantity by selecting **Quantity adjustment**.
- Investigate on-hand inventory in other companies by selecting **Intercompany on-hand**.

## Understand on-hand information for warehouse-enabled items

On the **On-hand list** page, items that are enabled for warehouse management processes (WMS) differ from non-WMS items in the following ways:

- WMS-enabled items are indicated by a check mark in the **Uses the warehouse management process** column. They also show helpful warnings. You can learn more about each warning by hovering over it.
- For both WMS-enabled items and non-WMS items, values in the physical inventory columns follow the same aggregation principles of filtering and requested dimensions. The value is placed on the most specific storage dimension. In the example that follows this list, **Physical inventory** is shown per license plate, except in the case of location *BULK-001* in Warehouse *24* (in row 7), because that location isn't license plate–enabled.
- Values that are shown for **Physical reserved** work differently for WMS-enabled items and non-WMS items. Because WMS-enabled items use [reservation hierarchies](../warehousing/flexible-warehouse-level-dimension-reservation.md), **Physical reserved** values are presented at the hierarchy level that is associated with the item. Therefore, in the example that follows this list, additional rows 1 and 5 are added next to rows that represent **Physical inventory** values. Different processes reserve at different levels. In the example, row 1 is related to sales process reservations that are made at the warehouse level, whereas row 5 is related to a counting operation.
- Empty rows might be included (such as row 2 in the example that follows this list). These rows indicate that there's currently no on-hand inventory, related reservation, or related order on the dimension, but there was in the past.

:::image type="content" source="media/on-hand-page-example.png" alt-text="Screenshot that shows an example of information on the On-hand list page." lightbox="media/on-hand-page-example.png":::

## <a name="grid-filters"></a>Filter on the output of the inventory on-hand list

Several columns in the **On-hand** grid let you sort or filter by values in that column by selecting the column heading. A QuickFilter at the top of the grid provides additional filtering options. These filters apply to the results, not to the source tables. Use the [examples](#examples) later in this article to understand how this behavior can affect your results.

> [!NOTE]
> You can't filter and sort by all columns. Most of the quantity columns don't include sorting and filtering controls, because they're calculated fields. The **On order** column is an exception.

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

- **Item Number** \| *is exactly* \| *IA0001*
- **Available Physical** \| *less than or equal* \| *1*

Here's the resulting output.

| Item Number | Site | Warehouse | Physical Inventory | Available Physical |
|---|---|---|---|---|
| IA0001 | 1 | 1 | 1 | 1 |
| IA0001 | 1 | 3 | 1 | 1 |

### Scenario 2

The **On-hand list** page is set up to show the following final dimensions:

- Item number
- Site

In the **Filters** pane, the following filtering criteria are set up:

- **Item Number** \| *is exactly* \| *IA0001*
- **Available Physical** \| *less than or equal* \| *1*

Here's the resulting output.

| Item Number | Site | Physical Inventory | Available Physical |
|---|---|---|---|
| IA0001 | 1 | 2 | 2 |

Note that the settings in the **Filters** pane apply to the detailed (non-aggregated) inventory table that is shown at the beginning of this section. Therefore, the criterion **Available Physical** \| *less than or equal* \| *1* finds two rows from that table (the first and third rows, each of which shows an **Available Physical** value of *1*). However, in this scenario, the **On-hand list** page isn't set up to show the **Warehouse** dimension. Therefore, it aggregates the two original rows into a single resulting row, because both rows have identical values in all the dimensions that are shown. This row appears to violate the filtering criterion, because the **Available Physical** value is shown as *2*. However, the result is correct, because the settings in the **Filters** pane apply to the source table, not to the aggregated table that is shown on the **On-hand list** page.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
