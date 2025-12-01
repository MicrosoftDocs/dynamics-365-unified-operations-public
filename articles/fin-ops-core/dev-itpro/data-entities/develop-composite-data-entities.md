---
title: Develop composite data entities
description: Learn about composite entities, a concept that allows you to build a single entity by using multiple entities that are related to each other. 
author: johnmichalak
ms.author: johnmichalak
ms.topic: how-to
ms.date: 10/29/2025
ms.reviewer: johnmichalak
audience: Developer
ms.assetid: 1cb19868-cbfd-4f45-bc47-39b9f303583d
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: 
ms.dyn365.ops.version: AX 7.0.0
---

# Develop composite data entities

[!include [banner](../includes/banner.md)]

A composite entity is a concept that lets you build a single entity by using multiple entities that are related to each other.

## What is a composite entity?

A composite entity is a concept that allows you to build a single entity by using multiple entities that are related to each other. The concept is heavily used in scenarios where an entity can be represented as a single document, like Sales header/line, Invoice header/line, and Vendor Catalog. This concept is applicable in asynchronous integration scenarios rather than synchronous OData scenarios, and it's only supported from a data management platform. No programmatic interface for composite entities exists in X++. It's only supported for a data management platform that's part of XML file-based imports/exports.

## Example

Sales Header and Sales Line are two different entities in the system. If the customer requirement suggests that header and lines are part of a single document, then these two entities can be merged as a composite entity. Sample sales order entity: The composite entity (MySalesTableCompositeEntity) represents a sales order document, which is composed of Sales Order header entity (MySalesTableEntity) and Sales Order Line entity (MySalesTableLineEntity).

:::image type="content" source="./media/developingcompositeentities-17.png" alt-text="Screenshot of composite entity diagram showing MySalesTableCompositeEntity with MySalesTableEntity and MySalesTableLineEntity components.":::

Based on the linked entities, these entities can be exposed as an XML document with embedded element tags for entities. XML is the only way to expose a composite entity in data management.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Document>

<MySalesTableEntity SalesID="SO1" CurrencyCode="USD" CustAccount="Acc001">
<MySalesLineEntity SalesPrice="2.00" QtyOrdered="10.00" LineAmount="20.00" ItemId="1000" LineNum="1.00" SalesID="SO1"/>
<MySalesLineEntity SalesPrice="2.00" QtyOrdered="10.00" LineAmount="20.00" ItemId="4401" LineNum="2.00" SalesID="SO1"/>
</MySalesTableEntity>

<MySalesTableEntity SalesID="SO2" CurrencyCode="USD" CustAccount="Acc002">
<MySalesLineEntity SalesPrice="2.00" QtyOrdered="10.00" LineAmount="20.00" ItemId="4402" LineNum="1.00" SalesID="SO2"/>
</MySalesTableEntity>

