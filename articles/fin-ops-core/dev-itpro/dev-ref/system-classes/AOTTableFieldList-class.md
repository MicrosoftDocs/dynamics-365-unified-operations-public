---
title: AOTTableFieldList class
description: This topic describes the AOTTableFieldList class.
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

# Class AOTTableFieldList

[!include [banner](../../includes/banner.md)]

```xpp
class AOTTableFieldList extends TreeNode
```

The AOTTableFieldList class represents the Fields node of a table and is also used to add fields to a table.

## Remarks

This class lets you create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before this API is called. The developer can obtain general information on the node by using other methods.

## Examples

The following example adds a field of the enum type to the TutorialJournalName table.

```xpp
{ 
    AOTTableFieldList tfl = infolog.findNode( 
        '\\Data Dictionary\\Tables\\TutorialJournalName\\Fields'); 
```

```xpp
     if (!tfl.AOTFindChild('NewEnum')) 
     { 
         tfl.addEnum('NewEnum');  // Adds the field NewEnum. 
     } 
}
```

## Methods

| Method                             | Description                                                                         |
|------------------------------------|-------------------------------------------------------------------------------------|
| public void addInteger(str name)   | Adds a new field of the integer type to the list of fields for the current table.   |
| public void addGuid(str name)      |                                                                                     |
| public void addContainer(str name) | Adds a new field of the container type to the list of fields for the current table. |
| public void addInt64(str name)     |                                                                                     |
| public void addDateTime(str name)  |                                                                                     |
| public void addDate(str name)      | Adds a new field of the date type to the list of fields for the current table.      |
| public void addString(str name)    | Adds a new field of the string type to the list of fields for the current table.    |
| public void addReal(str name)      | Adds a new field of the real type to the list of fields for the current table.      |
| public void addTime(str name)      | Adds a new field of the time type to the list of fields for the current table.      |
| public void addEnum(str name)      | Adds a new field of the enum type to the list of fields for the current table.      |

## Method addInteger

Adds a new field of the integer type to the list of fields for the current table.

```xpp
public void addInteger(str name)
```

### Parameters - addInteger

name  
The name of the field to add.

### Remarks - addInteger

If the supplied name coincides with an existing field in the field list, an integer is appended to the name of the new field to make the field name unique. The developer must make sure that the name is not a reserved word; the method will not throw an error if a reserved word is specified. You can use the AOTfindChild method to determine whether a field name is already being used.

### Examples - addInteger

The following code example adds the NewInteger field, which is of the integer type, to the list of fields for the TutorialJournalName table.

```xpp
AOTTableFieldList tfl = infolog.findNode( 
    '\\Data Dictionary\\Tables\\TutorialJournalName\\Fields'); 
if (!tfl.AOTFindChild('NewInteger')) 
{ 
    tfl.addInteger('NewInteger'); 
}
```

## Method addGuid

```xpp
public void addGuid(str name)
```

### Parameters - addGuid

name  

## Method addContainer

Adds a new field of the container type to the list of fields for the current table.

```xpp
public void addContainer(str name)
```

### Parameters - addContainer

name  
The name of the field to add.

### Remarks - addContainer

If the supplied name coincides with an existing field in the field list, an integer is appended to the name of the new field to make the field name unique. The developer must make sure that the name is not a reserved word; the method will not throw an error if a reserved word is specified. You can use the AOTfindChild method to determine whether a field name is already being used.

### Examples - addContainer

The following code example adds the NewContainer and NewContainer1 fields, which are both of the container type, to the list of fields of the TutorialJournalName table.

```xpp
AOTTableFieldList tfl = infolog.findNode( 
    '\\Data Dictionary\\Tables\\TutorialJournalName\\Fields'); 
```

```xpp
// Add a NewContainer field. 
tfl.addContainer('NewContainer'); 
```

```xpp
// Add a NewContainer1 field. 
tfl.addContainer('NewContainer');
```

## Method addInt64

```xpp
public void addInt64(str name)
```

### Parameters - addInt64

name  

## Method addDateTime

```xpp
public void addDateTime(str name)
```

### Parameters - addDateTime

name  

## Method addDate

Adds a new field of the date type to the list of fields for the current table.

```xpp
public void addDate(str name)
```

### Parameters - addDate

