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
- **Fill missing values** – Choose whether the system should fill in placeholder values for time buckets where no value is provided by the input. In most cases, you should enable this feature because it results in improved forecasts.
- **Fill missing values strategy** – Select the strategy the system should use to choose values to enter into any empty time buckets. In the current version, the only available strategy is *Zeros*, which means all missing values are set to zero.

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
- **Fill missing values** – Choose whether the system should fill in placeholder values for time buckets where no value is provided by the input. In most cases, you should enable this feature because it results in improved forecasts. In the current version, all missing values are set to zero.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

### Handle outliers steps

*Handle outliers* steps identify and compensate for outlier data points in the input. These data points are considered anomalies that should be ignored or smoothed out to prevent them from throwing off the forecast calculation.

*Handle outliers* steps have the following settings:

- **Step name** – The specific name of the step. This name is also shown in the flowchart.
- **Description** – A short description of the step.
- **Created by** – The user who created the step.
- **Handle outliers** – Select one of the following options:

    - *Interquartile range (IQR)*: The IQR is the range between the first quartile (Q1) and the third quartile (Q3):

      #### Formula: **IQR=Q3−Q1**

      - Q1 (25th percentile): The value below which 25% of the data lies.
      - Q3 (75th percentile): The value below which 75% of the data lies.
      - The IQR measures the spread of the middle 50% of the data.
      - Any data outside of the Interquartile range will be be identified as outlier which will be smoothed later on.

    - *Seasonal and trend decomposition using Loess (STL)*
      
      #### Algorithm
      1. STL decomposes the time series into 3 components:
            1. **Trend**.
            1. **Seasonality**.
            1. **Residuals**: A residual is basically the raw time series after removing trend and seasonality from it.

        :::image type="content" source="media/stl-decomposition.png" alt-text="Diagram that shows 4 plots, an original time series, an upwards trend decomposed from the time series, a plot with spikes representing the seasonality of the time series and the residuals after removing trend and seasonality.":::
      
      2. STL tries to smooth the outliers using LOESS (Locally Estimated Scatterplot Smoothing).
      
      3. LOESS is a generalization of the moving average and polynomial regression, where it tries to fit a graph through scattered data points dots thus smooths the residuals during this process.

      :::image type="content" source="media/stl-fitting-plot.png" alt-text="Diagram that shows scattered plot of residuals and a graph that smoothes the residuals by attempting to fit it in the dots.":::
      
      4. After calculating mean and standard deviation, it uses them to get rid of the outliers and mitigate anomalies.
      
      5. Lastly, STL adds again the seasonality and the trend to the newly smoothed residual and you can proceed to the next step.
      
      

- **Interquartile range multiplier** – This field is available only when the **Handle outliers** field is set to *IQR*.
   - Multiplier of the IQR is determined by the user.​
     - Lower bound = Q1 - Multiplier  X IQR​
     - Upper bound = Q3 + Multiplier X IQR
   
   - A high multiplier increases the range within which data points are considered non-outliers.
   This results in having a more lenient definition of your boundaries and include more points
   Thus, the IQR method will be less sensitive to variations in the time series.
   - A low multiplier decreases the range within which data points are considered non-outliers
   That means you get stricter boundaries, and more data points are will get removed.
   
- **Correction methods** – This field is available only when the **Handle outliers** field is set to *IQR*. The 2 available options are Median/Mean, this will replace the outliers with the median/mean of the data.
- **Seasonality hint** – This field is available only when the **Handle outliers** field is set to *STL*. It influences the size of the window used for the LOESS smoother when estimating the seasonal component.
  - STL uses LOESS to smooth the seasonal component over time. The seasonal period helps divide the data into segments, ensuring the algorithm correctly extracts repeating patterns.
  For accurate decomposition:
  - A well-defined seasonal period captures the true periodicity of the data and  STL will successfully isolate the seasonality, making the trend and residuals more interpretable
  - An incorrect period results in poor seasonal extraction, leading to inaccurate trend and residual components.
    - Too short: May miss the full seasonal cycle, causing overlapping or incomplete patterns.
    - Too long: Adds unnecessary complexity, potentially treating random noise as seasonality.
