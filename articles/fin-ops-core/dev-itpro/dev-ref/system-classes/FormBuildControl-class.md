---
title: FormBuildControl class
description: This topic describes the FormBuildControl class.
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

# Class FormBuildControl

[!include [banner](../../includes/banner.md)]

```xpp
class FormBuildControl extends Object
```

The FormBuildControl class lets you create, read, update, and delete X++ code and metadata.

## Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

## Examples

## Methods

| Method                                                                                                                                    | Description                                                                                                                                        |
|-------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| public FormBuildControl addControl(FormControlType controlType, str controlName, \[FormBuildControl insertAfter\], \[boolean pushFront\]) | Adds a control to the control, based on the specified control type.                                                                                |
| public FormBuildControl addControlEx(str controlClass, str controlName, \[FormBuildControl insertAfter\], \[boolean pushFront\])          |                                                                                                                                                    |
| public FormBuildControl addDataField(int dataSourceId, FieldId fieldId, \[int arrayIndex\])                                               | Adds a control to the control, based on the specified data field information.                                                                      |
| public boolean allowEdit(\[boolean value\])                                                                                               |                                                                                                                                                    |
| public boolean autoDeclaration(\[boolean value\])                                                                                         |                                                                                                                                                    |
| public boolean canAddDataField(int dataSourceId, FieldId fieldId, \[int arrayIndex\])                                                     | Retrieves a value that indicates whether the specified data field can be added as a child control to the control.                                  |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                                                  |                                                                                                                                                    |
| public int containerId()                                                                                                                  | Retrieves the ID of the parent container for the control.                                                                                          |
| public int controlCount()                                                                                                                 | Retrieves the number of controls that are contained in the control.                                                                                |
| public FormBuildControl controlNum(int controlNo)                                                                                         | Retrieves a contained control by using the specified index.                                                                                        |
| public str countryRegionCodes(\[str value\])                                                                                              |                                                                                                                                                    |
| public boolean editAutoPostback(\[boolean value\])                                                                                        |                                                                                                                                                    |
| public boolean enabled(\[boolean value\])                                                                                                 |                                                                                                                                                    |
| public str helpText(\[str value\])                                                                                                        |                                                                                                                                                    |
| public str extendedStyle(\[str value\])                                                                                                   |                                                                                                                                                    |
| public int height(int value, \[int mode\])                                                                                                |                                                                                                                                                    |
| public int heightMode(\[int value\])                                                                                                      |                                                                                                                                                    |
| public int heightValue(\[int value\])                                                                                                     |                                                                                                                                                    |
| public str GetXppILImplementation()                                                                                                       |                                                                                                                                                    |
| public boolean hasUserSetting()                                                                                                           | Indicates whether the control has custom user settings.                                                                                            |
| public int id()                                                                                                                           | Retrieves the ID of the control.                                                                                                                   |
| public boolean isContainer()                                                                                                              | Retrieves a value that indicates whether the control is a container control.                                                                       |
| public boolean markAsUserAdd(\[boolean value\])                                                                                           | Marks or unmarks the control as a user-added control.                                                                                              |
| public int moveControl(int controlId, \[int insertAfterId\])                                                                              | Moves a specified control to the control.                                                                                                          |
| public str name(\[str value\])                                                                                                            |                                                                                                                                                    |
| public int neededPermission(\[int value\])                                                                                                |                                                                                                                                                    |
| public container SysObsoleteAttribute()                                                                                                   |                                                                                                                                                    |
| public str previewPartRef(\[str value\])                                                                                                  |                                                                                                                                                    |
| public boolean skip(\[boolean value\])                                                                                                    |                                                                                                                                                    |
| public boolean SysObsoleteAttribute(container data)                                                                                       |                                                                                                                                                    |
| public int userDisable(\[int value\])                                                                                                     | Gets or sets the value that indicates whether the control is disabled for the user.                                                                |
| public int userHeight(\[int value\])                                                                                                      | Gets or sets the custom user height for the control.                                                                                               |
| public int userHide(\[int value\])                                                                                                        | Gets or sets the value that indicates whether the control is hidden from the user.                                                                 |
| public int userOrgContainer(\[int value\])                                                                                                | Gets or sets the organization container for the control.                                                                                           |
| public int userOrgSibling(\[int value\])                                                                                                  | Gets or sets the organization sibling for the control.                                                                                             |
| public str userPromptText(\[str value\])                                                                                                  | Gets or sets the user label text for the control.                                                                                                  |
| public int userSecurityLevel(\[int value\])                                                                                               | Gets or sets the user security level for the control.                                                                                              |
| public int userSkip(\[int value\])                                                                                                        | Sets or returns the value that indicates whether the form control is skipped when the user press the TAB key to navigate the controls on the form. |
| public int userWidth(\[int value\])                                                                                                       | Sets or returns the width of the control in pixels.                                                                                                |
| public boolean visible(\[boolean value\])                                                                                                 |                                                                                                                                                    |
| public int width(int value, \[int mode\])                                                                                                 |                                                                                                                                                    |
| public int widthMode(\[int value\])                                                                                                       |                                                                                                                                                    |
| public int widthValue(\[int value\])                                                                                                      |                                                                                                                                                    |
| public void RegisterXppILImplementation(str className)                                                                                    |                                                                                                                                                    |
| public void new(FormContainer container)                                                                                                  |                                                                                                                                                    |
| public void resetUserSetting()                                                                                                            | Resets the user settings for the control.                                                                                                          |

