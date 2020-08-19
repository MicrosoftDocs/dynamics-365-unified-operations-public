---
title: FormDataObject class
description: This topic describes the FormDataObject class.
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

# Class FormDataObject

[!include [banner](../../includes/banner.md)]


```xpp
class FormDataObject extends FormObject
```

The FormDataObject class represents the fields, affects how controls that refer to a field are displayed on form data sources, and modifies lookup and validation behavior.

## Remarks

By changing the properties, you affect how controls that refer to the field are displayed. Furthermore, if you override the methods on this class, the behavior on lookup and validation can be modified. By using the properties on the FormDataObject class instead of properties on the individual controls, you make sure that the various representations of the same field are handled consistently. This also makes upgrades easier.

## Examples

## Methods

| Method                                                                                                      | Description                                                                                                                                                             |
|-------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public Common lookupReference(\[FormReferenceControl formReferenceControl\])                                |                                                                                                                                                                         |
| public Common resolveReference(\[FormReferenceControl formReferenceControl\])                               |                                                                                                                                                                         |
| public str resolveAmbiguousReference(\[FormControl formControl\])                                           |                                                                                                                                                                         |
| public int allowAdd(\[int value\])                                                                          | Sets or returns the value of the allowAdd property for the form data object.                                                                                            |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can modify the contents of the control.                                                                                                     |
| public FieldId dataField(\[FieldId value\])                                                                 |                                                                                                                                                                         |
| public FormDataSource datasource()                                                                          |                                                                                                                                                                         |
| public boolean editAutoPostback(\[boolean value\])                                                          |                                                                                                                                                                         |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether the object is enabled or disabled.                                                                                                                   |
| public FieldId fieldId()                                                                                    |                                                                                                                                                                         |
| public str helpField()                                                                                      | Returns the Help text for the control.                                                                                                                                  |
| public str labelText()                                                                                      | Returns the label text for the control.                                                                                                                                 |
| public boolean mandatory(\[boolean value\])                                                                 | Sets or returns a value that indicates whether the data field is mandatory.                                                                                             |
| public boolean skip(\[boolean value\])                                                                      | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control that is associated with the data source. |
| public str toolTip()                                                                                        |                                                                                                                                                                         |
| public boolean validate()                                                                                   |                                                                                                                                                                         |
| public boolean visible(\[boolean value\])                                                                   | Sets or returns a value that indicates whether the control is visible.                                                                                                  |
| private void OnModified(\[FormDataObject sender\], \[FormDataFieldEventArgs e\])                            |                                                                                                                                                                         |
| private void OnValidated(\[FormDataObject sender\], \[FormDataFieldEventArgs e\])                           |                                                                                                                                                                         |
| public void modified()                                                                                      | Indicates that the field has been successfully validated and modified in the current record.                                                                            |
| private void OnValidating(\[FormDataObject sender\], \[FormDataFieldEventArgs e\])                          |                                                                                                                                                                         |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                                                         |
| public void restore()                                                                                       |                                                                                                                                                                         |
| public void lookup(FormControl formControl, str filterStr)                                                  |                                                                                                                                                                         |
| public void dataChanged()                                                                                   |                                                                                                                                                                         |
| public void jumpRef()                                                                                       |                                                                                                                                                                         |
| public void context()                                                                                       |                                                                                                                                                                         |
| public void find()                                                                                          |                                                                                                                                                                         |
| public void filter(\[str filterStr\], \[NoYes clearPrev\])                                                  |                                                                                                                                                                         |
| public void performFormLookup(xFormRun form, FormControl formControl)                                       |                                                                                                                                                                         |

## Method lookupReference

```xpp
public Common lookupReference([FormReferenceControl formReferenceControl])
```

### Parameters - lookupReference

formReferenceControl  

### Return Value - lookupReference

## Method resolveReference

```xpp
public Common resolveReference([FormReferenceControl formReferenceControl])
```

### Parameters - resolveReference

formReferenceControl  

### Return Value - resolveReference

## Method resolveAmbiguousReference

```xpp
public str resolveAmbiguousReference([FormControl formControl])
```

### Parameters - resolveAmbiguousReference

formControl  

### Return Value - resolveAmbiguousReference

## Method allowAdd

Sets or returns the value of the allowAdd property for the form data object.

```xpp
public int allowAdd([int value])
```

### Parameters - allowAdd

value  
The value to assign to the allowEdit property.

### Return Value - allowAdd

A FormAllowAdd enumeration value that indicates whether the allowAdd property is set to No, Restricted, or Yes.

### Examples - allowAdd

The following example shows how to retrieve and set the allowAdd property.

```xpp
// fdo previously assigned to a FormDataObject object. 
// Retrieve the allowAdd property. 
nAllowAdd = fdo.allowAdd(); 
// Set the allowAdd property. 
fdo.allowAdd(FormAllowAdd::Restricted);
```

## Method allowEdit

Determines whether the user can modify the contents of the control.

```xpp
public boolean allowEdit([boolean value])
```

### Parameters - allowEdit

value  
The value to assign to the allowEdit property.

### Return Value - allowEdit

true if the control can be modified; otherwise, false.

### Remarks - allowEdit

If this property is set on a container control, modifications are disabled or enabled for all controls in the container.

### Examples - allowEdit

