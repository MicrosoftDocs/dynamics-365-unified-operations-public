---
title: Custom drivers in Dynamics 365 Finance business performance planning
description: This article describes how to define and use custom drivers in business performance planning.
author: ShielaSogge
ms.author: romainpham
ms.topic: how-to
ms.date: 06/11/2025
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-12-03
ms.search.form: 
ms.dyn365.ops.version: 
---


# Custom drivers in Dynamics 365 Finance business performance planning
This article describes how to extend a planning cube with additional drivers—such as Price, Quantity, or Discount—in addition to the default Amount driver, to support more granular or driver-based planning logic.

## Overview
Business performance planning enables planners to perform driver-based modeling directly within planning cubes. In addition to the default **Amount** driver, you can define additional drivers like **Quantity**, 
**Price**, **Discount**, or other user-defined inputs at the cube creation stage. These drivers support flexible allocation, and downstream calculations using the calculated column and DAX measures.

### Prerequisites
•	You must have access to Business performance planning in Dynamics 365 Finance.
•	You must have appropriate security roles to create cubes and upload data.

### Add additional drivers
To add additional drivers, follow these steps:
1.	In Business performance planning, go to **Cubes**.
2.	Select **+ New cube**.
3.	Select relevant dimensions. For example, **Product**, **Region**, or **Channel**.
4.	In the driver section, add drivers.
5.	Enter driver names separated by commas. For example, **Profit**, **Loss**, or **Margin**.
   o	If left blank, **Amount driver** is added by default.
6. Click **+ Add driver** to add other drivers:
 - **Quantity**
 - **Price**
 - **Discount**
 - **Headcount**
 
Each driver appears as a separate editable column in the cube and available for formulas.

>[!Tip]
> Each driver must be defined before you upload data into the cube. After data is loaded, driver structure is locked.

### Write-back from Power BI and Excel
All drivers created in a cube, including the default **Amount** driver and any custom drivers like **Price**, **Quantity**, or **Discount** can be edited directly in supported write-back experiences:
 - Power BI Table Edit visual, matrix visual, graphical planning visual, and variance visuals
 - Excel using the BPP Excel Add-in

This enables planners to:
•	Enter values directly into the driver fields
•	Update planning scenarios interactively
•	Trigger allocation when values are entered at an aggregated level
•	Trigger real-time recalculations through computed columns
Unlike computed columns, driver fields are fully editable and user-controlled through these write-back surfaces.

### Limitations
•	 You can't add or remove drivers after data is uploaded into the cube.
•	 You can reference any defined driver, within the same cube, in a computed column after the cube is created.

### Example 

If you want to calculate revenue as Price * Quantity, follow these steps:
1. Add **Price** and **Quantity** drivers.
2. Create a computed column:  Revenue = Price * Quantity.

For more information, see [Create calculated columns]
