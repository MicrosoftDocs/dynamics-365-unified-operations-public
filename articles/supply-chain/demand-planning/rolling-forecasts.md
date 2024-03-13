---
title: Rolling forecasts (preview)
description: Rolling forecasts let you establish a regular schedule by which your time series can automatically update and extend their forecast horizon based on the latest data and assumptions.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 03/12/2024
audience: Application User
ms.search.region: Global
ms.custom: bap-template
ms.collection:
  - bap-ai-copilot
---
 
# Rolling forecasts (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!-- KFM: Preview until April 1 -->

Rolling forecasts let you establish a regular schedule by which your time series can automatically update and extend their forecast horizon based on the latest data and assumptions. Rolling forecasts help to align the demand planning process with the changing business environment and improve the accuracy and reliability of the forecasts.

The following illustration shows an example of a rolling forecast that recurs on the first of each month.

:::image type="content" source="media/rolling-forecast-monthly.svg" alt-text="Example of a monthly rolling forecast" lightbox="media/rolling-forecast-monthly.svg":::

<!-- KFM: Add this when event-triggered processes are supported:

The following illustration shows an example of when rolling forecast processes could run and what their outputs could be.

:::image type="content" source="media/rolling-forecast-processes.svg" alt-text="Example of rolling forecast processes and output" lightbox="media/rolling-forecast-processes.svg":::

-->

[!INCLUDE [preview-note](../includes/preview-note.md)]

## How to use rolling forecasts

Once you have set up a rolling forecast, you can view different versions of the same time series to compare the historical demand, the current forecast, and the previous forecast. You can also modify, review, and edit the forecast as needed. Rolling forecasts automatically update and extend the forecast horizon each time they run.

Rolling forecasts can help you to monitor the performance of your demand planning process, identify and address issues by collaborating on the same forecast, and adjust your plans accordingly. Rolling forecasts can also help you to communicate and collaborate with other stakeholders (such as sales, marketing, and finance) and align your demand planning with the strategic goals of your organization.

> [!NOTE]
> On a continuous basis, if a forecast is fully recalculated, its baseline forecast is automatically recalculated and edits made during the previous period aren't kept. <!--KFM: This isn't clear. Please revise. -->

## Set up rolling forecasts

You can fully automate a rolling forecast by scheduling each of its processes (import data, run a transformation, run a calculation, run a forecast, and export the forecast).

Follow these steps to schedule a process.

1. Go to one of the following pages, depending on which type of process you want to schedule:
    - **Data management** \> **Import**
    - **Data management** \> **Export**
    - **Operations** \> **Forecast profile**
    - **Operations** \> **Calculations**
    - **Operations** \> **Transformations**

1. Select the profile that you want to schedule or create a new profile.
    - If you're create a new profile, then work through the creation wizard as usual. When you get to the **Set run schedule** page of the wizard, you can set up a schedule by making the settings described in the rest of this procedure. However, to fully automate most types of processes, you must have an existing time series, so we recommend that you run the profile for the first time manually to create the required time series and then edit the profile to set up the schedule using that time series.
    - If you're editing an existing profile, then go the **Run Schedule** tab.

1. Set **Run schedule** to one of the following values:
    - **None** – The process isn't scheduled to run automatically. You must run it manually.
    - **Recurring** – The process is triggered at a certain date and time according to the configured schedule (daily, weekly, or monthly).
<!--KFM: Add this when event-triggered processes are supported:
    - **Event triggered** – The process is triggered when a certain event occurs, such as when new historical data exists (such as for transformations) or when there's a new version of the input time series for the given process. -->

1. In the **Set run date recurrence** section, define when and how often the process should run, and set the start and end dates during which it should run.
1. In the **Output settings** section, choose how you want to save the output of the process. Choose one of the following options:
    - To create a new time series after each run, set **Save output as** to *Create new time series*. In the **Time series name** field, enter a base name for the new time series, and in the **Append to name** field, choose a dynamic suffix to add to the base name, which will give each time series a unique name. You can choose to use the *Run date*, *Run month*, or *Run month & year* as your suffix.
    - To add a new version to an existing time series after each run, set **Save output as** to *New version of the same time series*. Then set **Use existing time series** to the target time series (it must already exist). We recommend that you also select the **Save current as a version before overwriting** check box to maintain traceability of the whole process and make sure the system doesn't accidentally overwrite any version work in progress. For more information about how time series versions work, see [Time series and planning data](time-series.md).
