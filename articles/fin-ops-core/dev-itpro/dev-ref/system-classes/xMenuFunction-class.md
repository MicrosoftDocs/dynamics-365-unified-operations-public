---
title: xMenuFunction class
description: This topic describes the xMenuFunction class.
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

# Class xMenuFunction

[!include [banner](../../includes/banner.md)]

```xpp
class xMenuFunction extends SecureNode
```

The xMenuFunction class represents an interface to other objects, providing an easy way to access and run any Form, Report, Job, Class, and Query.

## Remarks

You refer to an Application object using a xMenuFunction object and its methods and properties. For example, you can:

-   Use the Run Method to run the object referenced in the property
-   Create a xMenuFunction object and make a reference to the object it runs (or references to). This enables you to manipulate the arguments passed to the object before running it

Note: This system class represents MenuItem nodes in the AOT. This class enables you to create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before calling this API.

## Examples

## Methods

| Method                                                                                                  | Description                                                                                                                               |
|---------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public str changedBy(\[str value\])                                                                     | Gets or sets the name of the user who last changed the application object.                                                                |
| public Date changedDate(\[Date value\])                                                                 | Gets or sets the date when an application object was last changed.                                                                        |
| public str changedTime(\[str value\])                                                                   | Gets or sets the time when an application object was last changed.                                                                        |
| public boolean checkAccessRights()                                                                      |                                                                                                                                           |
| public int copyCallerQuery(\[int value\])                                                               |                                                                                                                                           |
| public int correctPermissions(\[int value\])                                                            |                                                                                                                                           |
| public str countryRegionCodes(\[str value\])                                                            |                                                                                                                                           |
| public ObjectRun create(\[xArgs args\])                                                                 | Creates and returns a reference to an application object.                                                           |
| public str createdBy(\[str value\])                                                                     | Gets or sets the name of the user who created the application object.                                                                     |
| public int createPermissions(\[int value\])                                                             |                                                                                                                                           |
| public Date creationDate(\[Date value\])                                                                | Gets or sets the date an application object was created.                                                                                  |
| public str creationTime(\[str value\])                                                                  |                                                                                                                                           |
| public int deletePermissions(\[int value\])                                                             |                                                                                                                                           |
| public str disabledImage(\[str value\])                                                                 | Gets or sets the disabled image of the button.                                                                                            |
| public int disabledImageLocation(\[int value\])                                                         |                                                                                                                                           |
| public int disabledResource(\[int value\])                                                              | Gets or sets the resource ID of the image to use as the disabled button image.                                                            |
| public int enumParameter(\[int value\])                                                                 | Gets or sets the enumParameter property that is passed to the object that is run by the MenuFunction class.                               |
| public EnumId enumTypeParameter(\[EnumId value\])                                                       | Gets or sets the enumTypeParameter property for the MenuFunction class.                                                                   |
| public int formViewOption(\[int value\])                                                                |                                                                                                                                           |
| public Query getRootQuery()                                                                             |                                                                                                                                           |
| public boolean hasRunPermissions(\[xArgs args\])                                                        | Checks if the xMenuFunction object has execute permissions and run() may be called successfully.                                          |
| public str helpText(\[str value\])                                                                      | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                  |
| public int imageLocation(\[int value\])                                                                 |                                                                                                                                           |
| public str label(\[str value\])                                                                         | Gets or sets the label for a control.                                                                                                     |
| public str linkedPermissionObject(\[str value\])                                                        |                                                                                                                                           |
| public str linkedPermissionObjectChild(\[str value\])                                                   |                                                                                                                                           |
| public int linkedPermissionType(\[int value\])                                                          |                                                                                                                                           |
| public int maintainUserLicense(\[int value\])                                                           |                                                                                                                                           |
| public boolean multiSelect(\[boolean value\])                                                           |                                                                                                                                           |
| public str name(\[str value\])                                                                          | Gets or sets the name that is used in code to identify a form, report, table, query, or other application object. |
| public int needsRecord(\[int value\])                                                                   |                                                                                                                                           |
| public str normalImage(\[str value\])                                                                   |                                                                                                                                           |
| public int normalResource(\[int value\])                                                                |                                                                                                                                           |
| public str object(\[str value\])                                                                        | Gets or sets the object that is run by the MenuFunction class.                                                                            |
| public int objectType(\[int value\])                                                                    |                                                                                                                                           |
| public int openMode(\[int value\])                                                                      |                                                                                                                                           |
| public Guid origin(\[Guid value\])                                                                      |                                                                                                                                           |
| public str parameters(\[str value\])                                                                    | Gets or sets the list of parameters that are passed to objects that are run by the MenuFunction class.                                    |
| public str query(\[str value\])                                                                         |                                                                                                                                           |
| public int readPermissions(\[int value\])                                                               |                                                                                                                                           |
| public str reportDesign(\[str value\])                                                                  |                                                                                                                                           |
| public int runOn(\[int value\])                                                                         |                                                                                                                                           |
| public MenuItemType type()                                                                              |                                                                                                                                           |
| public int updatePermissions(\[int value\])                                                             |                                                                                                                                           |
| public int viewUserLicense(\[int value\])                                                               |                                                                                                                                           |
| public str web(\[str value\])                                                                           |                                                                                                                                           |
| public int webAccess(\[int value\])                                                                     |                                                                                                                                           |
| public str webMenuItemName(\[str value\])                                                               |                                                                                                                                           |
| public str webPage(\[str value\])                                                                       |                                                                                                                                           |
| public boolean webSecureTransaction(\[boolean value\])                                                  |                                                                                                                                           |
| public void run(\[xArgs args\])                                                                         | Runs the xMenuFunction object.                                                                                                            |
| ::public static void runCalled(str Name, MenuItemType type, \[boolean setContextMenu\], \[xArgs args\]) |                                                                                                                                           |
| ::public static void runClient(str Name, MenuItemType type, \[boolean setContextMenu\], \[xArgs args\]) |                                                                                                                                           |
| ::public static void runServer(str Name, MenuItemType type, \[boolean setContextMenu\], \[xArgs args\]) |                                                                                                                                           |
| public void new(str Name, MenuItemType type)                                                            | Creates a new xMenuFunction object by passing xMenuFunction's name and MenuItemType to the xMenuFunction constructor.                     |
| public void AOTrun(\[xArgs args\])                                                                      | Compiles this node and its subtree in the Application Object Tree (AOT).                                                                  |

