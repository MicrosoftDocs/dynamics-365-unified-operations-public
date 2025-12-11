---
title: What's new or changed in Demand planning
description: This article lists new features, fixes, improvements, and known issues for each released version of Demand planning in Microsoft Dynamics 365 Supply Chain Management.
author: AndersEvenGirke
ms.author: aevengir
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: whats-new
ms.date: 09/09/2025
ms.custom: 
  - bap-template
---

# What's new or changed in Demand planning

This article lists new features, fixes, improvements, and known issues for each released version of Demand planning in Microsoft Dynamics 365 Supply Chain Management.

## Version 1.1.0.4

### New feature introduced in version 1.1.0.4

This version of Demand planning enhances basic forecast calculations by adding two new features:

- The new *Best fit model - version 3 (preview)* forecast algorithm now includes the *Croston's method* forecasting model. Designed specifically for intermittent demand, which is demand data with many zero-demand periods with occasional non-zero demands. Learn more in [Croston's method forecasting (preview)](croston-method.md).
- Forecasting with signals with the *XGBoost* forecast model has been extended to allow up to five signals. Learn more in [Forecast with signals (preview)](forecasts-with-signals.md).

### New fixes and improvements in version 1.1.0.4

This version of Demand planning introduces the following fixes and improvements:

- Increased stability.
- Improved performance when exporting forecast to Supply Chain Management with data aggregation.
- Improved forecast calculation performance.

## Version 1.0.0.3424

### New feature introduced in version 1.0.0.3424

This version of Demand planning enhances basic forecast calculations by adding two new features:

- The new *Best fit model - version 2 (preview)* forecast algorithm now applies naive forecasting when an input time series contains a low number of data points. This approach helps improve statistics forecasting results when input data is limited, such as for newly added products. Learn more at [Naive forecasting](naive-forecast-algorithm.md).
- Time freeze can now preserve all manual forecast adjustments. This option ensures that all manually adjusted cell values remain at the adjusted value even after you recalculate an existing forecast. No freeze rules are required. Learn more at [Limit automatic time series updates with time freezes](time-freeze.md).

### New fixes and improvements in version 1.0.0.3424

This version of Demand planning introduces the following fixes and improvements:

- Increased stability.
- Improvements to Generative insights.
- Improved forecast calculation performance.

## Version 1.0.0.3336

### New feature introduced in version 1.0.0.3336

This version of Demand planning enhances the *Copilot grid cursor* feature so that it now shows the impact of the signal input separately from the baseline for a selected forecasted cell. Learn more in [Copilot grid cursor](copilot-grid-cursor.md).

### New fixes and improvements in version 1.0.0.3336

This version of Demand planning introduces the following fixes and improvements:

- Increased stability.
- Auto-detect seasonality is improved to account for certain data compositions.
- Forecast calculations now respect the decimal precision set in the forecast profile.
- Improved the performance of forecast calculations.

## Version 1.0.0.2999

## New feature introduced in version 1.0.0.2999

This version of Demand planning marks the public preview of *Generative insights*, which offers detailed insights calculated using AI models. The production ready preview supports two metrics: *seasonality* and *signal correlation*. The system clusters forecast data based on distinct patterns found for each metric. For each cluster, the system provides insights such as its relative size and confidence level. You can also choose the major contributor across various dimensions in the forecast. Learn more in [Generative insights for Demand planning (production ready preview)](generative-insights.md).

## New fixes and improvements in version 1.0.0.2999

This version of Demand planning introduces the following fixes and improvements:

- Increased stability.
- Improvements in demo data. Features like row level security, time fence, and time freeze now work seamlessly when using demo data.

## Version 1.0.0.2794

### New features introduced in version 1.0.0.2794

This version of Demand planning adds several new features, as described in the following subsections.

#### Copilot grid cursor

The *Copilot grid cursor* offers detailed insights into a selected cell's value, including its original value, manual adjustments, and full adjustment history. User comments are also shown, to help make the changes easier to understand. Learn more in [Copilot grid cursor](copilot-grid-cursor.md).

#### New operator in rules: Select all

