---
title: Rolling forecasts
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

 
[!include [banner](../includes/banner.md)]

# Rolling forecasts

Rolling forecasts continuously update and extend their forecast horizon based on the latest data and assumptions. Rolling forecasts help to align the demand planning process with the changing business environment and improve the accuracy and reliability of the forecasts.

The following illustration shows an example of a rolling forecast that recurs on the first of each month.

:::image type="content" source="media/rolling-forecast-monthly.svg" alt-text="Example of a monthly rolling forecast" lightbox="media/rolling-forecast-monthly.svg":::

The following illustration shows an example of when rolling forecast processes could run and what their outputs could be.

:::image type="content" source="media/rolling-forecast-processes.svg" alt-text="Example of rolling forecast processes and output" lightbox="media/rolling-forecast-processes.svg":::

> [!NOTE]
> On a continuous basis, if a forecast is fully recalculated, its baseline forecast is automatically recalculated and edits made during the previous period aren't kept.

## Set up rolling forecasts

You can fully automate a rolling forecast by scheduling each of its steps (import data, run a transformation, run a calculation, run a forecast, and export the forecast). There are two types of schedules for each step:

- **Recurrent** – Triggered when a certain time and date are met according to the setup recurrence (daily, weekly or monthly). The schedule begins on the first instance after the start date, and then the X time will be set between the <!--KFM: incomplete sentence. Please finish... -->
- **Event triggered** – Triggered when a certain event occurs. This can occur when new historical data exists (such as for transformations), or when there is a new version of the input time series for the given step.

For each process, the schedule that applies will be shown <!-- KFM: Shown where? -->. For example, for import, the only available option will be to schedule <!-- KFM: Same as recurrent? -->. For transformation it will be recurrent or when new historical data has been imported. For the rest of the processes it will be either recurrent or when a new version of the existing time series exists.

To create the schedule there are two options:

<!--KFM: What kind of profiles are these? We should probably integrate these descriptions into the relevant profile topic. -->

- **When you are creating the profile:**  On the section **Set run schedule** on the wizard, it will allow you to create the recurrence and allow it to automatically run. Note you will need an existing time series if you want to run the fully automated process, so we recommend that you use first the profile with a manual run and then use the existing time series.
- **Once the profile is created:** To add or modify the schedule to go the Run Schedule tab on the profile itself and modify the settings
When scheduling for the Output settings, it is possible to create a new time series every time or to create a new version of the same time series. It is recommended to create a new version of the same (existing time series) so the process can be fully automated. To keep traceability of the whole process it is also recommended to Save current version as new version before overwriting.

## How to use rolling forecasts

Once you have set up the rolling forecasts in Demand planning, you can use the same worksheet <!--KFM: what worksheet? --> to compare the historical demand, the current forecast and the previous forecast. You can also modify, review, and edit the forecast as needed. Rolling forecasts automatically update and extend the forecast horizon each time they run.

Rolling forecasts can help you to monitor the performance of your demand planning process, identify and address issues by collaborating on the same forecast, and adjust your plans accordingly. Rolling forecasts can also help you to communicate and collaborate with other stakeholders, such as sales, marketing and finance, and align your demand planning with the strategic goals of the organization.