## Method changedBy

Gets or sets the name of the user who last changed the application object.

```xpp
public str changedBy([str value])
```

### Parameters - changedBy

value  
The value to set; optional.

### Return Value - changedBy

The name of the user.

## Method changedDate

Gets or sets the date when an application object was last changed.

```xpp
public Date changedDate([Date value])
```

### Parameters - changedDate

value  
The value to set; optional.

### Return Value - changedDate

The date when an application object was last changed.

## Method changedTime

Gets or sets the time when an application object was last changed.

```xpp
public str changedTime([str value])
```

### Parameters - changedTime

value  
The value to set; optional.

### Return Value - changedTime

The time when an application object was last changed.

## Method checkAccessRights

```xpp
public boolean checkAccessRights()
```

### Return Value - checkAccessRights

## Method copyCallerQuery

```xpp
public int copyCallerQuery([int value])
```

### Parameters - copyCallerQuery

value  

### Return Value - copyCallerQuery

## Method correctPermissions

```xpp
public int correctPermissions([int value])
```

### Parameters - correctPermissions

value  

### Return Value - correctPermissions

## Method countryRegionCodes

```xpp
public str countryRegionCodes([str value])
```

### Parameters - countryRegionCodes

value  

### Return Value - countryRegionCodes

## Method create

Creates and returns a reference to an application object.

```xpp
public ObjectRun create([xArgs args])
```

### Parameters - create

args  
An xArgs class object; optional.

### Return Value - create

A reference to an application object.

### Remarks - create

This method is used to create an application object. The object that is returned is assigned to an object variable. Note that the init function is invoked by the create function. Therefore you should not invoke it.

## Method createdBy

Gets or sets the name of the user who created the application object.

```xpp
public str createdBy([str value])
```

### Parameters - createdBy

value  

### Return Value - createdBy

The name of the user.

## Method createPermissions

```xpp
public int createPermissions([int value])
```

### Parameters - createPermissions

value  

### Return Value - createPermissions

## Method creationDate

Gets or sets the date an application object was created.

```xpp
public Date creationDate([Date value])
```

### Parameters - creationDate

value  

### Return Value - creationDate

The date an application object was created.

## Method creationTime

```xpp
public str creationTime([str value])
```