## Method addControl

Adds a control to the control, based on the specified control type.

```xpp
public FormBuildControl addControl(FormControlType controlType, str controlName, [FormBuildControl insertAfter], [boolean pushFront])
```

### Parameters - addControl

controlType  
The string value to set the name of the new control to.

<!-- -->

controlName  
The string value to set the name of the new control to.

<!-- -->

insertAfter  

<!-- -->

pushFront  

### Return Value - addControl

A FormBuildControl object that represents the newly added control.

## Method addControlEx

```xpp
public FormBuildControl addControlEx(str controlClass, str controlName, [FormBuildControl insertAfter], [boolean pushFront])
```

### Parameters - addControlEx

controlClass  

<!-- -->

controlName  

<!-- -->

insertAfter  

<!-- -->

pushFront  

### Return Value - addControlEx

## Method addDataField

Adds a control to the control, based on the specified data field information.

```xpp
public FormBuildControl addDataField(int dataSourceId, FieldId fieldId, [int arrayIndex])
```

### Parameters - addDataField

dataSourceId  
An integer value that indicates the index of the data field type; optional.

<!-- -->

fieldId  
An integer value that indicates the index of the data field type; optional.

<!-- -->

arrayIndex  
An integer value that indicates the index of the data field type; optional.

### Return Value - addDataField

A FormBuildControl object that represents the newly added control.

### Remarks - addDataField

The type of control that should be added is determined automatically, based on the specified data field information. The arrayIndex parameter has a default value of 1 when a value is not specified, so that the first index is assumed.

## Method allowEdit

```xpp
public boolean allowEdit([boolean value])
```

### Parameters - allowEdit

value  

### Return Value - allowEdit

## Method autoDeclaration

```xpp
public boolean autoDeclaration([boolean value])
```

### Parameters - autoDeclaration

value  

### Return Value - autoDeclaration

## Method canAddDataField

Retrieves a value that indicates whether the specified data field can be added as a child control to the control.

```xpp
public boolean canAddDataField(int dataSourceId, FieldId fieldId, [int arrayIndex])
```

### Parameters - canAddDataField

dataSourceId  
An integer value that indicates the index of the data field type; optional.

<!-- -->

fieldId  
An integer value that indicates the index of the data field type; optional.

<!-- -->

arrayIndex  
An integer value that indicates the index of the data field type; optional.

### Return Value - canAddDataField

A Boolean value that indicates whether the specified data field can be added as a child control to the control.

## Method configurationKey

```xpp
public ConfigurationKeyId configurationKey([ConfigurationKeyId value])
```

### Parameters - configurationKey

value  

### Return Value - configurationKey

## Method containerId

Retrieves the ID of the parent container for the control.

```xpp
public int containerId()
```

### Return Value - containerId

