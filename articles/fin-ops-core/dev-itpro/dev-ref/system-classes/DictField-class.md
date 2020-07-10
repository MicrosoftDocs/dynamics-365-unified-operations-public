---
title: DictField class
description: This topic describes the DictField class.
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

# Class DictField

[!include [banner](../../includes/banner.md)]

```xpp
class DictField extends Object
```

The DictField class provides information about a specified field in a specified table.

## Remarks

## Examples

The following example shows how to create an instance of the DictField class to determine whether a field is mandatory.

```xpp
macrolib.dictfield 
DictField df; 
int       nFlags; 
df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum)); 
if (df) 
{ 
    nFlags = df.flags(); 
    if (bitTest(nFlags,#DBF_MANDATORY)) 
    { 
        print ("The field is mandatory."); 
    } 
    else 
    { 
        print ("The field is not mandatory."); 
    } 
}
```

## Methods

| Method                                                                                                                | Description                                                                                                                               |
|-----------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public FieldId aliasFor()                                                                                             | Returns the ID of the alias field, if the field is an alias for another field.                                                            |
| public Alignment alignment()                                                                                          |                                                                                                                                           |
| public boolean allowEdit()                                                                                            |                                                                                                                                           |
| public boolean allowEditOnCreate()                                                                                    |                                                                                                                                           |
| public boolean aosAuthorization()                                                                                     |                                                                                                                                           |
| public int arrayIndex()                                                                                               |                                                                                                                                           |
| public int arraySize()                                                                                                | Returns the array size for the field (in other words, the array size of the underlying extended data type).                               |
| public Types baseType()                                                                                               | Returns the base type of the field, such as string, real, integer, date, time, enum, or container.                                        |
| public ConfigurationKeyId configurationKeyId()                                                                        | Returns the ID of the configuration key for the field.                                                                                    |
| public str dateTimeTimeZoneRuleFieldName(\[int arrayindex\])                                                          |                                                                                                                                           |
| public int displayHeight(\[boolean useDefaults\])                                                                     |                                                                                                                                           |
| public int displayLength(\[boolean useDefaults\])                                                                     |                                                                                                                                           |
| public EnumId enumId()                                                                                                | Returns the ID of the enumeration if the field is based on an enumeration.                                                                |
| public int flags(\[str ext\], \[Common record\])                                                                      | Returns an integer that defines the properties of the field. The flag values, such as DBF\_MANDATORY, are defined in the DictField macro. |
| public container getCountryRegionCodes()                                                                              |                                                                                                                                           |
| public FieldId getCountryRegionContextField()                                                                         |                                                                                                                                           |
| public str getPrimaryTableForSurrogateField()                                                                         |                                                                                                                                           |
| public str groupPrompt()                                                                                              | Returns the groupPrompt value for the field.                                                                                              |
| public str groupPromptDefined()                                                                                       | Returns the value of the groupPrompt property for the field.                                                                              |
| public str help(\[int arrayIndex\], \[boolean useInterfaceLanguage\])                                                 | Returns the Help text that is displayed for the field.                                                                                    |
| public str helpDefined()                                                                                              | Returns the value of the help property for the field.                                                                                     |
| public FieldId id()                                                                                                   | Returns the ID of the field.                                                                                                              |
| public boolean isIgnoreEDTRelation()                                                                                  |                                                                                                                                           |
| public boolean isMonocased()                                                                                          | Returns a value that indicates whether the database requires that the field be monocase.                                                  |
| public boolean isSql()                                                                                                | Returns a value that indicates whether the field is in the SQL database.                                                                  |
| public boolean isSurrogateForeignKey()                                                                                |                                                                                                                                           |
| public boolean isSystem()                                                                                             | Returns a value that indicates whether the field is a system field.                                                                       |
| public str label(\[int arrayIndex\])                                                                                  | Returns the label for the field.                                                                                                          |
| public str labelDefined()                                                                                             | Returns the value of the label property for the field.                                                                                    |
| public boolean mandatory()                                                                                            |                                                                                                                                           |
| public str name(\[DbBackend db\], \[int arrayindex\], \[FieldNameGenerationMode generationMode\], \[str tableAlias\]) | Returns the name of the field.                                                                                                            |
| public Guid origin()                                                                                                  |                                                                                                                                           |
| public str qualifiedLabel(\[int arrayIndex\])                                                                         |                                                                                                                                           |
| public str relatedTableName()                                                                                         |                                                                                                                                           |
| public str relationContext()                                                                                          |                                                                                                                                           |
| public DictRelation relationObject(\[int arrayIndex\])                                                                | Returns a DictRelation object for the field if the field is based on an extended data type that has a relation.                           |
| public AccessType rights(\[boolean ignoreContext\])                                                                   | Returns the access rights for the current user that are specified for the field.                                                          |
| public int stringLen()                                                                                                | Returns the string size of the field if the base type of the field is a string.                                                           |
| public TableId tableid()                                                                                              | Returns the ID of the table that contains the field.                                                                                      |
| public Types type()                                                                                                   | Returns the data type of the field.                                                                                                       |
| public ExtendedTypeId typeId()                                                                                        | Returns the ID of the extended data type if the field is based on an extended data type.                                                  |
| public boolean visible()                                                                                              |                                                                                                                                           |
| public void setLookupMode(boolean lookupMode)                                                                         |                                                                                                                                           |
| public void setSFKAutoAuthorizationMode(boolean sfkMode)                                                              |                                                                                                                                           |
| public void new(TableId tableId, FieldId fieldId, \[int arrayIndex\])                                                 | Initializes a new instance of the Object class.                                                                                           |

