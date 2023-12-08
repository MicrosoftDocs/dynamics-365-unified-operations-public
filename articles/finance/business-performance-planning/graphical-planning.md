---
# required metadata

title: Graphical planning visual
description: This article describes how to use the graphical planning visual in the Business performance planning application.
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

This article describes how to use the graphical planning visual in the Business performance planning application. To fully use the planning application, you must also install Power BI visuals. To learn more about installing Power BI visuals, see [Power BI visuals](/power-bi/developer/visuals/).

You can use the graphical planning visual to dynamically adjust underlying values by directly manipulating graphs and charts. Unlike traditional table-based data manipulation, this visual allows for precise adjustments through interactive chart interactions. The visual serves as an intuitive tool for presenting forecasts and budgets, facilitating a hands-on approach for stakeholders less familiar with detailed data.

## Purpose and benefits

The graphical planning visual streamlines the process of adjusting values in forecasts and budgets and offers an intuitive and visually interactive method for you to engage with and modify underlying data represented in charts and graphs. This includes:

- **Interactive Data Manipulation** - Seamlessly interact with visual elements, such as line charts, by directly adjusting data points to reflect business assumptions and changes in real time.
- **Enhanced Visualization for Decision-making** - Provide a visually intuitive tool for senior leadership to engage with forecasts and budgets, aiding in decision-making processes through hands-on data interaction.

## Set up the visual

1.  In Power BI, navigate to the workspace or report where you want to configure the visual.
2.  Drag the **Graphical planning visual** to the report canvas.
3.  Add your **API Base URL** to the **API Details** window of the visual.
4.  In the **Amount** column, enter a value the **Value** variable.
5.  Define the **X and Y axes** using the **Legend** variable, incorporating name columns from the dimensions you want to plot on the chart.

### Use the visual

After you install the visual and it's set up on the Power BI canvas, complete the following steps to begin using it in your planning.

1. Select the **Edit** pencil icon to enter edit mode.
2. On the line chart, drag points to adjust the values according to your business assumptions.
3. Select the **Save** icon to instantly reflect the changes in the data. The automatic update provides a more intuitive and visually appealing planning tool for clients and teams.

## Percentage entry

In addition to changing the data points by using absolute numbers, you can switch to **Percentage** mode and change the values as a percentage of the total.

## Lock totals

Using the **Pin** icon, you can enable the **lock total** mode which locks the total of all values. Any adjustment in that mode changes the values of all other elements in the visual to keep the total constant.

## Visual formatting

In the **Chart UI** properties, configure the background color, bar color, comparison bar color, font color, display units, and rounding to the nearest, which applies to the interval size when you drag on the bar.

## Total display

In the **Chart UU** properties, use the **Show Total Title** and **Show Total Indicator** properties to display the total and \$ variance of the **Value** and **Comparison** scenarios.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
