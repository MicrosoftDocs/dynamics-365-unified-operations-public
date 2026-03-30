---
title: Creating cubes overview (preview)
description: Learn how to create planning cubes using the new Data model builder experience available in Business performance planning version 1.14 and later.
author: twheeloc
ms.author: romainpham
ms.topic: overview
ms.date: 11/25/2025
ms.reviewer: theeloc
ms.collection: get-started
---

# Creating cubes (preview)

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

> [!NOTE]
> This article describes the **Data model builder (preview)** experience. The existing **Cubes** page is still available. For information about classic cube creation, see [Create a cube](create-cubes.md).

## Overview

In Business performance planning, a cube defines the structure of your planning model. A cube combines dimensions, such as Account, Cost center, or Date, with drivers. Drivers are the numeric values that users plan, forecast, and write back.

Cubes form the foundation for all planning and forecasting scenarios. After you publish a cube to Microsoft Dataverse, you can extend it with calculated columns, security, audit tracking, and allocation logic.

Starting in version **1.14**, the **Data model builder (preview)** feature introduces a new, visual approach to cube creation.  
It enables model builders to:
- Create cubes faster and more intuitively.  
- Tag and classify datasets from Excel to identify the fact table and associated dimensions.  
- Import fully defined cube structures from JSON files, including relationships, facts, and dimensions.  
- Preview model structure before publishing.  
- Build draft cubes that you can refine, validate, and extend before committing.


### Key concepts

A cube is the core data structure in Business performance planning. It defines how planning, forecasting, and analysis are organized.

- **Facts** - Represent numeric data that you can aggregate and analyze, such as sales, operating expenses, or headcount.  
- **Dimensions** - Describe how you want to slice and view your fact data. For example, by Account, Department, Period, or Scenario.  
- Each dimension typically contains one or more columns. For example, a Time dimension might include Date, Month, Quarter, and Year.  
- **Drivers** - The numeric input values that users plan or adjust during forecasting. Drivers can later be combined through computed columns that express formula-based logic. For example, *Revenue = Units Sold × Unit Price*.  
- Facts, dimensions, and drivers together define the structure of a planning model. You can then publish the model to Microsoft Dataverse for data ingestion, write-back, and reporting.  

For more information, see [Business performance planning overview](business-performance-planning-overview.md).

### Available cube creation methods

Use the following methods to create cubes:
 - [Existing dimensions](BPP-cub-dim.md) - Build a cube schema from scratch by using existing Business performance planning dimensions already defined in your environment.
 - [Excel](bpp-cube-Excel.md) - Upload one or several Excel files that contain fact and dimension data. Business performance planning automatically detects, classifies, and links datasets to shape the planning model.
 - [JSON](bpp-json.md) - Import a preconfigured cube definition from a JSON file to quickly deploy or migrate models.


#### After you create a cube

After you publish a cube to Dataverse, you can:
- Load fact data by using [dataflows](load-data-dataflows.md) or Excel upload.  
- Add [custom drivers](custom-drivers.md) or [calculated columns](calculated-columns.md) to extend logic.  
- Enable [cube audit](cube-audit.md) or the **Non-Clustered Columnstore Index** for performance and traceability.  
- Export or import cube definitions for re-use across environments.

> [!TIP]
> Use the **Cubes (preview)** workspace to manage both **Draft** and **Published** cubes in one unified view.

### Known limitations (preview)

The following limitations apply to the current Cube (preview) experience:

- You can't modify published dimensions within the Cube (preview) interface.
- Dimension changes that you make in Power Apps or the Business performance planning dimensions section don't appear visually in Cube (Preview), though they remain active in Dataverse.
- All schema changes still appear in connected Power BI and Excel reports.
- Support for cross-cube linking and automatic synchronization will be introduced in a future release.

### Next steps

- [Create a cube from existing dimensions](bpp-cub-dim.md)  
- [Create a cube from Excel](bpp-cube-excel.md)  
- [Create a cube from JSON](bpp-json.md)  
- [Load data using dataflows](load-data-dataflows.md)  
- [Create calculated columns](calculated-columns.md)