## Method aliasFor

Returns the ID of the alias field, if the field is an alias for another field.

```xpp
public FieldId aliasFor()
```

### Return Value - aliasFor

The ID of the alias field for the field; 0 (zero) if the field is not an alias for another field.

### Remarks - aliasFor

When the user enters data in a field, the validateField method of the table is called. If the validateField method cannot perform a lookup on the value, it checks whether an alias exists. If an alias field exists, the validateField method performs a lookup on the alias field.

### Examples - aliasFor

The following example shows the retrieval of the alias field for a field.

```xpp
DictField df; 
fieldId   fId; 
df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum));
if (df) 
{ 
    fId = df.aliasFor(); 
    if (0 != fId) 
    { 
        print (strfmt("Field alias: %1", fieldid2name(tablenum(CustTable), fId))); 
    } 
}
```

## Method alignment

```xpp
public Alignment alignment()
```

### Return Value - alignment

## Method allowEdit

```xpp
public boolean allowEdit()
```

### Return Value - allowEdit

## Method allowEditOnCreate

```xpp
public boolean allowEditOnCreate()
```

### Return Value - allowEditOnCreate

## Method aosAuthorization

```xpp
public boolean aosAuthorization()
```

### Return Value - aosAuthorization

## Method arrayIndex

```xpp
public int arrayIndex()
```

### Return Value - arrayIndex

## Method arraySize

Returns the array size for the field (in other words, the array size of the underlying extended data type).

```xpp
public int arraySize()
```

### Return Value - arraySize

The array size for the field; 1 if the field is not an array.

### Examples - arraySize

The following example shows the retrieval of the array size for a field.

```xpp
DictField df; 
Types     t; 
df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum));  
if (df) 
{ 
    print strfmt("The arraySize is %1.", df.arraySize()); 
}
```

## Method baseType

Returns the base type of the field, such as string, real, integer, date, time, enum, or container.

```xpp
public Types baseType()
```

### Return Value - baseType

A Types value that specifies the type of the field.

### Examples - baseType

The following example shows the retrieval of the base type of a field.

```xpp
DictField df;
df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum)); 
if (df)
{
    print strfmt("The field type is %1.", df.baseType());
}
```

## Method configurationKeyId

Returns the ID of the configuration key for the field.

```xpp
public ConfigurationKeyId configurationKeyId()
```

### Return Value - configurationKeyId

