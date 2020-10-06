---
title: FormBuildDataSource class
description: This topic describes the FormBuildDataSource class.
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

# Class FormBuildDataSource

[!include [banner](../../includes/banner.md)]

```xpp
class FormBuildDataSource extends FormBuildObjectSet
```

The FormBuildDataSource class lets you create, read, update, and delete X++ code and metadata.

## Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

## Examples

## Methods

| Method                                                                            | Description                                                                                                               |
|-----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------|
| public FormBuildDataSource addReferenceDataSource(str name, \[str joinRelation\]) |                                                                                                                           |
| public boolean allowCheck(\[boolean value\])                                      |                                                                                                                           |
| public boolean allowCreate(\[boolean value\])                                     |                                                                                                                           |
| public boolean allowDeferredLoad(\[boolean value\])                               |                                                                                                                           |
| public boolean allowDelete(\[boolean value\])                                     |                                                                                                                           |
| public boolean allowEdit(\[boolean value\])                                       | Determines whether the user can change the contents of the control.                                                       |
| public boolean autoNotify(\[boolean value\])                                      |                                                                                                                           |
| public boolean autoQuery(\[boolean value\])                                       |                                                                                                                           |
| public boolean autoSearch(\[boolean value\])                                      |                                                                                                                           |
| public FormBuildDataSource baseDataSource()                                       |                                                                                                                           |
| public str company(\[str value\])                                                 |                                                                                                                           |
| public FieldId counterField(\[FieldId value\])                                    |                                                                                                                           |
| public boolean crossCompanyAutoQuery(\[boolean value\])                           |                                                                                                                           |
| public boolean delayActive(\[boolean value\])                                     |                                                                                                                           |
| public int extends(\[AnyType value\])                                             |                                                                                                                           |
| public str GetXppILImplementation()                                               |                                                                                                                           |
| public IndexId index(\[IndexId value\])                                           |                                                                                                                           |
| public boolean insertAtEnd(\[boolean value\])                                     |                                                                                                                           |
| public boolean insertIfEmpty(\[boolean value\])                                   |                                                                                                                           |
| public boolean isBaseDataSource()                                                 |                                                                                                                           |
| public boolean isInheritanceDataSource()                                          |                                                                                                                           |
| public boolean isMasterDataSource()                                               |                                                                                                                           |
| public str joinRelation(\[str value\])                                            |                                                                                                                           |
| public int joinSource(\[AnyType value\])                                          |                                                                                                                           |
| public int linkType(\[int value\])                                                |                                                                                                                           |
| public FormBuildDataSource masterDataSource()                                     |                                                                                                                           |
| public int maxAccessRight(\[int value\])                                          |                                                                                                                           |
| public int maxRecordsToLoad(\[int value\])                                        |                                                                                                                           |
| public str name(\[str value\])                                                    | Gets or sets the name that is used in code to identify a form, report, table, query, or another MSDAX application object. |
| public boolean onlyFetchActive(\[boolean value\])                                 |                                                                                                                           |
| public int optionalRecordMode(\[int value\])                                      |                                                                                                                           |
| public int startPosition(\[int value\])                                           |                                                                                                                           |
| public TableId table(\[TableId value\])                                           | Gets or sets the table ID associated with the object.                                                                     |
| public int validTimeStateAutoQuery(\[int value\])                                 |                                                                                                                           |
| public int validTimeStateUpdate(\[int value\])                                    |                                                                                                                           |
| public void RegisterXppDataFieldILImplementation(str fieldName, str className)    |                                                                                                                           |
| public void RegisterXppILImplementation(str className)                            |                                                                                                                           |
| public void SetDataLinkType(QueryDataLinkType linkType, str parentDataSource)     |                                                                                                                           |

## Method addReferenceDataSource

```xpp
public FormBuildDataSource addReferenceDataSource(str name, [str joinRelation])
```

### Parameters - addReferenceDataSource

name  

<!-- -->

joinRelation  

### Return Value - addReferenceDataSource

## Method allowCheck

```xpp
public boolean allowCheck([boolean value])
```

### Parameters - allowCheck

value  

### Return Value - allowCheck

## Method allowCreate

```xpp
public boolean allowCreate([boolean value])
```

### Parameters - allowCreate

value  

### Return Value - allowCreate

## Method allowDeferredLoad

```xpp
public boolean allowDeferredLoad([boolean value])
```

### Parameters - allowDeferredLoad

value  

### Return Value - allowDeferredLoad

## Method allowDelete

```xpp
public boolean allowDelete([boolean value])
```

### Parameters - allowDelete

value  

### Return Value - allowDelete

## Method allowEdit

Determines whether the user can change the contents of the control.

```xpp
public boolean allowEdit([boolean value])
```

### Parameters - allowEdit

value  

### Return Value - allowEdit

true if the control can be edited; otherwise, false.

### Remarks - allowEdit

