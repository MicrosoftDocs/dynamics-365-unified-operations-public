---
title: DictEnum class
description: This topic describes the DictEnum class.
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

# Class DictEnum

[!include [banner](../../includes/banner.md)]

```xpp
class DictEnum extends Object
```

The DictEnum class obtains meta-information about the base enum enumerations in the Application Object Tree (AOT).

## Remarks

For backward compatibility, a special naming convention for methods that convert to or from properties is used.

|                 |                                |                          |
|-----------------|--------------------------------|--------------------------|
|      Name       |            ReqDate             | Symbol (typed as string) |
|      Label      | @SYS18075 ("Requirement date") |      Name or Label       |
|   FeatureKey    |         ReqSchedAction         |        FeatureKey        |
|    EnumValue    |               0                |          Value           |
| Position in AOT |       First (Index = 0)        |          Index           |

This example is from the ActionBasicDateType base enum. For general information about enumerations, see the Developer's Guide.

## Examples

## Methods

| Method                                                            | Description                                                                                                               |
|-------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------|
| public ConfigurationKeyId configurationKeyId()                    | Returns the configuration key ID for the enumeration.                                                                     |
| public int displayLength(\[boolean useLongestLabel\])             |                                                                                                                           |
| public container getCountryRegionCodes()                          |                                                                                                                           |
| public str help(\[boolean useInterfaceLanguage\])                 | Retrieves the Help text for this enumeration.                                                                             |
| public str helpDefined()                                          | Returns the value of the help property for this enumeration.                                                              |
| public EnumId id()                                                | Returns the enumeration ID of the enumeration.                                                                            |
| public ConfigurationKeyId index2ConfigurationKey(int index)       |                                                                                                                           |
| public container index2CountryRegionCodes(int index)              |                                                                                                                           |
| public str index2Label(int index)                                 | Returns the label of the enumeration item that is specified by an index.                                                  |
| public str index2LabelId(int index)                               |                                                                                                                           |
| public str index2Name(int index)                                  | Returns the label of the enumeration item that is specified by an index.                                                  |
| public str index2Symbol(int index)                                | Returns the symbol or name of the enumeration item that is specified by an index.                                         |
| public int index2Value(int index)                                 | Returns the value of the enumeration item that is specified by an index.                                                  |
| public str label()                                                | Returns the label text of the enumeration.                                                                                |
| public str labelDefined()                                         | Returns the value of the label property for this enumeration.                                                             |
| public str name()                                                 | Returns the name of the enumeration.                                                                                      |
| public int name2Value(str name)                                   | Returns the enumeration value of the item that is referenced by its label.                                                |
| public boolean showAsRadio()                                      | Returns a value that indicates whether the enumeration should be displayed by using radio buttons instead of a combo box. |
| public int symbol2Value(str name)                                 | Returns the enumeration value of the item, referenced by its symbol or name.                                              |
| public ConfigurationKeyId value2ConfigurationKey(int value)       | Returns the configuration key ID of a specified enumeration value.                                                        |
| public container value2CountryRegionCodes(int value)              |                                                                                                                           |
| public str value2Label(int value)                                 | Returns the label of a specified enumeration value.                                                                       |
| public str value2Name(int value)                                  | Returns the name of a specified enumeration value.                                                                        |
| public str value2Symbol(int value)                                | Returns the symbol, or the value of the Name property, of a specified enumeration value.                                  |
| public int values()                                               | Returns the number of items in the enumeration.                                                                           |
| ::public static str queryFilterNames2Values(QueryFilter filter)   |                                                                                                                           |
| ::public static str queryFilterValues2Names(QueryFilter filter)   |                                                                                                                           |
| ::public static str queryRangeNames2Values(QueryBuildRange range) |                                                                                                                           |
| ::public static str queryRangeValues2Names(QueryBuildRange range) |                                                                                                                           |
| ::public static int value2id(AnyType value)                       | Returns the enumeration ID of a specified value.                                                                          |
| public void new(EnumId typeId)                                    | Initializes a new instance of the Object class.                                                                           |

## Method configurationKeyId

Returns the configuration key ID for the enumeration.

```xpp
public ConfigurationKeyId configurationKeyId()
```

### Return Value - configurationKeyId

The configuration key ID for the enumeration; 0 (zero) if there is no configuration key ID for the enumeration.

### Examples - configurationKeyId

The following example shows the retrieval of the configuration key ID for an enumeration.

```xpp
DictEnum de; 
int      i; 
de = new DictEnum(enumName2Id("ActionType")); 
print int2str(de.configurationKeyId());
```

## Method displayLength

```xpp
public int displayLength([boolean useLongestLabel])
```

### Parameters - displayLength

useLongestLabel  

### Return Value - displayLength

## Method getCountryRegionCodes

```xpp
public container getCountryRegionCodes()
```

### Return Value - getCountryRegionCodes

## Method help

Retrieves the Help text for this enumeration.

```xpp
public str help([boolean useInterfaceLanguage])
```

