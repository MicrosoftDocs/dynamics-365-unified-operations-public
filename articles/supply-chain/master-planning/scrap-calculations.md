---
title: Set up scrap to calculate raw material requirements
description: This article describes how to set up your bills of material (BOMs), formulas, and route operations to record the quantity of raw material that is scrapped during manufacturing. This information lets the master planning engine calculate the quantity of raw materials that must be purchased to produce the desired quantity of final product.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: Route, RouteTable, EcoResProductDetailsExtended, BOMConsistOf, BOMTable
ms.topic: how-to
ms.date: 12/08/2022
ms.custom: bap-template
---

# Set up scrap to calculate raw material requirements

[!include [banner](../includes/banner.md)]

This article describes how to set up your bills of material (BOMs), formulas, and route operations to record the quantity of raw material that is scrapped during manufacturing. This information lets the master planning engine calculate the quantity of raw materials that must be purchased to produce the desired quantity of final product.

Scrap is the quantity of raw material that is left over and can't be used after manufacturing an item. You can set up scrap in the following places:

- Formula or BOM line
- Route operations

## Scrap for route operations

*Route scrap* is the scrap produced during an operation in a route.

### Set up scrap for route operations

To read or set the amount of scrap produced by an existing route operation, follow these steps:

1. Go to **Production control \> All routes**.
1. On the list pane, select the route you want to work with.
1. On the Action Pane, open the **Route** tab and select **Route details**.
1. The **Route details** page opens. The top grid lists each operation in the route. For each operation, you can read or set the following values, which relate to the amount of raw material consumed as scrap for the operation:
    - **Scrap percentage** – Specify the percentage of the input raw material that is consumed as scrap during the current operation.
    - **Accumulated** – The calculated accumulated scrap percentage for this operation in the route. The calculation is as follows: \[Accumulated\] = (\[Accumulated % for the following operation\] × 100) ÷ (100 - \[Scrap percentage\]). This value is calculated by the system and is read only.

### Calculate scrap for route operations

Suppose you are producing an item *FG*, which uses 100 pieces of raw material*RM*. To produce the FG, you use a route with 3 operations (Operation-1, Operation-2, and Operation-3).

If the BOM line for RM doesn't specify which operation consumes the raw material, then the system assumes it's the first one. Therefore, the system calculates the quantity of RM that must be available at the beginning of Operation-1 to result in the required quantity of FG.

Suppose the route operations require the following input:

- Operation-1 requires X liters of RM as input.
- Operation-2 requires the output of Operation-1 as input.
- Operation-3 requires the output of Operation-2 as input.

If each operation has a scrap percentage of 10%, then to find out how many liters of RM are needed as initial input to produce 100 liters of FG, the system makes the following calculations:

- Operation-1: X × (1 – 10%) = Y
- Operation-2: Y × (1 – 10%) = Z
- Operation-3: Z × (1 – 10%) = 100 liters of FG

Solving for X, we get:

X = 100 ÷ (0.9 × 0.9 × 0.9) = 137 liters of RM as input

Now suppose that the raw material is only consumed starting later in the route (at Operation-2). To indicate this, the BOM line must be configured with **Oper. Nr**. set to the operation number of that operation (see also the next section for details about how to make this setting). If each operation has a **Scrap percentage** of 10%, then to find out how many pieces of RM are needed as initial input to produce 100 liters of FG, the system makes the following calculations:

- Operation-1: X = Y
- Operation-2: Y × (1 – 10%) = Z
- Operation-3: Z × (1 – 10%) = 100 liters of FG

Solving for X, this time we get:

X = Y = 100 ÷ (0.9 × 0.9) = 123 liters of RM as input

## Scrap for BOMs and formulas

*BOM scrap* and*formula scrap* are types of scrap that are produced in relation to a specific BOM or formula line (depending on the type of product you are manufacturing). BOMs and formulas can include both constant and variable scrap.

### Set up scrap for BOMs and formulas

To read or set the amount of scrap produced by the BOM or formula for a released product, follow these steps:

1. Go to **Product information management \> Products \> Released products**.
1. In the grid, find and select the product you want to work with.
1. On the Action Pane, open the **Engineer** tab and, depending on what type of product it is, select **BOM versions** or **Formula versions**.
1. The **BOM versions** or **Formula versions** page opens. On the list pane, select the version you want to work with.
1. On the **Bill of materials lines** or **Formula lines** fast tab, select the line you want to set up scrap for.
1. From the FastTab toolbar, select **Edit**.
1. The **Edit BOM line** or **Edit Formula line** dialog opens. On the **General** tab, make the following setting as needed:
    - **Oper. No.** – If the current line is only consumed during a specific route operation, then enter the operation number of that route operation here. This value must be an integer that matches the related operation number shown on the **Route details** page. If you leave this blank, the system will assume the line is consumed starting from the first operation.

1. Open the **Consumption calculation** tab and make the following setting as needed:
    - **Constant scrap** – Enter the quantity of scrap that is always the same for a single production run, regardless of the quantity of finished goods that are manufactured. Specify the scrap using the same unit as on the BOM or formula line.
    - **Variable scrap** – Variable scrap grows in proportion to the quantity of finished goods produced. Specify the amount of scrap created as a percentage of the raw material required as input for the route. For example, if the variable scrap for a raw material is 20%, and the route requires 100 liters of that material as input for a given production run, then the required purchase quantity would be 120 liters (not including constant scrap, if any).

1. Select **OK** to apply your settings and close the dialog.

You can also make these settings on the BOM or formula directly (rather than going to the **Released products** page) by opening one of the following pages:

- **Product information management \> Bills of materials and formulas \> Bills of materials**
- **Product information management \> Bills of materials and formulas \> Formulas**

From either of those pages, open a BOM or formula and then make settings similar to those described previously for working from the **Released products** page.

### Calculate scrap for BOMs and formulas

Based on the configured constant and variable BOM or formula scrap values, the system uses the following calculation to find the quantity of raw material that must be purchased to meet your actual raw material requirement.

\[Purchased material\] = \[Required raw material\] × (1 + \[Variable BOM or formula scrap\]) + \[Constant BOM or formula scrap\])

Suppose you have the following requirements and scrap:

- Constant scrap = 10 liters
- Variable scrap = 20%
- Required raw material = 100 liters

Therefore, to meet your material requirements, you must purchase the following quantity of raw material:

\[Purchased material\] = 100 liters × 1.20 + 10 liters = 130 liters

## Calculate raw material requirements based on the total scrap

If both route scrap and BOM or formula scrap are set up, the system will automatically calculate how much raw material will be needed to produce a certain quantity of finished goods using the following formula:

\[Purchased raw material\] = \[Total start quantity according to route calculation\] × (1 + \[Variable BOM or formula scrap\]) × \[Batch size\] + \[Constant BOM or formula scrap\]

Where \[Batch size\] is the number of pieces of the final good to be produced.
