---
title: Create a cube from JSON (preview)
description: Learn how to create planning cubes by importing a JSON cube schema using the Data model builder (preview) experience in Business performance planning.
author: ShielaSogge
ms.author: romainpham
ms.topic: how-to
ms.date: 11/25/2025
ms.reviewer: twheeloc
ms.collection: get-started
---

# Create a cube from JSON (preview)

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

> [!NOTE]
> This article describes the **Data model builder (preview)** experience. The existing **Cubes** page is still available. For information about classic cube creation, see [Create a cube](create-cubes.md).

## Overview

The **Create cube from JSON (preview)** feature allows you to import a complete cube definition—including facts, dimensions, relationships, and drivers—from a preconfigured JSON file.  
This option is ideal for partners, consultants, or administrators who need to deploy or migrate predefined planning models across Business performance planning environments.

Unlike the Excel or dimension-based workflows, the JSON import defines the entire cube schema in a single step—making it especially efficient for template deployment or environment setup.

For more information about cubes, facts, dimensions, or drivers, see [Cubes (preview)](bpp-create-cubes.md#key-concepts) for an overview of how cubes are structured and used in Business performance planning.

### Create a cube from JSON

The first step is to select a data source that lets you:

- Import a cube definition previously exported from another environment using the **Import and export cubes and dimensions** feature.  
- Deploy standardized planning templates across tenants or environments.  
- Restore cubes from backup configurations.

To create a cube from a JSON file, follow these steps:

1. Go to **Model > Cubes (preview)**, select **+ New cube**.
1. In the **Data source** step, choose **Import cube (JSON)**.

### Upload JSON file

Upload your JSON file by dragging it into the upload box or selecting **Browse files**.

After upload, Business performance planning validates the file and checks that it contains a valid cube structure—including:

- One fact table definition  
- One or more dimension definitions  
- Relationship mappings  
- Driver and column definitions  

> [!NOTE]
> The **Data model builder (preview)** currently supports importing only one cube per JSON file. If the uploaded file contains multiple cubes, an error message is displayed:  
> **Error parsing JSON: Multiple cubes import isn't supported. Upload one cube at a time.**

Once validated, a live preview of your cube model appears on the right-hand pane.

### Review imported structure

The **Review** page summarizes the cube configuration extracted from the JSON file and displays:

- The cube name and its associated Dataverse table name  
- Drivers (numeric columns)
- Calculated columns   
- Fact table  
- Dimensions and detected relationships  

The only editable property is the cube name. All other elements, drivers, relationships, and dimensions, are imported directly from the JSON file and can't be modified until the cube is created in draft mode.

> [!TIP]
> If a validation errors appear, check that all referenced dimensions exist in your environment or update the JSON to use valid dimension names.

### Create draft cube

Select **Create** to generate the cube in **Draft** mode.  
In the **Data model view**, you can now edit the structure:

- Rename cube
- Rename, add or delete drivers  
- Rename, add or delete dimensions (from existing Business performance planning dimensions, Excel files, or manually created dimensions)  
- Enable or disable features under **Properties > Advanced**:  
  - **Audit** - track write-back and user changes  
  - **Non-Clustered Columnstore Index (NCCI)** - improves performance for large datasets  

The JSON import creates only the cube schema, no data is imported. To load data into your cube, use [Dataflows](load-data-dataflows.md) after publishing.  
When satisfied with the structure, select **Publish**.

### Publish the cube

Publishing the cube converts the imported cube schema into physical **Dataverse** tables and relationships. The cube status is **Published**, and becomes available for analytics, planning, and write-back in Power BI or Excel.

After the cube is published, you can:

- Load fact data using Dataflows.  
- Define calculated columns using the Dataverse formula column engine  
- Connect your cube to Power BI or Excel for data entry and scenario planning

> [!IMPORTANT]
> Computed columns and data import become available only after the cube has been published.

## Example JSON file

Here’s a valid example of a cube definition JSON file that can be imported through this workflow:

```json
{
  "Tables": [
    {
      "LogicalName": "msdyn_xpnadim_company",
      "DisplayName": "Company",
      "PrimaryColumnName": "msdyn_name",
      "IsDimension": true,
      "Columns": [
        { "LogicalName": "msdyn_description", "DisplayName": "Description", "DataType": "StringType" },
        { "LogicalName": "msdyn_name", "DisplayName": "Name", "DataType": "StringType" }
      ]
    },
    {
      "LogicalName": "msdyn_xpnadim_department",
      "DisplayName": "Department",
      "PrimaryColumnName": "msdyn_name",
      "IsDimension": true,
      "Columns": [
        { "LogicalName": "msdyn_description", "DisplayName": "Description", "DataType": "StringType" },
        { "LogicalName": "msdyn_name", "DisplayName": "Name", "DataType": "StringType" }
      ]
    },
    {
      "LogicalName": "msdyn_xpnadim_account",
      "DisplayName": "Account",
      "PrimaryColumnName": "msdyn_name",
      "IsDimension": true,
      "Columns": [
        { "LogicalName": "msdyn_accounttype", "DisplayName": "Account type", "DataType": "StringType" },
        { "LogicalName": "msdyn_pnlcategory", "DisplayName": "PnL category", "DataType": "StringType" },
        { "LogicalName": "msdyn_name", "DisplayName": "Name", "DataType": "StringType" }
      ]
    },
    {
      "LogicalName": "msdyn_xpnacube_contosofinancials",
      "DisplayName": "ContosoFinancials",
      "PrimaryColumnName": "msdyn_xpnacube_contosofinancials_name",
      "IsDimension": false,
      "Columns": [
        {
          "LogicalName": "msdyn_amount",
          "DisplayName": "Amount",
          "DataType": "DecimalType",
          "Options": { "Precision": 2, "MinValue": -100000000000, "MaxValue": 100000000000 }
        }
      ]
    }
  ],
  "Relations": [
    { "ReferencingTableName": "msdyn_xpnacube_contosofinancials", "RelatedTableName": "msdyn_xpnadim_company" },
    { "ReferencingTableName": "msdyn_xpnacube_contosofinancials", "RelatedTableName": "msdyn_xpnadim_department" },
    { "ReferencingTableName": "msdyn_xpnacube_contosofinancials", "RelatedTableName": "msdyn_xpnadim_account" }
  ]
}
```

## Known limitations (Preview)

The following limitations currently apply to Data model builder (preview):
- Published dimensions can’t be modified directly in the Cube (preview) interface - After a cube is published, you can’t add or remove columns within a dimension from the Cube (preview) workspace.
- Changes made to dimensions outside the Cube (preview) experience aren’t reflected in the model view - If you update a dimension, for example, by adding or deleting columns—in the **Dimensions** area of the Business performance planning app or in the **Power Apps maker portal**, those updates won’t currently appear in the Cube (preview) visual interface.

These changes are applied at the Dataverse level in which the updated structure and data remain available in Power BI and Excel reports connected to the same environment.

> [!NOTE]
> This limitation will be removed in an upcoming release. Future versions of the Data model builder will reflect dimension updates automatically in the Cube (preview) interface.

## Next steps

- [Create a cube from Excel (preview)](bpp-create-cubes.md)  
- [Create a cube from JSON (preview)](bpp-json.md)  
- [Load data using dataflows](load-data-dataflows.md)  
- [Create calculated columns](calculated-columns.md)

