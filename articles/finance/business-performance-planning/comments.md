---
title: Comments visual
description: Learn how to use the Comments visual in the Business performance planning application, including prerequisites and outlines on functionality and configuration.
author: ShielaSogge
ms.author: twheeloc
ms.topic: article
ms.date: 12/08/2023
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-12-03
ms.search.form: 
ms.dyn365.ops.version: 
---

# Comments visual

[!include [banner](../includes/banner.md)]

This article describes how to use the **Comments** visual in the Business performance planning application. To fully use this application, you must also install Microsoft Power BI visuals. For information about how to install Power BI visuals, see [Power BI visuals](/power-bi/developer/visuals).

Effective communication is vital during the planning phase. Planners often have to clarify assumptions that underlie their figures, whereas stakeholders must be able to dive into specifics and engage in discussions. The **Comments** visual offers an integrated solution for collecting, managing, and discussing commentary within your team during the planning process.

The primary purpose of the **Comments** visual is to link **commentary** to **data values**. This link helps facilitate discussions and explanations that are related to specific data points. Therefore, teams can collectively address business assumptions and collaboratively navigate the planning process.

The **Comments** visual provides the following features:

- **Integrated communication hub** – A centralized platform for gathering and addressing feedback ensures that all stakeholders can contribute insights and suggestions during planning.
- **Enhanced collaboration** – Teams can discuss underlying assumptions, clarify the rationale behind forecasted numbers, and ensure that data consumers are well-informed.

## Prerequisites

Before you use the **Comments** visual, prepare a sample comment (for example, **Test comment**) in an appropriate data cell.

## Install the Comments visual

1. In Power BI, go to the workspace or report where you want to configure the Matrix Planner.
2. Drag the **Matrix Planning** and **Comments** visuals onto the report canvas.
3. For the **Matrix Planning** visual, drag the **Name** columns from each dimension into the corresponding fields in the **Visualization** pane.
4. For the **Comments** visual, drag the **Comment** field from your cube into the **Comments** parameter.
5. Apply the same filter context (that is, the same set of slicers) that's used in the Matrix Planner to the **Comments** visual. In this way, you ensure the alignment of data between the two visuals.
6. In the **API Details** window for the visual, add your API base URL and cube name.
7. Optional: Add a **Status Dimension Name** value to allow only items in the specified dimension to be selected.

When you've finished, the **Comments** visual shows comments in tabular format in the data.

## Functionality

- **Collate comments at the cell level** – Aggregate and show comments that are linked to specific cell or pivot coordinates in the data.
- **Facilitate comment management** – A tabular view lets you manage and work through comments during the planning phase.
- **Ensure data consistency** – Matching filter contexts are required to maintain consistency between the **Comments** visual and the Matrix Planner. This requirement ensures that the same dataset is examined.

## Configuration options

- **Pivot property** – If you add one of the dimensions to the **Pivot** section of the visual, the values of that dimension appear in the columns instead of the rows.
- **Filter property** – Power BI slicer values aren't automatically transferred to the visual. Therefore, if you have a slicer somewhere on the page, and you want to pass the filtered values from that slicer to the **Comments** visual, you must explicitly configure this behavior by using the **Filters** section of the visual. For example, if the page includes the **DimOrganization** slicer, you must add this field to the **Filters** section of the **Comments** visual. Only then is the selected value of the filter transferred to the **Comments** visual.
- **Editing amounts** – Activate this option in the properties to edit the amount that's related to the coordinate in the visual.
- **Entering comments directly in the Matrix Planning visual** – Enter comments directly in the **Matrix Planning** visual without having to add more **Comments** visuals.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