The following example shows how to retrieve and set the value of the allowEdit property.

```xpp
// Return the value. 
info (strfmt("allowEdit: %1", this.allowEdit())); 
// Set the value. 
this.allowEdit(false);
```

## Method dataField

```xpp
public FieldId dataField([FieldId value])
```

### Parameters - dataField

value  

### Return Value - dataField

## Method datasource

```xpp
public FormDataSource datasource()
```

### Return Value - datasource

## Method editAutoPostback

```xpp
public boolean editAutoPostback([boolean value])
```

### Parameters - editAutoPostback

value  

### Return Value - editAutoPostback

## Method enabled

Determines whether the object is enabled or disabled.

```xpp
public boolean enabled([boolean value])
```

### Parameters - enabled

value  
A Boolean value that specifies whether the control is enabled.

### Return Value - enabled

true if the object is enabled; otherwise, false.

### Remarks - enabled

The enabled property lets you enable or disable a control at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message that provides read-only information.

### Examples - enabled

The following example shows how to retrieve and set the enabled property for a control.

```xpp
// Return the value of the enabled property. 
info(strfmt("enabled: %1", this.enabled())); 
// Set the enabled property. 
this.enabled(false);
```

## Method fieldId

```xpp
public FieldId fieldId()
```

### Return Value - fieldId

## Method helpField

Returns the Help text for the control.

```xpp
public str helpField()
```

### Return Value - helpField

The Help text for the control; an empty string if there is no Help text for the control.

### Examples - helpField

The following example shows how to use the helpField method.

```xpp
str strHelp; 
strHelp = this.helpField();
```

## Method labelText

Returns the label text for the control.

```xpp
public str labelText()
```

### Return Value - labelText

The label text for the control; an empty string if there is no label text for the control.

## Method mandatory

Sets or returns a value that indicates whether the data field is mandatory.

```xpp
public boolean mandatory([boolean value])
```

### Parameters - mandatory

value  
The value to assign to the mandatory property of the field.

### Return Value - mandatory

true if the field is mandatory; otherwise, false.

### Examples - mandatory

The following example shows how to retrieve and set the mandatory property for the field.

```xpp
// Return the value of the mandatory property. 
info (strfmt("mandatory: %1", fdo.mandatory())); 
// Set the value of the mandatory property. 
fdo.mandatory(false);
```

## Method skip

Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control that is associated with the data source.

```xpp
public boolean skip([boolean value])
```

### Parameters - skip

value  
The value to assign to the skip property of the data source that is associated with the control; optional.

### Return Value - skip

true if the control is skipped when the user presses the TAB key to move to the control that is associated with the data source; otherwise, false.

### Remarks - skip

If the enabled property is true, the allowEdit property is false, and the skip property is true, the user cannot change the contents of the control but can still copy the contents of the control. Controls are skipped if either the control's skip value is true or the data source's skip value is true.

### Examples - skip

The following shows how to retrieve and set the skip property of a data source for a control.

```xpp
// Return the value of the skip property. 
info(strfmt("skip: %1", this.skip())); 
// Set the value of the skip property. 
this.skip(true);
```

## Method toolTip

```xpp
public str toolTip()
```

### Return Value - toolTip

## Method validate

```xpp
public boolean validate()
```

### Return Value - validate

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

Controls that refer to a data source field are visible only when the visible property is set to true on both the control and the underlying data source field. If you set the property on the data source field instead of on the control, you guarantee that the field is handled consistently throughout the form. This makes upgrades easier.

## Method OnModified

```xpp
private void OnModified([FormDataObject sender], [FormDataFieldEventArgs e])
```

### Parameters - OnModified

sender  

<!-- -->

e  

## Method OnValidated

```xpp
private void OnValidated([FormDataObject sender], [FormDataFieldEventArgs e])
```

### Parameters - OnValidated

sender  

<!-- -->

e  

## Method modified

Indicates that the field has been successfully validated and modified in the current record.

```xpp
public void modified()
```

### Remarks - modified

This method is called from the modified method on controls if the validation methods returned true. You can override this method to allow for recalculation of other values that are based on the modified values. The call to the super() method guarantees that the modifiedField method on the table is called. Modified means that the value of the field on the current record has changed, but the value is not written to the database before the record is saved.

## Method OnValidating

```xpp
private void OnValidating([FormDataObject sender], [FormDataFieldEventArgs e])
```

### Parameters - OnValidating

sender  

<!-- -->

e  

## Method registerOverrideMethod

```xpp
public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])
```

### Parameters - registerOverrideMethod

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

## Method restore

```xpp
public void restore()
```

## Method lookup

```xpp
public void lookup(FormControl formControl, str filterStr)
```

### Parameters - lookup

formControl  

<!-- -->

filterStr  

## Method dataChanged

```xpp
public void dataChanged()
```

## Method jumpRef

```xpp
public void jumpRef()
```

## Method context

```xpp
public void context()
```

## Method find

```xpp
public void find()
```

## Method filter

```xpp
public void filter([str filterStr], [NoYes clearPrev])
```

### Parameters - filter

filterStr  

<!-- -->

clearPrev  

## Method performFormLookup

```xpp
public void performFormLookup(xFormRun form, FormControl formControl)
```

### Parameters - performFormLookup

form  

<!-- -->

formControl  

