---
# required metadata

title: Business performance planning application graphical planning visual
description: This article describes how to use the graphical planning visual in the Business performance planning application
author: ShielaSogge
ms.date: 11/28/2023
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
# Graphical planning
This article describes how to use the graphical planning visual in the Business performance planning application. You must also install Power BI visuals to fully use the planning application. To learn more about installing Power BI visuals, see [Power BI visuals](/power-bi/developer/visuals/).


## Overview

The graphical planning visual empowers users to dynamically adjust underlying values by manipulating graphs and charts directly. Unlike traditional table-based data manipulation, this visual allows for precise adjustments through interactive chart interactions. It serves as an intuitive tool for presenting forecasts and budgets, facilitating a hands-on approach for stakeholders less familiar with detailed data.

## Purpose and Benefits

It streamlines the process of adjusting values in forecasts and budgets, offering an intuitive and visually interactive method for users to engage with and modify underlying data represented in charts and graphs.

-   **Interactive Data Manipulation**

    Seamlessly interact with visual elements, such as line charts, by directly adjusting data points to reflect business assumptions and changes in real time.

-   **Enhanced Visualization for Decision-making**

    Provide a visually intuitive tool for senior leadership to engage with forecasts and budgets, aiding in decision-making processes through hands-on data interaction.

# Getting Started

## Prerequisites

1.  Import business performance planning visuals from AppSource. Learn More.
2.  Connect PowerBI to your Dataverse environment. Learn More.
3.  Understanding Allocation. Learn More.
4.  

## Installation Guide

1.  Open Power BI: Launch the Power BI application and access your desired workspace or report where you intend to configure the Matrix Planner.
2.  Position the visual: Drag the Graphical planning visual to the report canvas.
3.  Add your **API Base URL** to the API Details window of the visual.
4.  Set the **Value** variable with the relevant **Amount** column.
5.  Define the **X and Y axes** using the **Legend** variable, incorporating name columns from the desired dimensions for plotting on the chart.

## Compatibility

Info on PBI versions where the visual is compatible.

# Using the Visual

Once the visual is installed and setup on the Power BI canvas, follow the below steps to begin using it in your planning exercise.

1.  Click the “Edit” pencil icon to enter edit mode.
2.  Drag points on the line chart to adjust values according to your business assumptions.
3.  Click the “Save” icon to instantly reflect the changes in the data, providing a more intuitive and visually appealing planning tool for clients and teams.

## Percentage Entry

In addition to changing data points using absolute numbers, you can also switch to percentage mode which will allow you to change the values as a percentage of the total.

## Lock Totals

Using the pin icon, you can enable the **lock total** mode which will lock the total of all values. Any adjustment in that mode will change the values of all other elements in the visual to keep the total constant.

## Visual Formatting

In the Chart UI properties, you can configure background color, bar color, comparison bar color, font color, display units, rounding to the nearest (applies to interval size when dragging on the bar).

## Total Display

Using the **Show Total Title** and **Show Total Indicator** properties in the **Chart UI** properties you can display the total and \$ variance of the **Value** and **Comparison** scenarios.
