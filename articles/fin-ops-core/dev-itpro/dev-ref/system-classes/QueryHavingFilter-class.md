---
title: QueryHavingFilter class
description: This topic describes the QueryHavingFilter class.
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

# Class QueryHavingFilter

[!include [banner](../../includes/banner.md)]

```xpp
class QueryHavingFilter extends TreeNode
```

## Remarks

## Examples

## Methods

| Method                                          | Description                                                                                                                               |
|-------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public AggregateFunction aggregateFunction()    |                                                                                                                                           |
| public QueryBuildDataSource dataSource()        |                                                                                                                                           |
| public boolean enabled(\[boolean value\])       | Determines whether to enable or disable the object.                                                                                       |
| public FieldId field(\[FieldId value\])         | Gets or sets the field ID associated with the object.                                                                                     |
| public int fieldArrayIndex()                    |                                                                                                                                           |
| public FieldName fieldName()                    |                                                                                                                                           |
| public str label(\[str value\])                 | Gets or sets the label for a control.                                                                                                     |
| public str name(\[str value\])                  | Gets or sets the name that is used in code to identify a form, report, table, query, or other application object. |
| public str prompt()                             |                                                                                                                                           |
| public int status(\[int value\])                | Gets or sets the status of an object.                                                                                                     |
| public TableId table(\[TableId value\])         | Gets or sets the table ID that is associated with the object.                                                                             |
| public TableId tableSelector(\[TableId value\]) |                                                                                                                                           |
| public str toString()                           | Returns a string that represents the current object.                                                                                      |
| public int typeof()                             |                                                                                                                                           |
| public boolean valid()                          |                                                                                                                                           |
| public str value(\[str value\])                 |                                                                                                                                           |
| public void finalize()                          |                                                                                                                                           |

## Method aggregateFunction

```xpp
public AggregateFunction aggregateFunction()
```

### Return Value - aggregateFunction

## Method dataSource

```xpp
public QueryBuildDataSource dataSource()
```

### Return Value - dataSource

## Method enabled

Determines whether to enable or disable the object.

```xpp
public boolean enabled([boolean value])
```

### Parameters - enabled

value  

### Return Value - enabled

true if the object is enabled; otherwise, false.

### Remarks - enabled

The enabled property enables controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

## Method field

Gets or sets the field ID associated with the object.

```xpp
public FieldId field([FieldId value])
```

### Parameters - field

value  

### Return Value - field

The current value of the field ID associated with the object.

## Method fieldArrayIndex

```xpp
public int fieldArrayIndex()
```

### Return Value - fieldArrayIndex

## Method fieldName

```xpp
public FieldName fieldName()
```

### Return Value - fieldName

## Method label

Gets or sets the label for a control.

```xpp
public str label([str value])
```

### Parameters - label

value  

### Return Value - label

The current value of the label string.

### Remarks - label

The label determines which text is displayed in the control or adjacent to it. The label property value cannot exceed 250 characters.

## Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other application object.

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
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, or classes.

## Method prompt

```xpp
public str prompt()
```

### Return Value - prompt

## Method status

Gets or sets the status of an object.

```xpp
public int status([int value])
```

### Parameters - status

value  

### Return Value - status

The current value of the status of the object.

## Method table

Gets or sets the table ID that is associated with the object.

```xpp
public TableId table([TableId value])
```

### Parameters - table

value  

### Return Value - table

The current value of the table ID that is associated with the object.

## Method tableSelector

```xpp
public TableId tableSelector([TableId value])
```

### Parameters - tableSelector

value  

### Return Value - tableSelector

## Method toString

Returns a string that represents the current object.

```xpp
public str toString()
```

### Return Value - toString

A string that represents the current object.

### Remarks - toString

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and type of the method, such as instance or static.

## Method typeof

```xpp
public int typeof()
```

### Return Value - typeof

## Method valid

```xpp
public boolean valid()
```

### Return Value - valid

## Method value

```xpp
public str value([str value])
```

### Parameters - value

value  

### Return Value - value

## Method finalize

```xpp
public void finalize()
```

