---
title: Design calculation models
description: Learn about calculation models, which let you arrange and configure steps to define the calculation that is done by a calculation profile.
author: AndersEvenGirke
ms.author: aevengir
ms.topic: how-to
ms.date: 11/29/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Design calculation models

[!include [banner](../includes/banner.md)]

*Calculation models* let you arrange and configure steps to define the calculation that's done by a calculation profile. Each model presents a flowchart that graphically represents the calculation that the model does.

## Create and customize a calculation model

To create and customize a calculation model, you must first open an existing calculation profile. (Learn more in [Work with calculation profiles](calculation-profiles.md).) You can then fully customize the model that the selected profile uses by adding, removing, and arranging steps, and configuring settings for each of them.

Follow these steps to create and customize a calculation model.

1. On the navigation pane, select **Operations** \> **Calculations**.
1. Select the calculation profile that you want to create or customize a calculation model for.
1. On the **Calculation Model** tab, there will always be at least one step (of the *Input* type) at the top of the flow chart. The model is processed from top to bottom, and the last step must be a step of the *Save** type. Add, remove, and arrange steps as you require, and configure settings for each of them. For guidelines, see the illustration after this procedure.
1. When you've finished designing your calculation model, select the **Validate** button :::image type="icon" source="media/button-validate-model.png" border="false"::: in the upper-right corner. The system runs a few tests to validate that your model will work, and then provides feedback. Fix any issues that the validation test reports.
1. Continue to work until your model is ready. Then, on the Action Pane, select **Save**.
1. If you want to save your calculation model as a preset, so that it's available when you and other users create a new calculation profile, select the **Save as model template** button :::image type="icon" source="media/button-save-model-as-template.png" border="false"::: in the upper-right corner.

The following illustration highlights the information and controls that are available for steps in a calculation model.

:::image type="content" source="media/calculation-flowchart-elements.svg" alt-text="Screenshot that shows calculation model elements." lightbox="media/calculation-flowchart-elements.svg":::

Legend:

1. **Step icon** – A symbol that represents the role of the step.
1. **Step type** – The type of step. This text usually describes the type of calculation or other action that the step represents.
1. **Step name** – The name that's applied to the step. Usually, you can manually enter this text in each step's settings. However, some types of steps have a predefined value here.
1. **Step actions** – Open a menu of actions that you can take on the step. Although some of these actions are specific to the step type, many are common to all steps. If any actions appear dimmed, they can't be used because of the step's current position or for some other contextual reason. Here are some common actions that are available:

    - **Settings** – Open a dialog box where you can configure settings for the step.
    - **Remove** – Remove the step.
    - **Move Up** and **Move Down** – Reposition the step in the flowchart.
    - **Set to 'Pass Through'** – Temporarily disable a currently enabled step without deleting it or its settings.
    - **Unset 'Pass Through'** – Reenable a currently disabled step.
    - **Connect with** – For steps that support multiple inputs, specify the second input. The first input is automatically set based on where you put the step.

1. **Add a step** – Add a new step at the selected location. (If you insert a new *Input* step, that step will always be put at the top of a new flow, not at the button location.)

## Calculation step types

This section describes the purpose of each type of calculation step. It also explains how to use and configure each type.

### Input steps

Each *Input* step represents a time series that provides input to the calculation model.

*Input* steps have the following options that you can set:

- **Time series** – The time series added by the step. When you first set up an *Input* step, the **Configure step** dialog provides a button that lets you choose the time series to add. After you have added a time series, the dialog shows the name of the time series and provides an **Edit** button that lets you change the time series and a **Filter** button that lets you set up filtering criteria based on fixed dates, relative dates, and/or field values.
- **Time series version** – If the selected time series includes more than one version, then you can select a specific version here. By default, it uses the latest (current) version.

### Arithmetic operator steps

*Arithmetic operator* steps do a calculation that combines values from two input time series. You might use this type of step, for example, to calculate the expected margins of a forecast by subtracting the cost of goods sold (COGS) from the expected revenue.

