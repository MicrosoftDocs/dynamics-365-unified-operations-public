---
title: SPLITLIST ER function
description: This article provides information about how the SPLITLIST Electronic reporting (ER) function is used.
author: kfend
ms.date: 03/15/2021
ms.prod: 
ms.technology: 
audience: Application User, IT Pro
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 24223e13-727a-4be6-a22d-4d427f504ac9
ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
---

# SPLITLIST ER function

[!include [banner](../includes/banner.md)]

The `SPLITLIST` function splits the specified list into sublists (or batches), each of which contains the specified number of records. It then returns the result as a new *Record list* value that consists of the batches.

## Syntax 1

```vb
SPLITLIST (list, number)
```

## Syntax 2

```vb
SPLITLIST (list, number, on-demand reading flag)
```

## Arguments

`list`: *Record list*

The valid path of a data source of the *Record list* data type.

`number`: *Integer*

The maximum number of records per batch.

`on-demand reading flag`: *Boolean*

A *Boolean* value that specifies whether elements of sublists should be generated on demand.

## Return values

*Record list*

The resulting list of records.

## Usage notes

The list of batches that is returned contains the following elements:

 - **Value:** *List*

    The list of records that belong to the current batch.

- **BatchNumber:** *Integer*

    The number of the current batch in the returned list.

When the on-demand reading flag is set to **True**, sublists are generated upon request which allows for a reduction in memory consumption but may cause performance degradation if elements aren't used sequentially.

## Example

In the following illustration, a **Lines** data source is created as a record list that has three records. This list is divided into batches, each of which contains up to two records.

<a href="./media/picture-splitlist-datasource.jpg"><img src="./media/picture-splitlist-datasource.jpg" alt="Data source that is divided into batches" class="alignnone wp-image-290681 size-full" width="397" height="136" /></a>

The following illustration shows the designed format layout. In this format layout, bindings to the **Lines** data source are created to generate output in XML format. This output presents individual nodes for each batch and the records in it.

<a href="./media/picture-splitlist-format.jpg"><img src="./media/picture-splitlist-format.jpg" alt="Format layout that has bindings to a data source" class="alignnone wp-image-290691 size-full" width="374" height="161" /></a>

The following illustration shows the result when the designed format is run.

<a href="./media/picture-splitlist-result.jpg"><img src="./media/picture-splitlist-result.jpg" alt="Result of running the format" class="alignnone wp-image-290701 size-full" width="358" height="191" /></a>

## Additional resources

[List functions](er-functions-category-list.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
