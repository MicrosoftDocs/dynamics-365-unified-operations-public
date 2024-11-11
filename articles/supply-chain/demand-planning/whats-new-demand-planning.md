---
title: What's new or changed in Demand planning
description: This article lists new features, fixes, improvements, and known issues for each released version of Demand planning in Microsoft Dynamics 365 Supply Chain Management.
author: aevengir
ms.author: aevengir
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: conceptual
ms.date: 09/25/2024
ms.custom: 
  - bap-template
---

# What's new or changed in Demand planning

This article lists new features, fixes, improvements, and known issues for each released version of Demand planning in Microsoft Dynamics 365 Supply Chain Management.

## Version 1.0.0.1700

### New feature introduced in version 1.0.01700

This version of Demand planning adds several new features, as described in the following subsections.

#### Select input for forecasts and calculations at the model level

In previous versions of Demand planning, the input time series used by forecast and calculation profiles was set at the *profile* level. This setting is now part of the *model* configuration, which improves usability while adding flexibility to your model designs (including the ability to add a signal input). As before, each forecast or calculation model starts with an *Input* action card, but now it includes a setting where you choose the time series to use as input for the model. You can also choose a time series version and add filters based on dates and/or dimensions (such as products and locations). As with all action cards, you access these settings by opening the **Actions** menu (ellipsis button) on the card.

#### Apply input filters in calculation profiles

You can now filter the input used in calculation profiles. Filters can be based on dates and/or dimensions (such as products and locations). It was already possible to apply filters in forecast profiles.

#### Analyze demand plans with Copilot

Copilot cursor prompts in Demand planning let you explore specific data points or data ranges in a forecast or time series. Each prompt presents a set of predefined questions that you can ask Copilot, which then returns insights into notable shifts, trends, anomalies, or deviations across multiple dimensions. Copilot replies using natural-language summaries and visuals, which make it easy for you to digest the information and use it to make informed decisions.

#### Forecast with signals (preview)

One way to improve the accuracy of a forecast is to include input signal data beyond just historical sales. This version of Demand planning adds a new *Signal* action card, which lets planners include any signal (such as inflation or weather data) as input to their forecast models. The current release supports up to one signal, though support for more signals might be added in a future release. The new *Forecast with signals* action card lets you combine the signal input and main input to create the forecast. In the current version, *Forecast with signals* always uses the XGBoost demand forecasting algorithm, but support for other algorithms might be added in a future release.

#### Autodetect seasonality patterns (preview)

Seasonality patterns typically vary for different products and different locations, so using forecast models that try to apply the same pattern everywhere can result in inaccurate forecasts. This version of Demand planning adds an algorithm that automatically detects seasonality patterns for each combination of location and product and applies the result to its forecast calculations to help improve forecast accuracy.

### New fixes and improvements in version 1.0.0.1700

This version of Demand planning introduces the following fixes and improvements:

- Increased stability.
- Improved forecast error messages.
- Improved the *best fit model* forecasting algorithm for datasets that contain low inventories of phased-out products.

## Version 1.0.0.1281

### New feature introduced in version 1.0.0.1281

This version adds support for *time fences*, which allow demand planning managers to establish policies that prevent planners from editing certain date ranges of a forecast. Time fences are both flexible and simple to maintain. Managers create time fence rules based on the dimensions available in each plan. For example, a single product could be set up with different time fences for each store or geographical location. Time fence rules can also apply based on each user's role. For example, a role-based time fence rule could allow managers to edit a forecast in a period that can't be edited by planners. Learn more in [Limit time series edits with time fences](time-fences.md).

### New fixes and improvements in version 1.0.0.1281

This version of Demand planning introduces the following fixes and improvements:

- Increased stability.
- Improved forecast error messages.

## Version 1.0.0.1232

### New features introduced in version 1.0.0.1232

Forecast calculation job-run records now provide an **Explainability** tab, which lists each combination of dimensions (such as item variant, warehouse location, and so on) the forecast was calculated for. For each combination, it shows the forecast algorithm that was used and the mean average percentage error (MAPE) for the calculation. A lower MAPE value indicates greater accuracy.  Learn more in [Work with forecast profiles](forecast-profiles.md).

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
