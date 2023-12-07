---
# required metadata

title: Business performance planning application comments visual
description: This article describes how to use the comments visual in the Business performance planning application.
author: ShielaSogge
ms.date: 12/03/2023
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

This article describes how to use the comments visual in the Business performance planning application. You must also install Power BI visuals to fully use the planning application. To learn more about installing Power BI visuals, see [Power BI visuals](/power-bi/developer/visuals).

## Overview

Effective communication is vital during the planning phase. Planners often need to clarify assumptions tied to their figures, while stakeholders require the ability to delve into specifics and engage in discussions. The Comments Visual offers an integrated solution to collect, manage, and discuss commentary within your team during the planning process.

The primary purpose of the Comments Visual is to link Commentary to Data Values. This helps facilitate discussions and explanations tied to specific data points, enabling teams to collectively address business assumptions and navigate through the planning process collaboratively.

## Benefits

-   **Integrated Communication Hub**

    Provides a centralized platform to gather and address feedback, ensuring all stakeholders can contribute insights and suggestions during planning.

-   **Enhanced Collaboration**

    Enables teams to discuss underlying assumptions, clarifying the rationale behind forecasted numbers and ensuring data consumers are well-informed.

# Getting Started

## Prerequisites

1.  Import business performance planning visuals from AppSource. Learn More.
2.  Connect PowerBI to your Dataverse environment. Learn More.
3.  Before initiating the use of the Comments Visual, prepare Sample Comment like **Test Comment** to a relevant data cell.

## Installation Guide

1.  Open Power BI: Launch the Power BI application and access your desired workspace or report where you intend to configure the Matrix Planner.
2.  Position the visual: Drag the Matrix Planning visual and Comments visual to the report canvas.
3.  For the Matrix Planning visual, Drag the "Name" columns from each dimension into the respective fields in the Visualization pane
4.  For the Comments Visual, drag the **Comment** field from your cube into the Comments parameter.
5.  Maintain Consistent Filter Context: Apply the same filter context (slicers) used in the Matrix Planner to the Comments Visual. This ensures alignment of data between both visuals.
6.  Add your **API Base URL** and **Cube name** to the API Details window of the visual and optionally a **Status Dimension Name** if you want to only allow selection of the items in the dimension that you have specified.
7.  Reviewing Comments: Upon completion, the Comments Visual will display comments in a tabular format within the data.

## Compatibility

Info on PBI versions where the visual is compatible.

# Using the Visual

## Functionality

-   **Collating Comments at Cell Level**

    Aggregates and displays comments tied to specific "cell" or pivot coordinates within the data.

-   **Facilitating Comment Management**

    Offers a tabular view to manage and work through comments during the planning phase.

-   **Ensuring Data Consistency**

    Requires matching filter contexts to maintain consistency between the Comments Visual and Matrix Planner, ensuring examination of the same dataset.

## Configuration Options

-   **Pivot Property**

    If you add one of the dimensions to the **Pivot** section of the visual, the values of that dimension will appear on the columns rather than rows.

-   **Filter Property**

    If you have a slicer somewhere on the page, and you want to pass the filtered values from the slicer to the comments visual, you need to do this explicitly by using the filters section of the visual. Power BI slicer values are not transferred automatically to the visual. For example, if **DimOrganization** is a slicer on the page, In order to get this filter's selected value to transfer to the comments visual, you need to add this field to the **Filter** section of the comments visual.

-   **Editing Amounts**

    It is possible to edit the amount related to the coordinate in the visual by activating this option in the properties.

-   **Entering comments directly in the Matrix planning visual**

    It is possible to enter comments directly in the Matrix planning visual without the need for the additional Comment Visual.
