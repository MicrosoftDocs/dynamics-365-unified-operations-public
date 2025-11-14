---
title: Create a cube from Excel (Preview)
description: Learn how to create planning cubes in Business performance planning by importing Excel files using the Data model builder (preview) experience.
author: romainpham
ms.author: romainpham
ms.topic: how-to
ms.date: 11/23/2025
ms.reviewer: twheeloc
ms.collection: get-started
---

# Create a cube from Excel (Preview)

> [!IMPORTANT]
> This article describes the **Data model builder (preview)** experience, available under **Cubes (preview)** in the Business performance planning navigation pane.  
> The existing **Cubes** page remains available for backward compatibility until migration to the new experience is complete.  
> To use the classic cube creation flow, see [Create a cube (Classic)](create-cubes.md).

---

## Create a cube from Excel

You can create a new cube by importing one or several Excel files that contain fact and dimension data. Business performance planning automatically detects all worksheets in your uploaded files and guides you to tag, validate, and preview the resulting planning model.

 - The **Create cube from Excel** workflow currently supports creating one cube per iteration.
 - You can upload multiple Excel files at once. For example, one file containing the fact data and others containing related dimensions.
 - Across all uploaded files, you can tag only one table as the Fact.
 - All remaining tagged tables are treated as Dimensions.
 - Attempting to tag more than one fact table (from the same or different files) results in errors, because multiple fact tables introduce ambiguity in relationships within a single cube model.

### Choose data source
From **Model > Cubes (Preview)**, select **+ New cube**.  
In the **Data source** step, choose **Excel workbook (.xlsx)** as your source.  
Other options include **Business performance planning dimensions** and **Import cube (JSON)**.

### Upload Excel files
Upload one or more Excel files that contain the fact and dimension data for your model. You can select additional files later by choosing **+ Add new files**.  
Each file is validated and displayed in the list of uploaded files.

### Select sheets
Business performance planning automatically lists all the worksheets or named tables detected in your uploaded Excel files.  
Select the sheets you want to include in your model.  
Each selected sheet appears as a table in the next step.

### Tag table types
In this step, assign each selected table as either a **Fact** or **Dimension**.
- You must tag at least one table as the Fact.  
- Once you tag a table as Fact, all other tables are automatically tagged as Dimensions.  
- If you tag Dimensions first, the system won’t automatically tag any table as Fact. You’ll need to select one manually.
- After the Fact is tagged, all tables appear in the **Preview** pane, showing the detected relationships between them.

> [!TIP]
> Business performance planning validates that you’ve tagged one fact table. If not, an error such as *Tag at least one table as Fact* appears.

---

### Set relationships
The system detects relationships between the fact table and dimensions based on matching sheet names or matching column names.  

For example:
- If a dimension sheet is named Customer and the fact table has a column named Customer, the relationship is automatically recognized.  
- If both tables share a column with the same name, such as *Cust_ID*, Business performance planning automatically creates the join.

If a relationship isn’t automatically detected, you can manually map the columns in the **Set relationships** pane.

> [!TIP]
> All fact columns must be mapped to a dimension to proceed.

### Confirm drivers
Business performance planning scans the columns in the Fact table to detect potential drivers columns that contain numeric values. These are automatically preselected as drivers.

- You can deselect any detected driver using the dropdown list.  
- At this stage, you can’t add new drivers that don’t exist in the file. Additional drivers can be added later once the cube draft is created.

Drivers are numeric columns that will be editable in Power BI or Excel for planning input.

### Review and create draft
The **Review** page summarizes the configuration:
- Cube name  
- Selected fact table  
- Dimensions  
- Drivers  

You can rename the cube or delete drivers before proceeding.  
Select **Create** to generate a **Draft** cube.
The cube now appears under **Draft** in the left-hand panel.

### Refine the draft cube
In **Draft** mode, your cube opens in the **Data Model View**, displaying the relationships between your fact and dimension tables.  

You can:
- Add or delete drivers.  
- Add or delete dimensions (from existing Business performance planning dimensions, additional Excel files, or manually configured ones).  
- Enable or disable optional features under **Properties > Advanced**, such as:  
  - **Audit**, which records write-back and user changes.  
  - **Non-Clustered Columnstore Index (NCCI)**, which improves performance for large datasets.

> [!NOTE]
> The Excel upload creates only the **schema** of the cube—no data is imported at this stage.  
> To load actual data into the cube, use [Dataflows](load-data-into-bpp-using-dataflows.md) after publishing.

When your model structure is finalized, select **Publish**.

### Publish and add data
Publishing converts the cube schema into physical Dataverse tables and relationships to use in planning and analytics.  
The cube status updates to **Published** in the navigation pane.

Once published, you can:
- Load fact data using **Dataflows**.  
- Create calculated columns using the Dataverse formula column engine.   
- Connect your cube to Power BI or Excel for real-time write-back planning.

> [!IMPORTANT]
> Calculated columns and data become available after the cube is published.

### Known limitations (preview)

The following limitations currently apply to the Data model builder Create a cube from Excel (preview) experience:
- Published dimensions can’t be modified directly in the Cube (preview) interface - After a cube is published, you can’t add or remove columns within a dimension from the Cube (preview) workspace.
- Changes made to dimensions outside the Cube (preview) experience aren’t reflected in the model view - If you update a dimension, for example, by adding or deleting columns, in the **Dimensions** area of the Business performance planning or in the **Power Apps maker portal**, those updates won’t currently appear in the Cube (preview) visual interface.
However, these changes are still applied at the Dataverse level, the updated structure and data remain available in Power BI and Excel reports connected to the same environment.
- Numeric dimension values in Excel may be incorrectly detected as drivers - During cube creation from Excel files, if a column in the fact table that should represent a dimension (for example, *CustomerID* or *DepartmentCode*) contains only numeric values, it’s automatically detected as a driver instead of a dimension. This causes the intended dimension to appear disconnected from the fact table in the model view.

To workaround this issues, follow these steps:  
  1. Proceed with the cube creation until the Draft cube is created.  
  2. In the **Properties** pane, ensure the column isn't marked as a driver.  
  3. Delete the disconnected dimension from the cube.  
  4. Save the draft.  
  5. In **Properties**, select **+ Add new > New > Excel workbook**, and re-add the same dimension.  
  6. The system now allows you to link it correctly to the fact table.

- Dimensions created from Excel uploads automatically generate a “Name” column as the primary key - When creating dimensions through Excel uploads, each new dimension automatically includes a system-generated **Name** column, which becomes the primary key for that dimension. Unlike the legacy experience, you can’t currently select an existing column to serve as the primary key. This behavior will be updated in a future release to allow users to define which column acts as the primary key during creation.

This limitation will be removed in an upcoming release. Future versions of the Data model builder will: 
 - Reflect dimension updates automatically in the Cube (preview) interface
 - Automatically detect numeric dimension identifiers
 - The Excel upload flow will support user-defined primary key columns

## Next steps

- [Create a cube from existing dimensions (preview)](create-cube-from-existing-dimensions-preview.md)  
- [Create a cube from JSON (preview)](create-cube-from-json-preview.md)  
- [Load data using dataflows](load-data-into-bpp-using-dataflows.md)  
- [Create calculated columns](create-calculated-columns.md)