The ID of the parent container.

## Method controlCount

Retrieves the number of controls that are contained in the control.

```xpp
public int controlCount()
```

### Return Value - controlCount

An integer value that indicates the number of controls that are contained in the control if it is a container control; otherwise, 0.

## Method controlNum

Retrieves a contained control by using the specified index.

```xpp
public FormBuildControl controlNum(int controlNo)
```

### Parameters - controlNum

controlNo  
An integer value that indicates the index of the child control to retrieve.

### Return Value - controlNum

A FormBuildControl object that represents the child control that has the specified index if this is a container control; otherwise, nullNothingnullptrunita null reference (Nothing in Visual Basic).

### Remarks - controlNum

If the specified controlNo parameter is out of range, an exception is raised.

## Method countryRegionCodes

```xpp
public str countryRegionCodes([str value])
```

### Parameters - countryRegionCodes

value  

### Return Value - countryRegionCodes

## Method editAutoPostback

```xpp
public boolean editAutoPostback([boolean value])
```

### Parameters - editAutoPostback

value  

### Return Value - editAutoPostback

## Method enabled

```xpp
public boolean enabled([boolean value])
```

### Parameters - enabled

value  

### Return Value - enabled

## Method helpText

```xpp
public str helpText([str value])
```

### Parameters - helpText

value  

### Return Value - helpText

## Method extendedStyle

```xpp
public str extendedStyle([str value])
```

### Parameters - extendedStyle

value  

### Return Value - extendedStyle

## Method height

```xpp
public int height(int value, [int mode])
```

### Parameters - height

value  

<!-- -->

mode  

### Return Value - height

## Method heightMode

```xpp
public int heightMode([int value])
```

### Parameters - heightMode

value  

### Return Value - heightMode

## Method heightValue

```xpp
public int heightValue([int value])
```

### Parameters - heightValue

value  

### Return Value - heightValue

## Method GetXppILImplementation

```xpp
public str GetXppILImplementation()
```

### Return Value - GetXppILImplementation

## Method hasUserSetting

Indicates whether the control has custom user settings.

```xpp
public boolean hasUserSetting()
```

### Return Value - hasUserSetting

A Boolean value that indicates whether the control has custom user settings.

## Method id

Retrieves the ID of the control.

```xpp
public int id()
```

### Return Value - id

The ID of the control.

## Method isContainer

Retrieves a value that indicates whether the control is a container control.

```xpp
public boolean isContainer()
```

### Return Value - isContainer

A Boolean value that indicates whether the control is a container control.

## Method markAsUserAdd

Marks or unmarks the control as a user-added control.

```xpp
public boolean markAsUserAdd([boolean value])
```

### Parameters - markAsUserAdd

value  
A Boolean value that indicates whether to mark the control as a user-added control.

### Return Value - markAsUserAdd

A Boolean value that indicates whether the control was marked as a user-added control.

## Method moveControl

Moves a specified control to the control.

```xpp
public int moveControl(int controlId, [int insertAfterId])
```

### Parameters - moveControl

controlId  
An integer value that indicates the ID of the control to insert the control after; optional.

<!-- -->

insertAfterId  
An integer value that indicates the ID of the control to insert the control after; optional.

### Return Value - moveControl

1 if the control was moved successfully; otherwise, 0.

### Remarks - moveControl

In general, if the specified control can be contained in the control and can be moved from the container that it is currently in, this method should succeed. However, in some cases, such as for the reference group control instance, controls cannot be moved.

## Method name

```xpp
public str name([str value])
```

### Parameters - name

value  

### Return Value - name

## Method neededPermission

```xpp
public int neededPermission([int value])
```

### Parameters - neededPermission

value  

### Return Value - neededPermission

## Method SysObsoleteAttribute

```xpp
public container SysObsoleteAttribute()
```

### Return Value - SysObsoleteAttribute

## Method previewPartRef

```xpp
public str previewPartRef([str value])
```

### Parameters - previewPartRef

value  

### Return Value - previewPartRef

## Method skip

```xpp
public boolean skip([boolean value])
```

### Parameters - skip

value  

### Return Value - skip

