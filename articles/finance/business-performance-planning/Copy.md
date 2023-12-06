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

1.  Import business performance planning visuals from AppSource. Learn More.
2.  Connect PowerBI to your Dataverse environment. Learn More.
3.  Understanding Allocation. Learn More.
4.  

## Installation Guide

1.  Open Power BI: Launch the Power BI application and access your desired workspace or report where you intend to configure the Matrix Planner.
2.  Position the visual: Drag the Copy visual to the report canvas.
3.  Add your **API Base URL** and **Cube name** to the API Details window of the visual. This will provide business performance planning app the details it needs to read and write data from the Cube.

## Compatibility

Info on PBI versions where the visual is compatible.

# Using the Visual

## Functionality

### Copying Data

This custom visual enables copying data between different scenarios and models with the option to use any level of detail. For example, copying data from the previous quarter’s sales actuals as the basis for a new plan (upcoming quarter's sales forecast) based on the most recent quarter's "baseline”. You could build this either as a whole or with further dimension detail like only a particular cost center, product, etc.

Instead of creating forecasts from scratch, document assumptions about business evolution between quarters.

## Configuration options

-   **Defining Copy Criteria**
    -   Click the "**+**" sign at the top-right corner of the Copy Wizard.
    -   Configure fields for copy criteria, focusing on two dimensions: Fiscal Quarter and Scenario.
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
