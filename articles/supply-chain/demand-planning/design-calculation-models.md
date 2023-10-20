---
title: Design calculation models
description: Calculation models let you arrange and configure various tiles to define the calculation made by a calculation profile. Each model presents a flowchart that is a graphical representation of the calculation it makes.
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

# Design calculation models

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

*Calculation models* let you arrange and configure various tiles to define the calculation made by a calculation profile. Each model presents a flowchart that is a graphical representation of the calculation it makes.

## Create and customize a calculation model

To create and customize a calculation model, you must start by opening an existing calculation profile (see also [Calculation profiles](calculation-profiles.md)). From there, you'll be able to fully customize the model used by your selected profile by adding, removing, and arranging tiles and making configuration settings for each of them.

Follow these steps to create and customize a calculation model:

1. On the navigation pane, select **Operations \> Calculations**.

1. Select the calculation profile that you want to create or customize a calculation model for and then open the **Calculation Model** tab.

1. There will always be at least one tile (an **Input** tile) at the top of the flow chart. The model is processed from top to bottom, and the last tile must be a **Save** tile. Add, remove, and arrange tiles as needed, and make configuration settings for each of them. See the illustration after this procedure for guidelines.

1. When you're done designing your calculation model, select the **Validate** button :::image type="icon" source="media/button-validate-model.png" border="false"::: in the top-right corner. The system will run a few tests to make sure your model will work and will then provide feedback. Fix any issues reported by the validation test.

1. Continue working until your model is ready. Then, on the Action Pane, select **Save**.

1. If you'd like to save your calculation model as a preset, which will be available when you and other users create a new calculation profile, then select the **Save as model template** button :::image type="icon" source="media/button-save-model-as-template.png" border="false"::: in the top-right corner.

The following illustration highlights the information and controls available for tiles in a calculation model.

:::image type="content" source="media/calculation-flowchart-elements.svg" alt-text="Calculation model elements" lightbox="media/calculation-flowchart-elements.svg":::

Legend:

1. **Tile icon** – Symbolizes the role of the tile.
1. **Tile type** – The type of tile that it is. This text usually describes the type of calculation or other action that the tile represents.
1. **Tile name** – A name applied to the specific tile. Usually, you can enter this text manually in each tile's settings, but some types of tiles have a predefined value here.
1. **Tile actions** – Select this button to open a drop-down list of actions you can take on the tile. Some of these entries are specific to the tile type, but many are common to all tiles. Some entries might be grayed out because they can't be used due to the tile's current positioning or some other contextual reason. Common commands include:
    - **Settings** – Open a dialog that lets you set configuration settings for the tile.
    - **Remove** – Remove the tile.
    - **Move Up** and **Move Down** – Reposition the tile in the flowchart.
    - **Set to 'Pass Through'** – Temporarily disable a currently enabled tile without deleting it or its settings.
    - **Unset 'Pass Through'** – Reenable a currently disabled tile.
    - **Connect with** – For tiles that support multiple inputs, select this entry to specify the second input. The first input is set automatically according to where you choose to place the tile.
1. **Add a tile** – Select this button to add a new tile at the selected location. (If you insert a new *input* tile, then that tile will be placed at the top of a new flow rather than at the button location.)

## Calculation tile types

This section describes the purpose of each type of calculation tile and how to use and configure each of them.

### Input tiles

Each input tile represents a time series that provides input to the calculation model.

Each input tile you add is automatically assigned a name that includes an integer that matches an index ID of a time series listed on the **Included** tab of the **Input Data** tab (for example, *Time Series 1*, *Time Series 2*, and so on). You can't edit the name.

Input tiles have just one setting: **Fill missing values**.

### Arithmetic operator tiles

Arithmetic operator tiles perform a calculation that combines values from two input time series.

You might use this tile to calculate the expected margins of a forecast by subtracting the cost of goods sold (COGS) from expected revenue.

Arithmetic operator tiles implement the following calculation:

> f(x) = a(x) *&lt;operator&gt;* b(x)

Where *&lt;operator&gt;* is one of: +, -, \*, /

To use this tile, your calculation model must have at least two input time series in parallel columns. The first series is at the top of the column where you create the tile. The second series must start with an input tile and can have any number of tiles in it but must still be open (not end with a save tile). To identify the second series, open the tile's **Action** menu and select *Connect with*. The flowchart then updates to show the two columns combining at the arithmetic operator tile.

Arithmetic operator tiles offer the following settings:

- **Step name** – A specific name for the tile. This name is also shown in the flowchart.
- **Description** – A short description of the tile.
- **Crated by** – The user who created the tile.
- **Value 1** – The first series in the calculation (a(x)), which is on the left side of the operator. Choose *Input 1* or*Input 2*.
- **Operator** – The operator applied between **Value 1** and **Value 2**. Select add (+), subtract (-). multiply (\*) or divide (/).
- **Value 2** – The second series in the calculation (b(x)), which is on the right side of the operator. Choose *Input 1* or*Input 2*.

### Constant arithmetic operator tiles

Constant arithmetic operator tiles perform a calculation that applies a constant arithmetic operation to each value in an input time series.

Arithmetic operator tiles implement the following calculation:

> f(x) = a(x) *&lt;operator&gt;* C

Where:

- *&lt;operator&gt;* is one of: +, -, \*, /
- *C* is a constant value