### Parameters - creationTime

value  

### Return Value - creationTime

## Method deletePermissions

```xpp
public int deletePermissions([int value])
```

### Parameters - deletePermissions

value  

### Return Value - deletePermissions

## Method disabledImage

Gets or sets the disabled image of the button.

```xpp
public str disabledImage([str value])
```

### Parameters - disabledImage

value  

### Return Value - disabledImage

The full name of an image file; the system supports all of the GDI-supported image formats.

### Remarks - disabledImage

This property has precedence over the disabledResource property value. It is used if both of these properties are set.

## Method disabledImageLocation

```xpp
public int disabledImageLocation([int value])
```

### Parameters - disabledImageLocation

value  

### Return Value - disabledImageLocation

## Method disabledResource

Gets or sets the resource ID of the image to use as the disabled button image.

```xpp
public int disabledResource([int value])
```

### Parameters - disabledResource

value  

### Return Value - disabledResource

The resource ID of the image to use as the disabled button image. Both icon and bitmap images are supported.

## Method enumParameter

Gets or sets the enumParameter property that is passed to the object that is run by the MenuFunction class.

```xpp
public int enumParameter([int value])
```

### Parameters - enumParameter

value  

### Return Value - enumParameter

The enumParameter property that is passed to the object that is run by the MenuFunction class.

## Method enumTypeParameter

Gets or sets the enumTypeParameter property for the MenuFunction class.

```xpp
public EnumId enumTypeParameter([EnumId value])
```

### Parameters - enumTypeParameter

value  

### Return Value - enumTypeParameter

The enumTypeParameter property for the MenuFunction class.

## Method formViewOption

```xpp
public int formViewOption([int value])
```

### Parameters - formViewOption

value  

### Return Value - formViewOption

## Method getRootQuery

```xpp
public Query getRootQuery()
```

### Return Value - getRootQuery

## Method hasRunPermissions

Checks if the xMenuFunction object has execute permissions and run() may be called successfully.

```xpp
public boolean hasRunPermissions([xArgs args])
```

### Parameters - hasRunPermissions

args  
An xArgs class object as would be passed to the run() method; optional.

### Return Value - hasRunPermissions

true if necessary permissions exist to successfully call run().

### Remarks - hasRunPermissions

This function may throw in case of permissions failure.

## Method helpText

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

```xpp
public str helpText([str value])
```

### Parameters - helpText

value  

### Return Value - helpText

The string to be displayed at the bottom of the screen.

### Remarks - helpText

Set the HelpText property for an object by using the property dialog box. The help text must not exceed 250 characters.

## Method imageLocation

```xpp
public int imageLocation([int value])
```

### Parameters - imageLocation

value  

### Return Value - imageLocation

## Method label

Gets or sets the label for a control.

```xpp
public str label([str value])
```

### Parameters - label

value  

### Return Value - label

The current value of the label string.

### Remarks - label

The label determines which text is displayed in the control or adjacent to it. The label property value cannot exceed 250 characters.

## Method linkedPermissionObject

```xpp
public str linkedPermissionObject([str value])
```

### Parameters - linkedPermissionObject

value  

### Return Value - linkedPermissionObject

## Method linkedPermissionObjectChild

```xpp
public str linkedPermissionObjectChild([str value])
```

### Parameters - linkedPermissionObjectChild

value  

### Return Value - linkedPermissionObjectChild

## Method linkedPermissionType

```xpp
public int linkedPermissionType([int value])
```

### Parameters - linkedPermissionType

value  

### Return Value - linkedPermissionType

## Method maintainUserLicense

```xpp
public int maintainUserLicense([int value])
```

### Parameters - maintainUserLicense

value  

### Return Value - maintainUserLicense

## Method multiSelect

```xpp
public boolean multiSelect([boolean value])
```

### Parameters - multiSelect

value  

### Return Value - multiSelect

## Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other application object.

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

## Method needsRecord

```xpp
public int needsRecord([int value])
```

### Parameters - needsRecord

value  

### Return Value - needsRecord

## Method normalImage

```xpp
public str normalImage([str value])
```

### Parameters - normalImage

value  

### Return Value - normalImage

## Method normalResource

```xpp
public int normalResource([int value])
```

### Parameters - normalResource

value  

### Return Value - normalResource

## Method object

Gets or sets the object that is run by the MenuFunction class.