To improve efficiency and make queries easier to formulate, Demand planning now provides a *select all* operator. The new operator is available in the following policies: *time fence*, *time freeze*, and *row level access*. Learn more in learn more in [Using the select all operator](time-fences.md#select-all).

#### Multiple rules for time freezes

Demand planning now lets you assign multiple time freeze rules to *Forecast* and *Forecast with signals* steps. Each rule can have a different time freeze horizon. In this way, updates to a continuous forecast calculation are prevented during the selected periods. Learn more in [Limit automatic time series updates with time freezes](time-freeze.md).

### New fixes and improvements in version 1.0.0.2794

This version of Demand planning introduces the following fixes and improvements:

- Increased stability
- New demo data with seasonal clusters

## Version 1.0.0.2502

### New features introduced in version 1.0.0.2502

This version of Demand planning adds several new features, as described in the following subsections.

#### Autodetection of seasonality patterns is now available for all forecast algorithms (preview)

Automatic detection of seasonality patterns was introduced in Demand planning version 1.0.01700, but it was previously available only for the ARIMA [forecast algorithm](forecast-algorithm-types.md). In this version, it's now available for all forecast algorithms.

#### Time freeze rules

*Time freeze rules* let demand planning managers establish policies that prevent forecast calculations from recalculating and overwriting manual adjustments in an existing forecast during a specified date range. Time freeze rules are based on the dimensions that are available in each forecast, and they are easy to maintain. Learn more in [Limit automatic time series updates with time freezes](time-freeze.md).

#### Generative insights into seasonality patterns (production ready preview)

Generative insights provide AI-generated insights into your data. The initial preview of the feature provides generative insights into your seasonality patterns. Visual displays make it easy for planners to understand seasonality data and make business decisions based on it. Information is clustered (grouped) according to the detected seasonality patterns. For each cluster, generative insights provide a confidence score and describe the seasonality pattern in natural language. The system also indicates the proportion of planning items that follow the pattern. Learn more in [Generative insights for Demand planning (production ready preview)](generative-insights.md).

#### Simplified security role dependencies

The *Basic user* security role no longer has to be applied to all users of Demand planning. Instead, Demand planning now incorporates all privileges from the *App Opener* security role into the *Demand planning contributor* and *Demand planning manager* security roles. Learn more in [Security roles and row-level security in Demand planning](users-access.md).

### New fixes and improvements in version 1.0.0.2502

This version of Demand planning introduces the following fixes and improvements:

- Increased stability.
- New demo data that includes seasonal clusters.

## Version 1.0.0.1700

### New features introduced in version 1.0.01700

This version of Demand planning adds several new features, as described in the following subsections.

#### Select input for forecasts and calculations at the model level

In previous versions of Demand planning, the input time series used by forecast and calculation profiles was set at the *profile* level. This setting is now part of the *model* configuration, which improves usability while adding flexibility to your model designs (including the ability to add a signal input). As before, each forecast or calculation model starts with an *Input* step, but now it includes a setting where you choose the time series to use as input for the model. You can also choose a time series version and add filters based on dates and/or dimensions (such as products and locations). As with all steps, you access these settings by opening the **Actions** menu (ellipsis button) on the card. Learn more in [Design calculation models](design-calculation-models.md) and [Design forecast models](design-forecast-models.md).

#### Apply input filters in calculation models

You can now filter the input used in calculation models. Filters can be based on dates and/or dimensions (such as products and locations). It was already possible to apply filters in forecast models. Learn more in [Design calculation models](design-calculation-models.md).

#### Analyze demand plans with Copilot

Copilot cursor prompts in Demand planning let you explore specific data points or data ranges in a forecast or time series. Each prompt presents a set of predefined questions that you can ask Copilot, which then returns insights into notable shifts, trends, anomalies, or deviations across multiple dimensions. Copilot replies using natural-language summaries and visuals, which make it easy for you to digest the information and use it to make informed decisions. Learn more in [Analyze demand plans with Copilot](demand-planning-copilot.md).

#### Forecast with signals (preview)

One way to improve the accuracy of a forecast is to include input signal data beyond just historical sales. This version of Demand planning adds a new *Signal* step, which lets planners include any signal (such as inflation or weather data) as input to their forecast models. The current release supports up to one signal, though support for more signals might be added in a future release. The new *Forecast with signals* step lets you combine the signal input and main input to create the forecast. In the current version, *Forecast with signals* always uses the XGBoost demand forecasting algorithm, but support for other algorithms might be added in a future release. Learn more in [Forecast with signals](forecasts-with-signals.md).

#### Autodetect seasonality patterns (preview)

Seasonality patterns typically vary for different products and different locations, so using forecast models that try to apply the same pattern everywhere can result in inaccurate forecasts. This version of Demand planning adds an algorithm that automatically detects seasonality patterns for each combination of location and product and applies the result to its forecast calculations to help improve forecast accuracy. Automatic seasonality detection is only available when you use the ARIMA [forecast algorithm](forecast-algorithm-types.md). Learn more in [Design forecast models](design-forecast-models.md#forecast-steps).

### New fixes and improvements in version 1.0.0.1700

This version of Demand planning introduces the following fixes and improvements:

- Increased stability.
- Improved forecast error messages.
- Improved the *best fit model* forecasting algorithm for datasets that contain low inventories of phased-out products.

## Version 1.0.0.1281

### New feature introduced in version 1.0.0.1281

This version adds support for *time fences*, which allow demand planning managers to establish policies that prevent planners from editing certain date ranges of a forecast. Time fences are both flexible and simple to maintain. Managers create time fence rules based on the dimensions available in each plan. For example, a single product could be set up with different time fences for each store or geographical location. Time fence rules can also apply based on each user's role. For example, a role-based time fence rule could allow managers to edit a forecast in a period that can't be edited by planners. Learn more in [Limit manual time series edits with time fences](time-fences.md).

### New fixes and improvements in version 1.0.0.1281

This version of Demand planning introduces the following fixes and improvements:

- Increased stability.
- Improved forecast error messages.

## Version 1.0.0.1232

### New features introduced in version 1.0.0.1232

Forecast calculation job-run records now provide an **Explainability** tab, which lists each combination of dimensions (such as item variant, warehouse location, and so on) the forecast was calculated for. For each combination, it shows the forecast algorithm that was used and the mean average percentage error (MAPE) for the calculation. A lower MAPE value indicates greater accuracy. Learn more in [Work with forecast profiles](forecast-profiles.md).

### New fixes and improvements in version 1.0.0.1232

This version of Demand planning introduces the following fixes and improvements:

- Increased stability.
- Transformation jobs that include the **Country/Region** column are now processed correctly. Previously, these jobs failed with an error.
- Improved the **Microsoft finance and operations apps** export data provider.
- Improved error messages shown during transformation, calculation, forecast, export, and import operations.
- Improved translation coverage in supported languages.

## Version 1.0.0.1182

### New features introduced in version 1.0.0.1182

The Microsoft Dynamics 365 Finance and Operations data provider now lets you choose which legal entities to import from. This applies to all data entities that contain a data area ID, including custom-built data entities. Learn more in [Import data into Demand planning](import-data.md).

### New fixes and improvements in version 1.0.0.1182

This version of Demand planning introduces the following fixes and improvements:

- Increased stability.
- Improved the ARIMA forecast model. The model now provides better error messages if it fails due to a data error.
- Improved the best fit forecast model. Calculations now succeed provided at least one of the models provides a result.
- Each organization instance can now run up to five forecasts in parallel. Newly created forecasts will only run in parallel provided all existing forecast jobs have already started (in the *Executing* state). If one or more existing forecast jobs are still waiting to start (in the *Created* state) when a new forecast is created, then all forecasts will be executed sequentially.

## Version 1.0.0.1132

### New features introduced in version 1.0.0.1132

This version of Demand planning focuses on quality and stability improvements and has no new features.

### New fixes and improvements in version 1.0.0.1132

This version of Demand planning introduces the following fixes and improvements:

- Increased stability.
- Fixed an issue with data transformations that caused zero values to appear in output.
- Improved the *best fit* forecast model.

## Version 1.0.0.1067

Version 1.0.0.1067 is the first general availability (GA) release of Demand planning in Microsoft Dynamics 365 Supply Chain Management.
