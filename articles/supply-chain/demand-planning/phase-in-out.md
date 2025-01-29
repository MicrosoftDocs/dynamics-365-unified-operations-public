---
title: Use phase in/out functionality to simulate planned changes
description: Learn how to use phase in/out functionality to set up forecasts and calculations that simulate changes that you plan to make.
author: AndersEvenGirke
ms.author: aevengir
ms.topic: how-to
ms.date: 11/29/2024
ms.custom: 
  - bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Use phase in/out functionality to simulate planned changes

Phase in/out functionality lets you set up forecasts and calculations that simulate changes that you plan to make. Here are some examples:

- Phase out a product that's no longer popular or that's leaving the market.
- Phase in a new product.
- Replace an older product with a new, similar one.
- Open a new store or warehouse that should be similar to an existing one.

To apply calculations of this type, add a *Phase in/out* step to the relevant calculation model or forecast model. The *Phase in/out* step uses a *phase in/out rule group* to modify a selected data column based on values that are found in the same column or another column of the time series. Each phase in/out rule group defines selection criteria that identify input and output columns, a period to apply the calculation during, and a scaling factor to apply during that period.

## Example: Phase in a new product that replaces an existing product

You're introducing a new product (Speaker V2) that replaces a similar existing product (Speaker V1). You expect that customers will increasingly choose the new speaker. However, you also expect that the total number of speakers that are sold each month will remain about the same as last year and follow a familiar seasonal sales pattern. Therefore, you add the following phase in/out calculations to next year's forecast:

- For the first six months of next year, you'll offer Speaker V2 at a premium price. Therefore, you predict that the quantity of Speaker V2 that you sell will be 40 percent of the quantity of Speaker V1 that you sold during the same month last year. Speaker V1 will make up the difference, and you'll sell 60 percent of the quantity that you sold last year.
- After six months, you'll slightly lower the price of Speaker V2. Therefore, for the last half of next year, you predict that the quantity of Speaker V2 that you sell will be 75 percent of the quantity of Speaker V1 that you sold last year. The quantity of Speaker V1 that you sell will be 25 percent of the quantity that you sold last year.
- After a year, you expect that sales of Speaker V2 will completely replace sales of Speaker V1.

To add this calculation to a forecast model, you set up a phase in/out rule group that has the following rules:

- **Phase in rule 1** – This rule applies from January through June. For each month, select the forecast quantity based on last year's sales of Speaker V1, multiply it by 40 percent, and add the result to the forecast quantity for Speaker V2. (The forecast quantity for Speaker V2 is currently 0 \[zero\], because it's a new product.)
- **Phase out rule 1** – This rule applies from January through June. For each month, select the forecast quantity based on last year's sales of Speaker V1, multiply it by 60 percent, and set the result as the new forecast quantity for Speaker V1.
- **Phase in rule 2** – This rule applies from July through December. For each month, select the forecast quantity based on last year's sales of Speaker V1, multiply it by 75 percent, and add the result to the forecast quantity for Speaker V2.
- **Phase out rule 2** – This rule applies from July through December. For each month, select the forecast quantity based on last year's sales of Speaker V1, multiply it by 25 percent, and set the result as the new forecast quantity for Speaker V1.

The following table shows an example of forecasted sales before the phase in and phase out calculations are applied.

| Product    | Jan | Feb | Mar | Apr | May | Jun | Jul | Aug | Sep | Oct | Nov | Dec |
|------------|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| Speaker V1 | 100 | 100 | 100 | 100 | 100 | 100 | 100 | 100 | 100 | 100 | 100 | 100 |

The following table shows an example of forecasted sales after the phase in and phase out calculations are applied.

| Product    | Jan | Feb | Mar | Apr | May | Jun | Jul | Aug | Sep | Oct | Nov | Dec |
|------------|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| Speaker V1 | 60  | 60  | 60  | 60  | 60  | 60  | 25  | 25  | 25  | 25  | 25  | 25  |
| Speaker V2 | 40  | 40  | 40  | 40  | 40  | 40  | 75  | 75  | 75  | 75  | 75  | 75  |