name  
The name of the field to add.

### Remarks - addDate

If the supplied name coincides with an existing field in the field list, an integer is appended to the name of the new field to make the field name unique. The developer must make sure that the name is not a reserved word; the method will not throw an error if a reserved word is specified. You can use the AOTfindChild method to determine whether a field name is already being used.

### Examples - addDate

The following code example adds the NewDate field, which is of the date type, to the list of fields for the TutorialJournalName table.

```xpp
AOTTableFieldList tfl = infolog.findNode( 
    '\\Data Dictionary\\Tables\\TutorialJournalName\\Fields'); 
if (!tfl.AOTFindChild('NewDate')) 
{ 
    tfl.addDate('NewDate'); 
}
```

## Method addString

Adds a new field of the string type to the list of fields for the current table.

```xpp
public void addString(str name)
```

### Parameters - addString

name  
The name of the field to add.

### Remarks - addString

If the supplied name coincides with an existing field in the field list, an integer is appended to the name of the new field to make the field name unique. It is up to the developer to make sure that the name is not a reserved word; the method will not throw an error if a reserved word is specified. You can use the AOTfindChild method to determine whether a field name is already being used.

### Examples - addString

The following example adds the NewString field, which is of the string type, to the list of fields for the TutorialJournalName table.

```xpp
{ 
    AOTTableFieldList tfl = infolog.findNode( 
        '\\Data Dictionary\\Tables\\TutorialJournalName\\Fields'); 
    if (!tfl.AOTFindChild('NewString')) 
    { 
        tfl.addString('NewString'); 
    } 
}
```

## Method addReal

Adds a new field of the real type to the list of fields for the current table.

```xpp
public void addReal(str name)
```

### Parameters - addReal

name  
The name of the field to add.

### Remarks - addReal

If the supplied name coincides with an existing field in the field list, an integer is appended to the name of the new field to make the field name unique. It is up to the developer to make sure that the name is not a reserved word; the method will not throw an error if a reserved word is specified. You can use the AOTfindChild method to determine whether a field name is already being used.

### Examples - addReal

The following example adds the NewReal and NewReal1 fields, which is of the real type, to the list of fields for the TutorialJournalName table.

```xpp
AOTTableFieldList tfl = infolog.findNode( 
    '\\Data Dictionary\\Tables\\TutorialJournalName\\Fields'); 
// Add the field NewReal. 
tfl.addReal('NewReal'); 
// Add the field NewReal1. 
tfl.addReal('NewReal');
```

## Method addTime

Adds a new field of the time type to the list of fields for the current table.

```xpp
public void addTime(str name)
```

### Parameters - addTime

name  
The name of the field to add.

### Remarks - addTime

If the supplied name coincides with an existing field in the field list, an integer is appended to the name of the new field to make the field name unique. The developer must make sure that the name is not a reserved word; the method will not throw an error if a reserved word is specified. You can use the AOTfindChild method to determine whether a field name is already being used.

### Examples - addTime

The following code example adds the NewTime field, which is of the time type, to the list of fields of the TutorialJournalName table.

```xpp
AOTTableFieldList tfl = infolog.findNode( 
    '\\Data Dictionary\\Tables\\TutorialJournalName\\Fields'); 
if (!tfl.AOTFindChild('NewTime')) 
{ 
    tfl.addTime('NewTime'); 
}
```

## Method addEnum

Adds a new field of the enum type to the list of fields for the current table.

```xpp
public void addEnum(str name)
```

### Parameters - addEnum

name  
The name of the field to add.

### Remarks - addEnum

If the supplied name coincides with an existing field in the field list, an integer is appended to the name of the new field to make the field name unique. It is up to the developer to make sure that the name is not a reserved word; the method will not throw an error if a reserved word is specified. You can use the AOTfindChild method to determine whether a field name is already being used.

### Examples - addEnum

The following example adds the NewEnum field, which is of the enum type, to the list of fields of the TutorialJournalName table.

```xpp
AOTTableFieldList tfl = infolog.findNode( 
    '\\Data Dictionary\\Tables\\TutorialJournalName\\Fields'); 
if (!tfl.AOTFindChild('NewEnum')) 
{ 
    tfl.addEnum('NewEnum');  // adds the field NewEnum 
}
```

