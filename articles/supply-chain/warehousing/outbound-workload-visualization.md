---
# required metadata

title: Outbound workload visualization
description: Outbound workload visualization enables warehouse managers and supervisors to create custom workload charts that can be used to monitor progress of current work and what is left of it. Warehouse managers can create multiple views and set up auto refresh as needed.
author: Mirzaab
manager: tfehr
ms.date: 08/28/2020
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
ms.author: mirzaab
ms.search.validFrom: 2020-08-28
ms.dyn365.ops.version: Release 10.0.13
---

# Outbound workload visualization

[!include [banner](../includes/banner.md)]

Outbound workload visualization is suitable to be displayed on warehouse performance screens.

Advanced setup capabilities accessible from the **Outbound workload visualization** page enable warehouse managers and supervisors to create custom workload charts that can be used to monitor progress of current work and what is left of it. Warehouse managers can create multiple views and set up auto refresh as needed.

This functionality can be used to track the progress of picking work. The feature is integrated with labor management and, if labor management is set, visualization can show a calculation of the number of hours left for the displayed picking work (filtered).

## Turn on the outbound workload visualization feature

Before you can use this feature, it must be turned on in your system. Admins can use the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Warehouse management*
- **Feature name:** *Outbound workload visualization*

## Set up outbound workload visualizations

To set up your visualizations, you will create a collection of filters, and design each of them to show a different type of analysis. You'll use the **Configure filters** page to design your filters.

To set up an outbound workload visualization:

1. Go to **Warehouse management \> Warehouse monitoring reports \> Outbound workload visualization**.

1. The **Outbound workload visualization** page opens. This is where your visualization will be shown once you create some filters. You can create as many filters (views) as you want, and all are saved under your user account for later use. This means that each user will have their own set of self-created filters, which aren't shared with other users.

1. On the Action Pane, open the **Filters** tab and then select **Configure filters**.

1. The **Configure filters** page opens. Select **New** on the Action Pane to add new filter and make the following settings for it:

    - **X-axis group table** – Select the table that contains the field by which you will group the X-axis values.
    - **X-axis group field** – Select the field (from the selected **X-axis group table**) by which you will group the X-axis values.
    - **X-axis value table** – Select the table that contains the field by which the groups can be further analyzed.
    - **X-axis value field** –Select the field (from the selected **X-axis value table**) that provides values to be analyzed for each of the groups
    - **Auto-refresh** – Choose whether the visualization should be auto-refreshed.
    - **Refresh interval (minutes)** – Enter the number of minutes between each auto refresh.
    - **Display level** – Choose whether the chart should display _Open lines_ or _Open header counts_.
    - **Picking type** – If you have set the **Display level** to _Open lines_, then this setting controls whether the count of open work lines on the chart includes _Initial_ picks, _Staged_ picks, or both _Initial and staged picks_.
    - **Site** – Select the site for which the chart should be loaded.
    - **Warehouse** – Select the warehouse for which the chart should be loaded.
    - **Days to include** – Enter the number of days in the past for which the chart is generated.
    - **Work order type** – Select the outbound work order types to filter on.

    ![Configure filters](media/work-viz-filters-1.png "Configure filters")

1. Close the **Configure filters** page to return to the **Outbound workload visualizations** page, which now shows data based on your new filter settings. Your new filter is now available and selected in the **Filter** drop-down list. The following information and settings are available at the top of the chart:
    - **Filter** - This list includes all of the filters that you have created so far. Choose a filter to see its data in the chart.
    - **Last refreshed** - Shows the date and time the information in the chart was last updated.
    - **Estimated/actual time**: If you have labor standards set on your system, then set this to *Yes* if you'd like to show accumulated estimated picking times at the top of each column in the chart. If you aren't using labor standards, this setting is disabled.

    ![Example visualization](media/work-viz-chart.png "Example visualization")

1. The chart is active, so you can select any bar on the chart to view the associated work line details.

    ![Work line details](media/work-viz-work-details.png "Work line details")

## Example: Outbound workload visualization for zones

Suppose you want to set up a visualization that shows work lines for each zone and their status (_Open_, _Closed_, or _Canceled_). To do this, you could set up a filter with the following settings:

- **Filter name** – Enter a name for this filter (such as _Zone vs. work status_).
- **Description** – Enter a short description for this filter (such as _Zone vs. work status_).
- **X-axis group table** – Select _Locations._
- **X-axis group** – Select _Zone ID_.
- **X-axis value table** – Select _Work_ (because we want to view work per zone).
- **X-axis value field** – Select _Work status_ (because we want to see work status).
- **Auto refresh** – Choose whether you would like to auto refresh visualization.
- **Picking type** – Select _Initial picks and staged picks_. This means that we want to include both initial picks and picks from staging locations. So, essentially, all pick work lines we have.
- **Display level** – Select _Open lines_ (because we want to view it per line, not per work header).

The resulting chart might look like this:

![Example visualization](media/work-viz-chart.png "Example visualization")

This example chart shows two zones identified as **FLOOR** and **BULK**, plus a zone called **Blank**. Zone **Blank** represents all work lines that aren't members of any zones. The chart always shows all unrelated filtered data as **Blank** to provide as much visibility as possible. The chart shows three closed lines and four open lines in zone **FLOOR**; four closed lines, one open line, and 24 canceled lines in zone **BULK**; and 8 closed lines that aren't part of any zone and are therefore listed as **Blank**.