## Manage phase in/out rule groups

Use phase in/out rule groups to define the phase in/out calculations that are applied in your forecast and calculation models. To create, view, or edit a rule group, follow these steps.

1. On the navigation pane, select **Configuration** \> **Phase in/out**.
1. Follow one of these steps:

    - To create a new rule group, select **New** on the Action Pane. A wizard guides you through the steps for creating the group.
    - To view or edit an existing rule group, select the link for it in the **Name** column of the grid to open its details page.

1. The details page and wizard pages provide nearly identical fields that you can set:

    - **Name** – Enter a name for the rule group.
    - **Description** – Enter a short description of the rule group.
    - **Owner** – Select the user account that owns the rule group. (This field is available only in the wizard.)
    - **Active** – Set this option to *Yes* or *No*. Only active rules groups can be assigned to the phase in/out steps of your forecast or calculation models.
    - **Rules** – Use the fields on this tab to define the phase in/out calculations that the group does. For information about how to use these fields, see the next section.

1. Follow one of these steps:

    - If you're creating a new group, select **Review and finish** on the last wizard page to save your rule group and open its details page.
    - If you're editing an existing group, save your settings by selecting **Save** or **Save & close** on the Action Pane.

## Set up rules

Each rule group must have at least one rule and might have several rules. You set up rules on the **Rules** tab of either the details page or the **Add rules** page of the new group wizard. The process is the same in both places.

Use the buttons on the toolbar to add, remove, and edit rules. You can include as many rules as you need for each group. Each time that you add or edit a rule, the **Edit rule** dialog box appears.

:::image type="content" source="media/edit-rule-dialog.png" alt-text="Screenshot of the Edit rule dialog box." lightbox="media/edit-rule-dialog.png":::

In the **Edit rule** dialog box, set the following fields for each rule:

- **Rule name** – Enter a name for the rule. Choose a name that makes the rule easy to identify in the rule list.
- **Start date** – Enter the first date when the rule should apply.
- **End date** – Enter the last date when the rule should apply. For a phase in rule, data will stop being copied on this date. (By this date, you should have actual sales data to base your forecasts on.) For a phase out rule, time series values will fall to 0 (zero) on this date unless another phase out rule applies immediately after this rule.
- **Rule type** – Select one of the following values to specify the type of rule:

    - *Phase in* – The rule takes a value from the data column that you identify in the **Copy data from** section, multiplies it by the **Uplift/reduction factor (%)** value, and adds the result to the data column that you identify in the **Apply data to** section.
    - *Phase out* – The rule takes a value from the data column that you identify in the **Copy data from** section, multiplies it by the **Uplift/reduction factor (%)** value, and sets the result as the new value for the same data column that you identify in the **Copy data from** section.

- **Uplift/reduction factor (%)** – Specify a factor (as a percentage) to apply to the input time series values.
- **Copy data from** – Use this section to specify criteria for selecting input values for the calculation. You can use the **Add condition** button to add as many rows as you need. The data tables that are listed are the data tables that are defined in Demand planning. (Learn more in [View and customize tables for holding imported data](tables.md).) You typically use this section to identify a product from the product table that you want to phase in or out.
- **Apply data to** – This section applies only to phase in rules. (Phase out rules always apply to the same data columns that are identified in the **Copy data from** section.) Specify criteria for selecting the data column that the phase in rule applies to. You typically use this section to identify a new product that you're phasing in. You can use the **Add condition** button to add as many rows as you need.

## Assign rule groups to phase in/out steps

After you finish setting up your rule groups, you can use them by putting *Phase in/out* steps at the appropriate positions in your calculation models and forecast models. Learn more in [Design calculation models](design-calculation-models.md) and [Design forecast models](design-forecast-models.md).