</Document>
```

Each node in the XML represents attributes from an individual entity. For example - &lt;MySalesTableEntity SalesID="SO1" CurrencyCode="USD" CustAccount="Acc001"&gt; SalesId, CurrencyCode, and CustAccount are attributes from MySalesTableEntity.

## Building the composite entity

There's a node for composite data entities under **Data model**. Let's take the example of MySalesTableEntity.

### Step 1: Identify and create the individual entities for the composite entity

Ensure that the entities are related to each other. In this example, the individual entities are MySalesTableEntity and MySalesLineEntity.

### Step 2: Add relations between individual entities

Add a relation to parent entity in the **relations** node. Example – MySalesLineEntity has relationship to MySalesTableEntity.

:::image type="content" source="./media/developingcompositeentities-18.png" alt-text="Screenshot of entity relations configuration showing MySalesLineEntity relationship to MySalesTableEntity.":::

### Step 3: Create a new composite entity

1. Add a new **Dynamics 365** artifact item of type **Composite entity** to the project.
1. In designer mode, select the entity and choose **New Root Data Entity Reference**.

    :::image type="content" source="./media/developingcompositeentities-2.png" alt-text="Screenshot of composite entity designer context menu with New Root Data Entity Reference option highlighted.":::

1. Set the data entity to parent data entity. In this case, it's MySalesTableEntity.
1. Select the parent entity node and choose **New Embedded Data Entity Reference**.

    :::image type="content" source="./media/developingcompositeentities-3.png" alt-text="Screenshot of composite entity designer showing New Embedded Data Entity Reference option in context menu.":::

1. Set the embedded data entity as the child entity. In this case, it's MySalesLineEntity.
1. Set the **Relation** property from the dropdown list on the embedded data entity properties.

    :::image type="content" source="./media/developingcompositeentities-4.png" alt-text="Screenshot of embedded data entity properties panel showing Relation property dropdown configuration.":::

1. Composite entity supports multilevel child entities.

### Step 4: Create relationships between staging tables

Create relationships between the parent and child entity staging tables based on the natural keys. For example, staging tables for MySalesTable and MySalesLine are linked by SalesID, DefinitionGroup, and ExecutionId.

1. Add a foreign key relation on the MySalesLineStaging table.

    :::image type="content" source="./media/developingcompositeentities-5.png" alt-text="Screenshot of staging table foreign key relation configuration for MySalesLineStaging table.":::

1. Add two columns, RowId and ParentRowId (type int), on all the staging tables associated with the composite data entity. Refer to the SysCompositeHeaderStaging table for the column properties.

    :::image type="content" source="./media/developingcompositeentities-7.png" alt-text="Screenshot of staging table columns showing RowId and ParentRowId configuration with integer data types.":::

These columns are used to define runtime relationships during the target data movement.

- Create a cluster index on the staging tables, which includes RowId, ParentRowId, DefinitionGroup, and ExecutionId. This is for performance reasons.
- Compile and synchronize the artifacts.

### Step 5: Set up the metadata for DMFEntity

For local testing, the composite entity metadata needs to be refreshed.

1. Go to **DIXF Parameters** > **Entity settings**. Select **Refresh entity list**.

    :::image type="content" source="./media/developingcompositeentities-8.png" alt-text="Screenshot of DIXF Parameters Entity settings page with Refresh entity list button highlighted.":::

1. Alternatively, you can write the following job to refresh the composite entity list metadata.

    ```xpp
    DMFDataPopulation::refreshCompositeEntityList();
    ```

1. Execute the job. This refreshes the metadata required for the entity lookup.

> [!NOTE]
> Currently, this is a workaround. In the future, a feature is enabled to refresh the list at compile/sync time.

### Step 6: Test the entity locally

Import and export the data as a normal entity from the DIXF standard process. Refer to the following steps for importing and exporting entity.

> [!NOTE]
> The source types of XML-Attribute or XML-Element are supported for composite entities. In entity execution parameters, composite entities can't be imported in parallel using parallel processing settings.

## Import a composite entity

1. Select **Import**.
1. Enter **Name**, **Source data format**, and **Entity name**.
1. The **Source data format** is either xml-attribute or xml-element.
1. Select **Import now**.
1. The number of records created/updated/pending is shown.

## Export a composite entity

1. Select **Export**.
1. Enter **Name**, **Source data format**, and **Entity name**.
1. Select **Add entity** and **Export now**.
1. Select **Download package**.

## General troubleshooting guidelines

- **Issue**: The exported composite XML file isn't imported. The scenario that produces this:

  - Export a file for composite entity.
  - Import the same file.
  - Mapping fails and the file isn't imported.

- **Root cause**:

    1. Check if the exported file has lines or related child entity information.
  1. If no lines or related child entity information, then the lines aren't mapped during import.

- **Resolution**:

    1. Create a sample file with all child entities.
  1. Use this file for initial mapping only.
  1. When the mapping is successful, import the actual file, which doesn't have the line data into the entity. Use reimport or upload a new file.
  1. This imports files with partial data (blank child records), depending on the validity of the records.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
