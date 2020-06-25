---
title: DictRelation class
description: This topic describes the DictRelation class.
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

# Class DictRelation

[!include [banner](../../includes/banner.md)]

```xpp
class DictRelation extends Object
```

The DictRelation class can be used to manage dictionary relations for the tables.

## Remarks

## Examples

## Methods

| Method                                                                                                                | Description                                                          |
|-----------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------|
| public Cardinality Cardinality()                                                                                      | Retrieves the cardinality value.                                     |
| public boolean createNavigationPropertyMethods()                                                                      |                                                                      |
| public boolean EDTRelation()                                                                                          | Retrieves the extended data type (EDT) relation state.               |
| public str entityRelationshipRole()                                                                                   | Retrieves the name of the entity relationship role.                  |
| public str entityRelationshipRoleLabelId()                                                                            | Retrieves the label ID for the name of the entity relationship role. |
| public TableId externTable()                                                                                          | Returns the ID of the external table that is used for the relation.  |
| public boolean isSelfLink()                                                                                           | Verifies whether the relation is self-linked.                        |
| public int lineExternTableValue(int lineNumber)                                                                       | Retrieves the external table value for the given line.               |
| public int lines()                                                                                                    | Retrieves the number of the lines in the relation.                   |
| public int lineSourceEDT(int lineNumber)                                                                              | Retrieves the source EDT value for the given table line.             |
| public RelationshipSubType lineSubType(int lineNumber)                                                                | Retrieves the sub-type for the given table line.                     |
| public int lineTableValue(int lineNumber)                                                                             | Retrieves the value for the given table line.                        |
| public TableRelation lineType(int lineNumber)                                                                         | Retrieves the relation type for the given table line.                |
| public TableId loadFieldRelation(FieldId fieldId, \[TableScope tableScope\], \[Common record\], \[boolean isLookup\]) | Loads a relation that is specified by a field ID.                    |
| public TableId loadNameRelation(str name)                                                                             | Loads the relation for the given name.                               |
| public TableId loadTableRelation(TableId tableId, \[TableScope tableScope\], \[Common record\])                       | Loads a table relation.                                              |
| public str navigationPropertyNameOverride()                                                                           |                                                                      |
| public RelatedTableCardinality RelatedTableCardinality()                                                              | Retrieves the cardinality for the related table.                     |
| public str RelatedTableRole()                                                                                         | Retrieves the role name for the related table.                       |
| public RelationshipType relationshipType()                                                                            | Retrieves the relationship type.                                     |
| public str Role()                                                                                                     | Retrieves the role name.                                             |
| public TableId table()                                                                                                | Returns the table ID of the relation.                                |
| public boolean useDefaultRoleNames()                                                                                  |                                                                      |
| public boolean validate()                                                                                             | Validates a relation.                                                |
| ::public static boolean isSurrogateForeignKeyRelation(TableId tableId, str relationName)                              | Verifies whether there is surrogate foreign key relation.            |
| public void new(int id, \[UtilElementType Util\_Element\_Type\], \[int index\])                                       | Initializes a new instance of the Object class.                      |

## Method Cardinality

Retrieves the cardinality value.

```xpp
public Cardinality Cardinality()
```

### Return Value - Cardinality

The cardinality value.

## Method createNavigationPropertyMethods

```xpp
public boolean createNavigationPropertyMethods()
```

### Return Value - createNavigationPropertyMethods

## Method EDTRelation

Retrieves the extended data type (EDT) relation state.

```xpp
public boolean EDTRelation()
```

### Return Value - EDTRelation

A Boolean value that indicates whether the EDT relation is available.

## Method entityRelationshipRole

Retrieves the name of the entity relationship role.

```xpp
public str entityRelationshipRole()
```

### Return Value - entityRelationshipRole

The name of the entity relationship role.

## Method entityRelationshipRoleLabelId

Retrieves the label ID for the name of the entity relationship role.

```xpp
public str entityRelationshipRoleLabelId()
```

### Return Value - entityRelationshipRoleLabelId

The label ID for the entity relationship role.

## Method externTable

Returns the ID of the external table that is used for the relation.

```xpp
public TableId externTable()
```

### Return Value - externTable

The ID of the external table that is used for the relation; 0 (zero) if the relation has not yet been loaded.

### Examples - externTable

The following example shows the retrieval of the external table ID.

```xpp
Dictionary dict; 
DictRelation dr; 
int i;  
dict = new Dictionary(); 
dr = new DictRelation(dict.tableName2Id("CustTable")); 
// Load a relation by name 
dr.loadNameRelation("CompanyData");  // Also returns the external table ID. 
print "The external table ID is: " + int2str(dr.externTable());
```

## Method isSelfLink

