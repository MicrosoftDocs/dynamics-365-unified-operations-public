---
title: Creating cubes overview (Preview)
description: Learn how to create planning cubes using the new Data Model Builder experience available in Business performance planning version 1.14 and later.
author: twheeloc
ms.author: romainpham
ms.topic: overview
ms.date: 11/23/2025
ms.reviewer: theeloc
ms.collection: get-started
---

# Creating cubes (Preview)

> [!IMPORTANT]
> The **Data Model Builder** experience for cube creation is available starting with **Business performance planning version 1.14**.  
> The new cube creation page is accessible under **Cubes (Preview)**.  
> The previous cube creation flow remains available under **Cubes** for backward compatibility.  
> For the classic experience, see [Create a cube (Classic)](create-cubes.md).

---

## Overview


In **Business performance planning (BPP)**, a *cube* defines the structure of your planning model.  
A cube combines **dimensions**—such as *Account*, *Cost Center*, or *Date*—with **drivers**, which are the numeric values that users plan, forecast, and write back.

Cubes form the foundation for all planning and forecasting scenarios and can be extended with calculated columns, security, audit tracking, and allocation logic once published to **Microsoft Dataverse**.

Starting in version **1.14**, the **Data Model Builder (Preview)** introduces a new, visual approach to cube creation.  
It enables model builders to:
- Create cubes faster and more intuitively.  
- Tag and classify datasets from Excel to identify the fact table and associated dimensions.  
- Import fully defined cube structures from JSON files, including relationships, facts, and dimensions.  
- Preview model structure before publishing.  
- Build draft cubes that can be refined, validated, and extended before committing.

---

## Key concepts

A **cube** is the core data structure in **Business Performance Planning (BPP)** that defines how planning, forecasting, and analysis are organized.

- **Facts** represent numeric data that can be aggregated and analyzed, such as sales, operating expenses, or headcount.  
- **Dimensions** describe how you want to slice and view your fact data — for example by *Account*, *Department*, *Period*, or *Scenario*.  
- Each dimension typically contains one or more columns (for example, a *Time* dimension might include *Date*, *Month*, *Quarter*, and *Year*).  
- **Drivers** are the numeric input values that users plan or adjust during forecasting. Drivers can later be combined through **computed columns** that express formula-based logic (for example, *Revenue = Units Sold × Unit Price*).  
- Facts, dimensions, and drivers together define the structure of a **planning model**, which can then be published to **Microsoft Dataverse** for data ingestion, write-back, and reporting.  

For background on how these components work together, see [Business performance planning overview](business-performance-planning-overview.md).

---

## Available creation methods

| Method | Description | Typical use case |
|---------|--------------|------------------|
| [Create a cube from existing dimensions (Preview)](create-cube-from-existing-dimensions-preview.md) | Build a cube schema from scratch using existing BPP dimensions already defined in your environment. | Ideal for administrators who want full control over the cube structure. |
| [Create a cube from Excel (Preview)](create-cube-from-excel-preview.md) | Upload one or several Excel files containing fact and dimension data. BPP automatically detects, classifies, and links datasets to shape the planning model. | Best for analysts or finance users working from existing spreadsheets. |
| [Create a cube from JSON (Preview)](create-cube-from-json-preview.md) | Import a preconfigured cube definition from a JSON file to quickly deploy or migrate models. | Designed for partners or advanced users managing multiple tenants. |

---

## After a cube is created

Once a cube has been published to Dataverse, you can:
- Load fact data using [dataflows](load-data-into-bpp-using-dataflows.md) or Excel upload.  
- Add [custom drivers](custom-drivers.md) or [calculated columns](create-calculated-columns.md) to extend logic.  
- Enable [cube audit](cube-audit.md) or the **Non-Clustered Columnstore Index** for performance and traceability.  
- Export or import cube definitions for re-use across environments.

> [!TIP]
> Use the **Cubes (Preview)** workspace to manage both **Draft** and **Published** cubes in one unified view.

---

## Version availability

| Experience | Version | Navigation location |
|-------------|----------|----------------------|
| Classic cube creation | Versions up to **1.13** | **Cubes** |
| Data Model Builder (Preview) | Available from **1.14** onward | **Cubes (Preview)** |
| Draft cube visualization | Available from **1.14** onward | **Cubes (Preview)** |

---

### Known limitations (Preview)

The following limitations apply to the current Cube (Preview) experience:

- **Published dimensions can’t be modified within the Cube (Preview) interface.**
- **Dimension changes made in Power Apps or the BPP Dimensions section aren’t reflected visually in Cube (Preview)**, though they remain active in Dataverse.
- **All schema changes are still reflected in connected Power BI and Excel reports.**
- Support for cross-cube linking and automatic synchronization will be introduced in a future release.



---

## Next steps

- [Create a cube from existing dimensions (Preview)](create-cube-from-existing-dimensions-preview.md)  
- [Create a cube from Excel (Preview)](create-cube-from-excel-preview.md)  
- [Create a cube from JSON (Preview)](create-cube-from-json-preview.md)  
- [Load data using dataflows](load-data-into-bpp-using-dataflows.md)  
- [Create calculated columns](create-calculated-columns.md)



