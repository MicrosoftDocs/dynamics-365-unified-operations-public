---
# required metadata

title: Graphical planning visual
description: This article describes how to use the Graphical planning visual in the Business performance planning application.
author: ShielaSogge
ms.date: 12/08/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2023-12-03
ms.dyn365.ops.version: Human Resources

---
# Graphical planning visual

[!include [banner](../includes/banner.md)]

This article describes how to use the **Graphical planning** visual in the Business performance planning application. To fully use this application, you must also install Microsoft Power BI visuals. For information about how to install Power BI visuals, see [Power BI visuals](/power-bi/developer/visuals/).

You can use the **Graphical planning** visual to dynamically adjust underlying values by directly manipulating charts. Unlike traditional table-based data manipulation, this visual allows for precise adjustments through chart interactions. It serves as an intuitive tool for presenting forecasts and budgets, and therefore facilitates a hands-on approach for stakeholders who are less familiar with detailed data.

## Purpose and benefits

The **Graphical planning** visual streamlines the process of adjusting values in forecasts and budgets. It provides an intuitive and visually interactive method for engaging with and modifying the underlying data that charts represent. Here are some of the benefits:

- **Interactive data manipulation** – Seamlessly interact with visual elements, such as line charts, by directly adjusting data points so that they reflect business assumptions and changes in real time.
- **Enhanced visualization for decision-making** – Senior leadership gets a visually intuitive tool that it can use to engage with forecasts and budgets. In this way, the visual helps with decision-making processes.

## Set up the Graphical planning visual

1. In Power BI, go to the workspace or report where you want to configure the visual.
2. Drag the **Graphical planning** visual onto the report canvas.
3. In the **API Details** window for the visual, add your API base URL.
4. In the **Amount** column, enter a value for the **Value** variable.
5. Define the x-axis and y-axis by using the **Legend** variable. Incorporate name columns from the dimensions that you want to plot on the chart.

## Use the Graphical planning visual

After you install the visual and set it up on the Power BI canvas, follow these steps to begin to use it in your planning.

1. Select the **Edit** button (pencil symbol) to enter edit mode.
2. On the line chart, drag points to adjust the values according to your business assumptions.
3. Select the **Save** button to make the data instantly reflect your changes. The automatic update provides a more intuitive and visually appealing planning tool for clients and teams.

## Percentage entry

In addition to using absolute numbers to change the data points, you can switch to **Percentage** mode and then change the values as a percentage of the total.

## Lock totals

By selecting the **Pin** button, you can enable lock total mode, which locks the total of all values. Any adjustment that you make then changes the values of all other elements in the visual, so that the total remains constant.

## Visual formatting

In the **Chart UI** properties, configure the background color, bar color, comparison bar color, font color, display units. In addition, you can configure rounding by dragging the bar to define an interval size. Values are then rounded to the nearest multiple of that interval.

## Total display

In the **Chart UI** properties, use the **Show Total Title** and **Show Total Indicator** properties to show the total and dollar variance of the **Value** and **Comparison** scenarios.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
