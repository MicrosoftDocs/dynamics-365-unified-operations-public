---
title: Firm planned orders
description: Learn how to firm planned orders. When planned orders are firmed, they become actual purchase orders, transfer orders, or production orders.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: ReqTransPo, ReqTransFirmLog
ms.topic: how-to
ms.date: 03/25/2026
ms.custom: 
  - bap-template
---

# Firm planned orders

[!include [banner](../../includes/banner.md)]

As part of the master planning process, you must *firm* (release) planned orders. When you firm planned orders, they become actual purchase orders, transfer orders, or production orders. These orders are also known as *released orders* or *open orders*.

Use one of three methods to firm planned orders:

- **Manual firming** – Select specific planned orders in a list, and then manually start the process.
- **Auto-firming** – Define a default firming time fence for coverage groups, individual items, and combinations of items and master plans. Then, during master planning runs, the system automatically firms planned orders if the order date is within the specified time fence for firming.
- **Query-based firming** – Define a query to select planned orders based on their properties. You can set up a batch job to run the query and firm matching orders on a regular schedule.

This article describes each method in detail.

## Manually firm planned orders

To manually firm planned orders, find and select the planned orders that you want to firm, and then manually start the firming process.

1. [Open any planned orders list page](approved-planned-order.md#view-planned-orders).
1. Use the **Filter** field, **Plan** field, and column headings to filter and sort the list so that you can find the planned orders that you're looking for.
1. Select the check box for each planned order that you want to firm. If you want to firm all the planned orders that are currently listed on the page (based on the filters that you applied), skip this step.
1. On the Action Pane, select one of the following buttons:

    - **Firm** – Firm only the selected planned orders.
    - **Firm all** – Firm all the planned orders that are currently listed on the page (based on the filters that you applied), regardless of any check boxes that are selected. This option can be useful if you're firming many planned orders.

1. In the **Firming** dialog box, on the **Parameters** FastTab, set the following fields. (Many of these fields take their default values from the **Standard update** tab on the **Master planning parameters** page.)

    - **Update marking** – Select the inventory marking policy to use when planned orders are firmed.
    - **Stop firming if an error occurs** – Set this option to *Yes* to stop firming all selected planned orders if an error occurs in one of them. Set this option to *No* if the **Parallelize firming** option is set to *Yes*.
    - **Parallelize firming** – This option is available only if you select two or more planned orders for firming. Set it to *Yes* to run the firming processes in parallel. Parallel firming can help improve performance.
    - **Number of threads** – This option is available only if you set the **Parallelize firming** option to *Yes*. Enter the number of threads to use to parallelize the firming process. For advice about how to use this option in master planning, see [Improve master planning performance](../master-planning-performance.md#number-of-threads).

        > [!NOTE]
        > A value of *0* (zero) for the **Number of threads** field increases the running time of master planning. Therefore, always set this field to a value that's more than 0.

    - **Group by vendor** – Set this option to *Yes* to group planned purchase orders and create one purchase order per vendor during firming. Alternatively, you can create one purchase order that has one line for each planned order.
    - **Group by buyer group** – Set this option to *Yes* to group planned purchase orders and create one purchase order that combines the vendor and buyer group. To use this option, you must also set the **Group by vendor** option to *Yes*.
    - **Group by purchase agreement** – Set this option to *Yes* to group planned purchase orders that have the same vendor as existing purchase agreements and create one purchase order per purchase agreement. This option is automatically enabled when **Group by vendor** is enabled. To use **Group by purchase agreement**, **Find purchase agreement** must be set to *Yes* on the **Master planning parameters** page.
    - **Group by period** (in the **Purchase orders** section) – Select the period to group planned purchase orders by. To use this option, you must also select the **Group by vendor** option.
    - **Group by period** (in the **Transfers** section) – Select the period to group planned transfer orders by. The orders are grouped based on **From warehouse** and **To warehouse** values.

    > [!NOTE]
    > Each of the "Group by" options causes the system to convert each planned order to a line in the single purchase order that results from the grouping.

    ![Parameters FastTab in the Firming dialog box.](./media/manual-firming.png "Parameters FastTab in the Firming dialog box")

1. On the **Run in the background** FastTab, set up the job so that it runs in batch mode. However, it doesn't make sense to set up a recurrent schedule when you're doing manual firming. The fields work just as they work for other types of [background jobs](../../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management. However, for manual firming, the batch job processes only the currently selected planned orders. It doesn't process any orders that fit the filters that are currently applied on the page.
1. Select **OK** to apply your settings and generate the firmed orders.

## Auto-firm planned orders

Automatic firming lets you firm planned orders as part of the master planning process. You can define a firming time fence for coverage groups, individual items, and combinations of items and master plans. Then, during master planning runs, the system automatically firms planned orders if the order date is within the specified time fence for firming. The system handles the order date (start date) differently based on whether the planned order was generated by Planning Optimization or by the deprecated planning engine.

> [!NOTE]
> You can auto-firm planned purchase orders only for items that are associated with a vendor.
>
> If you turn on change tracking, derived orders (that is, subcontract purchase orders) that the system firms have a status of *In-review*.

### Auto-firming with Planning Optimization vs. the deprecated master planning engine

You can use both Planning Optimization and the deprecated master planning engine to auto-firm planned orders. However, some important differences exist. For example, Planning Optimization uses the order date (that is, the start date) to determine which planned orders to firm, whereas the deprecated master planning engine uses the requirement date (that is, the end date). The following table summarizes the differences.

| Feature | Planning Optimization | Deprecated master planning engine |
|---|---|---|
| **Date basis** | Auto-firming is based on the order date (start date). | Auto-firming is based on the requirement date (end date). |
| **Lead time** | Because the order date (start date) triggers the firming, you don't have to consider the lead time as part of the firming time fence. | To help guarantee that the system firms orders quickly, the firming time fence must be longer than the lead time. |
| **Orders for the current week** | To firm all orders that must start during the current week, the firming time fence must be one week. | To firm all orders that must start during the current week, the firming time fence must be the lead time plus one week. |

### Set up auto-firming and the firming time fence

Turn on auto-firming by assigning an automated firming time fence to the relevant coverage setup, as described later in this section. If you don't turn on auto-firming for any coverage setup, or if you start planning from a specific page, such as the **Net requirements** page for a released product, the auto-firming process is skipped.

Grouping and marking options for auto-firming take their values from the **Standard update** tab on the **Master planning parameters** page.

You define the auto-firming time fence by the number of days that you enter for the relevant coverage setup. You can turn on auto-firming and control the firming time fence in the following ways:

- To define the default firming time fence for a coverage group, go to **Master planning** \> **Setup** \> **Coverage** \> **Coverage groups**, and select a coverage group. Then, on the **Other** FastTab, in the **Automatic firming time fence (days)** field, enter the number of days.
- To overwrite the firming time fence that you defined for the coverage group for a specific item, go to **Product information management** \> **Released products**. On the Action Pane, select **Plan**, and then select **Item coverage**. On the **General** tab, select **Override time fence**, and then, in the **Automatic firming time fence (days)** field, enter the number of days.
- To overwrite the firming time fence that you defined for the coverage group and item coverage for a specific master plan, go to **Master planning** \> **Setup** \> **Master plans**, and select a master plan. Then, on the **Time fence in days** FastTab, set the **Firming** option to *Yes*, and enter the number of days.

If you set all the previously mentioned time fences to *0* (zero), you effectively disable auto-firming for the relevant covered items.

## Firm planned orders by using a query

Query-based firming lets you plan to firm based on criteria that you define in advance. Unlike auto-firming, query-based firming lets you automate firming for different subsets of orders at different points in time. Additionally, you can use either manual or automated operations to firm different types of planned orders. You can also preview which firmed orders are selected based on your settings. Therefore, you can confirm that the selection fits your expectations.

You can combine auto-firming with query-based firming. For example, a query-based firming job has a forward time fence that is longer than the time fence for a matching auto-firming coverage configuration. Therefore, the query-based firming job processes its planned orders before the auto-firming is triggered. You can take advantage of this behavior to schedule orders for specific vendors differently than orders for similar products from other vendors.

To firm a planned order by using the query-based firming process, follow these steps:

1. Go to **Master-planning** \> **Master planning** \> **Run** \> **Planned order firming**.
1. In the **Planned order firming** dialog box, on the **Parameters** FastTab, set the basic processing, marking, and grouping options. These options work just as they do in the **Firming** dialog box. (See the previous section for descriptions.) Then, in the **Plan** section, set the following fields that are unique to the **Planned order firming** dialog box:

    - **Plan** – Select the master plan that should be applied during firming of the planned orders that this query finds.
    - **Firming time fence days forward** – Select how far in the future the various requirements and other considerations must be calculated by master planning.
    - **Firming time fence days backward** – Select how far in the past the various requirements and other considerations must be calculated by master planning.

    ![Parameters FastTab in the Planned order firming dialog box.](./media/planned-order-firming-main-1.png "Parameters FastTab in the Planned order firming dialog box")

1. To specify which records to include in the order, select the **Filter** button on the **Records to include** FastTab. A standard query dialog appears, where you can define selection criteria, sorting criteria, and joins. The fields work just as they do for other types of queries in Supply Chain Management. The fields are read-only and show values that are related to your query.

    ![Records to include FastTab on the Planned order firming dialog box.](./media/planned-order-firming-main-2.png "Records to include FastTab on the Planned order firming dialog box")

1. Select **Preview** to preview the content of your firmed order, based on your settings so far. The list of planned orders that the process firms is shown as a message. You can then adjust your settings as required until the preview shows the firmed order as you intend it.

    ![Example of a firmed order preview.](./media/planned-order-firming-preview.png "Example of a firmed order preview")

    > [!WARNING]
    > This feature firms all planned orders that match the filter criteria. Uncritical firming of planned orders can cause massive numbers of unwanted purchase, transfer, and production orders to be created. Before you continue, always use the **Preview** button to validate the records that the process includes.

1. On the **Run in the background** FastTab, set up the job so that it runs in batch mode, and/or set up a recurrent schedule. The fields work just as they do for other types of [background jobs](../../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.
1. Select **OK** to apply your settings and generate the firmed orders.

## Track firmed orders

To track planned orders that you firmed, go to **Master-planning** \> **Inquiries and reports** \> **Master planning** \> **Firming history**.

> [!NOTE]
> You can also access firming history from any of the planned order pages such as **Master-planning** \> **Master planning** \> **Planned orders**. The system creates firming history data for planned orders that you firm. Therefore, the firming history you see is unrelated to any planned order you select. The firming history you see is similar to the firming history you see when you access **Master-planning** \> **Inquiries and reports** \> **Master planning** \> **Firming history**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