### Parameters - help

useInterfaceLanguage  

### Return Value - help

A string that contains the Help text; an empty string if no Help text is defined.

### Remarks - help

The Help text is defined on the Help property of the base enumeration.

## Method helpDefined

Returns the value of the help property for this enumeration.

```xpp
public str helpDefined()
```

### Return Value - helpDefined

The value of the help property for this enumeration.

## Method id

Returns the enumeration ID of the enumeration.

```xpp
public EnumId id()
```

### Return Value - id

The enumeration ID of the enumeration.

## Method index2ConfigurationKey

```xpp
public ConfigurationKeyId index2ConfigurationKey(int index)
```

### Parameters - index2ConfigurationKey

index  

### Return Value - index2ConfigurationKey

## Method index2CountryRegionCodes

```xpp
public container index2CountryRegionCodes(int index)
```

### Parameters - index2CountryRegionCodes

index  

### Return Value - index2CountryRegionCodes

## Method index2Label

Returns the label of the enumeration item that is specified by an index.

```xpp
public str index2Label(int index)
```

### Parameters - index2Label

index  
The zero-based index of the enumeration in the AOT.

### Return Value - index2Label

The label of the enumeration item that specified by index; an empty string if index does not reference a valid enumeration item.

### Examples - index2Label

The following example shows the retrieval of the label for items in an enumeration.

```xpp
DictEnum de; 
int      i; 
de = new DictEnum(enumName2Id("ActionType")); 
for (i=0; i < de.values(); i++) 
{ 
    print int2str(i) + ", " + de.index2Label(i); 
}
```

## Method index2LabelId

```xpp
public str index2LabelId(int index)
```

### Parameters - index2LabelId

index  

### Return Value - index2LabelId

## Method index2Name

Returns the label of the enumeration item that is specified by an index.

```xpp
public str index2Name(int index)
```

### Parameters - index2Name

index  
The zero-based index of the enumeration in the AOT.

### Return Value - index2Name

The label of the enumeration item that is specified by index; an empty string if index does not reference a valid enumeration item.

### Remarks - index2Name

For backward compatibility with earlier versions, "Name" in DictEnum::value2Name refers to the enumeration item's label property. To make your code more readable, use the DictEnum::value2Label method instead of the DictEnum::value2Name method. To retrieve the value of the name property of the enumeration item as shown in the AOT, use the DictEnum::value2Symbol method.

### Examples - index2Name

The following example shows the retrieval of the label for items in an enumeration.

```xpp
DictEnum de; 
int      i; 
de = new DictEnum(enumName2Id("ActionType")); 
for (i=0; i < de.values(); i++) 
{ 
    print int2str(i) + ", " + de.index2Name(i); 
}
```

## Method index2Symbol

Returns the symbol or name of the enumeration item that is specified by an index.

```xpp
public str index2Symbol(int index)
```

### Parameters - index2Symbol

index  
The zero-based index of the enumeration in the AOT.

### Return Value - index2Symbol

The symbol of the enumeration item that is specified by index; an empty string if index does not reference a valid enumeration item.

### Remarks - index2Symbol

The symbol corresponds to the Name property of the enumeration item in the AOT.

### Examples - index2Symbol

The following example shows the retrieval of the symbol for items in an enumeration.

```xpp
DictEnum de; 
int      i; 
de = new DictEnum(enumName2Id("ActionType")); 
for (i=0; i < de.values(); i++) 
{ 
    print int2str(i) + ", " + de.index2Symbol(i); 
}
```

## Method index2Value

Returns the value of the enumeration item that is specified by an index.

```xpp
public int index2Value(int index)
```

### Parameters - index2Value

index  
The zero-based index of the enumeration in the AOT.

### Return Value - index2Value

The value of the enumeration item that is specified by index.

### Examples - index2Value

The following example shows the retrieval of the value for items in an enumeration.

```xpp
DictEnum de; 
int      i; 
de = new DictEnum(enumName2Id("ActionType")); 
for (i=0; i < de.values(); i++) 
{ 
    print int2str(i) + ", " + int2str(de.index2Value(i)); 
}
```

## Method label

Returns the label text of the enumeration.

```xpp
public str label()
```

### Return Value - label

The name of the enumeration; an empty string if there is no label for the enumeration.

## Method labelDefined

Returns the value of the label property for this enumeration.

```xpp
public str labelDefined()
```

### Return Value - labelDefined

The value of the label property for this enumeration.

## Method name

Returns the name of the enumeration.

```xpp
public str name()
```

### Return Value - name

The name of the enumeration.

## Method name2Value

Returns the enumeration value of the item that is referenced by its label.

```xpp
public int name2Value(str name)
```

### Parameters - name2Value

name  
The label for the enumeration for which the enumeration value is being retrieved.

### Return Value - name2Value

The enumeration value for name; 255 if name is not a valid label of an enumeration.

### Remarks - name2Value

For backward compatibility with earlier versions, name refers to the label. Enumeration items that do not have labels cannot be found by using the DictEnum::name2Value method.

