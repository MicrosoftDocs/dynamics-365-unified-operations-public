---
title: Configure Supply risk assessment
description: Learn how to enable and set up Supply risk assessment, including prerequisites and an outline and process on configuring thresholds.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.topic: how-to 
ms.date: 5/19/2026 
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form: 
---

# Configure supply risk assessment

[!include [banner](../includes/banner.md)]

This article describes how to enable and set up supply risk assessment.

## Configure thresholds

Use the following procedure to configure the feature by selecting the minimum rates that you want the system to apply when it calculates your supply risks.

1. Go to **Procurement and sourcing > Setup > Supply risk assessment parameters**.
1. On the **General** tab, set the following fields:

    - **Requested receipt date acceptance rate** – Enter the minimum percentage of orders where vendors are expected to return a confirmed receipt date (CRD) that meets your requested receipt date (RRD).
    - **In-full delivery rate** – Enter the minimum percentage of deliveries that are expected to arrive in full (IF).
    - **On-Time delivery rate** – Enter the minimum percentage of deliveries that are expected to arrive on time (OT).
    - **On-time in-full delivery rate** – Enter the minimum percentage of deliveries that are expected to arrive on time and in full (OTIF).

    Each of these metrics is calculated as a rate within the relevant scope of analysis. Set the rates that you consider a risk for your business. By default, each rate threshold is set to 96 percent.

    :::image type="content" source="media/sra-parameters-general.png" alt-text="Screenshot of the General tab of the Supply risk assessment parameters page.":::

1. On the Action Pane, select **Save**.

## Initialize workspace data and configure refresh options

When you first turn on and set up the feature, the **Supply risk assessment** workspace doesn't show any data. However, because the system periodically updates the data, the workspace eventually shows data. Alternatively, you can manually initialize or refresh the data as described in the following procedure.

1. Go to **Procurement and sourcing > Workspaces > Supply risk assessment**.

    > [!NOTE]
    > You don't have to do anything in the **Supply risk assessment** workspace right now. However, you must visit it at least once after you enable the feature, to make the required data cache configuration available.

1. Go to **System administration > Setup > Data cache > Data set cache configuration**.
1. On the Action Pane, select **Edit**.
1. In the grid, select the row where the **Consumer** field is set to *VendSupplyRiskCacheDataSet*, and set the following fields for it:

    - **Enabled** – Select this checkbox to enable the system to keep the data in the **Supply risk assessment** workspace up to date. If you clear this checkbox, the data isn't updated.
    - **Refresh frequency (seconds)** – Specify how often (in seconds) the system should refresh the data in the **Supply risk assessment** workspace.
    - **Manual refresh** – Select this checkbox to enable the **Refresh data** button on the  **Data refresh status** tile on the **Supply risk assessment** page. If you clear this checkbox, the button is still shown, but it doesn't do anything.

1. On the Action Pane, select **Save**.
1. If you selected the **Manual refresh** checkbox and want to initialize or refresh the data in the **Supply risk assessment** workspace now, follow these steps:

    1. Go to **Procurement and sourcing > Workspaces > Supply risk assessment**.
    1. On the **Overview** tab, on the **Data refresh status** tile, select **Refresh data**.

## Refresh the analytics entity store data used by Power BI reports

If you didn't use purchase data for Power BI until now, you might need to refresh this data and and/or set it up so that it's automatically updated from now on. If this data isn't refreshed, your Power BI reports for supply risk assessment show errors.

1. Go to **System administration > Setup > Entity store**.
1. In the list pane, find and select the record named *Purchase cube*.
1. On the Action Pane, select **Edit**.
1. Select **Refresh** to start the refresh process. This process takes about 15 minutes.
1. To set up a scheduled refresh (recommended), set **Automatic refresh enabled** to *Yes*, and then set the **Recurrence** field to the desired refresh interval.
