---
# required metadata

title: Business performance planning application variance visual
description: This article describes how to use the variance visual in the business performance planning application.
author: ShielaSogge
ms.date: 12/07/2023
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
ms.dyn365.ops.version: 

---
# Variance visual

This article describes how to use the variance visual in the business performance planning application. You must also install Power BI visuals to fully use the planning application. To learn more about installing Power BI visuals, see [Power BI visuals](/power-bi/developer/visuals).

## Overview

The variance custom visual plays a pivotal role in budget variance analysis (BVA), enabling users to comprehend and address discrepancies between budgets and actual results. This visual generates sorted bar charts, showcasing the differences between two values, aiding in identifying key drivers behind variances. It empowers users to analyze root causes and refine future planning cycles by sorting variances from largest to smallest.

It aims to bridge the gap between budgeted and actual values, facilitating root cause analysis and driving informed decision-making by presenting variances in a clear, sorted format.

### Benefits

 - Efficient root cause analysis - Quickly identifies and sorts the most significant discrepancies between budgets and actuals, facilitating prompt investigation into underlying causes.
 - Enhanced planning insights - Enables users to understand discrepancies, fostering informed adjustments for improved future planning cycles.

## Prerequisites and installation
For more information about prerequisites and installation, see [Install Power BI visuals](powerBI-visual-install.md).

### Using the Visual

Utilize the variance visual to efficiently sort and visualize variances between budgeted and actual values, offering an intuitive and valuable tool within the reporting cycle.
You can also render customizable KPI cards and visualize variances in vertical or horizontal bar charts with small multiples display support and the option to switch between absolute, relative and waterfall variance displays according to IBCS principles as well as category drill down.

### Configuration Options

In the visual fields you can configure value, comparison value and small multiples.

### Visual Formatting

In the visual formatting properties, you can configure various options like colors for the chart, chart border, border color, chart background color, comparison bar color, formatting font size, KPI card features, formatting of values and what visual elements should be visible. For example, the total display on the top right and whether the users can switch between different variance types.

### Visualization and writeback

It's possible to change data in the underlying data source by dragging and dropping on the bars.
