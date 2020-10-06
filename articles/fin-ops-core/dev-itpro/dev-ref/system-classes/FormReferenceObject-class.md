---
title: FormReferenceObject class
description: This topic describes the FormReferenceObject class.
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

# Class FormReferenceObject

[!include [banner](../../includes/banner.md)]

```xpp
class FormReferenceObject extends FormDataObject
```

## Remarks

## Examples

## Methods

| Method                                                                    | Description                                                                                                                                                             |
|---------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public int allowAdd(\[int value\])                                        | Sets or returns the value of the allowAdd property for the form data object.                                                                                            |
| public boolean allowEdit(\[boolean value\])                               | Indicates whether the user can change the contents of the control.                                                                                                      |
| public FieldId dataField(\[FieldId value\])                               |                                                                                                                                                                         |
| public boolean enabled(\[boolean value\])                                 | Indicates whether to enable or disable the object.                                                                                                                      |
| public Common lookupReference(FormReferenceControl formReferenceControl)  |                                                                                                                                                                         |
| public boolean mandatory(\[boolean value\])                               | Sets or returns a value that indicates whether the data field is mandatory.                                                                                             |
| public Common resolveReference(FormReferenceControl formReferenceControl) |                                                                                                                                                                         |
| public boolean skip(\[boolean value\])                                    | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control that is associated with the data source. |
| public boolean visible(\[boolean value\])                                 | Sets or returns a value that indicates whether the control is visible.                                                                                                  |

## Method allowAdd

Sets or returns the value of the allowAdd property for the form data object.

```xpp
public int allowAdd([int value])
```

### Parameters - allowAdd

value  
The value that is assigned to the allowEdit property.

### Return Value - allowAdd

A FormAllowAdd enumeration value that indicates whether the allowAdd property is set to No, Restricted, or Yes.

## Method allowEdit

Indicates whether the user can change the contents of the control.

```xpp
public boolean allowEdit([boolean value])
```

### Parameters - allowEdit

value  

### Return Value - allowEdit

true if the control can be edited; otherwise, false.

### Remarks - allowEdit

When this property is set on a container control, modifications are disabled or enabled for all controls in the container.

## Method dataField

```xpp
public FieldId dataField([FieldId value])
```

### Parameters - dataField

value  

### Return Value - dataField

## Method enabled

Indicates whether to enable or disable the object.

```xpp
public boolean enabled([boolean value])
```

### Parameters - enabled

value  

### Return Value - enabled

true if the object is enabled; otherwise, false.

### Remarks - enabled

The enabled property allows for controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

## Method lookupReference

```xpp
public Common lookupReference(FormReferenceControl formReferenceControl)
```

### Parameters - lookupReference

formReferenceControl  

### Return Value - lookupReference

## Method mandatory

Sets or returns a value that indicates whether the data field is mandatory.

```xpp
public boolean mandatory([boolean value])
```

### Parameters - mandatory

value  
The value that is assigned to the mandatory property of the field.

### Return Value - mandatory

true if the field is mandatory; otherwise, false.

## Method resolveReference

```xpp
public Common resolveReference(FormReferenceControl formReferenceControl)
```

### Parameters - resolveReference

formReferenceControl  

### Return Value - resolveReference

## Method skip

Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control that is associated with the data source.

```xpp
public boolean skip([boolean value])
```

### Parameters - skip

value  
The value that is assigned to the skip property of the data source that is associated with the control; optional.

### Return Value - skip

true if the control is skipped when the user presses the TAB key to move to the control associated with the data source; otherwise, false.

### Remarks - skip

If the enabled property is true, the allowEdit property is false, and the skip property is true, the user cannot change the contents of the control but can still copy the contents of the control. Controls are skipped if the skip value of either the control or the data source is true.

## Method visible

Sets or returns a value that indicates whether the control is visible.

```xpp
public boolean visible([boolean value])
```

### Parameters - visible

value  
The value that is assigned to the visibility setting for the control.

### Return Value - visible

true if the control is visible; otherwise, false. The default is true.

### Remarks - visible

Controls that refer to a data source field are visible only when the visible property is set to true on both the control and the underlying data source field. By setting the property on the data source field instead of the control, you make sure that the field is handled consistently throughout the form. This makes upgrades easier.