Constant arithmetic operator tiles offer the following settings:

- **Step name** – A specific name for the tile. This name is also shown in the flowchart.
- **Description** – A short description of the tile.
- **Crated by** – The user who created the tile.
- **Value 1** – The first series in the calculation (a(x)), which is on the left side of the operator. Choose *Input 1* or*Input 2*.
- **Operator** – The operator applied. Select add (+), subtract (-). multiply (\*) or divide (/).
- **Constant** – The constant value applied to each time series value using the selected **Operator**.

### Date offset tiles

Date offset tiles shift the input time series by a fixed value along the X-axis.

You might use this tile to shift last year's demand one year forward so you can compare it to next year's forecast by overlaying the time-shifted demand graph over the forecast graph.

Date offset tiles implement the following calculation:

> f(x) = a(x &minus; t)

Where *t* is an integer of days, months, or years.

Date offset tiles offer the following settings:

- **Step name** – A specific name for the tile. The name is also shown in the flowchart.
- **Description** – A short description of the tile.
- **Crated by** – The user who created the tile.
- **Time value** – The amount of time forward to shift the input time series (using the specified **Time unit**).
- **Time unit** – The unit that applies to the **Time value**.

### Logical operator tiles

Logical operator tiles test whether a value exceeds a constant (threshold) at each point along a time series. It outputs a 1 for true and a 0 for false.

You might use this tile to evaluate when the forecast error is above a certain threshold in either direction, which could help you to focus on important products.

Logical operator tiles implement the following calculation:

> f(x) = ABS\[a(x)\] *&lt;operator&gt;* C

Where:

- &lt;operator&gt; is one of the following logical operators: &gt;, &gt;=, &lt;, &lt;=
- *C* is a constant
- ABS is optional and, if enabled, uses the absolute value (distance from zero) instead of the literal value.

Date offset tiles offer the following settings:

- **Step name** – A specific name for the tile. The name is also shown in the flowchart.
- **Description** – A short description of the tile.
- **Crated by** – The user who created the tile.
- **Apply ABS** – Set to *Yes* to use the absolute value (distance from zero) of the input series. Set to *No* to use the literal value (including +/- signs) of the input series.
- **Operator** – The logical operator applied when comparing against the **Constant** value.
- **Constant** – The constant value to be compared against the input time series.

### Merge tiles

Merge tiles merge two time series into a new time series by applying the selected merge logic. You can choose to merge the time series by min value, max value, average, or sum.

You might use this tile to calculate a merged result of two different forecast methods.

To use this tile, your calculation model must have at least two input time series in parallel columns. The first series is at the top of the column where you create the tile. The second series must start with an input tile and can have any number of tiles in it but must still be open (not end with a save tile). To identify the second series, open the tile's **Action** menu and select *Connect with*. The flowchart then updates to show the two columns combining at the merge tile.

Merge tiles provide a **Merge policy** setting, for which you can choose one of the following values:

- *Min value* – Takes the lowest of the two input values.
- *Max value* – Takes the largest of the two input values.
- *Average* – Calculates an average of the two input values.
- *Sum* – Adds the two input values together.

### Monetary value tiles

Monetary value tiles convert a forecast or historical demand time series based on sales units into a series of monetary values based on a selected price list. The calculation will first try to match the cost or price from a primary price list and then try a fallback price list if one is selected.

You might use this tile to convert a forecast (quantity) into expected revenue (monetary value).

Monetary value tiles implement the following calculation:​

> f(x) = a(x) &times; Price(product-ID)

Date offset tiles offer the following settings:

- **Step name** – A specific name for the tile. The name is also shown in the flowchart.
- **Description** – A short description of the tile.
- **Crated by** – The user who created the tile.
- **Primary price list** – Select the primary data table that contains your price list. The list includes all of the tables you have currently defined for use with Demand planning (see also [Set up tables](import-data.md)). The price list must include columns for product IDs and prices.
- **Fallback price list** – If the system can't find a matching price in the **Primary price list**, then it will check this price list (if selected).

### Ratio in percentage tiles

Ratio in percentage tiles calculate a ratio in percentage based on two input time series. You might use this to calculate the error percentage of a previous forecast based on a historical demand and forecast time series.

Ratio in percentage tiles implement the following calculation:​

> f(x) = &Sigma; {\[a(x) &minus; b(x)\] &divide; a(x)} &times; 100 %

To use this tile, your calculation model must have at least two input time series in parallel columns. The first series is at the top of the column where you create the tile. The second series must start with an input tile and can have any number of tiles in it but must still be open (not end with a save tile). To identify the second series, open the tile's **Action** menu and select *Connect with*. The flowchart then updates to show the two columns combining at the ratio in percentage tile.

Ratio in percentage tiles offer the following settings:

- **Step name** – A specific name for the tile. This name is also shown in the flowchart.
- **Description** – A short description of the tile.
- **Crated by** – The user who created the tile.
- **Value 1** – The first series in the calculation (a(x)). Choose *Input 1* or *Input 2*.
- **Value 2** – The second series in the calculation (b(x)). Choose *Input 1* or *Input 2*.

### Save tiles

Save tiles save the result of the calculation model as a new or updated series. All calculation models must end with a single save tile.

The calculated series will be saved according to the settings you make each time you run a calculation job as described in [Work with calculation profiles](calculation-profiles.md).
