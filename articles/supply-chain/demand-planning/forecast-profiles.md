---
title: Work with forecast profiles
description: Forecast profiles take an existing time series as input, prepares the data, and then run any of several available forecasting algorithms to create a new times series that predicts demand over a coming period.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/19/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Work with forecast profiles

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

The Demand planning app lets you build a collection of *forecast profiles*, each of which takes an existing time series as input, prepares the data, and then runs any of several available forecasting algorithms to create a new times series that predicts demand over a coming period.

Typically, a manager or system administrator will create the initial collection required profiles and, after that, forecasters and other users will be able to run the profiles to generate new calculated time series as needed.

## View and run existing forecast profiles

To generate a new forecast by running an existing forecast profile, follow these steps:

1. On the navigation pane, select **Operations \> Forecast profiles**.

1. Find the profile for the type of forecast you want to run and select the link in its **Name** column.

1. The detail page opens for your selected profile. It provides the following tabs:

    - **Summary** – Provides basic information about the profile. If you like, you can edit the **Name** and/or **Description** to make the profile easier to identify and work with.
    - **Horizon and time buckets** – Shows the granularity (bucket size) at which the forecast will be made (daily, weekly, or monthly) and the number of buckets that will be included in the forecast. You can modify the selections as needed. See the next section for details about how to work with these settings.
    - **Input data** – Shows the full list of available time series and indicates which of these are used by the selected profile. You can modify the selections as needed. See the next section for details about how to work with these settings.
    - **Forecast model** – Shows the forecast calculation made by the profile using a flowchart with interconnected tiles. Each tile does a specific type of operation and has settings that let you define how that operation works. See the next section for details about how to work with these settings.
    - **Jobs** – Shows a history of each time the profile was run, include date information, job status, and the times series that was generated. Select a link in the **Time Series** column to open that time series.

1. To run the profile, select **Run** on the Action Pane.

1. A dialog opens. Set **Output option** to one of the following values:
    - *Create a new time series*: The job will create a new time series. Enter a name for the new series in the**Time series name** field.
    - *Use an existing time series*: The job will overwrite or create a new version of an existing series. Use the settings provided to choose the target series, whether to overwrite or create a new version, and what thew new version should be called (if you choose to create one).

1. Select **Save and close**.

1. The new job is added to the grid on the **Jobs** tab, where you can follow the status of the new calculation. Select **Refresh** in the grid toolbar to refresh the status information.

## Create and manage forecast profiles

Each time your organization requires a new type of forecast, a manager or admin must create a new forecast profile. Once the profile is created, it will be available to users, who can run it as often as needed.

To create or edit a forecast profile, follow these steps:

1. On the navigation pane, select **Operations \> Forecast profiles**.

1. On the Action Pane, select **New**.

1. A setup wizard launches, open to the **Get started** page. Make the following settings:
    - **Name** – Enter a name for the new profile.
    - **Description** – Enter a short description of the profile.
    - **Owner** – Select the user account that owns the profile.

1. Select **Next**.

1. The **Set horizon and time buckets** page opens. Make the following settings:
    - **Time bucket** – Select the granularity (bucket size) at which the forecast should be made (daily, weekly, or monthly).
    - **Horizon in time buckets** – Enter the number of buckets to include in the forecast.

1. Select **Next**.

1. The **Select input data source** page opens. Use this page to choose which time series to use as input for your forecast. You must selected exactly one time series.
    - The **Available** tab shows the full list of available time series. To add a times series to the forecast, select its name in the grid and then select **Include data source** from the toolbar. By default, the most recent version of the time series will be used, but you can select older versions by going to the **Included** tab.
    - The **Included** tab shows the time series selected for use with this forecast. If more than one version is available, select the version you want to use from the **Output version** drop-down list.

1. When you're done selecting the input time series, select **Next.**

1. The **Select a forecasting model preset** page opens. Here, you can select a forecast model preset to use with your current profile. Browse the various presets listed under the **Available model presets** heading to see a preview of the forecast made by that preset. You'll be able to make settings and customize the forecast model as needed after you save the profile, so just pick the preset that's closest to what you're looking for and then select **Next**. For details about how to make settings and customize the forecast model used by a profile, and how to create new presets, see [Designing forecast models](designing-forecast-models.md).

1. The **Review and finish page** opens. It summarizes the settings you've made. Review your settings and then select **Review and finish** to create the new profile.

1. Your profile is now saved, but it hasn't run yet. If you're ready to run the forecast now, then select **Run** on the Action Pane.
