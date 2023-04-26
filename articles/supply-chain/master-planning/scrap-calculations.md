---
title: Set up scrap to calculate raw material requirements
description: This article describes how to set up your bills of materials (BOMs), formulas, and route operations to record the quantity of raw material that is scrapped during manufacturing. The master planning engine can then calculate the quantity of raw materials that must be purchased to produce the desired quantity of the final product.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: Route, RouteTable, EcoResProductDetailsExtended, BOMConsistOf, BOMTable
ms.topic: how-to
ms.date: 12/08/2022
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Set up scrap to calculate raw material requirements

[!include [banner](../includes/banner.md)]

This article describes how to set up your bills of materials (BOMs), formulas, and route operations to record the quantity of raw material that's scrapped during manufacturing. The master planning engine can then use this information to calculate the quantity of raw materials that must be purchased to produce the desired quantity of the final product.

*Scrap* is the quantity of raw material that's left over and can't be used after an item is manufactured. You can set up scrap in the following places:

- Formula or BOM line
- Route operations

## Scrap for route operations

*Route scrap* is the scrap that's produced during an operation in a route.

### Set up scrap for route operations

To view or set the amount of scrap that's produced by an existing route operation, follow these steps.

1. Go to **Production control \> All routes**.
1. In the list pane, select the route that you want to work with.
1. On the Action Pane, on the **Route** tab, select **Route details**.
1. The **Route details** page appears. The top grid lists each operation in the route. For each operation, you can view or set the following values that are related to the amount of raw material that was consumed as scrap for the operation:

    - **Scrap percentage** – Specify the percentage of the input raw material that's consumed as scrap during the operation.
    - **Accumulated** – The accumulated scrap percentage for the operation in the route. This value is read-only. The system calculates it in the following way:

        *Accumulated* = (*Accumulated percentage for the following operation* &times; 100) &divide; (100 – *Scrap percentage*)

### Calculate scrap for route operations

This section describes an example where you're producing item *FG*, which uses 100 pieces of raw material *RM*. To produce FG, you use a route that has three operations: *Operation-1*, *Operation-2*, and *Operation-3*.

If the BOM line for RM doesn't specify which operation consumes the raw material, the system assumes that the first operation (Operation-1) does. Therefore, it calculates the quantity of RM that must be available at the beginning of Operation-1 to produce the required quantity of FG.

First, consider a scenario where the route operations require the following input:

- Operation-1 requires *X* liters of RM as input.
- Operation-2 requires the output of Operation-1 as input.
- Operation-3 requires the output of Operation-2 as input.

If each operation has a scrap percentage of 10 percent, the system does the following calculations to determine how many liters of RM are required as initial input to produce 100 liters of FG:

- **Operation-1:** *X* &times; (1 – 10%) = *Y*
- **Operation-2:** *Y* &times; (1 – 10%) = *Z*
- **Operation-3:** *Z* &times; (1 – 10%) = 100 liters of FG

When you solve for *X*, you get the following result:

*X* = 100 &divide; (0.9 &times; 0.9 &times; 0.9) = 137 liters of RM as input

Next, consider a scenario where the raw material starts to be consumed only later in the route, at Operation-2. In this case, the **Oper. Nr.** value on the BOM line must be set to the operation number of that operation. (For more information about how to set this value, see the next section.) If each operation has a scrap percentage of 10 percent, the system does the following calculations to determine how many pieces of RM are required as initial input to produce 100 liters of FG:

- **Operation-1:** *X* = *Y*
- **Operation-2:** *Y* &times; (1 – 10%) = *Z*
- **Operation-3:** *Z* &times; (1 – 10%) = 100 liters of FG

When you solve for *X*, you get the following result:

*X* = *Y* = 100 &divide; (0.9 &times; 0.9) = 123 liters of RM as input

## Scrap for BOMs and formulas

*BOM scrap* and *formula scrap* are types of scrap that are produced in relation to a specific BOM line or formula line (depending on the type of product that you're manufacturing). BOMs and formulas can include both constant and variable scrap.

### Set up scrap for BOMs and formulas

To view or set the amount of scrap that's produced by the BOM or formula for a released product, follow these steps.

1. Go to **Product information management \> Products \> Released products**.
1. In the grid, find and select the product that you want to work with.
1. On the Action Pane, on the **Engineer** tab, select either **BOM versions** or **Formula versions**, depending on the type of product.
1. The **BOM versions** or **Formula versions** page appears. In the list pane, select the version that you want to work with.
1. On the **Bill of materials lines** or **Formula lines** FastTab, select the line that you want to set up scrap for.
1. On the toolbar of the FastTab, select **Edit**.
1. The **Edit BOM line** or **Edit Formula line** dialog appears. On the **General** tab, in the **Oper. No.** field, if the current line is consumed only during a specific route operation, enter the operation number of that route operation. The value must be an integer, and it must match the related operation number that's shown on the **Route details** page. If you leave this field blank, the system will assume that the line starts to be consumed during the first operation.
1. On the **Consumption calculation** tab, set the following fields as required:

    - **Constant scrap** – Enter the quantity of scrap that's always the same for a single production run, regardless of the quantity of finished goods that are manufactured. Specify the scrap in the same unit that's used on the BOM or formula line.
    - **Variable scrap** – Variable scrap grows in proportion to the quantity of finished goods that are produced. Specify the amount of scrap that's created as a percentage of the raw material that's required as input for the route. For example, if the variable scrap for a raw material is 20 percent, and the route requires 100 liters of that material as input for a given production run, the required purchase quantity is 120 liters (excluding any constant scrap).

1. Select **OK** to apply your settings and close the dialog box.

You can also configure the previously described settings directly on the BOM or formula instead of on the **Released products** page.

1. Follow one of these steps:

    - Go to **Product information management \> Bills of materials and formulas \> Bills of materials**.
    - Go to **Product information management \> Bills of materials and formulas \> Formulas**.

2. Open a BOM or formula, and then configure settings like those that are described in the previous procedure.

### Calculate scrap for BOMs and formulas

Based on the configured constant and variable BOM or formula scrap values, the system does the following calculation to determine the quantity of raw material that must be purchased to meet your actual raw material requirement:

*Purchased material* = (*Required raw material* &times; \[1 + *Variable BOM or formula scrap*\]) + *Constant BOM or formula scrap*

For example, you have the following requirements and scrap:

- Constant scrap = 10 liters
- Variable scrap = 20 percent
- Required raw material = 100 liters

In this case, to meet your material requirements, you must purchase the following quantity of raw material:

*Purchased material* = (100 liters &times; 1.20) + 10 liters = 130 liters

## Calculate raw material requirements based on the total scrap

If both route scrap and BOM or formula scrap are set up, the system automatically does the following calculation to determine how much raw material will be required to produce a specific quantity of finished goods:

*Purchased raw material* = *Total start quantity according to the route calculation* &times; (1 + *Variable BOM or formula scrap*) &times; *Batch size* + *Constant BOM or formula scrap*

(In this calculation, *Batch size* is the number of pieces of the final good that will be produced.)
