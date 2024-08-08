---
title: Work with forecast profiles
description: Learn how to work with forecast profiles, which prepare the data of an existing time series and then run forecasting algorithms to create a new time series.
author: t-benebo
ms.author: benebotg
ms.topic: how-to
ms.date: 10/19/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.collection:
  - bap-ai-copilot
ms.search.form:
---

# Work with forecast profiles

[!include [banner](../includes/banner.md)]

Demand planning lets you build a collection of *forecast profiles*. Each profile takes an existing time series as input, prepares the data, and then runs forecasting algorithms to create a new time series that predicts demand over a coming period.

Typically, a manager or system administrator creates the initial collection of required profiles. Forecasters and other users can then run the profiles to generate new calculated time series as they require.

## View and run existing forecast profiles

To generate a new forecast by running an existing forecast profile, follow these steps.

1. On the navigation pane, select **Operations** \> **Forecast profiles**.
1. Find the profile for the type of forecast that you want to run, and select the link for it in the **Name** column.

    The details page for the selected profile appears. It contains the following tabs:

    - **Summary** – This tab provides basic information about the profile. You can edit the name and/or description to make the profile easier to identify and work with.
    - **Horizon and time buckets** – This tab shows the granularity (bucket size) that the forecast will be made at (daily, weekly, or monthly) and the number of buckets that will be included in the forecast. You can modify the selections as you require. For information about how to work with the settings on this tab, see the [Create and manage forecast profiles](#create-profile) section.
    - **Input data** – This tab shows the full list of available time series and indicates which of them are used by the profile. You can change the selections as you require. For information about how to work with the settings on this tab, see the [Create and manage forecast profiles](#create-profile) section.
    - **Forecast model** – This tab shows the forecast calculation that the profile does. It uses a flowchart of interconnected tiles. Each tile does a specific type of operation and has settings that let you define how that operation works. For information about how to work with the settings on this tab, see the [Create and manage forecast profiles](#create-profile) section.
    - **Run schedule** – This tab lets you set up a schedule for the profile to run automatically. For details about this functionality and how to configure it, see [Rolling forecasts](rolling-forecasts.md).
    - **Jobs** – This tab shows a list of every run of the profile. It includes date information, the job status, and the time series that was generated. Select a link in the **Time Series** column to open the time series.

1. To run the profile, select **Run** on the Action Pane.
1. In the dialog box that appears, set the **Output option** field to one of the following values to define the output of the job:

    - *Create a new time series* – The job will create a new time series. If you select this value, enter a name for the new series in the **Time series name** field.
    - *Use an existing time series* – The job will overwrite an existing series or create a new version of it. If you select this value, use the fields that are provided to select the target series, specify whether you want to overwrite the existing version or create a new version, and, if you want to create a new version, specify the name of the new version.

1. Select **Save and close**.
1. The new job is added to the grid on the **Jobs** tab. There, you can follow the status of the new calculation. To update the status information, select **Refresh** on the grid toolbar.

## <a name="create-profile"></a> Create and manage forecast profiles

Each time that your organization requires a new type of forecast, a manager or admin must create a new forecast profile. After the profile is created, it becomes available to users, who can run it as often as they require.

To create or edit a forecast profile, follow these steps.

1. On the navigation pane, select **Operations** \> **Forecast profiles**.
1. On the Action Pane, select **New**.
1. A setup wizard is opened. On the **Get started** page, set the following fields:

    - **Name** – Enter a name for the new profile.
    - **Description** – Enter a short description of the profile.
    - **Owner** – Select the user account that owns the profile.

1. Select **Next**.
1. On the **Set horizon and time buckets** page, set the following fields:

    - **Time bucket** – Select the granularity (bucket size) that the forecast should be made at (daily, weekly, or monthly).
    - **Horizon in time buckets** – Enter the number of buckets to include in the forecast.

1. Select **Next**.
1. On the **Select input data source** page, select the time series to use as input for your forecast. You must select exactly one time series.

    - The **Available** tab shows the full list of available time series. To add a time series to the forecast, select its name in the grid, and then select **Include data source** on the toolbar. By default, the most recent version of the selected time series is used. However, you can select older versions on the **Included** tab.
    - The **Included** tab shows the time series that's selected for use with this forecast. If more than one version is available, select the version that you want to use in the **Output version** field.

1. When you've finished selecting the input time series, select **Next**.
1. On the **Select a forecasting model preset** page, you can select a forecast model preset to use with your current profile. Browse the presets that are listed under **Available model presets** to preview the forecast that each preset makes. You can configure settings and customize the forecast model as you require after you save the profile. Therefore, select the preset that's closest to what you're looking for, and then select **Next**. For information about how to configure settings and customize the forecast model that a profile uses, and how to create new presets, see [Design forecast models](design-forecast-models.md).
1. On the **Set run schedule** page, you can choose to set up a schedule for the profile to run automatically. For details about this functionality and how to configure it, see [Rolling forecasts](rolling-forecasts.md).
1. Select **Next**.
1. On the **Review and finish** page, review the summary of settings that you've configured, and then select **Review and finish** to create the new profile.
1. The profile is now saved, but it hasn't yet run. If you're ready to run the forecast now, select **Run** on the Action Pane.
