---
title: Create a cube from existing dimensions (Preview)
description: Learn how to create planning cubes from existing Business performance planning dimensions using the Data model builder (preview) experience.
author: romainpham
ms.author: romainpham
ms.topic: how-to
ms.date: 11/23/2025
ms.reviewer: twheeloc
ms.collection: get-started
---

# Create a cube from existing dimensions (Preview)

> [!IMPORTANT]
> This article describes the **Data Model Builder (Preview)** experience, available under **Cubes (Preview)** in the Business performance planning navigation pane.  
> The existing **Cubes** page remains available for backward compatibility until migration to the new experience is complete.  
> To use the classic cube creation flow, see [Create a cube (Classic)](create-cubes.md).

---

## Overview

In Business performance planning, administrators can now build planning models—also called *cubes*—in just a few clicks by using the new **Data Model Builder**. This experience replaces the step-by-step wizard used in previous versions and introduces a more visual, model-first approach to designing, validating, and publishing planning models.

For more information about cubes, facts, dimensions, or drivers, see [Key concepts in Creating cube overview](creating-cubes-preview.md#key-concepts) for an explanation of how cubes are structured and used in Business performance planning.

---

## Create and design a planning model

In Business performance planning, go to **Model > Cubes (Preview)** and select **+ New cube**.

You can create your planning model in one of three ways:

- **Create from existing dimensions:** Select dimensions already defined in your BPP environment.  
- **Upload Excel files:** Import data that contains both facts and dimensions.  
- **Import from JSON:** Import a full cube schema. For more information, see [Import and export cubes and dimensions](import-export-cubes-dimensions.md).

---

## Create a cube from existing Business performance planning dimensions

You can create a new cube from existing dimensions already available in your environment.  
This method is ideal when your organization already has master data defined in Dataverse (for example, *Account*, *Business unit*, *Currency*, *Date*, *Department*, *Scenario*).

### Start a new cube
From the **Cubes (Preview)** page, select **+ New cube**, and then choose **Business performance planning Dimensions**.

The system opens the **Data Model Builder** wizard, which guides you through five steps:

1. Data source selection  
2. Cube name  
3. Dimensions  
4. Drivers  
5. Review and publish  

### Name your cube
Enter a name for the cube (for example, *OPEX Plan*), and then select the check mark in the input box to validate the name.  
As you validate, the system automatically generates a draft Dataverse table name (for example, `msdyn_xpnacube_opexplan`).

The right panel shows a live preview of your model—initially a single node representing the cube and its write-back table.

### Choose dimensions
Next, select the dimensions to include in your cube.  
You can search or scroll through all previously created Business performance planning dimensions in your environment.  
Common examples include *Account*, *Business unit*, *Currency*, *Date*, and *Department*.

As you select each dimension, it automatically appears in the model preview pane.  
This lets you instantly see how your planning model takes shape, including relationships between facts and dimensions.

> [!TIP]
> You can add or remove dimensions anytime while the cube is in **Draft** mode, before publishing.

### Add drivers
Drivers represent the **numeric values** that can be entered or adjusted by users in planning reports.  
They are the core inputs of your planning model—such as *Amount*, *Target*, *Headcount*, or *Units Sold*.

Each driver appears as a numeric column in the cube’s fact table and can be directly written back from Power BI **Matrix Planning visuals** or from Excel.

Select **+ Add new** to define one or more drivers.  
Each driver is displayed as a column in the fact table within the cube structure.

> [!NOTE]
> In this creation flow, the cube only defines its **structure**.  
> Data, calculated columns, and advanced logic are added **after publication**, once the cube exists in Dataverse.


### Review your model
The **Review** page summarizes your configuration—showing the cube name, selected drivers, and dimensions.

At this stage, you can:
- Rename the cube.  
- Delete existing drivers or dimensions.  

After reviewing, select **Create** to save your draft cube.  
The cube appears under **Draft** in the left-hand panel.

Once in **Draft** mode, you can further refine the model by adding or removing drivers and dimensions before publishing.

### Visualize and publish
After creation, your cube opens in the **Data Model View**, displaying all relationships between the cube, its dimensions, and drivers.  
You can also preview the data existing in the dimensions used to create the cube.

In the **Properties** pane, you can:
- **Rename** the cube.  
- **Add or delete drivers.**  
- **Add or delete dimensions.** You can add dimensions from:  
  - Existing Business performance planning dimensions  
  - Excel files  
  - A new dimension that you manually configure from scratch  
- Open the **Advanced** menu to toggle additional features:  
  - **Audit**, which records write-back and user changes. For details, see [Audit cubes]((https://learn.microsoft.com/en-us/dynamics365/finance/business-performance-planning/cube-audit)) in Business performance planning.  
  - **Non-Clustered Columnstore Index**, which improves query and load performance for large datasets.

When the structure is complete, select **Publish**.  
Publishing converts the cube schema into physical Dataverse tables and relationships, preparing it for data ingestion and computed logic.

### Add data and computed columns
Once the cube is published:

- Use **Dataflows** to load data into your cube.  
- In the **Properties** pane, define calculated columns using the Dataverse formula column engine to create logic such as:  
  - *Revenue* = *Units Sold* × *Unit Price*  
  - *Gross Margin* = *Revenue* − *COGS*  
  - *FTE Cost* = *Headcount* × *Average Salary*  

These computed columns, together with editable drivers, enable driver-based planning and allocation logic across hierarchies.

> [!IMPORTANT]
> Data, calculated columns, and allocation logic become available only **after the cube is published**.


## Known limitations (Preview)

The following limitations currently apply to the Data model builder (preview) experience:
- Published dimensions can’t be modified directly in the Cube (Preview) interface - After a cube is published, you can’t add or remove columns within a dimension from the Cube (Preview) workspace.
- Changes made to dimensions outside the Cube (Preview) experience aren’t reflected in the model view - If you update a dimension—for example, by adding or deleting columns—in the **Dimensions** area of the Business performance planning or in the **Power Apps maker portal**, those updates won’t currently appear in the Cube (Preview) visual interface.

However, these changes **are still applied at the Dataverse level**. This means the updated structure and data remain available in Power BI and Excel reports connected to the same environment.

This limitation will be removed in an upcoming release. Future versions of the Data model builder will reflect dimension updates automatically in the Cube (Preview) interface.

### Next steps

- [Create a cube from Excel (Preview)](create-cube-from-excel-preview.md)  
- [Create a cube from JSON (Preview)](create-cube-from-json-preview.md)  
- [Load data using dataflows](load-data-into-bpp-using-dataflows.md)  
- [Create calculated columns](create-calculated-columns.md)


