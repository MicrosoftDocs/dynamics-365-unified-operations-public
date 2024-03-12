---
title: Rolling forecasts (preview)
description: Rolling forecasts are a way of continuously updating and extending the forecast horizon based on the latest data and assumptions. Rolling forecasts help to align the demand planning process with the changing business environment and improve the accuracy and reliability of the forecasts.
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

Rolling forecasts continuously update and extend their forecast horizon based on the latest data and assumptions. Rolling forecasts help to align the demand planning process with the changing business environment and improve the accuracy and reliability of the forecasts.

The following illustration shows an example of a rolling forecast that recurs on the first of each month.

:::image type="content" source="media/rolling-forecast-monthly.svg" alt-text="Example of a monthly rolling forecast" lightbox="media/rolling-forecast-monthly.svg":::

The following illustration shows an example of when rolling forecast processes could run and what their outputs could be.

:::image type="content" source="media/rolling-forecast-processes.svg" alt-text="Example of rolling forecast processes and output" lightbox="media/rolling-forecast-processes.svg":::

[!INCLUDE [preview-note](../includes/preview-note.md)]

## How to use rolling forecasts

Once you have set up a rolling forecast, you can use the same worksheet <!--KFM: what worksheet? --> to compare the historical demand, the current forecast, and the previous forecast. You can also modify, review, and edit the forecast as needed. Rolling forecasts automatically update and extend the forecast horizon each time they run.

Rolling forecasts can help you to monitor the performance of your demand planning process, identify and address issues by collaborating on the same forecast, and adjust your plans accordingly. Rolling forecasts can also help you to communicate and collaborate with other stakeholders, such as sales, marketing and finance, and align your demand planning with the strategic goals of the organization.

> [!NOTE]
> On a continuous basis, if a forecast is fully recalculated, its baseline forecast is automatically recalculated and edits made during the previous period aren't kept. <!--KFM: This isn't clear. Please revise. -->

## Set up rolling forecasts

<!-- KFM: Shorten this, move instructions to [Work with forecast profiles (preview)](forecast-profiles.md), and add a link to that topic here.  -->

You can fully automate a rolling forecast by scheduling each of its steps (import data, run a transformation, run a calculation, run a forecast, and export the forecast). There are two types of schedules for each step:

- **Recurrent** – Triggered at a certain date and time according to the configured schedule (daily, weekly, or monthly). The first run occurs on the first scheduled instance after the start date, and then the X time will be set between the<!--KFM: incomplete sentence. Please finish... -->.
- **Event triggered** – Triggered when a certain event occurs, such as when new historical data exists (such as for transformations) or when there's a new version of the input time series for the given step.

For each process, the schedule that applies is shown<!-- KFM: Shown where? -->. For example, for import, the only available option is to schedule<!-- KFM: Same as recurrent? -->. Transformations can be either recurrent or triggered by a new historical data import. Other processes can be either recurrent or triggered when a new version of the existing time series exists.

You can create the schedule at either of the following times:

- **While creating the profile** – The **Set run schedule** section of the wizard provides settings that let you set up the recurrence and allow it to run automatically. To fully automate the process, you must have an existing time series, so we recommend that you run the profile for the first time manually and then use the existing time series.
- **By editing an existing profile** – To add or modify the schedule to go the **Run Schedule** tab on the profile itself and modify the settings.

When scheduling for the output settings, you can set the system to create a new time series every time or to create a new version of the same time series. We recommend that you create a new version so the process can be fully automated. To keep traceability of the whole process, we recommend that you choose to save current version as new version before overwriting.
