---
title: Work with calculation profiles
description: Learn how to work with calculation profiles, which apply predefined calculations to one or more existing time series to generate a new time series as output.
author: aevengir
ms.author: aevengir
ms.topic: how-to
ms.date: 10/19/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Work with calculation profiles

[!include [banner](../includes/banner.md)]

Demand planning in Microsoft Dynamics 365 Supply Chain Management lets you build a collection of *calculation profiles*. Each profile takes one or more existing time series as input, and applies a set of predefined calculations to generate a new time series as output.

Here are some examples of purposes that you might use calculations for:

- Increase all forecasts by 10 percent.
- Combine two forecasts, so that the result is the average of the two.
- Remove outliers from the forecast by removing some values that are completely out of range.

Typically, a manager or system administrator creates the initial collection of required profiles. Forecasters and other users can then run the profiles to generate new calculated time series as they require.

## View and run existing calculation profiles

You have to run a calculation profile only as often as you import new data into the relevant tables. Some profiles must be run only occasionally, whereas others must be run almost every time that a user works with the app.

To generate a new calculated time series by running an existing calculation profile, follow these steps.

1. On the navigation pane, select **Operations** \> **Calculations**.
1. Find the profile for the type of calculation that you want to run, and select the link for it in the **Name** column.

    The details page for the selected profile appears. It contains the following tabs:

    - **Summary** – This tab provides basic information about the profile. You can edit the name and/or description to make the profile easier to identify and work with.
    - **Input data** – This tab shows the full list of available time series and indicates which of them are used by the selected profile. You can change the selections as you require. For information about how to work with the settings on this tab, see the [Create and manage calculation profiles](#create-and-manage-calculation-profiles) section.
    - **Calculation model** – This tab shows the calculation that the profile does. It uses a flowchart of interconnected tiles. Each tile does a specific type of operation and has settings that let you define how that operation works. For information about how to work with the settings on this tab, see the [Create and manage calculation profiles](#create-and-manage-calculation-profiles) section.
    - **Run schedule** – This tab lets you set up a schedule for the profile to run automatically. For details about this functionality and how to configure it, see [Rolling forecasts](rolling-forecasts.md).
    - **Jobs** – This tab shows a list of every run of the profile. It includes date information, the job status, and the time series that was generated. Select a link in the **Time Series** column to open the time series.

1. To run the profile, select **Run** on the Action Pane.
1. In the dialog box that appears, set the **Output option** field to one of the following values to define the output of the job:

    - *Create a new time series* – The job will create a new time series. If you select this value, enter a name for the new series in the **Time series name** field.
    - *Use an existing time series* – The job will overwrite an existing series or create a new version of it. If you select this value, use the fields that are provided to select the target series, specify whether you want to overwrite the existing version or create a new version, and, if you want to create a new version, specify the name of the new version.

1. Select **Save and close**.
1. The new job is added to the grid on the **Jobs** tab. There, you can follow the status of the new calculation. To update the status information, select **Refresh** on the grid toolbar.

## Create and manage calculation profiles

Each time that your organization requires a new type of calculation, a manager or admin must create a new calculation profile. After the profile is created, it becomes available to users, who can run it as often as they require.

To create or edit a calculation profile, follow these steps.

1. On the navigation pane, select **Operations** \> **Calculations**.
1. On the Action Pane, select **New**.
1. A setup wizard is opened. On the **Get started** page, set the following fields:

    - **Name** – Enter a name for the new profile.
    - **Description** – Enter a short description of the profile.
    - **Owner** – Select the user account that owns the profile.

1. Select **Next**.
1. On the **Select input data source** page, select the time series to use as input for your calculation.

    - The **Available** tab shows the full list of available time series. To add a time series to the calculation, select its name in the grid, and then select **Include data source** on the toolbar. By default, the most recent version of each time series is used. However, you can select older versions on the **Included** tab.
    - The **Included** tab shows the time series that are included for this calculation, in the order that you added them. If more than one version of a time series is available, select the version that you want to use in the **Output version** field. To remove a time series, select it, and then select **Remove** on the toolbar.

    You can add several time series. The selection order is important, because time series are assigned an index ID (shown in the **\#** column on the **Included** tab). This index ID is referenced in the name of each input tile that you add to the calculation model.

1. When you've finished selecting the input time series, select **Next**.
1. On the **Select and configure calculation model** page, you can select a calculation model preset to use with your current profile. Browse the presets that are listed under **Available model presets** to preview the calculation that each preset does. You can configure settings and customize the calculation model as you require after you save the profile. Therefore, select the preset that's closest to what you're looking for, and then select **Next**. For information about how to configure settings and customize the calculation model that a profile uses, and how to create new presets, see [Design calculation models](design-calculation-models.md).
1. On the **Set run schedule** page, you can choose to set up a schedule for the profile to run automatically. For details about this functionality and how to configure it, see [Rolling forecasts](rolling-forecasts.md).
1. Select **Next**.
1. On the **Review and finish** page, review the summary of settings that you've configured, and then select **Review and finish** to create the new profile.
1. Your profile is now saved, but it hasn't yet run. If you're ready to run the calculation now, select **Run** on the Action Pane.