## Method showAsRadio

Returns a value that indicates whether the enumeration should be displayed by using radio buttons instead of a combo box.

```xpp
public boolean showAsRadio()
```

### Return Value - showAsRadio

true if the enumeration style is radio button; otherwise, false.

## Method symbol2Value

Returns the enumeration value of the item, referenced by its symbol or name.

```xpp
public int symbol2Value(str name)
```

### Parameters - symbol2Value

name  
The symbol or name for the enumeration for which the enumeration value is being retrieved.

### Return Value - symbol2Value

The enumeration value for name; 255 if name is not a valid enumeration.

## Method value2ConfigurationKey

Returns the configuration key ID of a specified enumeration value.

```xpp
public ConfigurationKeyId value2ConfigurationKey(int value)
```

### Parameters - value2ConfigurationKey

value  
The integer value for the enumeration for which the configuration key is being retrieved.

### Return Value - value2ConfigurationKey

The configuration key ID for value; 0 (zero) if there is no configuration key for value or value is not a valid enumeration.

## Method value2CountryRegionCodes

```xpp
public container value2CountryRegionCodes(int value)
```

### Parameters - value2CountryRegionCodes

value  

### Return Value - value2CountryRegionCodes

## Method value2Label

Returns the label of a specified enumeration value.

```xpp
public str value2Label(int value)
```

### Parameters - value2Label

value  
The integer value for the enumeration for which the label is being retrieved.

### Return Value - value2Label

The label for value; an empty string if there is no label for value or value is not a valid enumeration.

### Remarks - value2Label

Enumeration items are not required to have a label. This method cannot be used to determine whether a value exists in the enumeration. To determine whether a value exists in the enumeration, use the DictEnum::value2Symbol method.

## Method value2Name

Returns the name of a specified enumeration value.

```xpp
public str value2Name(int value)
```

### Parameters - value2Name

value  
The integer value for the enumeration for which the label is being retrieved.

### Return Value - value2Name

The name for value; an empty string if there is no name for value or value is not a valid enumeration.

### Remarks - value2Name

To determine whether a value is in the enumeration, use the value2Symbol method instead. The value2Name method cannot be used to determine whether a value is in the enumeration, because enumeration items are not required to have a label.

## Method value2Symbol

Returns the symbol, or the value of the Name property, of a specified enumeration value.

```xpp
public str value2Symbol(int value)
```

### Parameters - value2Symbol

value  
The integer value for the enumeration for which the symbol is being retrieved.

### Return Value - value2Symbol

The symbol or name for value; an empty string if value is not a valid enumeration.

### Remarks - value2Symbol

Enumeration values are required to have a symbol. This method can be used to determine whether an enumeration value exists by checking whether the return value is an empty string.

## Method values

Returns the number of items in the enumeration.

```xpp
public int values()
```

### Return Value - values

The number of items in the enumeration.

### Remarks - values

Because values must be unique, the number of values is the same as the number of items.

### Examples - values

The following example shows how to retrieve the number of items in an enumeration and use that value in a loop.

```xpp
DictEnum de; 
int      i; 
de = new DictEnum(enumName2Id("ActionType")); 
for (i=0; i < de.values(); i++) 
{ 
    print int2str(i) + ", " + de.index2Name(i); 
}
```

## Method queryFilterNames2Values

```xpp
public static str queryFilterNames2Values(QueryFilter filter)
```

### Parameters - queryFilterNames2Values

filter  

### Return Value - queryFilterNames2Values

## Method queryFilterValues2Names

```xpp
public static str queryFilterValues2Names(QueryFilter filter)
```

### Parameters - queryFilterValues2Names

filter  

### Return Value - queryFilterValues2Names

## Method queryRangeNames2Values

```xpp
public static str queryRangeNames2Values(QueryBuildRange range)
```

### Parameters - queryRangeNames2Values

range  

### Return Value - queryRangeNames2Values

## Method queryRangeValues2Names

```xpp
public static str queryRangeValues2Names(QueryBuildRange range)
```

### Parameters - queryRangeValues2Names

range  

### Return Value - queryRangeValues2Names

## Method value2id

Returns the enumeration ID of a specified value.

```xpp
public static int value2id(AnyType value)
```

### Parameters - value2id

value  
The value for which the enumeration ID is being queried. The value parameter can be of any type.

### Return Value - value2id

The enumeration ID of value if value is an enumeration; otherwise, 0 (zero).

### Remarks - value2id

The value parameter can be of any type.

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(EnumId typeId)
```

### Parameters - new

typeId  
The ID of the enumeration.

### Remarks - new

The constructor does not fail if an invalid enum ID is supplied. However, when the DictEnum instance is used, a run-time error occurs. Note that EnumID values are unsigned integers and are therefore always in the range 0�65535.

### Examples - new

The following example creates an instance of the DictEnum class.

```xpp
DictEnum de; 
de = new DictEnum(enumName2Id("ActionType"));
```