```xpp
public str object([str value])
```

### Parameters - object

value  

### Return Value - object

The object that is run by the MenuFunction class.

### Remarks - object

The property value may be one of the following objects:

-   Form.
-   Report.
-   Job.
-   Class.
-   Query.

## Method objectType

```xpp
public int objectType([int value])
```

### Parameters - objectType

value  

### Return Value - objectType

## Method openMode

```xpp
public int openMode([int value])
```

### Parameters - openMode

value  

### Return Value - openMode

## Method origin

```xpp
public Guid origin([Guid value])
```

### Parameters - origin

value  

### Return Value - origin

## Method parameters

Gets or sets the list of parameters that are passed to objects that are run by the MenuFunction class.

```xpp
public str parameters([str value])
```

### Parameters - parameters

value  

### Return Value - parameters

The list of parameters that are passed to the object.

### Remarks - parameters

The parameters string format is Parameter1=Value1, Parameter2=Value2, and so on. Objects ignore passed, unrecognized parameters.

## Method query

```xpp
public str query([str value])
```

### Parameters - query

value  

### Return Value - query

## Method readPermissions

```xpp
public int readPermissions([int value])
```

### Parameters - readPermissions

value  

### Return Value - readPermissions

## Method reportDesign

```xpp
public str reportDesign([str value])
```

### Parameters - reportDesign

value  

### Return Value - reportDesign

## Method runOn

```xpp
public int runOn([int value])
```

### Parameters - runOn

value  

### Return Value - runOn

## Method type

```xpp
public MenuItemType type()
```

### Return Value - type

## Method updatePermissions

```xpp
public int updatePermissions([int value])
```

### Parameters - updatePermissions

value  

### Return Value - updatePermissions

## Method viewUserLicense

```xpp
public int viewUserLicense([int value])
```

### Parameters - viewUserLicense

value  

### Return Value - viewUserLicense

## Method web

```xpp
public str web([str value])
```

### Parameters - web

value  

### Return Value - web

## Method webAccess

```xpp
public int webAccess([int value])
```

### Parameters - webAccess

value  

### Return Value - webAccess

## Method webMenuItemName

```xpp
public str webMenuItemName([str value])
```

### Parameters - webMenuItemName

value  

### Return Value - webMenuItemName

## Method webPage

```xpp
public str webPage([str value])
```

### Parameters - webPage

value  

### Return Value - webPage

## Method webSecureTransaction

```xpp
public boolean webSecureTransaction([boolean value])
```

### Parameters - webSecureTransaction

value  

### Return Value - webSecureTransaction

## Method run

Runs the xMenuFunction object.

```xpp
public void run([xArgs args])
```

### Parameters - run

args  
An xArgs class object; optional.

### Remarks - run

This function is used to run a xMenuFunction object from code.

## Method runCalled

```xpp
public static void runCalled(str Name, MenuItemType type, [boolean setContextMenu], [xArgs args])
```

### Parameters - runCalled

Name  

<!-- -->

type  

<!-- -->

setContextMenu  

<!-- -->

args  

## Method runClient

```xpp
public static void runClient(str Name, MenuItemType type, [boolean setContextMenu], [xArgs args])
```

### Parameters - runClient

Name  

<!-- -->

type  

<!-- -->

setContextMenu  

<!-- -->

args  

## Method runServer

```xpp
public static void runServer(str Name, MenuItemType type, [boolean setContextMenu], [xArgs args])
```

### Parameters - runServer

Name  

<!-- -->

type  

<!-- -->

setContextMenu  

<!-- -->

args  

## Method new

Creates a new xMenuFunction object by passing xMenuFunction's name and MenuItemType to the xMenuFunction constructor.

```xpp
public void new(str Name, MenuItemType type)
```

### Parameters - new

Name  
A constant in the MenuItemType system enumeration: MenuItemType::Display, MenuItemType::Output, or MenuItemType::Action.

<!-- -->

type  
A constant in the MenuItemType system enumeration: MenuItemType::Display, MenuItemType::Output, or MenuItemType::Action.

### Remarks - new

When creating a xMenuFunction object, the parameters must uniquely identify an existing xMenuFunction. If not, Exception::Internal is thrown.

## Method AOTrun

Compiles this node and its subtree in the Application Object Tree (AOT).

```xpp
public void AOTrun([xArgs args])
```

### Parameters - AOTrun

args  

