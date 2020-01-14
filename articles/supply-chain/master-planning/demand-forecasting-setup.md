---
# required metadata

title: Demand forecasting setup
description: This topic describes the setup tasks that you must perform to prepare for demand forecasting.  
author: roxanadiaconu
manager: AnnBe
ms.date: 01/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ReqDemPlanDefaultAlgorithmParameters, ReqDemPlanForecastParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 72653
ms.assetid: c5fa4b09-512d-4349-ac51-cc13da69a160
ms.search.region: global
ms.search.industry: Manufacturing
ms.author: roxanad
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Demand forecasting setup

[!include [banner](../includes/banner.md)]

This topic describes the setup tasks that you must perform to prepare for demand forecasting.  

The setup tasks include setting up the following data and parameters.

## Item allocation key
A demand forecast is calculated for an item and its dimensions only if the item is part of an item allocation key. This rule is enforced to group large numbers of items, so that demand forecasts can be created more quickly. The item allocation key percentage is ignored when demand forecasts are generated. Forecasts are created based on historical data only. 

An item and its dimensions must be part of only one item allocation key if the item allocation key is used during forecast creation. 

To add a stock keeping unit (SKU) to an item allocation key, go to **Master planning** &gt; **Setup** &gt; **Demand forecasting** &gt; **Item allocation keys**. Use the **Assign items** page to assign an item to an allocation key.

## Intercompany planning groups
Demand forecasting generates cross-company forecasts. In Dynamics 365 Supply Chain Management, companies that are planned together are grouped into one intercompany planning group. To specify, per company, which item allocation keys should be considered for demand forecasting, associate an item allocation key with the intercompany planning group member by going to **Master planning** &gt; **Setup** &gt; **Intercompany planning groups**. 

By default, if no item allocation keys are assigned to intercompany planning group members, a demand forecast is calculated for all items that are assigned to all item allocation keys from all companies. Additional filtering options for companies and item allocation keys are available on the **Generate statistical baseline forecast** page. 

Review the number of items that are forecasted. Unnecessary items might cause increased costs when you use Microsoft Azure Machine Learning.

## Demand forecasting parameters
To set up demand forecasting parameters, go to **Master planning** &gt; **Setup** &gt; **Demand forecasting parameters**. Because demand forecasting runs cross-company, the setup is global. In other words, the setup applies to all companies. 

Demand forecasting generates the forecast in quantities. Therefore, the unit of measure that the quantity should be expressed in must be specified in the **Demand forecast unit** field. The unit of measure must be unique, to help guarantee that the aggregation and percentage distribution make sense. For more information about aggregation and percentage distribution, see [Make manual adjustments to the baseline forecast](manual-adjustments-baseline-forecast.md). For every unit of measure that is used for SKUs that are included in demand forecasting, make sure that there is a conversion rule for the unit of measure and the general forecasting unit of measure. When forecast generation is run, the list of items that don't have a unit of measure conversion is logged, so that you can easily correct the setup. 

Demand forecasting can be used to forecast both dependent and independent demand. For example, if only the **Sales order** check box is selected, and if all the items that are considered for demand forecasting are items that are sold, the system calculates independent demand. However, critical subcomponents can be added to item allocation keys and included in demand forecasting. In this case, if the **Production line** check box is selected, a dependent forecast is calculated. 

There are two methods for creating a baseline forecast. You can use forecasting models on top of historical data, or you can just copy over the historical data to the forecast. The **Forecast generation strategy** field lets you select between these two methods. To use forecast models, select **Azure Machine Learning**. 

By clicking **Forecast dimensions** in the left pane of the **Demand forecasting parameters** page, you can also select the set of forecast dimensions to use when the demand forecast is generated. A forecast dimension indicates the level of detail that the forecast is defined for. Company, site, and item allocation key are mandatory forecast dimensions, but you can also generate forecasts at the warehouse, inventory status, customer group, customer account, country/region, state, and item plus all item dimension levels. 

At any point, you can add forecast dimensions to the list of dimensions that are used for demand forecasting. You can also remove forecast dimensions from the list. However, manual adjustments are lost if you add or remove a forecast dimension. 

Not all items behave in the same manner from a demand forecasting perspective. Similar items can be grouped in one item allocation key, and parameters such as transaction types and forecast method settings can be set per item allocation key. Click **Item allocation keys** in the left pane of the **Demand forecasting parameters** page. 

To generate the forecast, Supply Chain Management uses a Machine Learning web service. To connect to the service, you must provide the following information if you sign in to Microsoft Azure Machine Learning Studio (classic):

-   Web service application programming interface (API) key
-   Web service endpoint URL
-   Azure storage account name
-   Azure storage account key

> [!NOTE]
> The Azure storage account name and key are required only if you use a custom storage account. If you deploy the on-premises version, you must have a custom storage account on Azure, so that Machine Learning can access the historical data. 

To create demand predictions, you can deploy your own service by using Machine Learning Studio or the Supply Chain Management demand forecasting experiments. Instructions for deploying the demand forecasting experiments as a web service are available in Supply Chain Management. On the **Demand forecasting parameters** page, click the **Azure Machine Learning** tab.

## Settings for the demand forecasting machine learning service
To view the parameters that can be configured for the demand forecasting service, go to **Master Planning** &gt; **Setup** &gt; **Demand forecasting** &gt; **Forecasting algorithm parameters**. The **Forecasting algorithm parameters** page shows the default values for the parameters. You can overwrite these parameters on the **Demand forecasting parameters** page. Use the **General** tab to overwrite the parameters globally, or use the **Item allocation keys** tab to overwrite the parameters per item allocation key. Parameters that are overwritten for an item allocation key affect only the forecast of items that are associated with that item allocation key.

### Forecast algorithm parameters

On the **Allocation keys** tab you can set the **Forecast algorithm parameters** for each item allocation key. The following options are available.
- **Confidence level percentage**: A confidence interval consists of a range of values that act as good estimates for the demand forecast. A 95% confidence level percentage indicates there is a 5% risk that the future demand falls outside the confidence interval range.
- **Force seasonality**: Specifies whether to force the model to use a certain type of seasonality. Applies to ARIMA and ETS only. Options: AUTO(default), NONE, ADDITIVE, MULTIPLICATIVE.
- **Forecasting model**: Options: ARIMA, ETS, STL, ETS+ARIMA, ETS+STL, ALL. To select best fit model, use **ALL**.
- **Maximum forecasted value**: Specifies the maximum value to use for predictions. Format: +1E[n] or numeric constant.
- **Minimum forecasted value**: Specifies the minimum value to use for predictions. Format: -1E[n] or numeric constant.
- **Missing value substitution**: Specifies how gaps in historical data are filled. Options: numeric value, MEAN, PREVIOUS, INTERPOLATE LINEAR, INTERPOLATE POLYNOMIAL.
- **Missing value substitution scope**: Specifies whether the value substitution applies only to the data range of each individual granularity attribute, or to the entire dataset. Options: GRANULARITY_ATTRIBUTE(default), GLOBAL.
- **Seasonality hint**: For seasonal data, provide a hint to the forecasting model to improve forecast accuracy. Format: integer number, representing the number of buckets a demand pattern repeats itself. For example, enter "6" for data that repeats itself every 6 months.
- **Test set size percentage**: Percentage of historical data to be used as a test set for forecast accuracy calculation. 

Additional resources
--------

[Demand forecasting overview](introduction-demand-forecasting.md)

[Generate a statistical baseline forecast](generate-statistical-baseline-forecast.md)

[Make manual adjustments to the baseline forecast](manual-adjustments-baseline-forecast.md)



