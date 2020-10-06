---
title: DictType class
description: This topic describes the DictType class.
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

# Class DictType

[!include [banner](../../includes/banner.md)]

```xpp
class DictType extends Object
```

The DictType class manages extended data types.

## Remarks

The SysDictType class extends DictType.

## Examples

## Methods

| Method                                                                | Description                                                                                                                                                              |
|-----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public Alignment alignment()                                          | Retrieves the alignment for the extended data type.                                                                                                                      |
| public int arraySize()                                                | Provides the array size for an extended data type.                                                                                                                       |
| public Types baseType()                                               | Provides the data type on which an extended data type is based, by using the Types enumeration.                                                                          |
| public ConfigurationKeyId configurationKeyId()                        | Returns the ID of the configuration key for the extended data type.                                                                                                      |
| public int displayHeight(\[boolean useDefaults\])                     | Retrieves the display height for the type.                                                                                                                               |
| public int displayLength(\[boolean useDefaults\])                     |                                                                                                                                                                          |
| public EnumId enumId()                                                | Provides the ID for the enumeration type on which an extended data type is based.                                                                                        |
| public ExtendedTypeId extend()                                        | Provides the ID for the extended data type that an extended data type extends.                                                                                           |
| public List extendedBy(\[boolean allLevels\])                         | Retrieves a list of type IDs for extended data types (EDTs) that are extended by the current EDT.                                                                        |
| public str formHelp()                                                 |                                                                                                                                                                          |
| public str getControlClass()                                          |                                                                                                                                                                          |
| public container getCountryRegionCodes()                              | Retrieves a container that holds the country/region codes that are defined.                                                                                              |
| public DictRelation getLookupRelation(\[int arrayIndex\])             |                                                                                                                                                                          |
| public AnyType getValue(\[int arrayIndex\])                           |                                                                                                                                                                          |
| public str help(\[int arrayIndex\], \[boolean useInterfaceLanguage\]) | Provides the Help text that is displayed for an extended data type or a specified array element, or for the extended data type that an extended data type extends.       |
| public str helpDefined(\[int arrayIndex\])                            | Returns the value of the help property for the extended data type.                                                                                                       |
| public ExtendedTypeId id()                                            | Provides the ID for an extended data type.                                                                                                                               |
| public boolean isExtendedFrom(str baseEDTName)                        | Determines whether the extended data type extends from the base extended data type that is provided.                                                                     |
| public int isRadioStyle()                                             | Indicates whether the style of an extended data type that is based on an Enum data type is a radio button or a combo box.                                                |
| public str label(\[int arrayIndex\])                                  | Provides the label that is displayed for an extended data type or a specified array element, or the label for the extended data type that an extended data type extends. |
| public str labelDefined(\[int arrayIndex\])                           | Returns the value of the label property for the extended data type.                                                                                                      |
| public str lookupTable(\[boolean useInheritedMetaData\])              |                                                                                                                                                                          |
| public str name()                                                     | Provides the name of an extended data type.                                                                                                                              |
| public DictRelation relationObject(\[int arrayIndex\])                | Provides information about relations that are defined for an extended data type or a specified array element by returning a DictRelation object.                         |
| public int stringLen()                                                | Provides the string length for an extended data type that is based on the string data type.                                                                              |
| public boolean stringRight()                                          | Indicates whether the string is right-justified for an extended data type that is based on the string data type.                                                         |
| ::public static Alignment getTypeAlignment(Types type)                |                                                                                                                                                                          |
| ::public static int getTypeDisplayHeight(Types type)                  |                                                                                                                                                                          |
| ::public static int getTypeDisplayLength(Types type)                  | Retrieves the display length for built-in types.                                                                                                                         |
| public void setValue(AnyType Value, \[int arrayEntry\])               |                                                                                                                                                                          |
| public void new(ExtendedTypeId typeId)                                | Initializes a new instance of the Object class.                                                                                                                          |
| public void setStringLen(int stringLen)                               | Sets the string length for an extended data type that is based on the string data type.                                                                                  |
| public void setStringRight(boolean right)                             | Indicates the string justification for an extended data type that is based on a String data type.                                                                        |

## Method alignment

Retrieves the alignment for the extended data type.

```xpp
public Alignment alignment()
```

### Return Value - alignment

The alignment for the extended data type.

## Method arraySize

Provides the array size for an extended data type.

```xpp
public int arraySize()
```

### Return Value - arraySize

An integer value for the array size; 1 if an extended data type does not have array elements.

### Examples - arraySize

In the following example, the arraySize method returns the array size for the XMLMapDimension extended data type.

```xpp
    DictType dicttype; 
    int i; 
    dicttype = new DictType(extendedTypeNum(XMLMapDimension)); 
    for (i = 1;  i < dicttype.arraySize(); i++) 
    { 
        print dicttype.label(i); 
        pause; 
    }
```

## Method baseType

Provides the data type on which an extended data type is based, by using the Types enumeration.

```xpp
public Types baseType()
```

### Return Value - baseType

