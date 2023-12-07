---
# required metadata

title: Business performance planning application copy visual
description: This article describes how to use the copy visual in the Business performance planning application.
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
# Copy visual

This article describes how to use the copy visual in the Business performance planning application. You must also install Power BI visuals to fully use the planning application. To learn more about installing Power BI visuals, see [Power BI visuals](/power-bi/developer/visuals).

## Overview

Copy visual empowers you to effortlessly transfer baseline data, including actuals or forecasts, into new planning or forecasting scenarios. You have the flexibility to choose the level of detail during copying, allowing for precise scenario creation. For instance, easily copy data from previous year's actuals as the foundation for a new plan, whether it is a complete copy or with specific dimensional filters, such as copying data for a particular department or product.

## Benefits

 - Time-saving functionality - by utilizing this visual, users can expedite the creation of forecasts and budgets. It eliminates the need to manually build each forecast from scratch, enabling a more rapid and efficient planning process.
 - Consistency and accuracy - Ensures consistency between historical data and planned budgets by facilitating the transfer of specific data coordinates. This alignment ensures accuracy and coherence within the planning structure.
 - Scenario analysis simplification - Allows the creation of diverse forecast scenarios by leveraging a base case. Users can build a foundational forecast and efficiently generate multiple variations by copying, thereby simplifying scenario analysis without starting anew for each permutation.


## Prerequisites

1.  Import business performance planning visuals from AppSource. [Microsoft AppSource]([https://appsource.microsoft.com])  To learn more about importing visuals, see [Importing visuals](/power-bi/developer/visuals/import-visual).
2.  Connect PowerBI to your Dataverse environment. For more information, see [Connect to Dataverse using a connector](/power-apps/maker/data-platform/data-platform-powerbi-connector?tabs=Dataverse#connect-to-dataverse-using-a-connector) or [Use DirectQuery in Power BI Desktop](/power-bi/connect-data/desktop-use-directquery).

>[!Tip]
>It's recommended to connect using **Direct Query**. When using direct query, after the cube is selected, there's a **Load selected tables** option. Select this option will auto-select any dimension tables that are used in the cube.

### Installation 

1.  Launch the Power BI application and go to your workspace or enter where you're going to configure the visual.
2.  Ensure that the visual has been downloaded from AppSource. See prerequisite step 1 above.  
3.  Position the visual by dragging the visual to the report canvas.
4.  Add your **API base URL** and **Cube name** to the API details window of the visual. This provides business performance planning the details to read and write data from the cube.
5.  To add the API details, select the **Format visual** tab in the report canvas. The API base URL will be the environment URL where planning has been installed. The environment URL must be preceded by https://. For example:  https://environment.d365.com. For more information, see [Find your environment and organization ID and name](/power-platform/admin/determine-org-id-name).

>[!Note]T
>he visual must be selected in the report canvas for the format visual tab to display.

### Using the copy visual

This custom visual enables copying data between different scenarios and models with the option to use any level of detail. For example, copying data from the previous quarter’s sales actuals as the basis for a new plan (upcoming quarter's sales forecast) based on the most recent quarter's "baseline”. You could build this either as a whole or with further dimension detail like only a particular cost center, or product.

Instead of creating forecasts from scratch, users can use document assumptions about business evolution between quarters.

### Example

To define the copy criteria, follow these steps:
1. Select a cube from the drop list at the top of the visual.
2. Click **Select**.
3. Click **+** at the top-right corner of the visual to configure fields for copy criteria, focusing on two dimensions.  For example:  Fiscal quarter and Scenario.
4. Specify the settings below:
 - **Dimension** = Scenario
 - **Column** = Name
 - **From** = Actual
 - **To** = Forecast
5. Configure the fiscal quarter by defining the following settings:
  - **Dimension** = MonthYear
  - **Column** = Fiscal quarter
  - **From** = FY2020 Q4
  - **To** = FY2021 Q4
6. To start the copy process, after the configuration are complete, click **Copy**.