The ID of the configuration key for the field; 0 (zero) if there is no configuration key for the field.

### Examples - configurationKeyId

The following example shows the retrieval of the configuration key ID and the configuration key name for a field.

```xpp
DictField df; 
configurationKeyId cki; 
DictConfigurationKey dck; 
df = new DictField(tablenum(BankAccountTable), fieldnum(BankAccountTable, CustPaymFeePost)); 
if (df) 
{ 
    cki = df.configurationKeyId(); 
    //    print df.helpDefined(); 
    if (0 != cki) 
    { 
        dck = new DictConfigurationKey(cki); 
        if (dck) 
        print strfmt("The configuration key is %1.", dck.name()); 
    } 
    else 
    { 
        print "No configuration key"; 
    } 
}
```

## Method dateTimeTimeZoneRuleFieldName

```xpp
public str dateTimeTimeZoneRuleFieldName([int arrayindex])
```

### Parameters - dateTimeTimeZoneRuleFieldName

arrayindex  

### Return Value - dateTimeTimeZoneRuleFieldName

## Method displayHeight

```xpp
public int displayHeight([boolean useDefaults])
```

### Parameters - displayHeight

useDefaults  

### Return Value - displayHeight

## Method displayLength

```xpp
public int displayLength([boolean useDefaults])
```

### Parameters - displayLength

useDefaults  

### Return Value - displayLength

## Method enumId

Returns the ID of the enumeration if the field is based on an enumeration.

```xpp
public EnumId enumId()
```

### Return Value - enumId

The enumeration ID if the field is based on an enumeration; otherwise, 0 (zero).

### Examples - enumId

The following example shows the retrieval of the enumeration ID and the enumeration name of a field that is based on an enumeration.

```xpp
DictField df; 
DictEnum  de; 
enumId    id; 
df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum)); 
if (df) 
{ 
    id = df.enumId(); 
    if (0 != id) 
    { 
        de = new DictEnum(id); 
        if (de) 
        { 
            print de.name(); 
        } 
    } 
}
```

## Method flags

Returns an integer that defines the properties of the field. The flag values, such as DBF\_MANDATORY, are defined in the DictField macro.

```xpp
public int flags([str ext], [Common record])
```

### Parameters - flags

ext  

<!-- -->

record  

### Return Value - flags

An integer value, where each bit corresponds to a field flag.

### Remarks - flags

Use the Global::bitTest Method method or the & operator to check individual flag values.

### Examples - flags

The following example shows the retrieval of the flags of a field to determine whether the field is mandatory.

```xpp
macrolib.dictfield 
DictField df; 
int       nFlags; 
df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum)); 
if (df) 
{ 
    nFlags = df.flags(); 
    if (bitTest(nFlags,#DBF_MANDATORY)) 
    { 
        print ("The field is mandatory."); 
    } 
    else 
    { 
        print ("The field is not mandatory."); 
    } 
}
```

## Method getCountryRegionCodes

```xpp
public container getCountryRegionCodes()
```

### Return Value - getCountryRegionCodes

## Method getCountryRegionContextField

```xpp
public FieldId getCountryRegionContextField()
```

### Return Value - getCountryRegionContextField

## Method getPrimaryTableForSurrogateField

```xpp
public str getPrimaryTableForSurrogateField()
```

### Return Value - getPrimaryTableForSurrogateField

## Method groupPrompt

Returns the groupPrompt value for the field.

```xpp
public str groupPrompt()
```

### Return Value - groupPrompt

The groupPrompt value for the field.

## Method groupPromptDefined

Returns the value of the groupPrompt property for the field.

```xpp
public str groupPromptDefined()
```

### Return Value - groupPromptDefined

The value of the groupPrompt property for the table.

## Method help

Returns the Help text that is displayed for the field.

```xpp
public str help([int arrayIndex], [boolean useInterfaceLanguage])
```

### Parameters - help

arrayIndex  
A Boolean value that indicates whether to use the user interface language for the Help text; optional.

<!-- -->