A Types enumeration value that indicates the data type.

### Remarks - baseType

You can convert the return value to a string by using the Global::Enum2Value method.

## Method configurationKeyId

Returns the ID of the configuration key for the extended data type.

```xpp
public ConfigurationKeyId configurationKeyId()
```

### Return Value - configurationKeyId

The ID of the configuration key for the extended data type.

## Method displayHeight

Retrieves the display height for the type.

```xpp
public int displayHeight([boolean useDefaults])
```

### Parameters - displayHeight

useDefaults  
A Boolean value that indicates whether to use the default values if the type does not have a length.

### Return Value - displayHeight

The display height for the type.

## Method displayLength

```xpp
public int displayLength([boolean useDefaults])
```

### Parameters - displayLength

useDefaults  

### Return Value - displayLength

## Method enumId

Provides the ID for the enumeration type on which an extended data type is based.

```xpp
public EnumId enumId()
```

### Return Value - enumId

The ID of the enumeration type on which the extended data type is based; 0 (zero) if the extended data type is not based on an enumeration.

### Remarks - enumId

You can use the baseType method to determine what the data type of an extended data type is.

## Method extend

Provides the ID for the extended data type that an extended data type extends.

```xpp
public ExtendedTypeId extend()
```

### Return Value - extend

The ID for the extended data type than an extended data type extends; 0 (zero) if the extended data type does not extend an extended data type.

### Examples - extend

In the following example, the extend method returns the ID for the extended data type that the ABCPercentA extended data type extends.

```xpp
    DictType dicttype; 
    dicttype = new DictType(extendedTypeNum(ABCPercentA)); 
    print dicttype.name() + " extends: " + extendedTypeId2Name(dicttype.extend());
```

## Method extendedBy

Retrieves a list of type IDs for extended data types (EDTs) that are extended by the current EDT.

```xpp
public List extendedBy([boolean allLevels])
```

### Parameters - extendedBy

allLevels  

### Return Value - extendedBy

A list of type IDs for EDTs that are extended by the current EDT.

## Method formHelp

```xpp
public str formHelp()
```

### Return Value - formHelp

## Method getControlClass

```xpp
public str getControlClass()
```

### Return Value - getControlClass

## Method getCountryRegionCodes

Retrieves a container that holds the country/region codes that are defined.

```xpp
public container getCountryRegionCodes()
```

### Return Value - getCountryRegionCodes

A container that holds country/region codes.

## Method getLookupRelation

```xpp
public DictRelation getLookupRelation([int arrayIndex])
```

### Parameters - getLookupRelation

arrayIndex  

### Return Value - getLookupRelation

## Method getValue

```xpp
public AnyType getValue([int arrayIndex])
```

### Parameters - getValue

arrayIndex  

### Return Value - getValue

## Method help

Provides the Help text that is displayed for an extended data type or a specified array element, or for the extended data type that an extended data type extends.

```xpp
public str help([int arrayIndex], [boolean useInterfaceLanguage])
```

### Parameters - help

arrayIndex  
A Boolean value that indicates whether the user interface language is used for the Help text; optional.

<!-- -->

useInterfaceLanguage  
A Boolean value that indicates whether the user interface language is used for the Help text; optional.

### Return Value - help

A string value for the Help text that is displayed for the extended data type, or for an array element if the arrayEntry value is provided. The Help text corresponds to the Help Text property for an extended data type or array element in the Application Object Tree (AOT). When an extended data type does not have Help text, the method returns the Help text that is defined for the extended data type that the extended data type extends.

## Method helpDefined

Returns the value of the help property for the extended data type.

```xpp
public str helpDefined([int arrayIndex])
```

### Parameters - helpDefined

arrayIndex  

### Return Value - helpDefined

The value of the help property for the extended data type, or for an array element if the arrayEntry value is provided. The Help text corresponds to the Help Text property for an extended data type or array element in the AOT.

## Method id

Provides the ID for an extended data type.

```xpp
public ExtendedTypeId id()
```

### Return Value - id

A data type value that indicates the ID for an extended data type.

## Method isExtendedFrom

Determines whether the extended data type extends from the base extended data type that is provided.

```xpp
public boolean isExtendedFrom(str baseEDTName)
```

### Parameters - isExtendedFrom

baseEDTName  
The name of the extended data type.

### Return Value - isExtendedFrom

true if the extended data type extends from the base extended data type that is provided; otherwise, false.

## Method isRadioStyle

Indicates whether the style of an extended data type that is based on an Enum data type is a radio button or a combo box.

```xpp
public int isRadioStyle()
```

### Return Value - isRadioStyle

1 if the style is a radio button; otherwise, 0 (zero).

## Method label

Provides the label that is displayed for an extended data type or a specified array element, or the label for the extended data type that an extended data type extends.

```xpp
public str label([int arrayIndex])
```

### Parameters - label

arrayIndex  

### Return Value - label

The label that is displayed for an extended data type, or the label for an array element if the arrayEntry value is provided. When an extended data type does not have a label, this method returns the label defined for the extended data type that an extended data type extends.