## Method SysObsoleteAttribute

```xpp
public boolean SysObsoleteAttribute(container data)
```

### Parameters - SysObsoleteAttribute

data  

### Return Value - SysObsoleteAttribute

## Method userDisable

Gets or sets the value that indicates whether the control is disabled for the user.

```xpp
public int userDisable([int value])
```

### Parameters - userDisable

value  
The value that indicates whether the control is disabled for the user; optional.

### Return Value - userDisable

1 if the control is disabled for the user; otherwise, 0.

## Method userHeight

Gets or sets the custom user height for the control.

```xpp
public int userHeight([int value])
```

### Parameters - userHeight

value  
The user height for the control; optional.

### Return Value - userHeight

The custom user height for the control.

## Method userHide

Gets or sets the value that indicates whether the control is hidden from the user.

```xpp
public int userHide([int value])
```

### Parameters - userHide

value  
The value that indicates whether the control is hidden from the user; optional.

### Return Value - userHide

1 if the control is hidden from the user; otherwise, 0.

### Remarks - userHide

The user specifies whether a control is hidden by right-clicking the control when it is viewable or right-clicking another control when the original control is hidden. The right-click opens a menu that can be used to hide or display the control. This method lets you programmatically determine and set the value.

## Method userOrgContainer

Gets or sets the organization container for the control.

```xpp
public int userOrgContainer([int value])
```

### Parameters - userOrgContainer

value  
The organization container to set for the control; optional.

### Return Value - userOrgContainer

The organization container for the control.

## Method userOrgSibling

Gets or sets the organization sibling for the control.

```xpp
public int userOrgSibling([int value])
```

### Parameters - userOrgSibling

value  
The organization sibling to set for the control; optional.

### Return Value - userOrgSibling

The organization sibling for the control.

## Method userPromptText

Gets or sets the user label text for the control.

```xpp
public str userPromptText([str value])
```

### Parameters - userPromptText

value  
The user label text to set for the control; optional.

### Return Value - userPromptText

The user label text for the control.

## Method userSecurityLevel

Gets or sets the user security level for the control.

```xpp
public int userSecurityLevel([int value])
```

### Parameters - userSecurityLevel

value  
The user security level to set for the control; optional.

### Return Value - userSecurityLevel

The user security level for the control.

## Method userSkip

Sets or returns the value that indicates whether the form control is skipped when the user press the TAB key to navigate the controls on the form.

```xpp
public int userSkip([int value])
```

### Parameters - userSkip

value  
The value to assign to the userSkip property; optional. The value is 1 if the user setting to skip the control is in effect; otherwise, it is 0.

### Return Value - userSkip

1 if the user setting to skip the control is in effect; otherwise, 0.

## Method userWidth

Sets or returns the width of the control in pixels.

```xpp
public int userWidth([int value])
```

### Parameters - userWidth

value  
The number of pixels to use as the width of the control; optional.

### Return Value - userWidth

The number of pixels that the user specified as the width of the control; 0 (zero) if the user did not specify a character width.

### Remarks - userWidth

The userWidth method returns the width in pixels, based on six times the number of characters. For example, if the user has specified 30 characters as the width of the control, the return value is 6 \* 30 = 180. To specify the width of the control in characters, users can right-click the control to open the setup form where the character specification is made.

## Method visible

```xpp
public boolean visible([boolean value])
```

### Parameters - visible

value  

### Return Value - visible

## Method width

```xpp
public int width(int value, [int mode])
```

### Parameters - width

value  

<!-- -->

mode  

### Return Value - width

## Method widthMode

```xpp
public int widthMode([int value])
```

### Parameters - widthMode

value  

### Return Value - widthMode

## Method widthValue

```xpp
public int widthValue([int value])
```

### Parameters - widthValue

value  

### Return Value - widthValue

## Method RegisterXppILImplementation

```xpp
public void RegisterXppILImplementation(str className)
```

### Parameters - RegisterXppILImplementation

className  

## Method new

```xpp
public void new(FormContainer container)
```

### Parameters - new

container  

## Method resetUserSetting

Resets the user settings for the control.

```xpp
public void resetUserSetting()
```