*Arithmetic operator* steps implement the following calculation:

f(x) = a(x) &lt;*operator*&gt; b(x)

In this formula, &lt;*operator*&gt; is one of the following arithmetic operators: \+, \-, \*, or /.

You can use this type of step only if your calculation model has at least two input time series in parallel branches. The first series is at the top of the branch where you create the step. The second series must start with an *Input* step. It can have any number of steps in it, but it must still be open. (In other words, it must not end with a *Save* step.) To specify the second series, open the step's **Action** menu, and select **Connect with**. The flowchart is then updated so that it shows the two branches combining at the *Arithmetic operator* step.

*Arithmetic operator* steps have the following fields that you can set:

- **Step name** – The specific name of the step. This name is also shown in the flowchart.
- **Description** – A short description of the step.
- **Created by** – The user who created the step.
- **Value 1** – The first series in the calculation (*a(x)*), which is on the left side of the operator. Select *Input 1* or *Input 2*.
- **Operator** – The operator that's applied between the first series (**Value 1**) and the second series (**Value 2**). Select whether to add (\+), subtract (\-), multiply (\*), or divide (/).
- **Value 2** – The second series in the calculation (*b(x)*), which is on the right side of the operator. Select *Input 1* or *Input 2*.

### Constant arithmetic operator steps

*Constant arithmetic operator* steps do a calculation that applies a constant arithmetic operation to each value in an input time series.

*Constant arithmetic operator* steps implement the following calculation:

f(x) = a(x) &lt;*operator*&gt; C

In this formula:

- &lt;*Operator*&gt; is one of the following arithmetic operators: \+, \-, \*, or /.
- *C* is a constant value.

*Constant arithmetic operator* steps have the following fields that you can set:

- **Step name** – The specific name of the step. This name is also shown in the flowchart.
- **Description** – A short description of the step.
- **Created by** – The user who created the step.
- **Operator** – The operator that's applied. Select whether to add (\+), subtract (\-), multiply (\*), or divide (/).
- **Constant** – The constant value that's applied to each time series value by using the selected operator.

### Date offset steps

*Date offset* steps shift the input time series by a fixed value along the x-axis. You might use this type of step, for example, to shift last year's demand one year forward, so that you can compare it to next year's forecast by overlaying the time-shifted demand graph on the forecast graph.

*Date offset* steps implement the following calculation:

f(x) = a(x &minus; t)

In this formula, *t* is an integer that represents the number of days, months, or years.

*Date offset* steps have the following fields that you can set:

- **Step name** – The specific name of the step. The name is also shown in the flowchart.
- **Description** – A short description of the step.
- **Created by** – The user who created the step.
- **Time value** – The amount of time to shift the input time series forward by. The amount is in the unit that's specified in the **Time unit** field.
- **Time unit** – The unit that applies to the time value.

### Logical operator steps

*Logical operator* steps test whether a value exceeds a constant (threshold) at each point along a time series. As output, it returns a *1* for true and a *0* (zero) for false. You might use this type of step, for example, to evaluate when the forecast error is above a specific threshold in either direction, so that you can focus on important products.

*Logical operator* steps implement the following calculation:

f(x) = ABS\[a(x)\] &lt;*operator*&gt; C

In this formula:

- &lt;*Operator*&gt; is one of the following logical operators: &gt;, &gt;=, &lt;, or &lt;=.
- *C* is a constant.
- *ABS* is optional. If it's enabled, the absolute value (that is, the distance from zero) is used instead of the literal value.

*Logical operator* steps have the following fields that you can set:

- **Step name** – The specific name of the step. The name is also shown in the flowchart.
- **Description** – A short description of the step.
- **Created by** – The user who created the step.
- **Apply ABS** – Set this option to *Yes* to use the absolute value (distance from zero) of the input series. Set it to *No* to use the literal value (including +/\- signs) of the input series.
- **Operator** – The logical operator that's applied for the comparison against the constant value.
- **Constant** – The constant value to compare against the input time series.

