---
# required metadata

title: SPLITLIST ER function
description: This topic explains how the SPLITLIST ER function is used
author: NickSelin
manager: kfend
ms.date: 11/29/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 58771
ms.assetid: 24223e13-727a-4be6-a22d-4d427f504ac9
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# <a name="SPLITLIST">SPLITLIST Function</a>

[!include [banner](../includes/banner.md)]

The `SPLITLIST` function splits the specified list into sub-lists (batches), each of which contains the specified number of records. Returns the result as a new *Record list* of batches.

## Syntax

```
SPLITLIST (list, number)
```

## Arguments

`list` : *Record list*

A valid path to a data source of the *Record list* data type.

`number`: *Integer*

The maximum number of records per batch.

## Returns

*Record list*

The result list of records.

## Usage notes

The returned list of batches contains the following elements:

-   **Value** : *List*

    List of records that belong to the current batch.

-   **BatchNumber** : *Integer*

    Number of the current batch in the returned list.

## Example

In the following illustration, a **Lines** data source is created as a record list of three records. This list is divided into batches, each of which contains up to two records.

<a href="./media/picture-splitlist-datasource.jpg"><img src="./media/picture-splitlist-datasource.jpg" alt="Data source that is divided into batches" class="alignnone wp-image-290681 size-full" width="397" height="136" /></a>

The following illustration shows the designed format layout. In this format layout, bindings to the Lin**es data source are created to generate output in XML format. This output presents individual nodes for each batch and the records in it.

<a href="./media/picture-splitlist-format.jpg"><img src="./media/picture-splitlist-format.jpg" alt="Format layout that has bindings to a data source" class="alignnone wp-image-290691 size-full" width="374" height="161" /></a>

The following illustration shows the result when the designed format is run.

<a href="./media/picture-splitlist-result.jpg"><img src="./media/picture-splitlist-result.jpg" alt="Result of running the format" class="alignnone wp-image-290701 size-full" width="358" height="191" /></a>

## Additional resources

[List functions](er-functions-category-list.md)
