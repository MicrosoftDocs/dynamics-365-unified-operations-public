---
# required metadata

title: Comments visual
description: This article describes how to use the comments visual in the Business performance planning application.
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
ms.dyn365.ops.version: 

---
# Comments visual

[!include [banner](../includes/banner.md)]

This article describes how to use the **Comments** visual in the Business performance planning application. To fully use the planning application, you must also install Power BI visuals. To learn more about installing Power BI visuals, see [Power BI visuals](/power-bi/developer/visuals).

Effective communication is vital during the planning phase. Planners often need to clarify assumptions tied to their figures, while stakeholders require the ability to delve into specifics and engage in discussions. The **Comments** visual offers an integrated solution to collect, manage, and discuss commentary within your team during the planning process.

The primary purpose of the **Comments** visual is to link **Commentary** to **Data values**. This link helps facilitate discussions and explanations tied to specific data points, enabling teams to collectively address business assumptions and navigate through the planning process collaboratively.

The **Comments** visual provides:

- **Integrated Communication Hub**: A centralized platform to gather and address feedback, ensuring all stakeholders can contribute insights and suggestions during planning.
- **Enhanced Collaboration** - Enables teams to discuss underlying assumptions, clarifying the rationale behind forecasted numbers and ensuring data consumers are well-informed.

## Prerequisites

Before you use of the **Comments** visual, prepare a sample comment like, **Test comment** to a relevant data cell.

## Install the Comments visual

1.  In Power BI, navigate to the workspace or report where you intend to configure the **Matrix Planner**.
2.  Drag the **Matrix Planning** visual and **Comments** visual to the report canvas.
3.  For the **Matrix Planning** visual, drag the **Name** columns from each dimension into the respective fields in the **Visualization** pane.
4.  For the **Comments** visual, drag the **Comment** field from your cube into the **Comments** parameter.
5.  Apply the same filter context (slicers) used in the **Matrix Planner** to the **Comments** visual. This ensures alignment of data between both visuals.
6.  Add your **API Base URL** and **Cube name** to the **API Details** window of the visual.
7.  Optional - Add a **Status Dimension Name** if you want to only allow selection of the items in the dimension that you have specified.

When you finish, the **Comments** visual will display comments in a tabular format within the data.

## Functionality

- **Collating Comments at Cell Level** - Aggregates and displays comments tied to specific cell or pivot coordinates within the data.
- **Facilitating Comment Management** - Offers a tabular view to manage and work through comments during the planning phase.
- **Ensuring Data Consistency** - Requires matching filter contexts to maintain consistency between the **Comments** visual and the **Matrix planner** visual, ensuring the same dataset is examined.

## Configuration options

- **Pivot Property** - If you add one of the dimensions to the **Pivot** section of the visual, the values of that dimension appear on the columns rather than rows.
- **Filter Property** - If you have a slicer somewhere on the page, and you want to pass the filtered values from the slicer to the comments visual, you need to do this explicitly by using the filters section of the visual. Power BI slicer values aren't transferred automatically to the visual. For example, if **DimOrganization** is a slicer on the page, you need to add this field to the **Filter** section of the comments visual to get this filter's selected value to transfer to the **Comments** visual.
- **Editing Amounts** - Edit the amount related to the coordinate in the visual by activating this option in the properties.
- **Entering comments directly in the Matrix planning visual** - Enter comments directly in the **Matrix planning** visual without the need for the additional **Comment** visual.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