### Remarks - label

The label that is returned corresponds to the Label property for an extended data type or array element in the AOT.

## Method labelDefined

Returns the value of the label property for the extended data type.

```xpp
public str labelDefined([int arrayIndex])
```

### Parameters - labelDefined

arrayIndex  

### Return Value - labelDefined

The value of the label property for the extended data type, or for an array element if the arrayEntry value is provided.

### Remarks - labelDefined

The return value corresponds to the Label property for an extended data type or array element in the AOT.

## Method lookupTable

```xpp
public str lookupTable([boolean useInheritedMetaData])
```

### Parameters - lookupTable

useInheritedMetaData  

### Return Value - lookupTable

## Method name

Provides the name of an extended data type.

```xpp
public str name()
```

### Return Value - name

A string value for the name. The name corresponds to the Name property for an extended data type in the AOT.

## Method relationObject

Provides information about relations that are defined for an extended data type or a specified array element by returning a DictRelation object.

```xpp
public DictRelation relationObject([int arrayIndex])
```

### Parameters - relationObject

arrayIndex  

### Return Value - relationObject

A DictRelation object that provides information about relations.

### Remarks - relationObject

If no relations are defined for the extended data type and array elements, subsequent use of the DictRelation instance will cause a run-time error.

### Examples - relationObject

In the following example, the relationObject method returns the DictRelation object for the XMLMapDimension extended data type.

```xpp
    DictType dicttype; 
    DictRelation dictrelation; 
    dicttype = new DictType(extendedTypeNum(XMLMapDimension)); 
    dictrelation = dicttype.relationObject(); 
    if(dictrelation) 
    { 
        print "Relation lines: " + int2str(dictrelation.lines()); 
    } 
    else 
    { 
        print "No relations defined."; 
     }
```

## Method stringLen

Provides the string length for an extended data type that is based on the string data type.

```xpp
public int stringLen()
```

### Return Value - stringLen

An integer that indicates the string length; 0 (zero) if an extended data type is not based on the string data type.

## Method stringRight

Indicates whether the string is right-justified for an extended data type that is based on the string data type.

```xpp
public boolean stringRight()
```

### Return Value - stringRight

true if the string is right-justified; otherwise, false.

### Remarks - stringRight

The return value corresponds to the Adjustment property for the extended data type in the AOT.

## Method getTypeAlignment

```xpp
public static Alignment getTypeAlignment(Types type)
```

### Parameters - getTypeAlignment

type  

### Return Value - getTypeAlignment

## Method getTypeDisplayHeight

```xpp
public static int getTypeDisplayHeight(Types type)
```

### Parameters - getTypeDisplayHeight

type  

### Return Value - getTypeDisplayHeight

## Method getTypeDisplayLength

Retrieves the display length for built-in types.

```xpp
public static int getTypeDisplayLength(Types type)
```

### Parameters - getTypeDisplayLength

type  
The type.

### Return Value - getTypeDisplayLength

The display length for the built-in type.

## Method setValue

```xpp
public void setValue(AnyType Value, [int arrayEntry])
```

### Parameters - setValue

Value  

<!-- -->

arrayEntry  

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(ExtendedTypeId typeId)
```

### Parameters - new

typeId  
A data type that indicates the ID for an extended data type.

### Remarks - new

This constructor does not fail if the typeId value is an invalid extended data type ID; however, when the DictType instance is used, a run-time error occurs. You can pass the name of the extended data type instead of an ID by using the extendedTypeNum function.

### Examples - new

The following example shows how to create an instance of the DictType class.

```xpp
    DictType dicttype; 
    dicttype = new DictType(extendedTypeNum(ABCModelType));
```

## Method setStringLen

Sets the string length for an extended data type that is based on the string data type.

```xpp
public void setStringLen(int stringLen)
```

### Parameters - setStringLen

stringLen  
An integer that indicates the string length.

### Remarks - setStringLen

This method lets you create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before this API is called. The string length corresponds to the StringSize property for the extended data type in the AOT.

### Examples - setStringLen

The following example sets the StringSize property to 10 for the AccountName extended data type.

```xpp
server static public void Main(Args _args) 
{ 
    DictType  dt; 
    dt = new DictType(ExtendedTypeNum(AccountName)); 
    if (dt) 
    { 
        dt.setStringLen(10); 
    } 
}
```

## Method setStringRight

Indicates the string justification for an extended data type that is based on a String data type.

```xpp
public void setStringRight(boolean right)
```

### Parameters - setStringRight

right  
A Boolean value: true for a right-justified string and false for a left-justified string.

### Remarks - setStringRight

This method lets you create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples - setStringRight

The following example sets the justification of the AccountName extended data type.

```xpp
server static public void Main(Args _args) 
{ 
    DictType dt; 
    dt = new DictType(ExtendedTypeNum(AccountName)); 
    if (dt) 
    { 
        dt.setStringRight(true); 
    } 
}
```

