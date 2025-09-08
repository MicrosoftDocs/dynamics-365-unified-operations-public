---
title: Naive forecasting (preview)
description: Learn about naive forecasting, which is a method to produce forecasts based on low data.
author: AndersEvenGirke
ms.author: aevengir
ms.topic: concept-article
ms.date: 09/10/2025
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Naive forecasting (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Forecasting models are useful for creating accurate forecasts when they have access to large amounts of data. However, in many cases, such data isn't available, leading to inaccurate results like overstocking or understocking. Naive forecasting is a method for handling small datasets that ensures forecasts are predictable and tied to historical data.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## The idea behind naive forecasting

### Models and data

Forecasting models use the training data you provide, and their ability to make useful predictions usually increases as the training dataset size grows. However, sometimes you can't provide enough data. For example, new products typically have only a few data points available to train a model. When that happens, regular forecasting models don't have enough information to identify trends and seasonality patterns in the data, which can lead to inaccurate forecasts.

### Consequences of insufficient data on models

When there's not enough data to train a model, the model's behavior can be difficult to predict. Sometimes, the model stops trying to find the right approach and instead selects a constant value as its output, usually the last encountered value or zero. In other cases, the model might identify and extend a trend based on limited data, resulting in forecasts that differ significantly from historical data. These inaccurate forecasts might result in overstocking or understocking.

### Naive forecasting as a fallback option

When confronted with unpredictable outcomes, demand planning can use naive forecasting as a fallback approach. Demand planning applies this method when the available data doesn't meet the requirements for standard forecasting models. Naive forecasting uses straightforward rules to produce approximate forecasts, reducing the uncertainty that arises from using regular models trained on limited datasets. Naive forecasting is only a fallback, not a replacement for regular forecasting models. Using naive forecasting within a dimension combination indicates that the data you provided might be insufficient.

## Conditions and thresholds for using naive forecasting

Naive forecasting applies when both of the following conditions are met:

1. You must use the *Best fit model - version 2 (preview)* (or newer) forecasting algorithm. Naive forecasting isn't available for other forecast algorithms or as a separate algorithm.
1. Your dataset size is below the defined threshold, with no seasonality automatically detected. The following rules apply:
    - If auto seasonality detection is on but no seasonality pattern is detected, Demand planning uses a threshold of 14 days, 12 weeks, or 12 months (depending on the size of the time buckets in your input time series). If the number of data points is less than double the threshold, it's considered low data, and naive forecasting applies.
    - If auto seasonality detection is on and a seasonality pattern is detected, Demand planning applies a regular forecasting model.
    - If auto seasonality detection is off, Demand planning uses the seasonality hint you provide instead of applying naive forecasting.

## How naive forecasting works

The behavior of the naive forecasting algorithm depends on the size of the input data and the threshold that triggers it. The algorithm uses one of three methods, as described in the following subsections.

### Copy and fill with zeros

The *copy and fill with zeros* method is used when the input dataset size is less than half of the threshold. Because only a small amount of data is available, naive forecasting copies the provided data and fills the remaining data points with zeros up to the threshold. This data is then repeated until predictions for all requested dates are found.

The following image shows an example of the *copy and fill with zeros* method. Input data appears in green, and forecasted data appears in blue. Because there are only 4 input data points, and the threshold is 12, the algorithm applies the *copy and fill with zeros* method, which results in the input values for March to June 2025 being copied to March to June 2026, with zero values inserted in between.

:::image type="content" source="media/naive-copy-and-fill-with-zeros.png" alt-text="Diagram showing example results from using the copy and fill with zeros method.":::

### Copy and linear interpolation

When the input dataset size is more than half the threshold but still less than the threshold, naive forecasting uses the *copy and linear interpolation* method. This method fills gaps in the data by using linear interpolation between the first and last data points, ensuring that filled data is closer to copied data compared to the *copy and fill with zeros* method.

The following image shows an example of the *copy and linear interpolation* method. Input data is shown in green and forecasted data is shown in blue. Because there are 8 input data points, and the threshold is 12, the algorithm applies the *copy and linear interpolation* method, which results in the input values for March–June 2025 being copied to March–June 2026, with linearly interpolated values inserted in between.

:::image type="content" source="media/naive-copy-and-linear-interpolation.png" alt-text="Diagram showing example results from using the copy and linear interpolation method.":::

### Averaged copy

When the input dataset is larger than the threshold but smaller than double the threshold, naive forecasting uses the *averaged copy* method. This method takes an average of values seen before and after the threshold and then uses these values to calculate predictions. This method ensures that calculated values reflect changes in the data and follow the seasonality determined by the threshold.

The following image shows an example of the *averaged copy* method. Input data is shown in green and forecasted data is shown in blue. Because there are 16 input data points, and the threshold is 12, the algorithm applies the *averaged copy* method, which results in the input values for July 2025 to February 2026 being copied to July 2026 to February 2027, with values for March to June 2027 being an average of values for March to June 2025 and March to June 2026.

:::image type="content" source="media/naive-averaged-copy.png" alt-text="Diagram showing example results from using the averaged copy method.":::

## Limitations and caveats

When you use naive forecasting, the following limitations and caveats apply:

- Naive forecasting isn't a forecasting model but a fallback method for low-data scenarios. [Check the explainability tables](forecast-profiles.md#review-forecast-job-run-history) for your forecast jobs to see which planning objects use the naive method, and consider improving the input data quality where possible.
- Naive forecasting assumes seasonality of the data based on a manual hint or predetermined thresholds. If there's a mismatch between the assumed seasonality and the actual seasonality of the data (for example, if the time series has different seasonality or no seasonality at all), naive forecasting might lead to suboptimal results.
- Zero values are considered when determining whether to use naive forecasting. For planning objects with data that extends far into the past (compared with the rest of the time series), naive forecasting isn't used. To find out how naive forecasting works on this type of data, consider changing the forecast start date to be closer to where data is present. Be careful, because this approach also impacts the accuracy of other models as it limits their training data.
