---
title: Croston's method forecasting (preview)
description: Learn about Croston's method, which is a forecasting algorithm designed to handle intermittent demand.
author: AndersEvenGirke
ms.author: aevengir
ms.reviewer: kamaybac
ms.search.form:
ms.topic: concept-article
ms.date: 11/06/2025
ms.custom: 
  - bap-template
---

# Croston's method forecasting (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Forecasting models are useful for creating accurate forecasts when they have access to large amounts of data. However, in some cases, such data isn't available, leading to inaccurate results that can cause overstocking or understocking. *Croston's method* is a forecasting algorithm designed specifically for *intermittent demand*, which is demand data that includes many zero-demand periods with occasional nonzero demands.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Models and data

Forecasting models typically rely on consistent, detailed historical data. As the dataset grows, models become better at identifying trends, seasonality, and patterns, which improves forecast accuracy. However, for some products, the data behaves differently; there are long stretches with no demand at all, followed by occasional spikes. In these cases, regular forecasting models might misinterpret the data and produce misleading predictions.

## Challenges with intermittent demand

Standard models struggle when the data includes many zero-demand periods. They might overreact to small changes, forecast zero across the board, or attempt to create a trend where none exists. These inaccurate outputs can lead to poor inventory decisions, such as overstocking low-usage items or understocking critical spare parts.

## Croston's method as a fallback option

As with [naive forecasting](naive-forecast-algorithm.md), Croston's method is a fallback option. Demand planning applies this method when the available data doesn't meet the requirements for standard forecasting models. When the system chooses to use Croston's method within a dimension combination, it indicates that the data you provided might be insufficient.

## Conditions and thresholds for using Croston's method

Croston's method forecasting applies when all of the following conditions are met:

- You're using the *Best fit model - version 3 (preview)* (or newer) forecasting algorithm. Croston's method isn't available for other forecast algorithms or as a separate algorithm.
- Your dataset doesn't fulfill the conditions for using the [naive forecasting algorithm](naive-forecast-algorithm.md).
- Your dataset doesn't have a clear seasonal pattern.
- Over 80% of values in the input time series are equal to zero.

## How Croston's method works

Croston's method doesn't try to guess exactly *when* the next demand will happen. Instead, it provides a steady, average forecast over time that reflects:

- How frequently the item is needed.
- How large the average demand is when it occurs.

The forecast stays stable and realistic, without reacting to random fluctuations or zero-demand periods. This approach gives planners a clearer view of what to expect over time.

The following image shows an example time series where Croston's method is a suitable forecasting algorithm.

:::image type="content" source="media/croston-method/crostons-method-example.png" alt-text="An example time series where Croston's method is a suitable forecasting algorithm" lightbox="media/croston-method/crostons-method-example.png":::

In this example, the demand history (green line) shows that most periods have zero orders, with occasional spikes that don't follow a pattern. This example is a typical case where Croston's method is appropriate. Instead of chasing the noise, Croston's method produces a flat forecast line (the blue line), which reflects the average demand and its frequency weighted toward recent data.

## Limitations and caveats

When you use Croston's method, the following limitations and caveats apply:

- Croston's method isn't a forecasting model that you can choose. The system uses it as a fallback for datasets when most data points are zero. [Check the explainability tables](forecast-profiles#review-forecast-job-run-history) for your forecast jobs to see which planning objects use Croston's method and consider improving the input data quality where possible.
- Adding a seasonal hint prevents the best fit algorithm from selecting Croston's method, forcing it to choose an alternative.
- The method predicts only the average interval between demands—not *when* the next demand will occur—and doesn't provide a probability distribution of sizes. Instead, it produces a flat line for a stable, realistic forecast.
- The model gives more weight to recent demand activity, allowing the forecast to better reflect current usage volume.