### Merge steps

*Merge* steps merge two time series into a new time series by applying the selected merge logic. You can merge the time series by minimum value, maximum value, average, or sum. You might use this type of step, for example, to calculate a merged result of two forecast methods.

You can use this type of step only if your calculation model has at least two input time series in parallel branches. The first series is at the top of the branch where you create the step. The second series must start with an *Input* step. It can have any number of steps in it, but it must still be open. (In other words, it must not end with a *Save* step.) To specify the second series, open the step's **Action** menu, and select **Connect with**. The flowchart is then updated so that it shows the two branches combining at the *Merge* step.

*Merge* steps have just one field that you can set: **Merge policy**. Select one of the following values:

- *Min value* – Take the lowest of the two input values.
- *Max value* – Take the largest of the two input values.
- *Average* – Calculate the average of the two input values.
- *Sum* – Add the two input values together.

### Monetary value steps

*Monetary value* steps convert a forecast or historical demand time series that's based on sales units into a series of monetary values that are based on a selected price list. The calculation first tries to match the cost or price from a primary price list. It then tries a fallback price list if one is selected. You might use this type of step, for example, to convert a forecast (quantity) into expected revenue (monetary value).

*Monetary value* steps implement the following calculation:​

f(x) = a(x) &times; Price(product-ID)

*Monetary value* steps have the following fields that you can set:

- **Step name** – The specific name of the step. The name is also shown in the flowchart.
- **Description** – A short description of the step.
- **Created by** – The user who created the step.
- **Primary price list** – Select the primary data table that contains your price list. The list includes all the tables that are currently defined for use with Demand planning. (Learn more in [Set up tables](import-data.md).) The price list must include columns for product IDs and prices.
- **Fallback price list** – If the system can't find a matching price in the primary price list, it checks any price list that you select here.

### Phase in/out steps

*Phase in/out* steps modify the values of a data column in a time series to simulate the gradual phasing in of a new element (such as a new product or warehouse) or phasing out of an old element. The phase in/out calculation lasts for a specific period and uses values that are drawn from the same time series (from either the same data column that is being adjusted or another data column that represents a similar element).

*Phase in/out* steps have the following fields that you can set:

- **Step name** – The specific name of the step. This name is also shown in the flowchart.
- **Description** – A short description of the step.
- **Created by** – The user who created the step.
- **Rule group** – The name of the rule group that defines the calculation that the step does.

For more information about phase in/out functionality, including details about how to set up your phase in/out rule groups, see [Use phase in/out functionality to simulate planned changes](phase-in-out.md).

### Ratio in percentage steps

*Ratio in percentage* steps calculate a ratio in percentage, based on two input time series. You might use this type of step, for example, to calculate the error percentage of a previous forecast, based on a historical demand and forecast time series.

*Ratio in percentage* steps implement the following calculation:​

f(x) = &Sigma; \{\[a(x) &minus; b(x)\] &divide; a(x)\} &times; 100 %

You can use this type of step only if your calculation model has at least two input time series in parallel branches. The first series is at the top of the branch where you create the step. The second series must start with an *Input* step. It can have any number of steps in it, but it must still be open. (In other words, it must not end with a *Save* step). To specify the second series, open the step's **Action** menu, and select **Connect with**. The flowchart is then updated so that it shows the two branches combining at the *Ratio in percentage* step.

*Ratio in percentage* steps have the following fields that you can set:

- **Step name** – The specific name of the step. This name is also shown in the flowchart.
- **Description** – A short description of the step.
- **Created by** – The user who created the step.
- **Value 1** – The first series in the calculation (*a(x)*). Select *Input 1* or *Input 2*.
- **Value 2** – The second series in the calculation (*b(x)*). Select *Input 1* or *Input 2*.

### Save steps

*Save* steps save the result of the calculation model as a new or updated series. All calculation models must end with a single *Save* step.

The calculated series will be saved according to the settings that you configure each time that you run a calculation job as described in [Work with calculation profiles](calculation-profiles.md).
