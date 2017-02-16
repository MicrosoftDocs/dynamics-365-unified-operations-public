---
# required metadata

title: Demand forecasting overview
description: Demand forecasting is used to predict independent demand from sales orders and dependent demand at any decoupling point for customer orders. The enhanced demand forecast reduction rules provide an ideal solution for mass customization.
author: YuyuScheller
manager: AnnBe
ms.date: 2016-03-29 13 - 45 - 42
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: ReqDemPlanCreateForecastDialog
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 2094
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 72004
ms.assetid: 1621e012-b63e-4676-a8c3-6f4b7f7719f4
ms.search.region: global
ms.search.industry: Manufacturing
ms.author: roxanad
ms.dyn365.ops.intro: Feb-16
ms.dyn365.ops.version: AX 7.0.0

---

# Demand forecasting overview

Demand forecasting is used to predict independent demand from sales orders and dependent demand at any decoupling point for customer orders. The enhanced demand forecast reduction rules provide an ideal solution for mass customization.

To generate the baseline forecast, a summary of historical transactions is passed to a Microsoft Azure Machine Learning service that is hosted on Azure. Because this service isn't shared among users, it can easily be customized to meet industry-specific requirements. You can use Dynamics 365 for Operations to visualize the forecast, adjust the forecast, and view key performance indicators (KPIs) about forecast accuracy.

## Key features of demand forecasting
Here are some of the main features of demand forecasting:

-   Generate a statistical baseline forecast that is based on historical data.
-   Use a dynamic set of forecast dimensions.
-   Visualize demand trends, confidence intervals, and adjustments of the forecast.
-   Authorize the adjusted forecast to be used in planning processes.
-   Remove outliers.
-   Create measurements of forecast accuracy.

## Major themes in demand forecasting
Three major themes are implemented in demand forecasting:

-   **Modularity** – Demand forecasting is modular and easy to configure. You can turn the functionality on and off by changing the configuration key at **Trade** &gt; **Inventory forecast** &gt; **Demand forecasting**.
-   **Reuse of the Microsoft stack** – Microsoft launched the Machine Learning platform in February 2015. Machine Learning, which is now part of the Microsoft Cortana Analytics Suite, lets you quickly and easily create predictive analysis experiments, such as demand estimation experiments, by using algorithms R or Python programming languages and a simple drag-and-drop interface.
    -   You can download the Dynamics 365 for Operations Demand forecasting experiments, change them to meet your business requirements, publish them as a web service on Azure, and use them to generate demand forecasts. The experiments are available for download if you've purchased a Dynamics 365 for Operations subscription for a production planner as enterprise level user.
    -   You can download any of the currently available demand prediction experiments from the [Cortana Analytics Gallery](https://gallery.cortanaanalytics.com/). Whereas the Dynamics 365 for Operations Demand forecasting experiments are automatically integrated with Dynamics 365 for Operations, customers and partners must handle the integration of experiments that they download from the [Cortana Analytics Gallery](https://gallery.cortanaanalytics.com/). Therefore, experiments from the [Cortana Analytics Gallery](https://gallery.cortanaanalytics.com/) aren't as straightforward to use as the Dynamics 365 for Operations Demand forecasting experiments. You must modify the code of the experiments so that they use the Dynamics 365 for Operations application programming interface (API).
    -   You can create your own experiments in Microsoft Azure Machine Learning Studio, publish them as services on Azure, and use them to generate demand forecasts.
    -   If you don’t require high performance, or if you don't require that a large amount of data be processed, you can use the Machine Learning free tier. We recommend that you always start from this tier, especially during implementation and testing phases. If you require higher performance and additional storage, you can use the Machine Learning standard tier. This tier requires an Azure subscription and involves additional costs. For details about Machine Learning pricing, see <http://aka.ms/machine-learning-price-info>.
-   **Forecast reduction at any decoupling point** – Demand forecasting in Dynamics 365 for Operations builds on this functionality, which lets you forecast both dependent and independent demand at any decoupling point.

## Basic flow in demand forecasting
The following diagram shows the basic flow in demand forecasting. [![demand forecasting introduction diagram](./media/demand-forecasting-introduction.png)](./media/demand-forecasting-introduction.png)Demand forecast generation starts in Dynamics 365 for Operations. Historical transactional data from the Dynamics 365 for Operations transactional database is gathered and populates a staging table. This staging table is later fed to a Machine Learning service. By performing minimal customization, you can plug various data sources into the staging table. The data sources can include Microsoft Excel files, comma-separated value (CSV) files, and data from Microsoft Dynamics AX 2009 and Microsoft Dynamics AX 2012. Therefore, you can generate demand forecasts that consider historical data that is spread among multiple systems. However, the master data, such as item names and units of measure, must be the same across the various data sources. If you use the Dynamics 365 for Operations Demand forecasting Machine Learning experiments, they look for a best fit among five time series forecasting methods to calculate a baseline forecast. The parameters for these forecasting methods are managed in Dynamics 365 for Operations. The forecasts, historical data, and any changes that were made to the demand forecasts in previous iterations are then available in Dynamics 365 for Operations. You can use Dynamics 365 for Operations to visualize and modify the baseline forecasts. Manual adjustments must be authorized before the forecasts can be used for planning.

## Limitations
Demand forecasting in Dynamics 365 for Operations is a tool that helps customers in the manufacturing industry create forecasting processes. It offers the core functionality of a demand forecasting solution and is designed so that it can easily be extended. Demand forecasting might not be the best fit for customers in industries such as retail, wholesale, warehousing, transportation, or other professional services.

See also
--------

[Demand forecasting setup](demand-forecasting-setup.md)

[Generating a statistical baseline forecast](generate-statistical-baseline-forecast.md)

[Making manual adjustments to the baseline forecast](manual-adjustments-baseline-forecast.md)

[Authorizing the adjusted forecast](authorize-adjusted-forecast.md)

[Monitoring forecast accuracy](monitor-forecast-accuracy.md)

[Remove outliers from historical transaction data when calculating a demand forecast](remove-historical-outliers-calculating-demand-forecast.md)

