---
title: What's new or changed in Demand planning
description: This article lists new features, fixes, improvements, and known issues for each released version of Demand planning in Microsoft Dynamics 365 Supply Chain Management.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: conceptual
ms.date: 08/21/2024
ms.custom: 
  - bap-template
---

# What's new or changed in Demand planning

This article lists new features, fixes, improvements, and known issues for each released version of Demand planning in Microsoft Dynamics 365 Supply Chain Management.

## Version 1.0.0.1225

### New features introduced in version 1.0.0.1225

Forecast calculation job-run records now provide an **Explainability** tab, which lists each combination of dimensions (such as item variant, warehouse location, and so on) the forecast was calculated for. For each combination, it shows the forecast algorithm that was used and the mean average percentage error (MAPE) for the calculation. A lower MAPE value indicates greater accuracy.  Learn more in [Work with forecast profiles](forecast-profiles.md).

### New fixes and improvements in version 1.0.0.1225

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
