---
title: Forecast with signals (preview)
description: Learn how to work with forecasts that combine multiple inputs.
author: AndersEvenGirke
ms.author: aevengir
ms.topic: how-to
ms.date: 11/29/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Forecast with signals (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

One way to improve the accuracy of a forecast is to include input signal data beyond just historical sales. You can add signals in your forecast models by including a *Signal* step, which lets you include any signal as input data. The new *Forecast with signals* step then lets you combine the signal input and main input to create the forecast.

This article describes how to set up a forecast model that includes both a primary input (such as historical sales) and a signal input (such as inflation or weather data).

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

<!--KFM: More detail needed here. -->

## Set up a forecast model that includes both input and a signal

Follow these steps to set up a forecast that includes both input and a signal.

1. Create a new forecast profile as described in [Create and manage forecast profiles](forecast-profiles.md#create-profile).
1. On the **Select a forecasting model preset** page, select *None*.
1. After you've created and saved the profile, select the **Forecast model** tab.
1. Set up your model as follows. (Learn more in [Design forecast models](design-forecast-models.md).)
    - Use an *Input* tile to set up your primary time series.
    - Add a *Signal* tile to set up your signal time series in a parallel branch.
    - Add other steps as required to condition the data in each branch.
    - Add a *Forecast with signals* step to combine the two branches.
    - Complete the model by adding a *Save* step.

    :::image type="content" source="media/forecast-with-signal-model.png" alt-text="A simple forecast model using forecast with signal" lightbox="media/forecast-with-signal-model.png":::

1. On the Action Pane, select **Save**.
