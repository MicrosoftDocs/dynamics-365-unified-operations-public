---
title: Work with calculation profiles
description: The Demand planning app lets you build a collection of calculation profiles, each of which takes one or more existing time series as input, then applies a set of predefined calculations to generate a new time series as output.
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

# Work with calculation profiles

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

The Demand planning app lets you build a collection of *calculation profiles*, each of which takes one or more existing time series as input, then applies a set of predefined calculations to generate a new time series as output. You might use calculations for any of the following purposes and more:

- Increase all forecast by 10%
- Combine two different forecasts, which result is using the average of the two
- Remove outliers on the forecast by removing out some values that may be completely our of range

Typically, a manager or system administrator will create the initial collection required profiles and, after that, forecasters and other users will be able to run the profiles to generate new calculated time series as needed.

## View and run existing calculation profiles

You only need to run a calculation profile as often as you import new data into the relevant tables. Some profiles will only need to be run occasionally, while others might be run nearly every time a user works with the app.

To generate a new calculated time series by running an existing calculation profile, follow these steps:

1. On the navigation pane, select **Operations \> Calculations**.

1. Find the profile for the type of calculation you want to run and select the link in its **Name** column.

1. The detail page opens for your selected profile. It provides the following tabs:
    - **Summary** – Provides basic information about the profile. If you like, you can edit the **Name** and/or **Description** to make the profile easier to identify and work with.
    - **Input data** – Shows the full list of available time series and indicates which of these are used by the selected profile. You can modify the selections as needed. See the next section for details about how to work with these settings.
    - **Calculation model** – Shows the calculation made by the profile using a flowchart with interconnected tiles. Each tile makes a specific type of operation and has settings that let you define how that operation works. See the next section for details about how to work with these settings.
    - **Jobs** – Shows a list of each time the profile was run, include date information, job status, and the times series that was generated. Select a link in the **Time Series** column to open that time series.

1. To run the profile, select **Run** on the Action Pane.

1. A dialog opens. Set **Output option** to one of the following values:
    - *Create a new time series*: The job will create a new time series. Enter a name for the new series in the**Time series name** field.
    - *Use an existing time series*: The job will overwrite or create a new version of an existing series. Use the settings to provided to choose the target series, whether to overwrite or create a new version, and what thew new version should be called (if you choose to create one).

1. Select **Save and close**.

1. The new job is added to the grid on the **Jobs** tab, where you can follow the status of the new calculation. Select **Refresh** in the grid toolbar to refresh the status information.

## Create and manage calculation profiles

Each time your organization requires a new type of calculation, a manager or admin must create a new calculation profile. Once the profile is created, it will be available to users, who can run it as often as needed.

To create or edit a calculation profile, follow these steps:

1. On the navigation pane, select **Operations \> Calculations**.

1. On the Action Pane, select **New**.

1. A setup wizard launches, open to the **Get started** page. Make the following settings:
    - **Name** – Enter a name for the new profile.
    - **Description** – Enter a short description of the profile.
    - **Owner** – Select the user account that owns the profile.

1. Select **Next**.

1. The **Select input data source** page opens. Use this page to choose which time series to use as input for your calculation.
    - The **Available** tab shows the full list of available time series. To add a times series to the calculation, select its name in the grid and then select **Include data source** from the toolbar. By default, the most recent version of each time series will be used, but you can select older versions by going to the **Included** tab.
    - The **Included** tab shows the time series that are included for this calculation in the order you added them. For time series that have more than one version available, select the version you want to use from the **Output version** drop-down list. To remove a time series, select it and then select **Remove** from the toolbar.

You can add several time series. The selection order is important because time series are assigned an index ID (shown in the **\#** column on the **Included** tab), which is referenced in the name of each input tile you add to the calculation model.

1. When you're done selecting the input time series, select **Next.**

1. The **Select and configure calculation model** page opens. Here, you can select a calculation model preset to use with your current profile. Browse the various presets listed under the **Available model presets** heading to see a preview of the calculation made by that preset. You'll be able to make settings and customize the calculation model however needed after you save the profile, so just pick the preset that's closest to what you're looking for and then select **Next**. For details about how to make settings and customize the calculation model used by a profile, and how to create new presets, see [Design calculation models](design-calculation-models.md).

1. The **Review and finish page** opens. It summarizes the settings you've made. Review your settings and then select **Review and finish** to create the new profile.

1. Your profile is now saved, but it hasn't run yet. If you're ready to run the calculation now, then select **Run** on the Action Pane.

