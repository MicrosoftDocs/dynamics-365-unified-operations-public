Copy

# Introduction & Purpose

## Overview

Copy visual empowers you to effortlessly transfer baseline data, including actuals or forecasts, into new planning or forecasting scenarios. You have the flexibility to choose the level of detail during copying, allowing for precise scenario creation. For instance, easily copy data from previous year's actuals as the foundation for a new plan, whether it is a complete copy or with specific dimensional filters, such as copying data for a particular department or product.

## Benefits

-   **Time-saving Functionality**

    By utilizing this visual, users can expedite the creation of forecasts and budgets. It eliminates the need to manually build each forecast from scratch, enabling a more rapid and efficient planning process.

-   **Consistency and Accuracy**

    Ensures consistency between historical data and planned budgets by facilitating the transfer of specific data coordinates. This alignment ensures accuracy and coherence within the planning structure.

-   **Scenario Analysis Simplification**

    Allows the creation of diverse forecast scenarios by leveraging a base case. Users can build a foundational forecast and efficiently generate multiple variations by copying, thereby simplifying scenario analysis without starting anew for each permutation.

# Getting Started

## Prerequisites

1.  Import business performance planning visuals from AppSource. [Microsoft AppSource]([https://appsource.microsoft.com])  Learn more about importing visuals [Importing visuals](https://learn.microsoft.com/en-us/power-bi/developer/visuals/import-visual).
2.  Connect PowerBI to your Dataverse environment. [Connect to Dataverse using a Connector](https://learn.microsoft.com/en-us/power-apps/maker/data-platform/data-platform-powerbi-connector?tabs=Dataverse#connect-to-dataverse-using-a-connector) or [Use DirectQuery in Power BI Desktop](https://learn.microsoft.com/en-us/power-bi/connect-data/desktop-use-directquery)

[!Tip]  
It is recommended to connect using **Direct Query**.  When using direct query, after the cube is selected, there is an option to **Load selected tables**.  Selecting this option will auto-select any dimension tables that are used in the cube.

## Installation Guide

1.  Open Power BI: Launch the Power BI application and access your desired workspace or report where you intend to configure the visual.
2.  Ensure that the visual has been downloaded from AppSource.  See Pre-requisite step 1 above.  
3.  Position the visual: Drag the visual to the report canvas.
4.  Add your **API Base URL** and **Cube name** to the API Details window of the visual. This will provide business performance planning app the details it needs to read and write data from the Cube. To add the API details, select the **Format visual** tab in the report canvas.  The API base URL will be the Environment URL where planning has been installed.  The environment URL must be preceded by https://.  For example:  https://environment.d365.com.  Learn more [Find your environment and organization ID and name](https://learn.microsoft.com/en-us/power-platform/admin/determine-org-id-name)  Note:The visual must be selected in the report canvas for the Format visual tab to display.



# Using the Visual

## Functionality

### Copying Data

This custom visual enables copying data between different scenarios and models with the option to use any level of detail. For example, copying data from the previous quarter’s sales actuals as the basis for a new plan (upcoming quarter's sales forecast) based on the most recent quarter's "baseline”. You could build this either as a whole or with further dimension detail like only a particular cost center, product, etc.

Instead of creating forecasts from scratch, document assumptions about business evolution between quarters.

## Configuration example

-   **Defining Copy Criteria**
    -   Select a Cube from the drop list at the top of the visual
    -   Select the **Select** button
    -   Click the "**+**" sign at the top-right corner of the visual
    -   Configure fields for copy criteria, focusing on two dimensions.  For example:  Fiscal Quarter and Scenario.
-   **Scenario Configuration**

    Specify the settings below

    -   **Dimension** = Scenario.
    -   **Column** = Name.
    -   **From** = Actual.
    -   **To** = Forecast.
-   **Fiscal Quarter Configuration**

    Define the settings:

    -   **Dimension** = MonthYear.
    -   **Column** = Fiscal Quarter.
    -   **From** = FY2020 Q4.
    -   **To** = FY2021 Q4.
-   **Initiating Copy Process**

    Once configurations are set, click **Copy**
