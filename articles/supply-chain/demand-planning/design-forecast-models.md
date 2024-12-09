---
title: Design forecast models
description: Learn about forecast models, which let you arrange and configure steps to define the forecast that is made by a forecast profile.
author: AndersEvenGirke
ms.author: aevengir
ms.topic: how-to
ms.date: 11/29/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Design forecast models

[!include [banner](../includes/banner.md)]

*Forecast models* let you arrange and configure steps to define the forecast that's made by a forecast profile. Each model presents a flowchart that graphically represents the calculation that the model does.

For a presentation about how forecast models and outlier removal methods work in Demand planning, see the following video on YouTube (starting at 16:53): [Deep dive into Demand Planning for Supply Chain Management | Dynamics 365 TechTalk](https://www.youtube.com/watch?v=H27SRU1ua-8&t=1013s).

## Create and customize a forecast model

To create and customize a forecast model, you must first open an existing forecast profile. (Learn more in [Work with forecast profiles](forecast-profiles.md).) You can then fully customize the model that the selected profile uses by adding, removing, and arranging steps, and configuring settings for each of them.

Follow these steps to create and customize a forecast model.

1. On the navigation pane, select **Operations** \> **Forecast profiles**.
1. Select the forecast profile that you want to create or customize a forecast model for.
1. On the **Forecast model** tab, there will always be at least one step (of the *Input* type) at the top of the flow chart. The model is processed from top to bottom, and the last step must be a step of the *Save* type. Add, remove, and arrange steps as you require, and configure settings for each of them. For guidelines, see the illustration after this procedure.
1. When you've finished designing your forecast model, select the **Validate** button :::image type="icon" source="media/button-validate-model.png" border="false"::: in the upper-right corner. The system runs a few tests to validate that your model will work, and then provides feedback. Fix any issues that the validation test reports.
1. Continue to work until your model is ready. Then, on the Action Pane, select **Save**.
1. If you want to save your forecast model as a preset, so that it's available when you and other users create a new forecast profile, select the **Save as model template** button :::image type="icon" source="media/button-save-model-as-template.png" border="false"::: in the upper-right corner.

The following illustration shows the information and controls that are available for steps in a forecast model.

:::image type="content" source="media/forecast-flowchart-elements.svg" alt-text="Screenshot that shows forecast model elements." lightbox="media/forecast-flowchart-elements.svg":::

Legend:

1. **Step icon** – A symbol that represents the purpose of the step.
1. **Step type** – The type of step. This text usually describes the type of roles, calculations, or other actions that the step represents.
1. **Step name** – The name that's applied to the step. Sometimes, you can enter manually this text in the step's settings. However, it usually indicates the value of one of the settings that were configured for the step.
1. **Step actions** – Open a menu of actions that you can take on the step. Although some of these actions are specific to the step type, most are common to all steps. If any actions appear dimmed, they can't be used because of the step's current position or for some other contextual reason. Here are some common actions that are available:

    - **Settings** – Open a dialog box where you can configure settings for the step.
    - **Remove** – Remove the step.
    - **Move Up** and **Move Down** – Reposition the step in the flowchart.
    - **Set to 'Pass Through'** – Temporarily disable a currently enabled step without deleting it or its settings.
    - **Unset 'Pass Through'** – Reenable a currently disabled step.
    - **Connect with** – For steps that support multiple inputs, specify the second input. The first input is automatically set based on where you put the step.

1. **Add a step** – Add a new step at the selected location.

## Forecast step types

This section describes the purpose of each type of forecast step. It also explains how to use and configure each type.

### Input steps

*Input* steps represent a time series that provides input to the forecast model. All forecast models must start with an *Input* step.

*Input* steps have the following settings:

- **Step name** – The specific name of the step. It automatically matches the name of the **Time series**.
- **Description** – A short description of the step.
- **Created by** – The user who created the step.
- **Time series** – The time series added by the step. When you first set up an *Input* step, the **Configure step** dialog provides a button that lets you choose the time series to add. After you have added a time series, the dialog shows the name of the time series and provides an **Edit** button that lets you change the time series and a **Filter** button that lets you set up filtering criteria based on fixed dates, relative dates, and/or field values.
- **Time series version** – If the selected time series includes more than one version, then you can select a specific version here. By default, it uses the latest (current) version.
- **Fill missing values** – <!-- KFM: Description needed. -->
- **Fill missing values strategy** – <!-- KFM: Description needed. -->

### Signal steps (preview)

[!INCLUDE [preview-banner-section](~/../shared-content/shared/preview-includes/preview-banner-section.md)]
<!-- KFM: Preview until further notice -->

*Signal* steps represent additional time series that can be combined with primary time series provided by the *Input* step. For example, the primary input provided by the *Input* step might represent historical sales, while the input provided by the *Signal* step might inflation or weather data.

When you add a *Signal* step, the system automatically creates a parallel branch in your model and places the step at the top of that branch. The initial branch always has an *Input* step at the top of it. Each branch can include any number of steps, but you'll eventually need to combine them using a *Forecast with signals* step.

*Signal* steps have the following settings:

- **Step name** – The specific name of the step. It automatically matches the name of the **Time series**.
- **Description** – A short description of the step.
- **Created by** – The user who created the step.
- **Time series** – The time series added by the step. When you first set up a *Signal* step, the **Configure step** dialog provides a button that lets you choose the time series to add. After you have added a time series, the dialog shows the name of the time series and provides an **Edit** button that lets you change the time series and a **Filter** button that lets you set up filtering criteria based on fixed dates, relative dates, and/or field values.
- **Time series version** – If the selected time series includes more than one version, then you can select a specific version here. By default, it uses the latest (current) version.
- **Fill missing values** – <!-- KFM: Description needed. -->

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

### Handle outliers steps

*Handle outliers* steps identify and compensate for outlier data points in the input. These data points are considered anomalies that should be ignored or smoothed out to prevent them from throwing off the forecast calculation.

*Handle outliers* steps have the following settings:

- **Step name** – The specific name of the step. This name is also shown in the flowchart.
- **Description** – A short description of the step.
- **Created by** – The user who created the step.
- **Handle outliers** – Select one of the following options:

    - *Interquartile range (IQR)* – <!-- KFM: Improved description needed. -->
    - *Seasonal and trend decomposition using loess (STL)* – <!-- KFM: Improved description needed. -->

- **Interquartile range multiplier** – This field is available only when the **Handle outliers** field is set to *IQR*. <!-- KFM: Improved description needed. -->
- **Correction methods** – This field is available only when the **Handle outliers** field is set to *IQR*. <!-- KFM: Improved description needed. -->
- **Seasonality hint** – This field is available only when the **Handle outliers** field is set to *STL*. <!-- KFM: Improved description needed. -->

### Forecast steps

*Forecast* steps apply a selected forecast algorithm to the input time series to create a forecast time series.

*Forecast* steps have the following settings:

- **Step name** – The specific name of the step. This name is also shown in the flowchart.
- **Description** – A short description of the step.
- **Created by** – The user who created the step.
- **Model type** – Select the forecast algorithm to use. For more information about each of the available algorithms, see [Demand forecasting algorithms](forecast-algorithm-types.md). Select one of the following algorithms:

    - *Best fit model*
    - *ARIMA* – Autoregressive integrated moving average
    - *ETS* – Error, trend, seasonality
    - *Prophet* – Facebook Prophet

- **Seasonality hint (in periods of time buckets)** – <!-- KFM: Description needed. -->

### Forecast with signals (preview)

[!INCLUDE [preview-banner-section](~/../shared-content/shared/preview-includes/preview-banner-section.md)]
<!-- KFM: Preview until further notice -->

This step generates a forecast based on two input time series. It always uses the XGBoost demand forecasting algorithm.

You can use this type of step only if your forecast model has at least two parallel branches (one starting with an *Input* step and one starting with a *Signal* step). The first branch is the one where you create the step. To specify the second branch, open the *Forecast with signals* step's **Action** menu, select **Connect with**, and then choose the step to connect to. The flowchart is then updated so that it shows the two branches combining at the *Forecast with signals* step.

*Forecast with signals* steps have the following settings:

- **Step name** – The specific name of the step. This name is also shown in the flowchart.
- **Description** – A short description of the step.
- **Created by** – The user who created the step.
- **Model type** – Select the forecast algorithm to use. In the current version, only the *XGBoost* algorithm is available.
- **Seasonality hint (in periods of time buckets)** – <!-- KFM: Description needed. -->

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

### Finance and operations – Azure Machine Learning steps

If you're already using your own Azure Machine Learning algorithms for demand forecasting in Supply Chain Management (as described in [Demand forecasting overview](../master-planning/introduction-demand-forecasting.md)), you can continue to use them while you use Demand planning. Just put a *Finance and operations – Azure Machine Learning* step in your forecast model instead of a *Forecast* step.

For information about how to set up Demand planning to connect to and use your Azure Machine Learning algorithms, see [Use your own custom Azure Machine Learning algorithms in Demand planning](custom-azure-machine-learning-algorithms.md).

### Phase in/out steps

*Phase in/out* steps modify the values of a data column in a time series to simulate the gradual phasing in of a new element (such as a new product or warehouse) or phasing out of an old element. The phase in/out calculation lasts for a specific period and uses values that are drawn from the same time series (from either the same data column that is being adjusted or another data column that represents a similar element).

*Phase in/out* steps have the following settings:

- **Step name** – The specific name of the step. This name is also shown in the flowchart.
- **Description** – A short description of the step.
- **Created by** – The user who created the step.
- **Rule group** – The name of the rule group that defines the calculation that the step does.

When you set up your forecast model, the position of the *Phase in/out* step affects the calculation result. To apply the phase in/out calculation to the historical sales numbers, put the *Phase in/out* step before the *Forecast* step (as shown on the left side of the following illustration). To apply the phase in/out calculation to the forecasted result, put the *Phase in/out* step after the *Forecast* step (as shown on the right side of the following illustration).

:::image type="content" source="media/phase-tile-position.png" alt-text="Screenshots that show the Phase in/out step in different positions relative to the Forecast step." lightbox="media/phase-tile-position.png":::

For more information about phase in/out functionality, including details about how to set up your phase in/out rule groups, see [Use phase in/out functionality to simulate planned changes](phase-in-out.md).

### Save steps

*Save* steps save the result of the forecast model as a new or updated series. All forecast models must end with a single *Save* step.

The forecast time series will be saved according to the settings that you configure each time that you run a forecast job as described in [Work with forecast profiles](forecast-profiles.md).

### Custom steps

<!--KFM: Description needed -->