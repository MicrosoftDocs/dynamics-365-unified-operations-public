# Designing forecast models

*Forecast models* let you arrange and configure various tiles to define the forecast made by a forecast profile. Each model presents a flowchart that is a graphical representation of the calculation it makes.

## Create and customize a forecast model

To create and customize a forecast model, you must start by opening an existing forecast profile (see also [View and run existing forecast profiles](view-and-run-existing-forecast-profiles.md)). From there, you'll be able to fully customize the model used by your selected profile by adding, removing, and arranging tiles and making configuration settings for each of them.

Follow these steps to create and customize a forecast model:

1.  On the navigation pane, select **Forecasts &gt; Forecast profiles**.

2.  Select the forecast profile that you want to create or customize a forecast model for and then open the **Forecast model** tab.

3.  There will always be at least one tile (an **Input** tile) at the top of the flow chart. The model is processed from top to bottom, and the last tile must be a **Save** tile. Add, remove, and arrange tiles as needed, and make configuration settings for each of them. See the illustration after this procedure for guidelines.

4.  When you're done designing your forecast model, select the ![](media/image6.png) **Validate** button in the top-right corner. The system will run a few tests to make sure your model will work and will then provide feedback. Fix any issues reported by the validation test.

5.  Continue working until your model is ready. Then, on the Action Pane, select **Save**.

6.  If you'd like to save your forecast model as a preset, which will be available when you and other users create a new forecast profile, then select the ![](media/image7.png) **Save as model template** button in the top-right corner.

The following illustration highlights the information and controls available for tiles in a forecast model.

![A screenshot of a computer Description automatically generated](media/image9.png)

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

    -   *Interquartile range (IQR)* –

    -   *Seasonal and trend decomposition using loess (STL)* –

- **Interquartile range multiplier** – This setting is only provided when **Handle outliers** is set to *IQR*.

- **Correction methods** – This setting is only provided when **Handle outliers** is set to *IQR*.

- **Seasonality hint** – This setting is only provided when **Handle outliers** is set to *STL*.

### Forecast tiles

Forecast tiles apply a selected forecast algorithm to the input time series to create a forecast time series.

Input tiles have just one setting: **Model type**. Use it to choose which forecast algorithm to use. For more information about each of the available algorithms, see [Demand forecasting algorithms in Demand planning](demand-forecasting-algorithms-in-demand-planning.md). Select one of the following algorithms.

-   *ARIMA* – Autoregressive integrated moving average

-   *ETS* – Error, trend, seasonality

-   *Prophet* – Facebook Prophet

-   *Best fit model* –

### Save tiles

Save tiles save the result of the forecast model as a new or updated series. All forecast models must end with a single save tile.

The forecast time series will be saved according to the settings you make each time you run a forecast job as described in [View and run existing forecast profiles](view-and-run-existing-forecast-profiles.md).