useInterfaceLanguage  
A Boolean value that indicates whether to use the user interface language for the Help text; optional.

### Return Value - help

The Help text or inherited Help text for the field.

### Remarks - help

If no Help text is defined for the field, this method returns the Help text for the extended data type that is used for the field, if applicable. If an array entry is specified, this method returns the Help text for the array element.

### Examples - help

The following example shows retrieval of the Help text for the field.

```xpp
DictField df; 
df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum)); 
if (df) 
{ 
    print df.help(); 
}
```

## Method helpDefined

Returns the value of the help property for the field.

```xpp
public str helpDefined()
```

### Return Value - helpDefined

The value of the help property for the field.

### Remarks - helpDefined

Unlike the help method, the helpDefined method does not return the Help text of the extended data type if the field is based on an extended data type and has no Help text defined for it.

### Examples - helpDefined

The following example shows retrieval of the defined Help text for the field.

```xpp
DictField df; 
df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum)); 
if (df) 
{ 
    print df.helpDefined(); 
}
```

## Method id

Returns the ID of the field.

```xpp
public FieldId id()
```

### Return Value - id

The ID of the field.

### Examples - id

The following example retrieves the ID of a field.

```xpp
DictField df; 
df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum)); 
if (df) 
{ 
    print df.id(); 
}
```

## Method isIgnoreEDTRelation

```xpp
public boolean isIgnoreEDTRelation()
```

### Return Value - isIgnoreEDTRelation

## Method isMonocased

Returns a value that indicates whether the database requires that the field be monocase.

```xpp
public boolean isMonocased()
```

### Return Value - isMonocased

true if the field is monocase; otherwise, false.

## Method isSql

Returns a value that indicates whether the field is in the SQL database.

```xpp
public boolean isSql()
```

### Return Value - isSql

true if the field is in the SQL database; otherwise, false.

### Examples - isSql

The following example determines whether the field is in the SQL database.

```xpp
    DictField df; 
    df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum)); 
    if (df) 
    { 
    if (df.isSql()) 
    { 
        print ("Field is in SQL database"); 
    } 
    else 
    { 
        print ("Field is not in SQL database"); 
    } 
    }
```

## Method isSurrogateForeignKey

```xpp
public boolean isSurrogateForeignKey()
```

### Return Value - isSurrogateForeignKey

## Method isSystem

Returns a value that indicates whether the field is a system field.

```xpp
public boolean isSystem()
```

### Return Value - isSystem

true if the field is a system field; otherwise, false.

## Method label

Returns the label for the field.

```xpp
public str label([int arrayIndex])
```

### Parameters - label

arrayIndex  

### Return Value - label

The label or inherited label value for the field.

### Remarks - label

If no label is provided for the field, this method returns the label for the extended data type for the field, if applicable. If an array entry is specified, this method returns the label for the array element.

## Method labelDefined

Returns the value of the label property for the field.

```xpp
public str labelDefined()
```

### Return Value - labelDefined

The value of the label property for the table; an empty string if there is no label text for the table.

### Remarks - labelDefined

Unlike the label method, the labelDefined method does not return the extended data type label if the field is based on an extended data type and has no label defined for it.

### Examples - labelDefined

The following example shows the retrieval of the defined label for a field.

```xpp
DictField df; 
df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum)); 
if (df) 
{ 
    print df.labelDefined(); 
}
```

## Method mandatory

```xpp
public boolean mandatory()
```

### Return Value - mandatory

## Method name

Returns the name of the field.

```xpp
public str name([DbBackend db], [int arrayindex], [FieldNameGenerationMode generationMode], [str tableAlias])
```

### Parameters - name

db  
The alias for the table; optional.

<!-- -->

arrayindex  
The alias for the table; optional.

<!-- -->

generationMode  
The alias for the table; optional.

<!-- -->

tableAlias  
The alias for the table; optional.

### Return Value - name

The name of the field.

### Examples - name

The following example shows the retrieval of the name of the field.

