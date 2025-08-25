---
title: Naïve forecasting
description: Learn about naïve forecasting, a way to handle forecasts based on low data.
author: KamilCzerniak
ms.author: kczerniak
ms.topic: article
ms.date: 08/25/2025
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Naïve forecasting

[!include [banner](../includes/banner.md)]

Forecasting models are a useful tool for creating accurate forecasts, provided they have access to large amounts of data. However, there are many cases in which such data is not available, leading to inaccurate results that can lead to over-/understocking. Naïve forecasting is a new method for handling small datasets, ensuring forecasts are predictable and related to historical data. 

## The idea behind naïve forecasting

### Models and data

Before we go into naïve forecasting , we need to talk about data. Any forecasting model is built from training data it is provided –   and its ability to make useful predictions  usually increases as the training dataset size goes up. However, there are situations where having enough data is not possible. One example is new products: if a new product has been introduced recently, it only has a couple of data points that can be used to train a model. When that happens, regular forecasting models do not have enough information to figure out trend and seasonality in data, leading to bad accuracy. 

### Consequences of not enough data on models

When not enough data can be provided to train models, their behaviour can be difficult to predict. In some cases, the model would give up on finding the right approach and instead select a constant value (usually the last encountered value or zero) as its output. In others, it identifies a trend from limited data and extends it, resulting in forecasts that differ significantly from historical data and may cause over- or understocking.

### Naïve forecasting as fallback option

When confronted with unpredictable outcomes, Demand planning uses naïve forecasting as a fallback approach. Demand planning applies this method when available data does not meet the requirements for standard forecasting models. Naïve forecasting relies on straightforward rules to produce approximate forecasts, reducing the uncertainty that may arise from regular models trained on limited datasets. It is intended solely as a fallback and not as a replacement for regular forecasting models. The use of naïve forecasting within a dimension combination indicates that the data provided may be insufficient. 

## Conditions for naive forecasting

There are three conditions that are checked when deciding whether to use naïve forecasting:
1.	Best fit model used: naïve forecasting is used by “Best fit model – version 2” or newer.   Please note that naïve forecasting is not available as a separate forecast model. 
1.	Low data condition : naïve forecasting is used only when the size of the dataset considered is low enough. This depends on auto seasonality settings:

    - If auto seasonality detection is on but seasonality is not detected, then Demand planning uses thresholds of 14 days or 12 weeks or 12 months, depending on time buckets.   If seasonality is detected, Demand planning uses regular forecasting models.

    - If auto seasonality detection is off, then Demand planning uses  seasonality hint that was provided by the user.

    If the number of data points available is less than double the threshold, then it’s considered to be low data and naïve forecasting is used. 

## How naïve forecasting works

The behaviour of naïve forecasting algorithm depends on the size of the data used for training and on which threshold triggered it. There are three methods used by the algorithm.

### Copy and fill with zeros

:::image type="content" source="media/naive-copy-and-fill-with-zeros.png" alt-text="The following image shows input data in green and forecasted data in blue. Because there are only four input data points, and the threshold is 12, the algorithm applies the copy and fill with zeros method, which results in the input values for March-June 2025 being copied to March-June 2026, with zero values inserted in between":::

This method is used when dataset size is below half of the threshold. As this is a very small amount of data, naïve forecasting simply copies the data that is provided and fills the rest with zeros up to the threshold –   this data is then repeated until predictions for all requested dates have been found. 

### Copy and linear interpolation

:::image type="content" source="media/naive-copy-and-linear-interpolation.png" alt-text="The following image shows input data in green and forecasted data in blue. Because there are eight input data points, and the threshold is 12, the algorithm applies the copy and linear method, which results in the input values for March-June 2025 being copied to March-June 2026, with linearly interpolated values inserted in between":::

For cases when dataset is above half and up to the threshold, copy and linear interpolation method is used. This method fills in the gaps in data with a linear interpolation between first and last data point, which ensures that filled data is closer to copied data compared to copy and zeros method.

### Averaged copy

:::image type="content" source="media/naive-averaged-copy.png" alt-text="The following image shows input data in green and forecasted data in blue. Because there are sixteen input data points, and the threshold is 12, the algorithm applies the averaged method, which results in the input values for July 2025-February 2026 being copied to July 2026-February 2027, with values for March-June 2027 being an average of values for March-June 2025 and March-June 2026":::

In case that the dataset is bigger than threshold but smaller than double the threshold (when regular forecasting models would be selected) naïve forecasting uses averaged copy method. This method takes an average of values seen below and above threshold and then applies them to calculate predictions. This method ensures that calculated values capture some of the changes observed in data, following seasonality determined by the threshold. 

## Limitations and caveats

1.	**Naïve forecasting is not a forecasting model, but a fallback method for low data scenarios. Please [check explainability tables](forecast-profiles.md#review-forecast-job-run-history) of forecast job runs to note which planning objects used naïve method and consider improving data quality where possible.**
1.	Naïve assumes seasonality of the data through manual hint  or pre-determined thresholds – if there is a mismatch between assumed seasonality and actual seasonality of the data (e.g., time series has different seasonality or no seasonality at all), then naïve forecasting may lead to suboptimal results.   
1.	Zero values are considered when determining whether to use naïve – this means that for planning objects with data that are far into the past (compared with the rest of the timeseries) naïve will not be used. If you want to find out how naïve would work on this type of data, consider changing forecast start date to be closer to where data is present. Please note that this will also impact accuracy of other models, as this will limit their training data (this change has been introduced in Best fit model – version 2).
