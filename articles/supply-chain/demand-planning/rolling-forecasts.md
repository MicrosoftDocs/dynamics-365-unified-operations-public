---
title: Rolling forecasts
description: Learn about rolling forecasts, which let you establish a regular schedule that your time series follow to automatically update and extend their forecast horizon.
author: AndersEvenGirke
ms.author: aevengir
ms.topic: overview
ms.date: 03/12/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Rolling forecasts

[!include [banner](../includes/banner.md)]

Rolling forecasts let you establish a regular schedule that your time series follow to automatically update and extend their forecast horizon based on the latest data and assumptions. Rolling forecasts help align the demand planning process with the changing business environment. They also help improve the accuracy and reliability of the forecasts.

The following illustration shows an example of a rolling forecast that recurs on the first of each month.

:::image type="content" source="media/rolling-forecast-monthly.svg" alt-text="Example of a monthly rolling forecast." lightbox="media/rolling-forecast-monthly.svg":::

> [!NOTE]
> On a continuous basis, when a forecast is fully recalculated, its baseline forecast is also automatically recalculated. Edits that were made during the previous period aren't kept.

<!-- KFM: Add this when event-triggered processes are supported:

The following illustration shows an example of when rolling forecast processes could run and what their outputs could be.

:::image type="content" source="media/rolling-forecast-processes.svg" alt-text="Example of rolling forecast processes and output" lightbox="media/rolling-forecast-processes.svg":::

-->

## How to use rolling forecasts

After you set up a rolling forecast, you can view different versions of the same time series to compare the historical demand, the current forecast, and the previous forecast. You can also modify, review, and edit the forecast as you require. Rolling forecasts automatically update and extend the forecast horizon each time that they run.

Rolling forecasts can help you monitor the performance of your demand planning process, identify and address issues by collaborating on a forecast, and adjust your plans accordingly. They can also help you communicate and collaborate with other stakeholders (such as sales, marketing, and finance), and align your demand planning with the strategic goals of your organization.

## Set up rolling forecasts

You can fully automate a rolling forecast by scheduling each of its processes (importing data, running a transformation, running a calculation, running a forecast, and exporting the forecast).

To schedule a process, follow these steps.

1. Go to one of the following pages, depending on the type of process that you want to schedule:

    - **Data management** \> **Import**
    - **Data management** \> **Export**
    - **Operations** \> **Forecast profile**
    - **Operations** \> **Calculations**
    - **Operations** \> **Transformations**

1. Select the profile that you want to schedule, or create a new profile.

    - If you're creating a new profile, work through the creation wizard in the usual way. When you reach the **Set run schedule** page of the wizard, you can set up a schedule by configuring the settings that are described in the rest of this procedure. However, to fully automate most types of processes, you must have an existing time series. Therefore, we recommend that you manually run the profile for the first time to create the required time series. Then edit the profile to set up the schedule by using that time series.
    - If you're editing an existing profile, select the **Run Schedule** tab.

1. Set the **Run schedule** field to one of the following values:

    - **None** – The process isn't scheduled to run automatically. You must manually run it.
    - **Recurring** – The process is triggered at a specific date and time, according to the configured schedule (daily, weekly, or monthly).
    <!--KFM: Add this when event-triggered processes are supported:
    - **Event triggered** – The process is triggered when a certain event occurs, such as when new historical data exists (such as for transformations) or when there's a new version of the input time series for the given process. -->

1. In the **Set run date recurrence** section, define when and how often the process should run, and set the start and end dates that it should run during.
1. In the **Output settings** section, follow one of these steps to specify how you want to save the output of the process:

    - To create a new time series after each run, set the **Save output as** field to *Create new time series*. Then, in the **Time series name** field, enter a base name for the new time series. In the **Append to name** field, select a dynamic suffix to add to the base name, so that each time series has a unique name. You can use the run date, the run month, or the run month and year as the suffix.
    - To add a new version to an existing time series after each run, set the **Save output as** field to *New version of the same time series*. Then set the **Use existing time series** field to the target time series. (The target time series must already exist.) We recommend that you also select the **Save current as a version before overwriting** checkbox to maintain the traceability of the whole process and ensure that the system doesn't accidentally overwrite any version work that's in progress. For more information about how time series versions work, see [Time series and planning data](time-series.md).
