---
title: Create a cube from Excel 
description: Learn how to create planning cubes in Business performance planning by importing Excel files using the Data model builder (preview) experience.
author: twheeloc
ms.author: romainpham
ms.topic: how-to
ms.date: 11/25/2025
ms.reviewer: twheeloc
ms.collection: get-started
---

# Create a cube from Excel

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

> [!NOTE]
> This article describes the **Data model builder (preview)** experience. The existing **Cubes** page is still available. For information about classic cube creation, see [Create a cube](create-cubes.md).

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
1. In the **Data source** step, choose **Excel workbook (.xlsx)** as your source.  
   Other options include **Business performance planning dimensions** and **Import cube (JSON)**.

### Upload Excel files

Upload one or more Excel files that contain the fact and dimension data for your model. You can select additional files later by choosing **+ Add new files**. Each file is validated and displayed in the list of uploaded files.

### Select sheets

Business performance planning automatically lists all the worksheets or named tables it detects in your uploaded Excel files.  
Select the sheets you want to include in your model.  
Each selected sheet appears as a table in the next step.

### Tag table types

In this step, assign each selected table as either a **Fact** or **Dimension**.

- You must tag at least one table as the **Fact**.  
- Once you tag a table as **Fact**, the system automatically tags all other tables as **Dimensions**.  
- If you tag **Dimensions** first, the system doesn't automatically tag any table as **Fact**. You need to select one manually.
- After you tag the **Fact**, the **Preview** pane shows all tables and the detected relationships between them.

Business performance planning validates that you tag one fact table. If you don't, you receive a **Tag at least one table as Fact** error.

### Set relationships

The system detects relationships between the fact table and dimensions based on matching sheet names or matching column names.  

For example:

- If a dimension sheet is named **Customer** and the fact table has a column named **Customer**, the system automatically recognizes the relationship.  
- If both tables share a column with the same name, such as *Cust_ID*, Business performance planning automatically creates the join.

If the system doesn't automatically detect a relationship, you can manually map the columns in the **Set relationships** pane. You must map all fact columns to a dimension to proceed.

### Confirm drivers

Business performance planning scans the **Fact** table columns to detect potential driver columns that contain numeric values. The system automatically preselects these columns as drivers.

- You can deselect any detected driver using the dropdown list.  
- At this stage, you can't add new drivers that don't exist in the file. You can add additional drivers later after you create the cube draft.

### Review and create draft

The **Review** page summarizes the configuration. You can rename the cube or delete drivers before proceeding.  
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
When you finalize your model structure, select **Publish**.

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

- You can't modify published dimensions directly in Cube (preview) - After you publish a cube, you can't add or remove columns within a dimension from the Cube (preview) workspace.
- Changes made to dimensions outside the Cube (preview) experience aren't reflected in the model view - If you update a dimension, for example, by adding or deleting columns, in the **Dimensions** area of the Business performance planning or in the **Power Apps maker portal**, those updates don't appear in the Cube (preview). These changes still apply at the Dataverse level, and the updated structure and data remain available in Power BI and Excel reports connected to the same environment.
- Numeric dimension values in Excel might be incorrectly detected as drivers - During cube creation from Excel files, if a column in the fact table that should represent a dimension, such as *CustomerID* or *DepartmentCode*, contains only numeric values, it's automatically detected as a driver instead of a dimension. This issue causes the intended dimension to appear disconnected from the fact table in the model view.

To workaround this issue, follow these steps:

  1. Create a cube until the Draft cube is created.  
  1. In the **Properties** pane, ensure the column isn't marked as a driver.  
  1. Delete the disconnected dimension from the cube.  
  1. Save the draft.  
  1. In **Properties**, select **+ Add new > New > Excel workbook**, and readd the same dimension.  
  1. You can now link it correctly to the fact table.

- Dimensions created from Excel uploads automatically generate a **Name** column as the primary key - When creating dimensions through Excel uploads, each new dimension automatically includes a **Name** column, which becomes the primary key for that dimension. You can't currently select an existing column to serve as the primary key. This behavior will be updated in a future release to allow users to define which column acts as the primary key during creation.

### Next steps

- [Create a cube from existing dimensions](BPP-cub-dim.md)  
- [Create a cube from JSON](bpp-json.md)  
- [Load data using dataflows](load-data-dataflows.md)  
- [Create calculated columns](calculated-columns.md)







