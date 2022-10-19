---
title: Configure supply risk assessment
description: This topic describes how to enable and set up Supply Risk Assessment.
author: cabeln
ms.author: cabeln
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to 
ms.date: 10/17/2022 
ms.custom: bap-template
---

# Configure supply risk assessment

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

## Turn on the supply risk assessment feature

Before you can use this feature, it must be turned on in your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Procurement and sourcing*
- **Feature name:** *Assess supply risks to prevent supply chain disruptions*

## Configure thresholds

Use the following procedure to configure the feature by choosing the minimum rates you would like the system to apply when calculating your supply risks.

1. Go to **Procurement and sourcing \> Setup \> Supply risk assessment parameters**.

    ![Supply risk assessment parameters, screenshot.](media/sra-parameters-general.png "Supply risk assessment parameters, screenshot")

1. Make the following settings on the **General** tab:
    - **Requested delivery date acceptance rate** – Enter the minimum percentage of orders where vendors are expected to return a confirmed delivery date (CDD) that meets your requested delivery date (RDD).
    - **In-full delivery rate** – Enter the minimum percentage of deliveries expected to arrive in-full (IF). <!-- KFM: original text was "(IT)". I assumed "IF". Please confirm. -->
    - **On-Time delivery rate** – Enter the minimum percentage of deliveries expected to arrive on-time (OT).
    - **On-time in-full delivery rate** – Enter the minimum percentage of deliveries expected to arrive on-time and in-full (OTIF).

    Each of these metrics is calculated as a rate within the relevant scope of analysis. Set the rates that you would regard as representing a risk for your business. By default, each rate threshold is set to 96%.

1. On the Action Pane, select **Save**.

## Initialize workspace data and configure refresh options

When you first turn on and set up this feature, the **Supply risk assessment** workspace won't show any data. The system updates this data periodically, so it will eventually populate, but you can also choose to initialize or refresh it manually, as described in the following procedure.

1. Go to **System administration \> Setup \> Data cache \> Data set cache configuration**.
1. On the Action Pane, select **Edit**.
1. In the grid, select the row where **Consumer** is *VendSupplyRiskCacheDataSet* and make the following settings for it:
    - **Enabled** – Select this checkbox to allow the system to keep the **Supply risk assessment** workspace data up to date. If you clear this checkbox, the data will never be updated. <!-- KFM: I assumed this. Please confirm. -->
    - **Refresh frequency (seconds)** – Specify how often (in seconds) the system should refresh the data shown on the **Supply risk assessment** workspace.
    - **Manual refresh** – Select this checkbox to add a **Refresh data** button on the **Supply risk assessment** page. Clear this checkbox to hide the button.
    - <!-- KFM: Several more settings are here. We should consider describing all of them and making recommendations. -->
1. On the Action Pane, select **Save**.
1. If you chose to enable **Manual refresh** and want to initialize or refresh the **Supply risk assessment** workspace now, do the following steps:
    - Go to **Procurement and sourcing \> Workspaces \> Supply risk assessment**.
    - Open the **Overview** tab.
    - ON the **Data refresh status** tile, select **Refresh data**.
