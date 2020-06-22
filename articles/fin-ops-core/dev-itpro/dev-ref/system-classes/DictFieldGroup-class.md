---
title: DictFieldGroup class
description: This topic describes the DictFieldGroup class.
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

# Class DictFieldGroup

[!include [banner](../../includes/banner.md)]

```xpp
class DictFieldGroup extends Object
```

The DictFieldGroup class provides information about a specific field group in a table.

## Remarks

For a code example that uses this class, see the DictFieldGroup.numberOfFields Method method.

## Examples

## Methods

| Method                                                                             | Description                                                                         |
|------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|
| public FieldId field(int fieldNumber)                                              | Returns the specified field from the field group.                                   |
| public str label()                                                                 | Returns the label text of the field group.                                          |
| public str labelId()                                                               | Returns the label ID of the field group.                                            |
| public str methodName(FieldId fieldId)                                             | Returns the name of the specified method from the field group.                      |
| public str name()                                                                  | Returns the name of the field group.                                                |
| public int numberOfFields()                                                        | Returns the number of table fields and edit and display methods in the field group. |
| public TableId tableid()                                                           | Returns the ID of the table that is associated with the field group.                |
| public void new(TableId tableId, str FieldGroupName, \[TableId includeBaseTable\]) | Initializes a new instance of the Object class.                                     |

## Method field

Returns the specified field from the field group.

```xpp
public FieldId field(int fieldNumber)
```

### Parameters - field

fieldNumber  
The one-based index to the list of fields in the field group. The index is in the same order as the Application Object Tree (AOT).

### Return Value - field

The field ID of the field. If the item is a display method, the ID is in the form 65280 + 0-based method index.

### Remarks - field

For a code example that uses the Field method, see the DictFieldGroup.numberOfFields Method method.

## Method label

Returns the label text of the field group.

```xpp
public str label()
```

### Return Value - label

The label text of the field group.

## Method labelId

Returns the label ID of the field group.

```xpp
public str labelId()
```

### Return Value - labelId

The label ID of the field group.

## Method methodName

Returns the name of the specified method from the field group.

```xpp
public str methodName(FieldId fieldId)
```

### Parameters - methodName

fieldId  
The field ID that is returned from a call to the field method for the method name to return. It is the responsibility of the developer to make sure that a valid field ID is used.

### Return Value - methodName

The name of the specified method from the field group; an empty string if the fieldId value is less than 65280.

### Remarks - methodName

Methods are specified by method index + 65280. For a code example that uses this method, see the DictFieldGroup.numberOfFields Method method.

## Method name

Returns the name of the field group.

```xpp
public str name()
```

### Return Value - name

The name of the field group.

## Method numberOfFields

Returns the number of table fields and edit and display methods in the field group.

```xpp
public int numberOfFields()
```

### Return Value - numberOfFields

The number of table fields and edit and display methods in the field group.

### Examples - numberOfFields

The following example shows the retrieval of the number of table fields and edit and display methods in a field group.

```xpp
    DictFieldGroup  fldGrp; 
    DictField       fld; 
    fieldId         fldId; 
    tableId         tblId; 
    int             i; 
    tblId = tablenum("CustTable"); 
    fldGrp = new DictFieldGroup(tblId,"AutoReport"); 
    if (fldGrp) 
    {     for (i=1; i <= fldGrp.numberOfFields(); i++) 
         { 
             fldId = fldGrp.field(i); 
             fld  = new DictField(tblId, fldId); 
             if (fld) 
             { 
                print 'Field: ' + fld.name() 
       + ' (' + int2str(fldId) + ')'; 
             } 
             else 
             { 
                print 'MethodName: ' + fldGrp.methodName(fldId)  
                + ' (' + int2str(fldId) + ')'; 
             } 
         } 
    }
```

## Method tableid

Returns the ID of the table that is associated with the field group.

```xpp
public TableId tableid()
```

### Return Value - tableid

The ID of the table that is associated with the field group.

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(TableId tableId, str FieldGroupName, [TableId includeBaseTable])
```

### Parameters - new

tableId  

<!-- -->

FieldGroupName  

<!-- -->

includeBaseTable  

### Remarks - new

For a code example that uses this method, see the DictFieldGroup.numberOfFields Method method.

