---
title: Create a cube from existing dimensions
description: Learn how to create planning cubes from existing Business performance planning dimensions using the Data model builder (preview) experience.
author: twheeloc
ms.author: romainpham
ms.topic: how-to
ms.date: 11/25/2025
ms.reviewer: twheeloc
ms.collection: get-started
---

# Create a cube from existing dimensions 

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

> [!NOTE]
> This article describes the **Data model builder (preview)** experience. The existing **Cubes** page is still available. For information about classic cube creation, see [Create a cube](create-cubes.md)


## Overview

In Business performance planning, administrators can now build planning models (cubes) using the new **Data model builder**. This experience replaces the step-by-step wizard in previous versions and introduces a more visual, model-first approach to designing, validating, and publishing planning models.

For more information about cubes, facts, dimensions, or drivers, see [Cubes (preview)](bpp-create-cubes.md) for an explanation of how cubes are structured and used in Business performance planning.


## Create and design a planning model
To create and design a cube, follow these steps:
1. In Business performance planning, go to **Model > Cubes (preview)** and select **+ New cube**.
You can create your planning model in the following ways:
- **Create from existing dimensions** - Select dimensions already defined in your Business performance planning environment.  
- **Upload Excel files** - Import data that contains both facts and dimensions.  
- **Import from JSON** - Import a full cube schema. For more information, see [Import and export cubes and dimensions](bpp-cubes-dim.md).


### Create a cube from existing Business performance planning dimensions

You can create a new cube from existing dimensions that are available in your environment. This method is ideal when your organization has master data defined in Dataverse. 
For example:
 - Account
 - Business unit
 - Currency
 - Date
 - Department
 - Scenario

### Start a new cube
To create a new cube, follow these steps:
1. On the **Cubes (Preview)** page, select **+ New cube**.
2. Select **Business performance planning dimensions**.
The **Data model builder** opens to help with:
 - Data source selection  
 - Cube name - Enter a name for the cube. Select the check mark in the input box to validate the name. As you validate, a draft Dataverse table name is automatically generated. The right panel shows a live preview of your model. It's initially a single node representing the cube and its write-back table.  
 - Dimensions - Search previously created Business performance planning dimensions in your environment. When you select each dimension, it automatically appears in the model preview pane, displaying relationships between facts and dimensions. You can add or remove dimensions while the cube is in **Draft** mode. 
 - Drivers - Drivers appear as a numeric column in the cube’s fact table, are the core inputs of your planning model, and can be directly written back from Power BI **Matrix Planning visuals** or from Excel.  

In this cube creation, the cube only defines its structure. Data, calculated columns, and advanced logic are added after the cube is published, once the cube exists in Dataverse.

 - Review - The **Review** page summarizes your configuration. You can rename the cube and delete existing drivers or dimensions. Select **Create** to save your draft cube. In **Draft** mode, you can further refine the model by adding or removing drivers and dimensions before publishing.
 - Visualize and publish - After creation, your cube opens in the **Data Model View**, displaying all relationships between the cube, its dimensions, and drivers.  

In the **Properties** pane, you can:
- **Rename** the cube.  
- **Add or delete drivers**  
- **Add or delete dimensions** 
- Open the **Advanced** menu to view:   
  - **Audit** - Records write-back and user changes. For more information, see [Audit cubes](cube-audit.md) in Business performance planning.  
  - **Non-Clustered Columnstore Index** - improves query and load performance for large datasets.

When the structure is complete, select **Publish**. Publishing converts the cube schema into physical Dataverse tables and relationships, preparing it for data ingestion and computed logic.

### Add data and computed columns
After the cube is published:
1. Use **Dataflows** to load data into your cube.
2. In the **Properties** pane, define calculated columns using the Dataverse formula column engine to create logic:  
  - *Revenue* = *Units Sold* × *Unit Price*  
  - *Gross Margin* = *Revenue* − *COGS*  
  - *FTE Cost* = *Headcount* × *Average Salary*  
These computed columns, together with editable drivers, enable driver-based planning and allocation logic across hierarchies.

> [!IMPORTANT]
> Data, calculated columns, and allocation logic are available after the cube is published.


#### Known limitations (preview)

The following limitations currently apply to the Data model builder (preview):
- Published dimensions can’t be modified directly in the Cube (preview) interface - After a cube is published, you can’t add or remove columns within a dimension from the Cube (preview) workspace.
- Changes made to dimensions outside the Cube (preview) workspace aren’t reflected in the model view. If you update a dimension, for example, by adding or deleting columns in the **Dimensions** area of the Business performance planning or in the **Power Apps maker portal**, those updates won’t appear in the Cube (preview) visual interface. However, these changes are still applied at the Dataverse level and the updated structure and data is available in Power BI and Excel reports connected to the same environment.


### Next steps

- [Create a cube from Excel](bpp-cube-Excel.md)  
- [Create a cube from JSON](bpp-json.md)  
- [Load data using dataflows](load-data-dataflows.md)  
- [Create calculated columns](calculated-columns.md)







