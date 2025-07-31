---
title: Forecast with signals (preview)
description: Learn how to work with forecasts that combine multiple inputs.
author: AndersEvenGirke
ms.author: aevengir
ms.topic: how-to
ms.date: 07/30/2025
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Forecast with signals (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

One way to improve the accuracy of a forecast is to include input signal data beyond just historical sales. You can add signals in your forecast models by including a *Signal* step. This type of step lets you include any signal as input data. You can then use the new *Forecast with signals* step to combine the signal input and main input to create the forecast.

This article explains how to set up a forecast model that includes both a primary input (such as historical sales) and a signal input (such as inflation or weather data).

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Set up a forecast model that includes both input and a signal

Follow these steps to set up a forecast that includes both input and a signal.

1. Create a new forecast profile as described in [Create and manage forecast profiles](forecast-profiles.md#create-profile).
1. On the **Select a forecasting model preset** page, select *None*.
1. After you create and save the profile, on the **Forecast model** tab, set up your model in the following way. (Learn more in [Design forecast models](design-forecast-models.md).)

    1. Use an *Input* step to set up your primary time series.
    1. Add a *Signal* step to set up your signal time series in a parallel branch.
    1. Add other steps as required to condition the data in each branch.
    1. Add a *Forecast with signals* step to combine the two branches.
    1. Complete the model by adding a *Save* step.

    :::image type="content" source="media/forecast-with-signal-model.png" alt-text="Screenshot of a simple forecast model that uses a Forecast with signals step." lightbox="media/forecast-with-signal-model.png":::

1. On the Action Pane, select **Save**.

## Align input and signal time series

To calculate a forecast with signals, the input and signal time series must be aligned. This means that they must have compatible time bucket sizes, dimensions, and time spans.

### Time span requirements

The time span of the signal time series must cover all of the historical input data that you want to consider and extend to the end of the forecast time horizon. If the input time series extends further into the past than the signal time series, then the forecast calculation will ignore all input data that is older than the oldest signal data. If the forecast time horizon extends further into the future than the signal time series, then the forecast will fail and you'll see an error message.

The following illustration provides examples of successful and unsuccessful time span alignments.

- The first example won't work because the signal time series doesn't include any data for the forecast horizon.
- The second example won't work because the signal time series doesn't include enough data to cover the full forecast horizon.
- The third example is perfectly aligned.
- The fourth example works, but the forecast will ignore the input data that is older than the oldest signal data.

:::image type="content" source="media/forecast-signal-time-overlap.svg" alt-text="Examples of how to align the time spans for the input and signal time series." lightbox="media/forecast-signal-time-overlap.svg":::

### Dimension requirements

The input and signal time series must have compatible dimensions. For example, if the input time series has dimensions for *Country* and *Month*, then the signal time series must also have *Country* and *Month* dimensions. The system uses these dimensions to align the two time series. If the dimensions don't match, the forecast calculation will fail and you'll see an error message.

The following illustration provides examples of successful and unsuccessful dimension alignments.

- The first example won't work because the signal time series has a *Country* dimension, but the input time series doesn't.
- The second example works because both time series include dimensions for both the *Country* and the *Month*.

:::image type="content" source="media/forecast-signal-dimension-match.svg" alt-text="Examples of how to align dimensions in the input and signal time series." lightbox="media/forecast-signal-dimension-match.svg":::