```xpp
DictField df; 
df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum)); 
if (df) 
{ 
    print df.name(); 
}
```

## Method origin

```xpp
public Guid origin()
```

### Return Value - origin

## Method qualifiedLabel

```xpp
public str qualifiedLabel([int arrayIndex])
```

### Parameters - qualifiedLabel

arrayIndex  

### Return Value - qualifiedLabel

## Method relatedTableName

```xpp
public str relatedTableName()
```

### Return Value - relatedTableName

## Method relationContext

```xpp
public str relationContext()
```

### Return Value - relationContext

## Method relationObject

Returns a DictRelation object for the field if the field is based on an extended data type that has a relation.

```xpp
public DictRelation relationObject([int arrayIndex])
```

### Parameters - relationObject

arrayIndex  

### Return Value - relationObject

A DictRelation object that represents the relations for the field; null, Nothing, nullptr, unit, a null reference (Nothing in Visual Basic) if there no relations are defined for the field, or if the field is not based on an extended data type.

## Method rights

Returns the access rights for the current user that are specified for the field.

```xpp
public AccessType rights([boolean ignoreContext])
```

### Parameters - rights

ignoreContext  

### Return Value - rights

The access rights for the current user that are specified for the field.

### Remarks - rights

This can be one of the values in the AccessType enumeration.

## Method stringLen

Returns the string size of the field if the base type of the field is a string.

```xpp
public int stringLen()
```

### Return Value - stringLen

The string size of the field if the base type of the field is a string; otherwise, 0 (zero).

### Examples - stringLen

The following example shows retrieving the string length of a field.

```xpp
DictField df; 
df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum)); 
if (df) 
{ 
    print strfmt("The string length is %1.", df.stringLen()); 
}
```

## Method tableid

Returns the ID of the table that contains the field.

```xpp
public TableId tableid()
```

### Return Value - tableid

The ID of the table that contains the field.

### Examples - tableid

The following example shows the retrieval of the table ID of a field.

```xpp
DictField df; 
df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum)); 
if (df) 
{ 
    print df.tableid(); 
}
```

## Method type

Returns the data type of the field.

```xpp
public Types type()
```

### Return Value - type

A Types value that specifies the type of the field.

### Remarks - type

If the field is based on an extended data type, Types::UserType is returned as the return value of this method.

### Examples - type

The following example shows the retrieval of the type of a field.

```xpp
DictField df; 
df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum)); 
if (df) 
{ 
    print df.type(); 
}
```

## Method typeId

Returns the ID of the extended data type if the field is based on an extended data type.

```xpp
public ExtendedTypeId typeId()
```

### Return Value - typeId

The ID of the extended data type if the field is based on an extended data type; otherwise, 0 (zero).

### Examples - typeId

The following example shows the retrieval of the extended data type ID for a field.

```xpp
DictField df; 
extendedTypeId eti; 
DictType  dt; 
df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum)); 
if (df) 
{ 
   eti = df.typeId(); 
   if (0 != eti) 
   { 
        dt = new DictType(eti); 
        if (dt) 
        { 
            print strfmt("The field is based on %1.", dt.name()); 
        } 
   } 
   else 
   { 
        print "The field is not based on an extended data type."; 
   } 
}
```

## Method visible

```xpp
public boolean visible()
```

### Return Value - visible

## Method setLookupMode

```xpp
public void setLookupMode(boolean lookupMode)
```

### Parameters - setLookupMode

lookupMode  

## Method setSFKAutoAuthorizationMode

```xpp
public void setSFKAutoAuthorizationMode(boolean sfkMode)
```

### Parameters - setSFKAutoAuthorizationMode

sfkMode  

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(TableId tableId, FieldId fieldId, [int arrayIndex])
```

### Parameters - new

tableId  

<!-- -->

fieldId  

<!-- -->

arrayIndex  

### Examples - new

The following example shows how to create an instance of the DictField class.

```xpp
DictField df; 
df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum)); 
// Check df for successful creation before proceeding. 
if (!df) 
{ 
// Take error action. 
}
```

