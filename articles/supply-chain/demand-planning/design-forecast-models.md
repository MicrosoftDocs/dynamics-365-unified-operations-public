---
title: Design forecast models
description: Forecast models let you arrange and configure various tiles to define the forecast made by a forecast profile. Each model presents a flowchart that is a graphical representation of the calculation it makes.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/19/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Designing forecast models

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

*Forecast models* let you arrange and configure various tiles to define the forecast made by a forecast profile. Each model presents a flowchart that is a graphical representation of the calculation it makes.

## <a name="forecasting-algorithms"></a>Demand forecasting algorithms

Demand planning includes three popular demand forecasting algorithms: *auto-ARIMA*, *ETS*, and*prophet*. Choosing the right demand forecasting algorithm depends on the specific characteristics of your historical data. auto-ARIMA shines when data follows stable patterns, ETS is a versatile choice for data with trends or seasonality, and Prophet excels with complex, real-world data. By understanding these algorithms and their strengths, you can make informed decisions to optimize your supply chain and meet customer demand.

This section describes how each of these algorithms works and their suitability for various types of historical demand data.

### Auto-ARIMA – The time traveler's delight

The auto-ARIMA algorithm is like a time traveler, taking you on a journey through past demand patterns to make informed predictions about the future. At its core, auto-ARIMA uses a technique called ARIMA (autoregressive integrated moving average), which combines three key components: autoregression, differencing, and moving averages.

Auto-ARIMA automatically identifies the best combination of these components to create a forecast model that fits your data like a glove. It works particularly well with time series data that exhibits a stable pattern over time, such as seasonal fluctuations or trends. If your historical demand follows a reasonably consistent path, auto-ARIMA might be your go-to forecasting method.

### ETS – The shape shifter

ETS (error, trend, seasonality) is a versatile demand forecasting algorithm that adapts to the shape of your data. Like a chameleon, it can change its approach based on the characteristics of your historical demand, making it suitable for a wide range of scenarios.

ETS decomposes the time series data into three essential components: error, trend, and seasonality. By understanding and modeling these components, ETS generates forecasts that capture the underlying patterns in your data. ETS works best with data that exhibits clear seasonal patterns, trends, or both, making it an excellent choice for businesses with seasonally affected products or services.

### Prophet – The visionary forecasting guru

Developed by Facebook's research team, Prophet is a modern and flexible forecasting algorithm that can handle the challenges of real-world data. It has a knack for dealing with missing values, outliers, and complex patterns, making it a visionary guru in the realm of demand forecasting.

Prophet works by decomposing the time series data into several components, such as trend, seasonality, and holidays, and fitting a model to each component. This approach allows Prophet to accurately capture the nuances in your data and produce reliable forecasts. Prophet is ideal for businesses with irregular demand patterns, frequent outliers, or those affected by special events like holidays or promotions.

### Best fit model

The best fit model uses machine learning to find out which of the other available algorithms best fits your data, for each product and dimensions combination. This way, different products could have different models used.

### Custom Azure machine learning algorithm

If you have a custom Azure machine learning algorithm that you'd like to use with your forecasting models, then you can use it in the Demand planning app.

## Create and customize a forecast model

To create and customize a forecast model, you must start by opening an existing forecast profile (see also [Work with forecast profiles](forecast-profiles.md)). From there, you'll be able to fully customize the model used by your selected profile by adding, removing, and arranging tiles and making configuration settings for each of them.

Follow these steps to create and customize a forecast model:

1. On the navigation pane, select **Forecasts \> Forecast profiles**.
1. Select the forecast profile that you want to create or customize a forecast model for and then open the **Forecast model** tab.
1. There will always be at least one tile (an **Input** tile) at the top of the flow chart. The model is processed from top to bottom, and the last tile must be a **Save** tile. Add, remove, and arrange tiles as needed, and make configuration settings for each of them. See the illustration after this procedure for guidelines.
1. When you're done designing your forecast model, select the :::image type="icon" source="media/button-validate-model.png" border="false"::: **Validate** button in the top-right corner. The system will run a few tests to make sure your model will work and will then provide feedback. Fix any issues reported by the validation test.
1. Continue working until your model is ready. Then, on the Action Pane, select **Save**.
1. If you'd like to save your forecast model as a preset, which will be available when you and other users create a new forecast profile, then select the :::image type="icon" source="media/button-save-model-as-template.png" border="false"::: **Save as model template** button in the top-right corner.

The following illustration highlights the information and controls available for tiles in a forecast model.

:::image type="content" source="media/forecast-flowchart-elements.svg" alt-text="Forecast model elements":::

Legend:

1. **Tile icon** – Illustrates the purpose of the tile.
2. **Tile type** – The type of tile that it is. This usually describes the type of roles, calculations, or other actions that the tile represents.
3. **Tile name** – A name applied to each specific tile. Sometimes, you can enter this manually in each tile's settings, but usually this indicates the value of one of they settings made for the tile.
4. **Tile actions** – Select this button to open a drop-down list of actions you can take on the tile. Some of these are specific to the tile type, but most are common to all tiles. Some entries might be grayed out because they can't be used due to the tile's current positioning or some other contextual reason. Common commands include:
    - **Settings** – Open a dialog that lets you set configuration settings for the tile.
    - **Remove** – Remove the tile.
    - **Move Up** and **Move Down** – Reposition the tile in the flowchart.
    - **Set to 'Pass Through'** – Temporarily disable a currently enabled tile without deleting it or its settings.
    - **Unset 'Pass Through'** – Reenable a currently disabled tile.
5. **Add a tile** – Select this button to add a new tile at the selected location.

## Forecast tile types

This section describes the purpose of each type of forecast tile and how to use and configure each of them.

### Input tiles

Input tiles represent the time series that provides input to the forecast model. This is the time series listed on the **Included** tab of the **Input Data** tab. You can't edit the name.

Input tiles have just one setting: **Fill missing values**.

### Handle outliers tiles

*Handle outliers* tiles identify and compensate for outlier data points in the input, which are considered anomalies that should be ignored or smoothed out to keep them from throwing off the forecast calculation.

Handle outlier tiles offer the following settings:

- **Handle outliers** – Choose one of the following options.
    - *Interquartile range (IQR)*
    - *Seasonal and trend decomposition using loess (STL)*

- **Interquartile range multiplier** – This setting is only provided when **Handle outliers** is set to *IQR*.

- **Correction methods** – This setting is only provided when **Handle outliers** is set to *IQR*.

- **Seasonality hint** – This setting is only provided when **Handle outliers** is set to *STL*.

### Forecast tiles

Forecast tiles apply a selected forecast algorithm to the input time series to create a forecast time series.

Input tiles have just one setting: **Model type**. Use it to choose which forecast algorithm to use. For more information about each of the available algorithms, see [Demand forecasting algorithms](#forecasting-algorithms). Select one of the following algorithms.

- *ARIMA* – Autoregressive integrated moving average
- *ETS* – Error, trend, seasonality
- *Prophet* – Facebook Prophet
- *Best fit model*

### Save tiles

Save tiles save the result of the forecast model as a new or updated series. All forecast models must end with a single save tile.

The forecast time series will be saved according to the settings you make each time you run a forecast job as described in [Work with forecast profiles](forecast-profiles.md).