When this property is set on a container control, modifications are disabled or enabled for all controls in the container.

## Method autoNotify

```xpp
public boolean autoNotify([boolean value])
```

### Parameters - autoNotify

value  

### Return Value - autoNotify

## Method autoQuery

```xpp
public boolean autoQuery([boolean value])
```

### Parameters - autoQuery

value  

### Return Value - autoQuery

## Method autoSearch

```xpp
public boolean autoSearch([boolean value])
```

### Parameters - autoSearch

value  

### Return Value - autoSearch

## Method baseDataSource

```xpp
public FormBuildDataSource baseDataSource()
```

### Return Value - baseDataSource

## Method company

```xpp
public str company([str value])
```

### Parameters - company

value  

### Return Value - company

## Method counterField

```xpp
public FieldId counterField([FieldId value])
```

### Parameters - counterField

value  

### Return Value - counterField

## Method crossCompanyAutoQuery

```xpp
public boolean crossCompanyAutoQuery([boolean value])
```

### Parameters - crossCompanyAutoQuery

value  

### Return Value - crossCompanyAutoQuery

## Method delayActive

```xpp
public boolean delayActive([boolean value])
```

### Parameters - delayActive

value  

### Return Value - delayActive

## Method extends

```xpp
public int extends([AnyType value])
```

### Parameters - extends

value  

### Return Value - extends

## Method GetXppILImplementation

```xpp
public str GetXppILImplementation()
```

### Return Value - GetXppILImplementation

## Method index

```xpp
public IndexId index([IndexId value])
```

### Parameters - index

value  

### Return Value - index

## Method insertAtEnd

```xpp
public boolean insertAtEnd([boolean value])
```

### Parameters - insertAtEnd

value  

### Return Value - insertAtEnd

## Method insertIfEmpty

```xpp
public boolean insertIfEmpty([boolean value])
```

### Parameters - insertIfEmpty

value  

### Return Value - insertIfEmpty

## Method isBaseDataSource

```xpp
public boolean isBaseDataSource()
```

### Return Value - isBaseDataSource

## Method isInheritanceDataSource

```xpp
public boolean isInheritanceDataSource()
```

### Return Value - isInheritanceDataSource

## Method isMasterDataSource

```xpp
public boolean isMasterDataSource()
```

### Return Value - isMasterDataSource

## Method joinRelation

```xpp
public str joinRelation([str value])
```

### Parameters - joinRelation

value  

### Return Value - joinRelation

## Method joinSource

```xpp
public int joinSource([AnyType value])
```

### Parameters - joinSource

value  

### Return Value - joinSource

## Method linkType

```xpp
public int linkType([int value])
```

### Parameters - linkType

value  

### Return Value - linkType

## Method masterDataSource

```xpp
public FormBuildDataSource masterDataSource()
```

### Return Value - masterDataSource

## Method maxAccessRight

```xpp
public int maxAccessRight([int value])
```

### Parameters - maxAccessRight

value  

### Return Value - maxAccessRight

## Method maxRecordsToLoad

```xpp
public int maxRecordsToLoad([int value])
```

### Parameters - maxRecordsToLoad

value  

### Return Value - maxRecordsToLoad

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

## Method onlyFetchActive

```xpp
public boolean onlyFetchActive([boolean value])
```

### Parameters - onlyFetchActive

value  

### Return Value - onlyFetchActive

## Method optionalRecordMode

```xpp
public int optionalRecordMode([int value])
```

### Parameters - optionalRecordMode

value  

### Return Value - optionalRecordMode

## Method startPosition

```xpp
public int startPosition([int value])
```

### Parameters - startPosition

value  

### Return Value - startPosition

## Method table

Gets or sets the table ID associated with the object.

```xpp
public TableId table([TableId value])
```

### Parameters - table

value  

### Return Value - table

The current value of the table ID associated with the object.

## Method validTimeStateAutoQuery

```xpp
public int validTimeStateAutoQuery([int value])
```

### Parameters - validTimeStateAutoQuery

value  

### Return Value - validTimeStateAutoQuery

## Method validTimeStateUpdate

```xpp
public int validTimeStateUpdate([int value])
```

### Parameters - validTimeStateUpdate

value  

### Return Value - validTimeStateUpdate

## Method RegisterXppDataFieldILImplementation

```xpp
public void RegisterXppDataFieldILImplementation(str fieldName, str className)
```

### Parameters - RegisterXppDataFieldILImplementation

fieldName  

<!-- -->

className  

## Method RegisterXppILImplementation

```xpp
public void RegisterXppILImplementation(str className)
```

### Parameters - RegisterXppILImplementation

className  

## Method SetDataLinkType

```xpp
public void SetDataLinkType(QueryDataLinkType linkType, str parentDataSource)
```

### Parameters - SetDataLinkType

linkType  

<!-- -->

parentDataSource  

