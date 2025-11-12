---
title: Create a cube from JSON (Preview)
description: Learn how to create planning cubes by importing a JSON cube schema using the Data Model Builder (Preview) experience in Business Performance Planning.
author: romainpham
ms.author: romainpham
ms.topic: how-to
ms.date: 10/23/2025
ms.reviewer: tammywheelock
ms.collection: get-started
---

# Create a cube from JSON (Preview)

> [!IMPORTANT]
> This article describes the **Data Model Builder (Preview)** experience, available under **Cubes (Preview)** in the **Business Performance Planning** navigation pane.  
> The existing **Cubes** page remains available for backward compatibility until migration to the new experience is complete.  
> To use the classic cube creation flow, see [Create a cube (Classic)](create-cubes.md).

---

## Overview

The **Create cube from JSON (Preview)** feature allows you to import a complete cube definition—including facts, dimensions, relationships, and drivers—from a preconfigured JSON file.  
This option is ideal for partners, consultants, or administrators who need to **deploy or migrate predefined planning models** across Business Performance Planning (BPP) environments.

Unlike the Excel or dimension-based workflows, the JSON import defines the entire cube schema in a single step—making it especially efficient for template deployment or environment setup.

> [!TIP]
> If you're new to cubes, facts, dimensions, or drivers, see [Key concepts in cube design](creating-cubes-preview.md#key-concepts) for an overview of how cubes are structured and used in Business Performance Planning.

---

## Create a cube from JSON

### Step 1: Choose data source

From **Model > Cubes (Preview)**, select **+ New cube**.  
In the **Data source** step, choose **Import cube (JSON)**.

This option lets you:
- Import a cube definition previously exported from another environment using the **Import and export cubes and dimensions** feature.  
- Deploy standardized planning templates across tenants or environments.  
- Restore cubes from backup configurations.

---

### Step 2: Upload JSON file

Upload your JSON file by dragging it into the upload box or selecting **Browse files**.

After upload, BPP validates the file and checks that it contains a valid cube structure—including:
- One **fact table** definition  
- One or more **dimension definitions**  
- Relationship mappings  
- Driver and column definitions  

> [!NOTE]
> The **Data Model Builder (Preview)** currently supports importing **only one cube per JSON file**.  
> If the uploaded file contains multiple cubes, the system displays an error message:  
> **“Error parsing JSON: Multiple cubes import is not supported. Please try uploading one cube at a time.”**

Once validated, a live preview of your cube model appears on the right-hand pane.

---

### Step 3: Review imported structure

The **Review** page summarizes the cube configuration extracted from the JSON file.  
It displays:
- The cube name and its associated Dataverse table name  
- Drivers (numeric columns)
- Calculated columns (if any)  
- Fact table  
- Dimensions and detected relationships  

At this stage, the only editable property is the **cube name**.  
All other elements—drivers, relationships, and dimensions—are imported directly from the JSON file and cannot be modified until the cube is created in draft mode.

> [!TIP]
> If validation errors appear, check that all referenced dimensions exist in your environment or update the JSON to use valid dimension names.

---

### Step 4: Create draft cube

Select **Create** to generate the cube in **Draft** mode.  
In the **Data Model View**, you can now edit the structure just like with other creation methods:

- Rename cube
- Rename, add or delete drivers  
- Rename, add or delete dimensions (from existing BPP dimensions, Excel files, or manually created dimensions)  
- Enable or disable features under **Properties > Advanced**, including:  
  - **Audit**, which tracks write-back and user changes  
  - **Non-Clustered Columnstore Index (NCCI)**, which improves performance for large datasets  

> [!NOTE]
> The JSON import creates only the **cube schema**—no data is imported.  
> To load data into your cube, use [Dataflows](load-data-into-bpp-using-dataflows.md) after publishing.

When satisfied with the structure, select **Publish**.

---

### Step 5: Publish the cube

Publishing converts the imported cube schema into physical **Dataverse** tables and relationships.  
The cube status updates to **Published**, and it becomes available for analytics, planning, and write-back in Power BI or Excel.

Once published, you can:
- Load fact data using **Dataflows**.  
- Define **calculated columns** using the Dataverse formula column engine—for example:  
  - *Revenue = Units Sold × Unit Price*  
  - *Gross Margin = Revenue − COGS*  
- Connect your cube to Power BI or Excel for data entry and scenario planning.

> [!IMPORTANT]
> Computed columns and data import become available only **after the cube has been published**.

---

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
---

## Known limitations (Preview)

The following limitations currently apply to the Data Model Builder (Cube Preview) experience:

- **Published dimensions can’t be modified directly in the Cube (Preview) interface.**  
  After a cube is published, you can’t add or remove columns within a dimension from the Cube (Preview) workspace.

- **Changes made to dimensions outside the Cube (Preview) experience aren’t reflected in the model view.**  
  If you update a dimension—for example, by adding or deleting columns—in the **Dimensions** area of the Business Performance Planning app or in the **Power Apps maker portal**, those updates won’t currently appear in the Cube (Preview) visual interface.

  However, these changes **are still applied at the Dataverse level**.  
  This means the updated structure and data **remain available in Power BI and Excel** reports connected to the same environment.

> [!NOTE]
> This limitation will be removed in an upcoming release. Future versions of the Data Model Builder will reflect dimension updates automatically in the Cube (Preview) interface.

---

## Next steps

- [Create a cube from Excel (Preview)](create-cube-from-excel-preview.md)  
- [Create a cube from JSON (Preview)](create-cube-from-json-preview.md)  
- [Load data using dataflows](load-data-into-bpp-using-dataflows.md)  
- [Create calculated columns](create-calculated-columns.md)
