---
title: Use phase in/out functionality to simulate planned changes
description: This article explains how to use phase in/out functionality to set up forecasts and calculations that simulate changes you're planning to make.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 05/29/2024
audience: Application User
ms.custom: 
  - bap-template
---

# Use phase in/out functionality to simulate planned changes

Phase in/out functionality lets you set up forecasts and calculations that simulate changes you're planning to make, such as:

- Phasing out a product that's no longer popular or is leaving the market
- Phasing in a new product
- Replacing an older product with a new, similar one
- Opening a new store or warehouse that should be similar to an existing one

To apply this type of calculation, add a *phase in/out tile* to the relevant calculation model or forecast model. The phase in/out tile uses a *phase in/out rule group* to modify a selected data column using values found in the same column or another column of the time series. Each phase in/out rule group defines selection criteria that identify input and output columns, a time period during which to apply the calculation, and a scaling factor to apply during that period.

## Example: Phase in a new product that replaces an existing product

Suppose you're introducing a new product (Speaker V2) that replaces a similar existing product (Speaker V1). You expect that customers will increasingly choose the new speaker, but the total number of speakers sold each month will remain about the same as last year, following a familiar seasonal sales pattern. Therefore, you could add the following phase in/out calculations to next year's forecast:

- For the first six months of next year, you offer Speaker V2 at a premium price. Therefore, you predict Speaker V2 will sell 40% of the quantity that Speaker V1 did for the same month the previous year. Speaker V1 will make up the difference and continue to sell 60% as much as last year.
- After six months, you'll lower the price of Speaker V2 slightly. So, for the last half of next year, you predict Speaker V2 will sell 75% of the quantity that Speaker V1 did, with Speaker V1 still selling 25%.
- After a year, you expect Speaker V2 to completely replace sales of Speaker V1.

To be able to add this calculation to a forecast model, you'd set up a phase in/out rule group with the following rules:

- **Phase in rule 1** – Applies from January to June. For each month, select the forecast quantity based on last year's sales of Speaker V1, multiply it by 40%, and add that to the forecast quantity for Speaker V2 (which is currently zero, since it's a new product).
- **Phase out rule 1** – Applies from January to June. For each month, select the forecast quantity based on last year's sales of Speaker V1, multiply it by 60%, and set that as the new forecast quantity for Speaker V1.
- **Phase in rule 2** – Applies from July to December. For each month, select the forecast quantity based on last year's sales of Speaker V1, multiply it by 75%, and add that to the forecast quantity for Speaker V2.
- **Phase out rule 2** – Applies from July to December. For each month, select the forecast quantity based on last year's sales of Speaker V1, multiply it by 25%, and set that as the new forecast quantity for Speaker V1.

The following table shows an example of forecasted sales before applying the phase in and phase out calculations.

| Product    | Jan | Feb | Mar | Apr | May | Jun | Jul | Aug | Sep | Oct | Nov | Dec |
|------------|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| Speaker V1 | 100 | 100 | 100 | 100 | 100 | 100 | 100 | 100 | 100 | 100 | 100 | 100 |

The following table shows an example of forecasted sales after applying the phase in and phase out calculations.

| Product    | Jan | Feb | Mar | Apr | May | Jun | Jul | Aug | Sep | Oct | Nov | Dec |
|------------|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| Speaker V1 | 60  | 60  | 60  | 60  | 60  | 60  | 25  | 25  | 25  | 25  | 25  | 25  |
| Speaker V2 | 40  | 40  | 40  | 40  | 40  | 40  | 75  | 75  | 75  | 75  | 75  | 75  |

## Manage phase in/out rule groups

Use phase in/out rule groups to define the phase in/out calculations to be applied in your forecast and calculation models. To create, view, or edit a rule group, follow these steps:

1. On the navigation pane, select **Configuration** \> **Phase in/out**.

1. Do one of the following steps:
    - To create a new rule group, select **New** on the Action Pane. A wizard guides you through the steps of creating the group.
    - To view or edit an existing rule group, find it in the grid and select the link for it in the **Name** column to open the details page of your selected group.

1. The details page and wizard pages provide nearly identical settings. Use them to make the following settings:
    - **Name** – Enter a name for the rule group.
    - **Description** – Enter a short description of the rule group.
    - **Owner** – Select the user account that owns the rule group. (This setting is only available in the wizard.)
    - **Active** – Set to *Yes* or*No*. Only active rules groups can be assigned the phase in/out tiles of your forecast or calculation models.
    - **Rules** – Use these settings to define the phase in/out calculations made by the group. See the next section for details about how to use these settings.

1. If you're creating a new group, select **Review and finish** on the last page to save your rule group and open its details page. If you're editing an existing group, save your settings by selecting **Save** or **Save & close** on the Action Pane.

## Set up rules

Each rule group must have at least one rule and might have several. You set up rules using the **Rules** tab of the details page or the **Add rules** page of the new-group wizard, both of which work the same.

Use the buttons on the toolbar to add, remove, and edit rules. You can include as many rules as you need for each group. Each time you add or edit a rule, the **Edit rule** dialog opens.

:::image type="content" source="media/edit-rule-dialog.png" alt-text="The Edit rule dialog." lightbox="media/edit-rule-dialog.png":::

Use the **Edit rule** dialog to make the following settings for each rule:

- **Rule name** – Enter a name for the rule. Choose a value that makes it easy to identify in the rule list.
- **Start date** – Enter the first date where the rule should apply.
- **End date** – Enter the last date where the rule should apply. For phase-in rules, data will stop being copied on this date (by this date, you should have actual sales data to base your forecasts on). For phase-out rules, time-series values will fall to zero on this date unless another phase-out rule applies immediately after this one.
- **Rule type** – Identify they type of rule it is by selecting one of the following values:
    - *Phase in* – The rule takes a value from the data column identified in the **Copy data from** section, multiplies it by the **Uplift/reduction factor (%)** value, and adds the result to the data column identified in the **Apply data to** section.
    - *Phase out* – The rule takes a value from the data column identified in the **Copy data from** section, multiplies it by the **Uplift/reduction factor (%)** value, and sets the result as the new value for the data column identified in the **Copy data from** section.

- **Uplift/reduction factor (%)** – Specify a factor (as a percentage) to apply to the input time series values.
- **Copy data from** – Specify criteria for selecting input values for the calculation. You can use the **Add condition button** to add as many rows as you need. The data tables listed are those defined in Demand planning (see also [View and customize tables for holding imported data](tables.md)). You might typically use this setting to identify a product from the product table that you want to phase in or out.
- **Apply data to** – This setting only applies for phase-in rules (phase-out rules always apply to the same data columns identified in the **Copy data from** section). Specify criteria for selecting the data column to which the phase-in rule applies. You might typically use this setting to identify a new product that you're phasing in. You can use the **Add condition button** to add as many rows as you need.

## Assign rule groups to phase in/out tiles

When you're done setting up your rule groups, you're ready to use them by placing phase in/out tiles at the appropriate positions in your calculation models and forecast models. For details about how to do this, see [Design calculation models](design-calculation-models.md) and [Design forecast models](design-forecast-models.md).
