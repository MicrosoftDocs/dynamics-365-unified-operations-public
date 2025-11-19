---
title: Create a cube from Excel 
description: Learn how to create planning cubes in Business performance planning by importing Excel files using the Data model builder (preview) experience.
author: twheeloc
ms.author: romainpham
ms.topic: how-to
ms.date: 11/23/2025
ms.reviewer: twheeloc
ms.collection: get-started
---

# Create a cube from Excel

> [!NOTE]
> This article describes the **Data model builder (preview)** experience. The existing **Cubes** page is still available. For information about classic cube creation, see [Create a cube](create-cubes.md)

## Create a cube 

You can create a new cube by importing one or several Excel files that contain fact and dimension data. Business performance planning automatically detects all worksheets in your uploaded files and guides you to tag, validate, and preview the resulting planning model.

 - The **Create cube from Excel** workflow currently supports creating one cube per iteration.
 - You can upload multiple Excel files at once. For example, one file containing the fact data and others containing related dimensions.
 - Across all uploaded files, you can tag only one table as the Fact.
 - All remaining tagged tables are treated as Dimensions.
 - Attempting to tag more than one fact table, from the same or different files, results in errors. Multiple fact tables introduce ambiguity in relationships within a single cube model.

### Choose data source
To select a data source, follow these steps:
1. Go to **Model > Cubes (preview)**, select **+ New cube**.
2. In the **Data source** step, choose **Excel workbook (.xlsx)** as your source.  
Other options include **Business performance planning dimensions** and **Import cube (JSON)**.

### Upload Excel files
Upload one or more Excel files that contain the fact and dimension data for your model. You can select additional files later by choosing **+ Add new files**. Each file is validated and displayed in the list of uploaded files.

### Select sheets
Business performance planning automatically lists all the worksheets or named tables detected in your uploaded Excel files.  
Select the sheets you want to include in your model.  
Each selected sheet appears as a table in the next step.

### Tag table types
In this step, assign each selected table as either a **Fact** or **Dimension**.
- You must tag at least one table as the **Fact**.  
- Once you tag a table as **Fact**, all other tables are automatically tagged as **Dimensions**.  
- If you tag **Dimensions** first, the system won’t automatically tag any table as **Fact**. You’ll need to select one manually.
- After the **Fact** is tagged, all tables appear in the **Preview** pane, showing the detected relationships between them.

> [!TIP]
> Business performance planning validates that one fact table is tagged. If not, you'll receive a **Tag at least one table as Fact** error.


### Set relationships
Relationships are detected between the fact table and dimensions based on matching sheet names or matching column names.  

For example:
- If a dimension sheet is named **Customer** and the fact table has a column named **Customer**, the relationship is automatically recognized.  
- If both tables share a column with the same name, such as *Cust_ID*, Business performance planning automatically creates the join.

If a relationship isn’t automatically detected, you can manually map the columns in the **Set relationships** pane. All fact columns must be mapped to a dimension to proceed.

### Confirm drivers
Business performance planning scans the **Fact** table columns to detect potential drivers columns that contain numeric values. These are automatically preselected as drivers.
- You can deselect any detected driver using the dropdown list.  
- At this stage, you can’t add new drivers that don’t exist in the file. Additional drivers can be added later after the cube draft is created.


### Review and create draft
The **Review** page summarizes the configuration and you can rename the cube or delete drivers before proceeding.  
Select **Create** to generate a **Draft** cube that appears under **Draft** in the left-hand panel.

### Refine the draft cube
In **Draft** mode, your cube opens in the **Data Model view**, displaying the relationships between your fact and dimension tables.  

You can:
- Add or delete drivers  
- Add or delete dimensions from existing Business performance planning dimensions, additional Excel files, or manually configured ones.  
- Enable or disable optional features under **Properties > Advanced**:   
  - **Audit** - Records write-back and user changes.  
  - **Non-Clustered Columnstore Index** - Improves performance for large datasets.

The Excel upload creates the schema of the cube. No data is imported at this stage. To load actual data into the cube, use [Dataflows](load-data-dataflows.md) after publishing.
When your model structure is finalized, select **Publish**.

### Publish and add data
Publishing converts the cube schema into physical Dataverse tables and relationships to use in planning and analytics.  
The cube status updates to **Published** and you can: 
- Load fact data using **Dataflows**.  
- Create calculated columns using the Dataverse formula column engine.   
- Connect your cube to Power BI or Excel for real-time write-back planning.

> [!IMPORTANT]
> Calculated columns and data are available after the cube is published.

### Known limitations (preview)

The following limitations currently apply to Create a cube from Excel:
- Published dimensions can’t be modified directly in Cube (preview) - After a cube is published, you can’t add or remove columns within a dimension from the Cube (preview) workspace.
- Changes made to dimensions outside the Cube (preview) experience aren’t reflected in the model view - If you update a dimension, for example, by adding or deleting columns, in the **Dimensions** area of the Business performance planning or in the **Power Apps maker portal**, those updates won’t appear in the Cube (preview). These changes are still applied at the Dataverse level, the updated structure and data remain available in Power BI and Excel reports connected to the same environment.
- Numeric dimension values in Excel may be incorrectly detected as drivers - During cube creation from Excel files, if a column in the fact table that should represent a dimension. For example, *CustomerID* or *DepartmentCode*, contains only numeric values, it’s automatically detected as a driver instead of a dimension. This causes the intended dimension to appear disconnected from the fact table in the model view.

To workaround this issues, follow these steps:  
  1. Create a cube until the Draft cube is created.  
  2. In the **Properties** pane, ensure the column isn't marked as a driver.  
  3. Delete the disconnected dimension from the cube.  
  4. Save the draft.  
  5. In **Properties**, select **+ Add new > New > Excel workbook**, and readd the same dimension.  
  6. You can now link it correctly to the fact table.

- Dimensions created from Excel uploads automatically generates a **Name** column as the primary key - When creating dimensions through Excel uploads, each new dimension automatically includes a **Name** column, which becomes the primary key for that dimension. You can’t currently select an existing column to serve as the primary key. This behavior will be updated in a future release to allow users to define which column acts as the primary key during creation.


### Next steps

- [Create a cube from existing dimensions](BPP-cub-dim.md)  
- [Create a cube from JSON](bpp-json.md)  
- [Load data using dataflows](load-data-dataflows.md)  
- [Create calculated columns](create-calculated-columns.md)


