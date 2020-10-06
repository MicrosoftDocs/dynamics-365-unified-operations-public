---
title: ReportSectionGroup class
description: This topic describes the ReportSectionGroup class.
author: robinarh
manager: tonyafehr
ms.date: 06/25/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

audience: Developer
ms.reviewer: rhaertle
ms.search.scope: Operations
ms.search.region: Global
ms.author: rhaertle
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Class ReportSectionGroup

[!include [banner](../../includes/banner.md)]

```xpp
class ReportSectionGroup extends TreeNode
```

The ReportSectionGroup class defines a collection of report sections.

## Remarks

A report section group can contain header sections, body sections, and footer sections. This class lets you create, read, update, and delete X++ code and metadata. You must have access to the development security key (SysDevelopment) before you call this API.

## Examples

## Methods

| Method                                                       | Description                                                                                                               |
|--------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------|
| public ReportSection addSection(ReportBlockType sectionType) |                                                                                                                           |
| public FieldId dataField(\[FieldId value\])                  |                                                                                                                           |
| public int delete()                                          |                                                                                                                           |
| public str name(\[str value\])                               | Gets or sets the name that is used in code to identify a form, report, table, query, or another MSDAX application object. |
| public ReportSection section(ReportBlockType sectionType)    |                                                                                                                           |
| public TableId table(\[TableId value\])                      | Gets or sets the table ID associated with the object.                                                                     |

## Method addSection

```xpp
public ReportSection addSection(ReportBlockType sectionType)
```

### Parameters - addSection

sectionType  

### Return Value - addSection

## Method dataField

```xpp
public FieldId dataField([FieldId value])
```

### Parameters - dataField

value  

### Return Value - dataField

## Method delete

```xpp
public int delete()
```

### Return Value - delete

## Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or another MSDAX application object.

```xpp
public str name([str value])
```

### Parameters - name

value  

### Return Value - name

The name that is used in code to identify an application object.

### Remarks - name

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

## Method section

```xpp
public ReportSection section(ReportBlockType sectionType)
```

### Parameters - section

sectionType  

### Return Value - section

## Method table

Gets or sets the table ID associated with the object.

```xpp
public TableId table([TableId value])
```

### Parameters - table

value  

### Return Value - table

The current value of the table ID associated with the object.