Verifies whether the relation is self-linked.

```xpp
public boolean isSelfLink()
```

### Return Value - isSelfLink

true if the relation is self-linked; otherwise, false.

## Method lineExternTableValue

Retrieves the external table value for the given line.

```xpp
public int lineExternTableValue(int lineNumber)
```

### Parameters - lineExternTableValue

lineNumber  

### Return Value - lineExternTableValue

The external table value.

## Method lines

Retrieves the number of the lines in the relation.

```xpp
public int lines()
```

### Return Value - lines

The number of the lines.

## Method lineSourceEDT

Retrieves the source EDT value for the given table line.

```xpp
public int lineSourceEDT(int lineNumber)
```

### Parameters - lineSourceEDT

lineNumber  

### Return Value - lineSourceEDT

The source EDT value.

## Method lineSubType

Retrieves the sub-type for the given table line.

```xpp
public RelationshipSubType lineSubType(int lineNumber)
```

### Parameters - lineSubType

lineNumber  

### Return Value - lineSubType

The sub-type for the given table line.

## Method lineTableValue

Retrieves the value for the given table line.

```xpp
public int lineTableValue(int lineNumber)
```

### Parameters - lineTableValue

lineNumber  

### Return Value - lineTableValue

The value for the table line.

## Method lineType

Retrieves the relation type for the given table line.

```xpp
public TableRelation lineType(int lineNumber)
```

### Parameters - lineType

lineNumber  

### Return Value - lineType

The table relation type for the given line.

## Method loadFieldRelation

Loads a relation that is specified by a field ID.

```xpp
public TableId loadFieldRelation(FieldId fieldId, [TableScope tableScope], [Common record], [boolean isLookup])
```

### Parameters - loadFieldRelation

fieldId  

<!-- -->

tableScope  

<!-- -->

record  

<!-- -->

isLookup  

### Return Value - loadFieldRelation

The ID of the table for the relation; null, Nothing, nullptr, unit, a null reference (Nothing in Visual Basic) if the method failed.

## Method loadNameRelation

Loads the relation for the given name.

```xpp
public TableId loadNameRelation(str name)
```

### Parameters - loadNameRelation

name  

### Return Value - loadNameRelation

The table ID for the table relation.

## Method loadTableRelation

Loads a table relation.

```xpp
public TableId loadTableRelation(TableId tableId, [TableScope tableScope], [Common record])
```

### Parameters - loadTableRelation

tableId  

<!-- -->

tableScope  

<!-- -->

record  

### Return Value - loadTableRelation

The table ID for the table relation.

## Method navigationPropertyNameOverride

```xpp
public str navigationPropertyNameOverride()
```

### Return Value - navigationPropertyNameOverride

## Method RelatedTableCardinality

Retrieves the cardinality for the related table.

```xpp
public RelatedTableCardinality RelatedTableCardinality()
```

### Return Value - RelatedTableCardinality

The cardinality for the related table.

## Method RelatedTableRole

Retrieves the role name for the related table.

```xpp
public str RelatedTableRole()
```

### Return Value - RelatedTableRole

The role name for the related table.

## Method relationshipType

Retrieves the relationship type.

```xpp
public RelationshipType relationshipType()
```

### Return Value - relationshipType

The relationship type.

## Method Role

Retrieves the role name.

```xpp
public str Role()
```

### Return Value - Role

The role name.

## Method table

Returns the table ID of the relation.

```xpp
public TableId table()
```

### Return Value - table

The table ID of the relation.

### Examples - table

The following example shows the retrieval of the table ID for a relation.

```xpp
Dictionary dict; 
DictRelation dr; 
dict = new Dictionary(); 
dr = new DictRelation(dict.tableName2Id("CustTable")); 
print dr.table();
```

## Method useDefaultRoleNames

```xpp
public boolean useDefaultRoleNames()
```

### Return Value - useDefaultRoleNames

## Method validate

Validates a relation.

```xpp
public boolean validate()
```

### Return Value - validate

true if the relation is valid; otherwise, false.

## Method isSurrogateForeignKeyRelation

Verifies whether there is surrogate foreign key relation.

```xpp
public static boolean isSurrogateForeignKeyRelation(TableId tableId, str relationName)
```

### Parameters - isSurrogateForeignKeyRelation

tableId  

<!-- -->

relationName  

### Return Value - isSurrogateForeignKeyRelation

true if there is a surrogate foreign key relation; otherwise, false.

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(int id, [UtilElementType Util_Element_Type], [int index])
```

### Parameters - new

id  
The relation index; optional. The default value is 1.

<!-- -->

Util\_Element\_Type  
The relation index; optional. The default value is 1.

<!-- -->

index  
The relation index; optional. The default value is 1.

