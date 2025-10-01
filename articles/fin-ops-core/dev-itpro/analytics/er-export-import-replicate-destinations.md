---
title: Export, import and replicate ER destinations
description: Learn how to export, import and replicate ER destinations.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/23/2025
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2016-05-31
ms.search.form: DocuType, ERSolutionTable
ms.dyn365.ops.version: AX 7.0.1
ms.assetid: f3055a27-717a-4c94-a912-f269a1288be6
---

# Export, import and replicate ER destinations

[!include [banner](../includes/banner.md)]

As of version **10.0.46** of Microsoft Dynamics 365 Finance, to streamline the process of configuring destinations across multiple legal entities or environments you can use these capabilities.

- **Export and import** destination configurations by using the [**Data Management Framework** (DMF)](../data-entities/data-entities-data-packages.md).
- **Replicate** destinations across multiple legal entities within the same environment.

These capabilities reduce manual effort, improve consistency, and make ER destination setup more scalable.  

## Export and import ER destinations

You can now use a dedicated **Data entity** to export and import ER destination configurations between environments.  

| Data entity name | Target data entity | Tables included |
|------------------|--------------------|-----------------|
| File destination | **ERFormatFileDestinationEntity** | ERFormatDestinationTable<br> ERFormatFileDestinationTable <br> ERFormatDestinationNamedTable |

For more information about data entities in Finance, see [Data entities overview](../data-entities/data-entities.md).

## Replicate ER destinations across legal entities

1. Go to **Organization administration** > **Electronic reporting** > **Electronic reporting destination** page.
2. In the list on the left-hand side, select one or more ER formats.  
3. On the action pane, select **Replicate** button.  
4. Choose one or more legal entities to copy destinations into.
5. (Optional) To also replicate **named destinations** that are used in **Print management** for configurable business documents, select the **Include named destinations** checkbox. For more information about named destinations used in **Print management**, see [Configure print management record-specific ER destinations](er-named-destinations.md).
6. Confirm to replicate.  

All destinations for the selected formats are copied into the chosen companies, including those using container fields.  

> [!TIP]  
> Replication can be applied to multiple formats and multiple legal entities in a single operation — saving significant setup time.  


