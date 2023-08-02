---
title: List of ER functions in the list category
description: This article provides information about the list functions that are supported in Electronic reporting (ER).
author: kfend
ms.date: 04/01/2020
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

# List of ER functions in the list category

[!include [banner](../includes/banner.md)]

Electronic reporting (ER) list functions can be used to extract information from, and perform operations on, data sources of the *Record list* and *Container (record)* data types. This article provides a summary of these functions.

## List of supported functions

| Function | Description |
|----------|-------------|
| [AllItems](er-functions-list-allitems.md)                 | This function runs as an in-memory selection. It returns a new flattened *Record list* value that consists of a list of records that represents all items that match the specified path. |
| [AllItemsQuery](er-functions-list-allitemsquery.md)       | This function runs as a joined SQL query. It returns a new flattened *Record list* value that consists of a list of records that represents all items that match the specified path. |
| [Count](er-functions-list-count.md)                       | This function returns an *Integer* value that represents the number of records in the specified list, if the list isn't empty. If the list is empty, this function returns **0** (zero). |
| [EmptyList](er-functions-list-emptylist.md)               | This function returns an empty *Record list* value by using the specified list as a source for the list structure.|
| [Enumerate](er-functions-list-enumerate.md)               | This function returns a new *Record list* value that consists of enumerated records of the specified list. |
| [Filter](er-functions-list-filter.md)                     | This function returns the specified list as a *Record list* value after the query has been changed so that it filters for the specified condition. |
| [First](er-functions-list-first.md)                       | This function returns the first record of the specified list as a *Container (record)* value, if that list isn't empty. If the list is empty, this function throws an exception. |
| [FirstOrNull](er-functions-list-firstornull.md)           | This function returns the first record of the specified list as a *Container (record)* value, if that record isn't empty. If the record is empty, this function returns a null *Container (record)* value. |
| [Index](er-functions-list-index.md)                       | This function returns a *Container (record)* value that is selected by using the specified numeric index in the specified list. If the index is out of range for the records in the specified list, this function throws an exception. |
| [IsEmpty](er-functions-list-isempty.md)                   | This function returns a *Boolean* value of **TRUE** if the specified list contains no records. Otherwise, it returns a *Boolean* value of **FALSE**. |
| [List](er-functions-list-list.md)                         | This function returns a *Record list* value that consists of a new list that is created from the specified arguments.|
| [ListDistinct](er-functions-list-listdistinct.md)         | This function calculates the specified expression as a selector for every record of the specified list. It returns a new *Record list* value that contains a single record for each unique selector value.|
| [ListJoin](er-functions-list-listjoin.md)                 | This function returns a *Record list* value that represents a new joined list that is created from the specified arguments.|
| [ListOfFields](er-functions-list-listoffields.md)         | This function returns a *Record list* value that is created based on the structure of the specified argument of the *Enumeration* or *Container (record)* type. |
| [ListOfFirstItem](er-functions-list-listoffirstitem.md)   | This function returns a *Record list* value that consists of only the first record of the specified list.|
| [OrderBy](er-functions-list-orderby.md)                   | This function returns the specified list as a *Record list* value after it has been sorted according to the specified arguments. These arguments can be defined as expressions. |
| [Repeat](er-functions-list-repeat.md)                     | This function builds a record that contains the field that has a value that matches the specified input. It then returns a new *Record list* of a record that is repeated a specified number of times. |
| [Reverse](er-functions-list-reverse.md)                   | This function returns the specified list as a *Record list* value in reversed sort order. |
| [Split](er-functions-list-split.md)                       | This function splits the specified input string into substrings and returns the result as a new *Record list* value. |
| [SplitList](er-functions-list-splitlist.md)               | This function splits the specified list into sublists (or batches), each of which contains the specified number of records. It then returns the result as a new *Record list* value that consists of the batches. |
| [SplitListByLimit](er-functions-list-splitlistbylimit.md) | This function splits the specified list into a new list of sublists (batches). The number of records in each batch is dynamically calculated. The function then returns the result as a new *Record list* value that consists of the batches. |
| [StringJoin](er-functions-list-stringjoin.md)             | This function returns a *String* value that consists of concatenated values of the specified field from the specified list. The values can be separated by the specified delimiter. |
| [Where](er-functions-list-where.md)                       | This function returns the specified list as a *Record list* value after it has been filtered according to the specified condition. |

## Additional resources

[Electronic Reporting overview](general-electronic-reporting.md)

[Formula designer in Electronic reporting](general-electronic-reporting-formula-designer.md)

[Electronic reporting formula language](er-formula-language.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
