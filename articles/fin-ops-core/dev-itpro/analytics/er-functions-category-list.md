---
# required metadata

title: List of ER functions of the List category
description: This topic provides information about what list functions are supported in ER.
author: NickSelin
manager: kfend
ms.date: 12/17/2019
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

# List functions

[!include [banner](../includes/banner.md)]

Electronic reporting (ER) list functions can be used to extract information from, and perform operations on, data sources of the *Record list* and *Container (record)* data type.
You can find a summary of these functions in this topic.

## List of supported functions

| **Function**  | **Description**                           |
|---------------|-------------------------------------------|
| [AllItems](er-functions-list-allitems.md)                 | Runs as an in-memory selection and returns a new flattened *Record list* as a list of records representing all items that match the specified path.                                   |
| [AllItemsQuery](er-functions-list-allitemsquery.md)       | Runs as a joined SQL query and returns a new flattened *Record list* as a list or records representing all items that match the specified path.                                         |
| [Count](er-functions-list-count.md)                       | Returns an *Integer* value as the number of records in the specified list, if the list is not empty. Otherwise, it returns a zero (0).                                                     |
| [EmptyList](er-functions-list-emptylist.md)               | Returns an empty *Record list* by using the specified list as a source for the list structure.                            |
| [Enumerate](er-functions-list-enumerate.md)               | Returns a new *Record list* that consists of enumerated records of the specified list.                              |
| [Filter](er-functions-list-filter.md)                     | Returns the specified list as a *Record list* after the query has been modified to filter for a given condition.          |
| [First](er-functions-list-first.md)                       | Returns the first record of the specified list as a *Container (record)*, if that list is not empty. Otherwise, it throws an exception.                                                  |
| [FirstOrNull](er-functions-list-firstornull.md)           | Returns the first record of the specified list as a *Container (record)*, if that record is not empty. Otherwise, it returns a null *Container (record)*.                                  |
| [Index](er-functions-list-index.md)                       | Returns a *Container (record)* that is selected by a specific numeric index in the specified list. An exception is thrown if the index is out of range of the records the specified list.|
| [IsEmpty](er-functions-list-isempty.md)                   | Returns a *Boolean* **TRUE** if the specified list contains no records. Otherwise, it returns a *Boolean* **FALSE**.          |
| [List](er-functions-list-list.md)                         | Returns a *Record list* as a new list that is created from specified arguments.                                        |
| [ListOfFields](er-functions-list-listoffields.md)         | Returns a *Record list* that is created based on the structure of a given argument of one of the following types: *Enumeration* or *Container (record)*.                      |
| [ListOfFirstItem](er-functions-list-listoffirstitem.md)   | Returns a *Record list* that contains only the first record of the specified list.                                         |
| [OrderBy](er-functions-list-orderby.md)                   | Returns the specified list as a *Record list* after it has been sorted according to the specified arguments. These arguments can be defined as expressions.                    |
| [Reverse](er-functions-list-reverse.md)                   | Returns the specified list as a *Record list* in reversed sort order.                                                      |
| [Split](er-functions-list-split.md)                       | Splits the specified input string into substrings. Returns the result as a new *Record list*.                              |
| [SplitList](er-functions-list-splitlist.md)               | Splits the specified list into sub-lists (batches), each of which contains the specified number of records. Returns the result as a new *Record list* of batches.                   |
| [SplitListByLimit](er-functions-list-splitlistbylimit.md) | Splits the specified list into a new list of sub-lists (batches), each of which contains the number of records that is dynamically calculated. The result is returned as a new *Record list* of batches.                                           |
| [StringJoin](er-functions-list-stringjoin.md)             | Returns a *String* that consists of concatenated values of the specified field from the specified list. The values can be separated by the specified delimiter.                       |
| [Where](er-functions-list-where.md)                       | Returns the specified list as a *Record list* after it has been filtered according to the specified condition.         |

## Additional resources

[Electronic Reporting overview](general-electronic-reporting.md)

[Formula designer in Electronic reporting](general-electronic-reporting-formula-designer.md)

[Electronic reporting formula language](er-formula-language.md)
