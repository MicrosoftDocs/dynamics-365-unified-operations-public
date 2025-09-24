---
title: Demand planning home page
description: Learn about Demand planning in Microsoft Dynamics 365 Supply Chain Management, Microsoft's next-generation collaborative demand planning solution.
author: AndersEvenGirke
ms.author: aevengir
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 01/30/2025
ms.custom: 
  - bap-template
---

# Demand planning home page

[!include [banner](../includes/banner.md)]

Inaccurate forecasts and demand plans can lead to lost revenue and inefficiency in the supply chain. However, forecasts that are infused with intelligence lead to more accurate and effective demand plans. Direct impact can be measured in improved revenue and fewer stockouts. Operating expenses are reduced in supply chains that require fewer fire drills.

*Demand planning in Microsoft Dynamics 365 Supply Chain Management* is Microsoft's next-generation collaborative demand planning solution. This app is powered by best-in-class forecasting algorithms and models, and offers immersive user experiences, intelligent reports, and analytics. It empowers organizations to build an agile, resilient, and sustainable demand planning practice that's fueled by intelligence and collaboration.

Demand planning provides the following capabilities:

- **A no-code approach** to demand modeling and planning configuration. Flexible building blocks enable the vast majority (over 85 percent) of demand planners who aren't data scientists to do what-if planning and analyze, optimize, and compare scenarios in minutes.
- **Seamless, on-the-fly aggregation and disaggregation**. Therefore, planners can edit forecasts at the corporate or product group level, and then zoom in and instantly see the impact at the regional and stock-keeping unit (SKU) levels.
- **Improved forecast accuracy** with automatic AI parameter tuning to help ensure accurate forecasting and preprocessing. External signals enable superior forecast accuracy by considering promotions or stockouts.
- **Disruption readiness** with interactive and fast what-if analysis. Version history enables tracking, evaluating forecast changes, and using the lessons learned to improve the decision making process.
- **Effective collaboration throughout the planning cycle**. This capability is enabled through Microsoft Teams in-context communication, in-product commenting, and restorable versions of forecast values throughout the planning process.
- **Increased agility through integrated planning and execution flow** with native integration with Supply Chain Management, customizable worksheets, and exception-based planning.

## The demand planning process

Demand planning provides functionality for the complete demand planning process. This process has the following steps:

1. **[Import data](import-data.md)** – Import your historical data, products, sites, warehouses, prices, and so on, into the app.

    > [!VIDEO https://learn-video.azurefd.net/vod/player?id=62832cd0-1bd9-456b-9dd1-3dc33a101b0b]

1. **[Create transformation](transform-data.md)** – Transform imported data from tables into time series by identifying data columns, choosing time buckets, and shifting dates. For example, you can shift historical data from last year to next year so that you can use it as a basis for the forecast. Alternatively, you can apply multiplications or combine data from different systems.
1. **[Create forecasts](forecast-profiles.md)** – Use different forecasting models (including your own Azure Machine Learning model) to create a forecast, or let AI determine which forecast model works best.

    > [!VIDEO https://learn-video.azurefd.net/vod/player?id=9d178a98-0a58-4765-9885-b73ee2ad17ef]

1. **[Review and adjust forecast](time-series.md)** – Work on the forecast, adjust values, and get different perspectives about how pricing, weather, promotional events, and other factors might affect the forecast. Collaborate to reach the most accurate forecast.

    > [!VIDEO https://learn-video.azurefd.net/vod/player?id=14bf0230-5088-49c6-9b14-685f322f2376]

1. **[Export data](export-data.md)** – After your forecast is done, you can export it to any external system that can consume forecasts.

:::image type="content" source="media/demand-planning-process.png" alt-text="Diagram that shows the steps in the demand planning process.":::

## Deep dive video

For a deep dive into the capabilities of Demand planning, watch the following video on YouTube: [Deep dive into Demand Planning for Supply Chain Management | Dynamics 365 TechTalk](https://www.youtube.com/watch?v=H27SRU1ua-8).

## Licensing

To use Demand planning in a production environment, each relevant user must have a license for it. Learn more in [Demand planning license requirements](demand-planning-licensing.md).