### When to use what?
| Scenario                             | IQR             | STL             |
|--------------------------------------|-----------------|-----------------|
| Data with Seasonal or Trend Patterns | Not Recommended | Recommended     |
| Robust Handling of Outliers          | Recommended     | Not Recommended |
| Sensitivity to Extreme Values        | Recommended     | Recommended     |
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

- **Seasonality hint (in periods of time buckets)** – 
Seasonality refers to regular and predictable patterns in a time series that occur at fixed intervals due to recurring events or influences. These patterns are often driven by factors such as weather, holidays, or economic cycles.

- **Example**: 
  - Increased retail sales every December due to holiday shopping.
  - Higher electricity demand during summer months due to air conditioning.

### **How is Seasonality Different from Cycles?**
While both seasonality and cycles involve repeating patterns, there are key differences:

| **Aspect**            | **Seasonality**                                              | **Cycles**                                                     |
|------------------------|------------------------------------------------------------|----------------------------------------------------------------|
| **Frequency**          | Fixed, regular intervals (e.g., daily, weekly, yearly).     | Variable, often irregular and influenced by external factors. |
| **Duration**           | Short-term and predictable (e.g., seasonal sales).         | Long-term and unpredictable (e.g., business cycles).          |
| **Cause**              | Calendar-based events or natural patterns.                 | Economic, social, or structural forces.                       |
| **Examples**           | Summer travel peaks, holiday shopping trends.              | Economic recession cycles, stock market booms and busts.      |

Specifying the seasonal period hint aids the forecasting algorithm/stl outlier to capture the periodicy in order to capture the patterns and take into account seasonality when forecasting the data or removing outlier.

### **Dangers of Incorrectly Specifying Seasonality**
Specifying the seasonality incorrectly (too long or too short) can significantly affect the analysis or forecasting results.

#### **1. Too Short Seasonality**
When the seasonal period is shorter than the actual cycle:
- **Missed patterns**: Important parts of the seasonal pattern are excluded, leading to incomplete seasonality extraction.
- **Trend contamination**: Some seasonal variations may be mistaken for the trend component, distorting the trend estimation.
- **Residual issues**: Residuals may show unexplained periodicity, indicating the model failed to capture seasonality properly.

**Example**: 
- Using a seasonal period of **6 months** for yearly retail sales data results in only part of the yearly cycle being captured, missing critical holiday season peaks.

#### **2. Too Long Seasonality**
When the seasonal period is longer than the actual cycle:
- **Overfitting**: Noise or random fluctuations may be falsely interpreted as seasonality.
- **Distorted decomposition**: Artificially long seasonal cycles can obscure the true trend or residual components.
- **Increased complexity**: The model may become unnecessarily complex, making it harder to interpret and validate.

**Example**: 
- Using a seasonal period of **24 months** for data with an annual cycle results in overfitting, where small irregularities in the data are treated as seasonal patterns.


#### Autodetect seasonality patterns (preview)

[!INCLUDE [preview-banner-section](~/../shared-content/shared/preview-includes/preview-banner-section.md)]
<!-- KFM: Preview until further notice -->

If you're using the ARIMA algorithm, then the **Seasonality hint (in periods of time buckets)** is replaced by the **Select seasonality detection setting (preview)** setting, which provides the following options:

- **Auto detection** – Select this option to enable an algorithm that automatically detects seasonality patterns for each combination of location and product and applies the result to its forecast calculations. Seasonality patterns typically vary for different products and different locations, so auto detection often works better than using forecast models that try to apply the same pattern everywhere.
- **Detection using hint** – Select this option to use the value that you enter in the **Seasonality hint (in periods of time buckets)** field to help identify seasonality patterns. This option works best when you know the seasonality pattern in advance. For example, if you see a weekly seasonality pattern and are using buckets in days, then enter *7* here. If your data has no seasonality, then enter *1* here. <!-- KFM: Check with Mostafa. -->

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

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
- **Seasonality hint (in periods of time buckets)** – Seasonality refers to a pattern of demand that fluctuates according to a regular, recurring schedule (such as a weekly pattern where most customers shop on Saturdays). If your data has such a pattern, then enter the frequency here (in time buckets). For example, if you see a weekly seasonality pattern and are using buckets in days, then enter *7* here. If your data has no seasonality, then enter *1* here. <!-- KFM: Check with Mostafa. -->

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
