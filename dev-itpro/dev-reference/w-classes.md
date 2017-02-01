---
# required metadata

title: W Classes | Microsoft Docs
description: System API classes that start with the letter W.
author: RobinARH
manager: AnnBe
ms.date: 2016-02-26 02:19:17
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: RobinARH
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 55901
ms.assetid: 38d0ef0f-f838-49e6-a2aa-0d8fb44e31a6
ms.region: Global
# ms.industry: 
ms.author: robinr

---

# W Classes

System API classes that start with the letter W.

Class WebActionMenuFunction
---------------------------

    class WebActionMenuFunction extends WebMenuFunction

The WebActionMenuFunction class lets you create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                   | Description                                                                                                 |
|----------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| public boolean big(\[boolean value\])                    |                                                                                                             |
| public int correctPermissions(\[int value\])             |                                                                                                             |
| public int createPermissions(\[int value\])              |                                                                                                             |
| public int deletePermissions(\[int value\])              |                                                                                                             |
| public int enumParameter(\[int value\])                  | Gets or sets the enumParameter property that is passed to the object that is run by the MenuFunction class. |
| public EnumId enumTypeParameter(\[EnumId value\])        | Gets or sets the enumTypeParameter property for the MenuFunction class.                                     |
| public int imageLocation(\[int value\])                  |                                                                                                             |
| public str linkedPermissionObject(\[str value\])         |                                                                                                             |
| public str linkedPermissionObjectChild(\[str value\])    |                                                                                                             |
| public int linkedPermissionType(\[int value\])           |                                                                                                             |
| public int maintainUserLicense(\[int value\])            | Microsoft internal use only.                                                                                |
| public boolean multiSelect(\[boolean value\])            |                                                                                                             |
| public boolean needsRecord(\[boolean value\])            |                                                                                                             |
| public str normalImage(\[str value\])                    |                                                                                                             |
| public int normalResource(\[int value\])                 |                                                                                                             |
| public str object(\[str value\])                         | Gets or sets the object that the MenuFunction class runs.                                                   |
| public int objectType(\[int value\])                     |                                                                                                             |
| public Guid origin(\[Guid value\])                       |                                                                                                             |
| public str parameters(\[str value\])                     | Gets or sets the list of parameters that are passed to objects that are run by the MenuFunction class.      |
| public int readPermissions(\[int value\])                |                                                                                                             |
| public str reportDesign(\[str value\])                   |                                                                                                             |
| public int runOn(\[int value\])                          |                                                                                                             |
| public int updatePermissions(\[int value\])              |                                                                                                             |
| public int viewUserLicense(\[int value\])                | Microsoft internal use only.                                                                                |
| ::public static void runCalled(str name, \[xArgs args\]) |                                                                                                             |
| public void AOTrun(\[xArgs args\])                       | Compiles this node and its sub-tree in the Microsoft Dynamics AX Application Object Tree (AOT).             |
| ::public static void runClient(str name, \[xArgs args\]) |                                                                                                             |
| public void run(\[xArgs args\])                          |                                                                                                             |
| public void new(str name)                                | Initializes a new instance of the TreeNode class.                                                           |
| ::public static void runServer(str name, \[xArgs args\]) |                                                                                                             |

### Method big

    public boolean big([boolean value])

#### Parameters

value  

#### Return Value

### Method correctPermissions

    public int correctPermissions([int value])

#### Parameters

value  

#### Return Value

### Method createPermissions

    public int createPermissions([int value])

#### Parameters

value  

#### Return Value

### Method deletePermissions

    public int deletePermissions([int value])

#### Parameters

value  

#### Return Value

### Method enumParameter

Gets or sets the enumParameter property that is passed to the object that is run by the MenuFunction class.

    public int enumParameter([int value])

#### Parameters

value  

#### Return Value

The enumParameter property that is passed to the object that is run by the MenuFunction class.

### Method enumTypeParameter

Gets or sets the enumTypeParameter property for the MenuFunction class.

    public EnumId enumTypeParameter([EnumId value])

#### Parameters

value  

#### Return Value

The enumTypeParameter property for the MenuFunction class.

### Method imageLocation

    public int imageLocation([int value])

#### Parameters

value  

#### Return Value

### Method linkedPermissionObject

    public str linkedPermissionObject([str value])

#### Parameters

value  

#### Return Value

### Method linkedPermissionObjectChild

    public str linkedPermissionObjectChild([str value])

#### Parameters

value  

#### Return Value

### Method linkedPermissionType

    public int linkedPermissionType([int value])

#### Parameters

value  

#### Return Value

### Method maintainUserLicense

Microsoft internal use only.

    public int maintainUserLicense([int value])

#### Parameters

value  
The new user license.

#### Return Value

The user license.

### Method multiSelect

    public boolean multiSelect([boolean value])

#### Parameters

value  

#### Return Value

### Method needsRecord

    public boolean needsRecord([boolean value])

#### Parameters

value  

#### Return Value

### Method normalImage

    public str normalImage([str value])

#### Parameters

value  

#### Return Value

### Method normalResource

    public int normalResource([int value])

#### Parameters

value  

#### Return Value

### Method object

Gets or sets the object that the MenuFunction class runs.

    public str object([str value])

#### Parameters

value  

#### Return Value

The object that the MenuFunction class runs.

#### Remarks

property value may be one of the following objects:

-   Form
-   Report
-   Job
-   Class
-   Query

### Method objectType

    public int objectType([int value])

#### Parameters

value  

#### Return Value

### Method origin

    public Guid origin([Guid value])

#### Parameters

value  

#### Return Value

### Method parameters

Gets or sets the list of parameters that are passed to objects that are run by the MenuFunction class.

    public str parameters([str value])

#### Parameters

value  

#### Return Value

The list of parameters that are passed to the object.

#### Remarks

The parameters string format is Parameter1=Value1, Parameter2=Value2, and so on. cts ignore passed, unrecognized parameters.

### Method readPermissions

    public int readPermissions([int value])

#### Parameters

value  

#### Return Value

### Method reportDesign

    public str reportDesign([str value])

#### Parameters

value  

#### Return Value

### Method runOn

    public int runOn([int value])

#### Parameters

value  

#### Return Value

### Method updatePermissions

    public int updatePermissions([int value])

#### Parameters

value  

#### Return Value

### Method viewUserLicense

Microsoft internal use only.

    public int viewUserLicense([int value])

#### Parameters

value  
The user license to view.

#### Return Value

The user license.

### Method runCalled

    public static void runCalled(str name, [xArgs args])

#### Parameters

name  

<!-- -->

args  

### Method AOTrun

Compiles this node and its sub-tree in the Microsoft Dynamics AX Application Object Tree (AOT).

    public void AOTrun([xArgs args])

#### Parameters

args  

### Method runClient

    public static void runClient(str name, [xArgs args])

#### Parameters

name  

<!-- -->

args  

### Method run

    public void run([xArgs args])

#### Parameters

args  

### Method new

Initializes a new instance of the TreeNode class.

    public void new(str name)

#### Parameters

name  

### Method runServer

    public static void runServer(str name, [xArgs args])

#### Parameters

name  

<!-- -->

args  

## Class WebContentItem
    class WebContentItem extends SecureNode

The WebContentItem class lets you create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                            | Description                                                                                                                               |
|---------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public str changedBy(\[str value\])               | Gets or sets the name of the user who last changed the application object.                                                                |
| public Date changedDate(\[Date value\])           | Gets or sets the date an application object was last changed.                                                                             |
| public str changedTime(\[str value\])             | Gets or sets the time an application object was last changed.                                                                             |
| public str createdBy(\[str value\])               | Gets or sets the name of the user who created the application object.                                                                     |
| public Date creationDate(\[Date value\])          | Gets or sets the date an application object was created.                                                                                  |
| public str creationTime(\[str value\])            |                                                                                                                                           |
| public int enumParameter(\[int value\])           | Gets or sets the enumParameter property that is passed to the object that is run by the MenuFunction class.                               |
| public EnumId enumTypeParameter(\[EnumId value\]) | Gets or sets the enumTypeParameter property for the MenuFunction class.                                                                   |
| public str helpText(\[str value\])                | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                  |
| public str label(\[str value\])                   | Gets or sets the label for a control.                                                                                                     |
| public str name(\[str value\])                    | Gets or sets the name that is used in code to identify a form, report, rable, query, or another Microsoft Dynamics AX application object. |
| public str object(\[str value\])                  | Gets or sets the object that the MenuFunction class runs.                                                                                 |
| public int objectType(\[int value\])              |                                                                                                                                           |
| public Guid origin(\[Guid value\])                |                                                                                                                                           |
| public str parameters(\[str value\])              | Gets or sets the list of parameters that are passed to objects that are run by the MenuFunction class.                                    |
| public str reportDesign(\[str value\])            |                                                                                                                                           |

### Method changedBy

Gets or sets the name of the user who last changed the application object.

    public str changedBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method changedDate

Gets or sets the date an application object was last changed.

    public Date changedDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was last changed.

### Method changedTime

Gets or sets the time an application object was last changed.

    public str changedTime([str value])

#### Parameters

value  

#### Return Value

The time an application object was last changed.

### Method createdBy

Gets or sets the name of the user who created the application object.

    public str createdBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method creationDate

Gets or sets the date an application object was created.

    public Date creationDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was created.

### Method creationTime

    public str creationTime([str value])

#### Parameters

value  

#### Return Value

### Method enumParameter

Gets or sets the enumParameter property that is passed to the object that is run by the MenuFunction class.

    public int enumParameter([int value])

#### Parameters

value  

#### Return Value

The enumParameter property that is passed to the object that is run by the MenuFunction class.

### Method enumTypeParameter

Gets or sets the enumTypeParameter property for the MenuFunction class.

    public EnumId enumTypeParameter([EnumId value])

#### Parameters

value  

#### Return Value

The enumTypeParameter property for the MenuFunction class.

### Method helpText

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property dialogue box.The help text must not exceed 250 characters.

### Method label

Gets or sets the label for a control.

    public str label([str value])

#### Parameters

value  

#### Return Value

The current value of the label string.

#### Remarks

The label determines which text is displayed in the control or adjacent to it.The label property value cannot exceed 250 characters.

### Method name

Gets or sets the name that is used in code to identify a form, report, rable, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, or classes.

### Method object

Gets or sets the object that the MenuFunction class runs.

    public str object([str value])

#### Parameters

value  

#### Return Value

The object that the MenuFunction class runs.

#### Remarks

property value may be one of the following objects:

-   Form
-   Report
-   Job
-   Class
-   Query

### Method objectType

    public int objectType([int value])

#### Parameters

value  

#### Return Value

### Method origin

    public Guid origin([Guid value])

#### Parameters

value  

#### Return Value

### Method parameters

Gets or sets the list of parameters that are passed to objects that are run by the MenuFunction class.

    public str parameters([str value])

#### Parameters

value  

#### Return Value

The list of parameters that are passed to the object.

#### Remarks

The parameters string format is Parameter1=Value1, Parameter2=Value2, and so on. cts ignore passed, unrecognized parameters.

### Method reportDesign

    public str reportDesign([str value])

#### Parameters

value  

#### Return Value

## Class webControlNode
    class webControlNode extends TreeNode

### Remarks

### Examples

### Methods

| Method                                                        | Description                                                                                                                                   |
|---------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public str AOTgetSource()                                     | Returns the source code of this node.                                                                                                         |
| public str changedBy(\[str value\])                           | Gets or sets the name of the user who last changed the application object.                                                                    |
| public Date changedDate(\[Date value\])                       | Gets or sets the date an application object was last changed.                                                                                 |
| public str changedTime(\[str value\])                         | Gets or sets the time an application object was last changed.                                                                                 |
| public str createdBy(\[str value\])                           | Gets or sets the name of the user who created the application object.                                                                         |
| public Date creationDate(\[Date value\])                      | Gets or sets the date an application object was created.                                                                                      |
| public str creationTime(\[str value\])                        |                                                                                                                                               |
| public str filename(\[str value\])                            |                                                                                                                                               |
| public List getRelatedWebControls(\[boolean firstLevelOnly\]) | Get a list of web controls that are related to this web control.                                                                              |
| public str helpText(\[str value\])                            | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                      |
| public str name(\[str value\])                                | Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics AX application object. |
| public Guid origin(\[Guid value\])                            |                                                                                                                                               |
| public str relativePath(\[str value\])                        |                                                                                                                                               |
| public str version(\[str value\])                             |                                                                                                                                               |
| ::public static webControlNode createFromFile(str fileName)   |                                                                                                                                               |
| public void AOTsetSource(str source, \[boolean isStatic\])    | Sets the source code of this node.                                                                                                            |

### Method AOTgetSource

Returns the source code of this node.

    public str AOTgetSource()

#### Return Value

The string that contains source code, if there is any; otherwise, nullNothingnullptrunita null reference (Nothing in Visual Basic).

#### Remarks

This function is overridden by nodes that have source code.

### Method changedBy

Gets or sets the name of the user who last changed the application object.

    public str changedBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method changedDate

Gets or sets the date an application object was last changed.

    public Date changedDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was last changed.

### Method changedTime

Gets or sets the time an application object was last changed.

    public str changedTime([str value])

#### Parameters

value  

#### Return Value

The time an application object was last changed.

### Method createdBy

Gets or sets the name of the user who created the application object.

    public str createdBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method creationDate

Gets or sets the date an application object was created.

    public Date creationDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was created.

### Method creationTime

    public str creationTime([str value])

#### Parameters

value  

#### Return Value

### Method filename

    public str filename([str value])

#### Parameters

value  

#### Return Value

### Method getRelatedWebControls

Get a list of web controls that are related to this web control.

    public List getRelatedWebControls([boolean firstLevelOnly])

#### Parameters

firstLevelOnly  
A value that indicates whether only the first level of web controls is checked.

#### Return Value

A list of related web controls.

### Method helpText

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property dialog box. The help text must not exceed 250 characters.

### Method name

Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in the code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, or classes.

### Method origin

    public Guid origin([Guid value])

#### Parameters

value  

#### Return Value

### Method relativePath

    public str relativePath([str value])

#### Parameters

value  

#### Return Value

### Method version

    public str version([str value])

#### Parameters

value  

#### Return Value

### Method createFromFile

    public static webControlNode createFromFile(str fileName)

#### Parameters

fileName  

#### Return Value

### Method AOTsetSource

Sets the source code of this node.

    public void AOTsetSource(str source, [boolean isStatic])

#### Parameters

source  
The value that specifies whether the method is static; optional.

<!-- -->

isStatic  
The value that specifies whether the method is static; optional.

#### Remarks

This method is overridden by nodes that have source code.

## Class WebDisplayContentItem
    class WebDisplayContentItem extends WebContentItem

The WebDisplayContentItem class enables you to create, read, update, and delete X++ code and metadata.

### Remarks

This class enables you to create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before calling this API.

### Examples

### Methods

| Method                    | Description                          |
|---------------------------|--------------------------------------|
| public void new(str name) | Creates a new WebDisplayContentItem. |

### Method new

Creates a new WebDisplayContentItem.

    public void new(str name)

#### Parameters

name  

## Class WebletItem
    class WebletItem extends SecureNode

The WebletItem class enables you to create, read, update, and delete X++ code and metadata.

### Remarks

This class enables you to create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before calling this API.

### Examples

### Methods

| Method                                            | Description                                                                                                                                   |
|---------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public str changedBy(\[str value\])               | Gets or sets the name of the user who last changed the application object.                                                                    |
| public Date changedDate(\[Date value\])           | Gets or sets the date an application object was last changed.                                                                                 |
| public str changedTime(\[str value\])             | Gets or sets the time an application object was last changed.                                                                                 |
| public str createdBy(\[str value\])               | Gets or sets the name of the user who created the application object.                                                                         |
| public Date creationDate(\[Date value\])          | Gets or sets the date an application object was created.                                                                                      |
| public str creationTime(\[str value\])            |                                                                                                                                               |
| public int enumParameter(\[int value\])           | Gets or sets the enumParameter property that is passed to the object that is run by the MenuFunction class.                                   |
| public EnumId enumTypeParameter(\[EnumId value\]) | Gets or sets the enumTypeParameter property for the MenuFunction class.                                                                       |
| public str helpText(\[str value\])                | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                      |
| public str label(\[str value\])                   | Gets or sets the label for a control.                                                                                                         |
| public str name(\[str value\])                    | Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics AX application object. |
| public str object(\[str value\])                  | Gets or sets the object that the MenuFunction class runs.                                                                                     |
| public int objectType(\[int value\])              |                                                                                                                                               |
| public Guid origin(\[Guid value\])                |                                                                                                                                               |
| public str parameters(\[str value\])              | Gets or sets the list of parameters that are passed to objects that are run by the MenuFunction class.                                        |
| public str reportDesign(\[str value\])            |                                                                                                                                               |
| public void new(str name)                         | Microsoft internal use only.                                                                                                                  |

### Method changedBy

Gets or sets the name of the user who last changed the application object.

    public str changedBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method changedDate

Gets or sets the date an application object was last changed.

    public Date changedDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was last changed.

### Method changedTime

Gets or sets the time an application object was last changed.

    public str changedTime([str value])

#### Parameters

value  

#### Return Value

The time an application object was last changed.

### Method createdBy

Gets or sets the name of the user who created the application object.

    public str createdBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method creationDate

Gets or sets the date an application object was created.

    public Date creationDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was created.

### Method creationTime

    public str creationTime([str value])

#### Parameters

value  

#### Return Value

### Method enumParameter

Gets or sets the enumParameter property that is passed to the object that is run by the MenuFunction class.

    public int enumParameter([int value])

#### Parameters

value  

#### Return Value

The enumParameter property that is passed to the object that is run by the MenuFunction class.

### Method enumTypeParameter

Gets or sets the enumTypeParameter property for the MenuFunction class.

    public EnumId enumTypeParameter([EnumId value])

#### Parameters

value  

#### Return Value

The enumTypeParameter property for the MenuFunction class.

### Method helpText

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property dialog box. The help text must not exceed 250 characters.

### Method label

Gets or sets the label for a control.

    public str label([str value])

#### Parameters

value  

#### Return Value

The current value of the label string.

#### Remarks

The label determines which text is displayed in the control or adjacent to it.The label property value cannot exceed 250 characters.

### Method name

Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enumerations, classes, and so on.

### Method object

Gets or sets the object that the MenuFunction class runs.

    public str object([str value])

#### Parameters

value  

#### Return Value

The object that the MenuFunction class runs.

#### Remarks

property value may be one of the following objects:

-   Form.
-   Report.
-   Job.
-   Class.
-   Query.

### Method objectType

    public int objectType([int value])

#### Parameters

value  

#### Return Value

### Method origin

    public Guid origin([Guid value])

#### Parameters

value  

#### Return Value

### Method parameters

Gets or sets the list of parameters that are passed to objects that are run by the MenuFunction class.

    public str parameters([str value])

#### Parameters

value  

#### Return Value

The list of parameters that are passed to the object.

#### Remarks

The parameters string format is Parameter1=Value1, Parameter2=Value2, and so on. cts ignore passed, unrecognized parameters.

### Method reportDesign

    public str reportDesign([str value])

#### Parameters

value  

#### Return Value

### Method new

Microsoft internal use only.

    public void new(str name)

#### Parameters

name  

## Class webListDefNode
    class webListDefNode extends TreeNode

### Remarks

### Examples

### Methods

| Method                                                     | Description                                                                                                                               |
|------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public str AOTgetSource()                                  | Returns the source code of this node.                                                                                                     |
| public str changedBy(\[str value\])                        | Gets or sets the name of the user who last changed the application object.                                                                |
| public Date changedDate(\[Date value\])                    | Gets or sets the date an application object was last changed.                                                                             |
| public str changedTime(\[str value\])                      | Gets or sets the time an application object was last changed.                                                                             |
| public str createdBy(\[str value\])                        | Gets or sets the name of the user who created the application object.                                                                     |
| public Date creationDate(\[Date value\])                   | Gets or sets the date an application object was created.                                                                                  |
| public str creationTime(\[str value\])                     |                                                                                                                                           |
| public str helpText(\[str value\])                         | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                  |
| public boolean mOSSOnly(\[boolean value\])                 |                                                                                                                                           |
| public str name(\[str value\])                             | Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics AX application object. |
| public Guid origin(\[Guid value\])                         |                                                                                                                                           |
| public str pageTitle(\[str value\])                        |                                                                                                                                           |
| public boolean publicPage(\[boolean value\])               |                                                                                                                                           |
| public str uRL(\[str value\])                              |                                                                                                                                           |
| public str webModule(\[str value\])                        |                                                                                                                                           |
| public void AOTsetSource(str source, \[boolean isStatic\]) | Sets the source code of this node.                                                                                                        |
| public void new(str name)                                  | Initializes a new instance of the TreeNode class.                                                                                         |

### Method AOTgetSource

Returns the source code of this node.

    public str AOTgetSource()

#### Return Value

The string that contains source code, if there is any; otherwise, nullNothingnullptrunita null reference (Nothing in Visual Basic).

#### Remarks

This function is overridden by nodes that have source code.

### Method changedBy

Gets or sets the name of the user who last changed the application object.

    public str changedBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method changedDate

Gets or sets the date an application object was last changed.

    public Date changedDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was last changed.

### Method changedTime

Gets or sets the time an application object was last changed.

    public str changedTime([str value])

#### Parameters

value  

#### Return Value

The time an application object was last changed.

### Method createdBy

Gets or sets the name of the user who created the application object.

    public str createdBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method creationDate

Gets or sets the date an application object was created.

    public Date creationDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was created.

### Method creationTime

    public str creationTime([str value])

#### Parameters

value  

#### Return Value

### Method helpText

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property dialogue box.The help text must not exceed 250 characters.

### Method mOSSOnly

    public boolean mOSSOnly([boolean value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, or classes.

### Method origin

    public Guid origin([Guid value])

#### Parameters

value  

#### Return Value

### Method pageTitle

    public str pageTitle([str value])

#### Parameters

value  

#### Return Value

### Method publicPage

    public boolean publicPage([boolean value])

#### Parameters

value  

#### Return Value

### Method uRL

    public str uRL([str value])

#### Parameters

value  

#### Return Value

### Method webModule

    public str webModule([str value])

#### Parameters

value  

#### Return Value

### Method AOTsetSource

Sets the source code of this node.

    public void AOTsetSource(str source, [boolean isStatic])

#### Parameters

source  
The value that specifies whether the method is static; optional.

<!-- -->

isStatic  
The value that specifies whether the method is static; optional.

#### Remarks

This method is overridden by nodes that have source code.

### Method new

Initializes a new instance of the TreeNode class.

    public void new(str name)

#### Parameters

name  

## Class WebManagedContentItem
    class WebManagedContentItem extends WebContentItem

This class is used to create a webManagedContentItem to use in EP for adding content to pages.

### Remarks

### Examples

### Methods

| Method                    | Description                                                 |
|---------------------------|-------------------------------------------------------------|
| public void new(str name) | Create a new webManagedContentItem with the passed in name. |

### Method new

Create a new webManagedContentItem with the passed in name.

    public void new(str name)

#### Parameters

name  
Name for the new webManagedContentItem.

## Class WebMenu
    class WebMenu extends TreeNode

The WebMenu class lets you create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                                   | Description                                                                                                                                   |
|--------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public str changedBy(\[str value\])                                      | Gets or sets the name of the user who last changed the application object.                                                                    |
| public Date changedDate(\[Date value\])                                  | Gets or sets the date an application object was last changed.                                                                                 |
| public str changedTime(\[str value\])                                    | Gets or sets the time an application object was last changed.                                                                                 |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\]) | Gets or sets the configuration key that is assigned to the control.                                                                           |
| public str createdBy(\[str value\])                                      | Gets or sets the name of the user who created the application object.                                                                         |
| public Date creationDate(\[Date value\])                                 | Gets or sets the date an application object was created.                                                                                      |
| public str creationTime(\[str value\])                                   |                                                                                                                                               |
| public boolean highlightSelected(\[boolean value\])                      |                                                                                                                                               |
| public str label(\[str value\])                                          | Gets or sets the label for a control.                                                                                                         |
| public str menuItemName(\[str value\])                                   |                                                                                                                                               |
| public WebMenuItemType menuItemType(\[WebMenuItemType value\])           |                                                                                                                                               |
| public str menuName()                                                    |                                                                                                                                               |
| public str name(\[str value\])                                           | Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics AX application object. |
| public int neededAccessLevel(\[int value\])                              | Gets or sets the neededAccessLevel property for the MenuFunction class.                                                                       |
| public Guid origin(\[Guid value\])                                       |                                                                                                                                               |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                |                                                                                                                                               |
| public boolean setCompany(\[boolean value\])                             |                                                                                                                                               |
| public boolean showParentModule(\[boolean value\])                       |                                                                                                                                               |
| public str webTarget(\[str value\])                                      |                                                                                                                                               |
| public void addSeparator()                                               |                                                                                                                                               |
| public void makeMenu(Object outputClass)                                 |                                                                                                                                               |
| public void addSubmenu(str name)                                         |                                                                                                                                               |
| public void new(str Name)                                                | Initializes a new instance of the TreeNode class.                                                                                             |
| public void addMenuitem(WebMenuFunction webMenuFunction)                 |                                                                                                                                               |

### Method changedBy

Gets or sets the name of the user who last changed the application object.

    public str changedBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method changedDate

Gets or sets the date an application object was last changed.

    public Date changedDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was last changed.

### Method changedTime

Gets or sets the time an application object was last changed.

    public str changedTime([str value])

#### Parameters

value  

#### Return Value

The time an application object was last changed.

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method createdBy

Gets or sets the name of the user who created the application object.

    public str createdBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method creationDate

Gets or sets the date an application object was created.

    public Date creationDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was created.

### Method creationTime

    public str creationTime([str value])

#### Parameters

value  

#### Return Value

### Method highlightSelected

    public boolean highlightSelected([boolean value])

#### Parameters

value  

#### Return Value

### Method label

Gets or sets the label for a control.

    public str label([str value])

#### Parameters

value  

#### Return Value

The current value of the label string.

#### Remarks

The label determines which text is displayed in the control or adjacent to it.The label property value cannot exceed 250 characters.

### Method menuItemName

    public str menuItemName([str value])

#### Parameters

value  

#### Return Value

### Method menuItemType

    public WebMenuItemType menuItemType([WebMenuItemType value])

#### Parameters

value  

#### Return Value

### Method menuName

    public str menuName()

#### Return Value

### Method name

Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in the code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enumeration types, or classes.

### Method neededAccessLevel

Gets or sets the neededAccessLevel property for the MenuFunction class.

    public int neededAccessLevel([int value])

#### Parameters

value  

#### Return Value

The current value of the neededAccessLevel property.

#### Remarks

The possible values for the AccessType system enumuration value are as follows:

-   AccessType::NoAccess
-   AccessType::View
-   AccessType::Edit
-   AccessType::Add
-   AccessType::Delete

### Method origin

    public Guid origin([Guid value])

#### Parameters

value  

#### Return Value

### Method securityKey

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  

#### Return Value

### Method setCompany

    public boolean setCompany([boolean value])

#### Parameters

value  

#### Return Value

### Method showParentModule

    public boolean showParentModule([boolean value])

#### Parameters

value  

#### Return Value

### Method webTarget

    public str webTarget([str value])

#### Parameters

value  

#### Return Value

### Method addSeparator

    public void addSeparator()

### Method makeMenu

    public void makeMenu(Object outputClass)

#### Parameters

outputClass  

### Method addSubmenu

    public void addSubmenu(str name)

#### Parameters

name  

### Method new

Initializes a new instance of the TreeNode class.

    public void new(str Name)

#### Parameters

Name  

### Method addMenuitem

    public void addMenuitem(WebMenuFunction webMenuFunction)

#### Parameters

webMenuFunction  

## Class WebMenuFunction
    class WebMenuFunction extends SecureNode

The WebMenuFunction class lets you create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                                                           | Description                                                                                                                                   |
|--------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public str changedBy(\[str value\])                                                              | Gets or sets the name of the user who last changed the application object.                                                                    |
| public Date changedDate(\[Date value\])                                                          | Gets or sets the date an application object was last changed.                                                                                 |
| public str changedTime(\[str value\])                                                            | Gets or sets the time an application object was last changed.                                                                                 |
| public str createdBy(\[str value\])                                                              | Gets or sets the name of the user who created the application object.                                                                         |
| public Date creationDate(\[Date value\])                                                         | Gets or sets the date an application object was created.                                                                                      |
| public str creationTime(\[str value\])                                                           |                                                                                                                                               |
| public str helpText(\[str value\])                                                               | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                      |
| public str label(\[str value\])                                                                  | Gets or sets the label for a control.                                                                                                         |
| public str name(\[str value\])                                                                   | Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics AX application object. |
| public Guid origin(\[Guid value\])                                                               |                                                                                                                                               |
| ::public static WebMenuFunction createWebMenuFunction(str name, WebMenuItemType webMenuItemType) |                                                                                                                                               |

### Method changedBy

Gets or sets the name of the user who last changed the application object.

    public str changedBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method changedDate

Gets or sets the date an application object was last changed.

    public Date changedDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was last changed.

### Method changedTime

Gets or sets the time an application object was last changed.

    public str changedTime([str value])

#### Parameters

value  

#### Return Value

The time an application object was last changed.

### Method createdBy

Gets or sets the name of the user who created the application object.

    public str createdBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method creationDate

Gets or sets the date an application object was created.

    public Date creationDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was created.

### Method creationTime

    public str creationTime([str value])

#### Parameters

value  

#### Return Value

### Method helpText

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property dialog box.The help text must not exceed 250 characters.

### Method label

Gets or sets the label for a control.

    public str label([str value])

#### Parameters

value  

#### Return Value

The current value of the label string.

#### Remarks

The label determines which text is displayed in the control or adjacent to it.The label property value cannot exceed 250 characters.

### Method name

Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in the code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, or classes.

### Method origin

    public Guid origin([Guid value])

#### Parameters

value  

#### Return Value

### Method createWebMenuFunction

    public static WebMenuFunction createWebMenuFunction(str name, WebMenuItemType webMenuItemType)

#### Parameters

name  

<!-- -->

webMenuItemType  

#### Return Value

## Class WebMenuItem
    class WebMenuItem extends TreeNode

The WebMenuItem class enables you to create, read, update, and delete X++ code and metadata.

### Remarks

This class enables you to create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before you call this API.

### Examples

### Methods

| Method                                                         | Description                                                                                                                               |
|----------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public str label()                                             |                                                                                                                                           |
| public str menuItemName(\[str value\])                         |                                                                                                                                           |
| public WebMenuItemType menuItemType(\[WebMenuItemType value\]) |                                                                                                                                           |
| public str name(\[str value\])                                 | Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics AX application object. |
| public str parameters(\[str value\])                           | Gets or sets the list of parameters that are passed to objects taht are run by the MenuFunction class.                                    |
| public boolean showParentModule(\[boolean value\])             |                                                                                                                                           |

### Method label

    public str label()

#### Return Value

### Method menuItemName

    public str menuItemName([str value])

#### Parameters

value  

#### Return Value

### Method menuItemType

    public WebMenuItemType menuItemType([WebMenuItemType value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method parameters

Gets or sets the list of parameters that are passed to objects taht are run by the MenuFunction class.

    public str parameters([str value])

#### Parameters

value  

#### Return Value

The list of parameters that are passed to the object.

#### Remarks

The parameters string format is Parameter1=Value1, Parameter2=Value2, and so on.cts ignore passed, unrecognized parameters.

### Method showParentModule

    public boolean showParentModule([boolean value])

#### Parameters

value  

#### Return Value

## Class webModuleNode
    class webModuleNode extends TreeNode

### Remarks

### Examples

### Methods

| Method                                                                   | Description                                                                                                                                    |
|--------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| public str changedBy(\[str value\])                                      | Gets or sets the name of the user who last changed the application object.                                                                     |
| public Date changedDate(\[Date value\])                                  | Gets or sets the date an application object was last changed.                                                                                  |
| public str changedTime(\[str value\])                                    | Gets or sets the time an application object was last changed.                                                                                  |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\]) | Gets or sets the configuration key that is assigned to the control.                                                                            |
| public str createdBy(\[str value\])                                      | Gets or sets the name of the user who created the application object.                                                                          |
| public Date creationDate(\[Date value\])                                 | Gets or sets the date an application object was created.                                                                                       |
| public str creationTime(\[str value\])                                   |                                                                                                                                                |
| public boolean extendedDataSecurity(\[boolean value\])                   |                                                                                                                                                |
| public boolean inheritNavigation(\[boolean value\])                      |                                                                                                                                                |
| public boolean inheritPermissions(\[boolean value\])                     |                                                                                                                                                |
| public str label(\[str value\])                                          | Gets or sets the label for a control.                                                                                                          |
| public str masterPage(\[str value\])                                     |                                                                                                                                                |
| public str menuItemName(\[str value\])                                   |                                                                                                                                                |
| public WebMenuItemType menuItemType(\[WebMenuItemType value\])           |                                                                                                                                                |
| public str moduleName()                                                  |                                                                                                                                                |
| public str modulePath()                                                  |                                                                                                                                                |
| public str name(\[str value\])                                           | Gets or sets the name that is used in the code to identify a form, report, rabble, query, or another Microsoft Dynamics AX application object. |
| public int neededAccessLevel(\[int value\])                              | Gets or sets the neededAccessLevel property for the MenuFunction class.                                                                        |
| public Guid origin(\[Guid value\])                                       |                                                                                                                                                |
| public boolean publicModule(\[boolean value\])                           |                                                                                                                                                |
| public str quickLaunch(\[str value\])                                    |                                                                                                                                                |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                |                                                                                                                                                |
| public boolean showLink(\[boolean value\])                               |                                                                                                                                                |
| public boolean showParentModule(\[boolean value\])                       |                                                                                                                                                |
| public void addSubModule(str name)                                       |                                                                                                                                                |
| public void new(str Name)                                                | Initializes a new instance of the TreeNode class.                                                                                              |
| public void addMenuitem(WebMenuFunction webMenuFunction)                 |                                                                                                                                                |

### Method changedBy

Gets or sets the name of the user who last changed the application object.

    public str changedBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method changedDate

Gets or sets the date an application object was last changed.

    public Date changedDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was last changed.

### Method changedTime

Gets or sets the time an application object was last changed.

    public str changedTime([str value])

#### Parameters

value  

#### Return Value

The time an application object was last changed.

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method createdBy

Gets or sets the name of the user who created the application object.

    public str createdBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method creationDate

Gets or sets the date an application object was created.

    public Date creationDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was created.

### Method creationTime

    public str creationTime([str value])

#### Parameters

value  

#### Return Value

### Method extendedDataSecurity

    public boolean extendedDataSecurity([boolean value])

#### Parameters

value  

#### Return Value

### Method inheritNavigation

    public boolean inheritNavigation([boolean value])

#### Parameters

value  

#### Return Value

### Method inheritPermissions

    public boolean inheritPermissions([boolean value])

#### Parameters

value  

#### Return Value

### Method label

Gets or sets the label for a control.

    public str label([str value])

#### Parameters

value  

#### Return Value

The current value of the label string.

#### Remarks

The label determines which text is displayed in the control or adjacent to it. The label property value cannot exceed 250 characters.

### Method masterPage

    public str masterPage([str value])

#### Parameters

value  

#### Return Value

### Method menuItemName

    public str menuItemName([str value])

#### Parameters

value  

#### Return Value

### Method menuItemType

    public WebMenuItemType menuItemType([WebMenuItemType value])

#### Parameters

value  

#### Return Value

### Method moduleName

    public str moduleName()

#### Return Value

### Method modulePath

    public str modulePath()

#### Return Value

### Method name

Gets or sets the name that is used in the code to identify a form, report, rabble, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enumerations, or classes.

### Method neededAccessLevel

Gets or sets the neededAccessLevel property for the MenuFunction class.

    public int neededAccessLevel([int value])

#### Parameters

value  

#### Return Value

The current value of the neededAccessLevel property.

#### Remarks

The possible values for the AccessType system enumeration value are as follows:

-   AccessType::NoAccess
-   AccessType::View
-   AccessType::Edit
-   AccessType::Add
-   AccessType::Delete

### Method origin

    public Guid origin([Guid value])

#### Parameters

value  

#### Return Value

### Method publicModule

    public boolean publicModule([boolean value])

#### Parameters

value  

#### Return Value

### Method quickLaunch

    public str quickLaunch([str value])

#### Parameters

value  

#### Return Value

### Method securityKey

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  

#### Return Value

### Method showLink

    public boolean showLink([boolean value])

#### Parameters

value  

#### Return Value

### Method showParentModule

    public boolean showParentModule([boolean value])

#### Parameters

value  

#### Return Value

### Method addSubModule

    public void addSubModule(str name)

#### Parameters

name  

### Method new

Initializes a new instance of the TreeNode class.

    public void new(str Name)

#### Parameters

Name  

### Method addMenuitem

    public void addMenuitem(WebMenuFunction webMenuFunction)

#### Parameters

webMenuFunction  

## Class WebOutputContentItem
    class WebOutputContentItem extends WebContentItem

This class represents a WebOutputContentItem in x++.

### Remarks

### Examples

### Methods

| Method                    | Description                         |
|---------------------------|-------------------------------------|
| public void new(str name) | Creates a new WebOutputContentItem. |

### Method new

Creates a new WebOutputContentItem.

    public void new(str name)

#### Parameters

name  

## Class webPageDefNode
    class webPageDefNode extends TreeNode

The webPageDefNode class enables you to create, read, update, and delete X++ code and metadata.

### Remarks

This class enables you to create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before calling this API.

### Examples

### Methods

| Method                                                     | Description                                                                                                                               |
|------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public str AOTgetSource()                                  | Gets the source of the node.                                                                                                              |
| public str changedBy(\[str value\])                        | Gets or sets the name of the user who last changed the application object.                                                                |
| public Date changedDate(\[Date value\])                    | Gets or sets the date an application object was last changed.                                                                             |
| public str changedTime(\[str value\])                      | Gets or sets the time an application object was last changed.                                                                             |
| public str createdBy(\[str value\])                        | Gets or sets the name of the user who created the application object.                                                                     |
| public Date creationDate(\[Date value\])                   | Gets or sets the date an application object was created.                                                                                  |
| public str creationTime(\[str value\])                     |                                                                                                                                           |
| public str helpText(\[str value\])                         | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                  |
| public str imageResource(\[str value\])                    |                                                                                                                                           |
| public boolean mOSSOnly(\[boolean value\])                 |                                                                                                                                           |
| public str name(\[str value\])                             | Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics AX application object. |
| public Guid origin(\[Guid value\])                         |                                                                                                                                           |
| public str pageTitle(\[str value\])                        |                                                                                                                                           |
| public str parentPage(\[str value\])                       |                                                                                                                                           |
| public boolean publicPage(\[boolean value\])               |                                                                                                                                           |
| public str uRL(\[str value\])                              |                                                                                                                                           |
| public boolean useContext(\[boolean value\])               |                                                                                                                                           |
| public str webModule(\[str value\])                        |                                                                                                                                           |
| public str wSSHelpTopic(\[str value\])                     |                                                                                                                                           |
| public void new(str name)                                  | Creates a new webPageDefNode.                                                                                                             |
| public void AOTsetSource(str source, \[boolean isStatic\]) | Set the source of the webPageDefNode to the given string.                                                                                 |

### Method AOTgetSource

Gets the source of the node.

    public str AOTgetSource()

#### Return Value

The source of the node.

#### Remarks

This method is overridden by nodes that have source code.

### Method changedBy

Gets or sets the name of the user who last changed the application object.

    public str changedBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method changedDate

Gets or sets the date an application object was last changed.

    public Date changedDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was last changed.

### Method changedTime

Gets or sets the time an application object was last changed.

    public str changedTime([str value])

#### Parameters

value  

#### Return Value

The time an application object was last changed.

### Method createdBy

Gets or sets the name of the user who created the application object.

    public str createdBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method creationDate

Gets or sets the date an application object was created.

    public Date creationDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was created.

### Method creationTime

    public str creationTime([str value])

#### Parameters

value  

#### Return Value

### Method helpText

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property dialog box.The help text must not exceed 250 characters.

### Method imageResource

    public str imageResource([str value])

#### Parameters

value  

#### Return Value

### Method mOSSOnly

    public boolean mOSSOnly([boolean value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method origin

    public Guid origin([Guid value])

#### Parameters

value  

#### Return Value

### Method pageTitle

    public str pageTitle([str value])

#### Parameters

value  

#### Return Value

### Method parentPage

    public str parentPage([str value])

#### Parameters

value  

#### Return Value

### Method publicPage

    public boolean publicPage([boolean value])

#### Parameters

value  

#### Return Value

### Method uRL

    public str uRL([str value])

#### Parameters

value  

#### Return Value

### Method useContext

    public boolean useContext([boolean value])

#### Parameters

value  

#### Return Value

### Method webModule

    public str webModule([str value])

#### Parameters

value  

#### Return Value

### Method wSSHelpTopic

    public str wSSHelpTopic([str value])

#### Parameters

value  

#### Return Value

### Method new

Creates a new webPageDefNode.

    public void new(str name)

#### Parameters

name  

### Method AOTsetSource

Set the source of the webPageDefNode to the given string.

    public void AOTsetSource(str source, [boolean isStatic])

#### Parameters

source  
Optional parameter marking if the source provided is static.

<!-- -->

isStatic  
Optional parameter marking if the source provided is static.

#### Remarks

This method is overridden by nodes which have source code.

## Class webStaticFileNode
    class webStaticFileNode extends TreeNode

The webStaticFileNode class lets you create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                     | Description                                                                                                                               |
|------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public str AOTgetSource()                                  | Gets the source of the node.                                                                                                              |
| public str changedBy(\[str value\])                        | Gets or sets the name of the user who last changed the application object.                                                                |
| public Date changedDate(\[Date value\])                    | Gets or sets the date an application object was last changed.                                                                             |
| public str changedTime(\[str value\])                      | Gets or sets the time an application object was last changed.                                                                             |
| public str createdBy(\[str value\])                        | Gets or sets the name of the user who created the application object.                                                                     |
| public Date creationDate(\[Date value\])                   | Gets or sets the date an application object was created.                                                                                  |
| public str creationTime(\[str value\])                     |                                                                                                                                           |
| public str filename(\[str value\])                         |                                                                                                                                           |
| public str helpText(\[str value\])                         | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                  |
| public str name(\[str value\])                             | Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics AX application object. |
| public Guid origin(\[Guid value\])                         |                                                                                                                                           |
| public str relativePath(\[str value\])                     |                                                                                                                                           |
| public str version(\[str value\])                          |                                                                                                                                           |
| public void AOTsetSource(str source, \[boolean isStatic\]) | Sets the source of the static file node to the given string.                                                                              |

### Method AOTgetSource

Gets the source of the node.

    public str AOTgetSource()

#### Return Value

The source of the node.

#### Remarks

This function is overridden by nodes that have source code.

### Method changedBy

Gets or sets the name of the user who last changed the application object.

    public str changedBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method changedDate

Gets or sets the date an application object was last changed.

    public Date changedDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was last changed.

### Method changedTime

Gets or sets the time an application object was last changed.

    public str changedTime([str value])

#### Parameters

value  

#### Return Value

The time an application object was last changed.

### Method createdBy

Gets or sets the name of the user who created the application object.

    public str createdBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method creationDate

Gets or sets the date an application object was created.

    public Date creationDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was created.

### Method creationTime

    public str creationTime([str value])

#### Parameters

value  

#### Return Value

### Method filename

    public str filename([str value])

#### Parameters

value  

#### Return Value

### Method helpText

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property dialog box.The help text must not exceed 250 characters.

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, or classes.

### Method origin

    public Guid origin([Guid value])

#### Parameters

value  

#### Return Value

### Method relativePath

    public str relativePath([str value])

#### Parameters

value  

#### Return Value

### Method version

    public str version([str value])

#### Parameters

value  

#### Return Value

### Method AOTsetSource

Sets the source of the static file node to the given string.

    public void AOTsetSource(str source, [boolean isStatic])

#### Parameters

source  
An optional parameter that marks whether the source that is provided is static.

<!-- -->

isStatic  
An optional parameter that marks whether the source that is provided is static.

#### Remarks

This method is overridden by nodes that have source code.

## Class WebUrlMenuFunction
    class WebUrlMenuFunction extends WebMenuFunction

The WebUrlMenuFunction class lets you create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                | Description                                                                                            |
|-------------------------------------------------------|--------------------------------------------------------------------------------------------------------|
| public boolean big(\[boolean value\])                 |                                                                                                        |
| public int closeDialogBehavior(\[int value\])         |                                                                                                        |
| public int correctPermissions(\[int value\])          |                                                                                                        |
| public int createPermissions(\[int value\])           |                                                                                                        |
| public int deletePermissions(\[int value\])           |                                                                                                        |
| public boolean hideActionPane(\[boolean value\])      |                                                                                                        |
| public boolean homePage(\[boolean value\])            |                                                                                                        |
| public int imageLocation(\[int value\])               |                                                                                                        |
| public str linkedPermissionObject(\[str value\])      |                                                                                                        |
| public str linkedPermissionObjectChild(\[str value\]) |                                                                                                        |
| public int linkedPermissionType(\[int value\])        |                                                                                                        |
| public int maintainUserLicense(\[int value\])         | Microsoft internal use only.                                                                           |
| public boolean multiSelect(\[boolean value\])         |                                                                                                        |
| public boolean needsRecord(\[boolean value\])         |                                                                                                        |
| public str normalImage(\[str value\])                 |                                                                                                        |
| public int normalResource(\[int value\])              |                                                                                                        |
| public Guid origin(\[Guid value\])                    |                                                                                                        |
| public str pageDefinition(\[str value\])              |                                                                                                        |
| public str parameters(\[str value\])                  | Gets or sets the list of parameters that are passed to objects that are run by the MenuFunction class. |
| public int readPermissions(\[int value\])             |                                                                                                        |
| public int updatePermissions(\[int value\])           |                                                                                                        |
| public str uRL(\[str value\])                         |                                                                                                        |
| public int viewUserLicense(\[int value\])             | Microsoft internal use only.                                                                           |
| public int windowMode(\[int value\])                  |                                                                                                        |
| public str windowParameters(\[str value\])            |                                                                                                        |
| public int windowSize(\[int value\])                  |                                                                                                        |
| public void new(str name)                             | Initializes a new instance of the TreeNode class.                                                      |

### Method big

    public boolean big([boolean value])

#### Parameters

value  

#### Return Value

### Method closeDialogBehavior

    public int closeDialogBehavior([int value])

#### Parameters

value  

#### Return Value

### Method correctPermissions

    public int correctPermissions([int value])

#### Parameters

value  

#### Return Value

### Method createPermissions

    public int createPermissions([int value])

#### Parameters

value  

#### Return Value

### Method deletePermissions

    public int deletePermissions([int value])

#### Parameters

value  

#### Return Value

### Method hideActionPane

    public boolean hideActionPane([boolean value])

#### Parameters

value  

#### Return Value

### Method homePage

    public boolean homePage([boolean value])

#### Parameters

value  

#### Return Value

### Method imageLocation

    public int imageLocation([int value])

#### Parameters

value  

#### Return Value

### Method linkedPermissionObject

    public str linkedPermissionObject([str value])

#### Parameters

value  

#### Return Value

### Method linkedPermissionObjectChild

    public str linkedPermissionObjectChild([str value])

#### Parameters

value  

#### Return Value

### Method linkedPermissionType

    public int linkedPermissionType([int value])

#### Parameters

value  

#### Return Value

### Method maintainUserLicense

Microsoft internal use only.

    public int maintainUserLicense([int value])

#### Parameters

value  
The new user license.

#### Return Value

The user license.

### Method multiSelect

    public boolean multiSelect([boolean value])

#### Parameters

value  

#### Return Value

### Method needsRecord

    public boolean needsRecord([boolean value])

#### Parameters

value  

#### Return Value

### Method normalImage

    public str normalImage([str value])

#### Parameters

value  

#### Return Value

### Method normalResource

    public int normalResource([int value])

#### Parameters

value  

#### Return Value

### Method origin

    public Guid origin([Guid value])

#### Parameters

value  

#### Return Value

### Method pageDefinition

    public str pageDefinition([str value])

#### Parameters

value  

#### Return Value

### Method parameters

Gets or sets the list of parameters that are passed to objects that are run by the MenuFunction class.

    public str parameters([str value])

#### Parameters

value  

#### Return Value

The list of parameters that are passed to the object.

#### Remarks

The parameters string format is Parameter1=Value1, Parameter2=Value2, and so on. CTS will ignore passed, unrecognized parameters.

### Method readPermissions

    public int readPermissions([int value])

#### Parameters

value  

#### Return Value

### Method updatePermissions

    public int updatePermissions([int value])

#### Parameters

value  

#### Return Value

### Method uRL

    public str uRL([str value])

#### Parameters

value  

#### Return Value

### Method viewUserLicense

Microsoft internal use only.

    public int viewUserLicense([int value])

#### Parameters

value  
A user license to view.

#### Return Value

The user license.

### Method windowMode

    public int windowMode([int value])

#### Parameters

value  

#### Return Value

### Method windowParameters

    public str windowParameters([str value])

#### Parameters

value  

#### Return Value

### Method windowSize

    public int windowSize([int value])

#### Parameters

value  

#### Return Value

### Method new

Initializes a new instance of the TreeNode class.

    public void new(str name)

#### Parameters

name  

## Class WinAPINative
    class WinAPINative extends Object

### Remarks

### Examples

### Methods

| Method                                                                                                                  | Description                                           |
|-------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------|
| ::public static Int64 createFontIndirect(Binary logfont)                                                                |                                                       |
| ::public static boolean deleteObject(Int64 hGDIObject)                                                                  |                                                       |
| ::public static boolean getCharABCWidthsI(Int64 hDC, Int64 firstGlyphIndex, Int64 glyphIndicesCount, Binary charWidths) |                                                       |
| ::public static int getDeviceCaps(Int64 hDC, int index)                                                                 |                                                       |
| ::public static int getFontData(Int64 hDC, int dwTable, int dwOffset, \[Binary pvBuffer\])                              |                                                       |
| ::public static int getFontUnicodeRanges(Int64 hDC, \[Binary lpgs\])                                                    |                                                       |
| ::public static int getGlyphIndices(Int64 hDC, str lpstr, Binary pgi, int fl)                                           |                                                       |
| ::public static Int64 getTextMetrics(Int64 hDC, Binary lpMetrics)                                                       |                                                       |
| ::public static int getUniscribeGlyphIndices(Int64 hDC, Int64 hGDIObject, str lpstr, Binary pgi)                        |                                                       |
| ::public static Int64 selectObject(Int64 hDC, Int64 hGDIObject)                                                         |                                                       |
| private void new()                                                                                                      | Initializes a new instance of the WinAPINative class. |

### Method createFontIndirect

    public static Int64 createFontIndirect(Binary logfont)

#### Parameters

logfont  

#### Return Value

### Method deleteObject

    public static boolean deleteObject(Int64 hGDIObject)

#### Parameters

hGDIObject  

#### Return Value

### Method getCharABCWidthsI

    public static boolean getCharABCWidthsI(Int64 hDC, Int64 firstGlyphIndex, Int64 glyphIndicesCount, Binary charWidths)

#### Parameters

hDC  

<!-- -->

firstGlyphIndex  

<!-- -->

glyphIndicesCount  

<!-- -->

charWidths  

#### Return Value

### Method getDeviceCaps

    public static int getDeviceCaps(Int64 hDC, int index)

#### Parameters

hDC  

<!-- -->

index  

#### Return Value

### Method getFontData

    public static int getFontData(Int64 hDC, int dwTable, int dwOffset, [Binary pvBuffer])

#### Parameters

hDC  

<!-- -->

dwTable  

<!-- -->

dwOffset  

<!-- -->

pvBuffer  

#### Return Value

### Method getFontUnicodeRanges

    public static int getFontUnicodeRanges(Int64 hDC, [Binary lpgs])

#### Parameters

hDC  

<!-- -->

lpgs  

#### Return Value

### Method getGlyphIndices

    public static int getGlyphIndices(Int64 hDC, str lpstr, Binary pgi, int fl)

#### Parameters

hDC  

<!-- -->

lpstr  

<!-- -->

pgi  

<!-- -->

fl  

#### Return Value

### Method getTextMetrics

    public static Int64 getTextMetrics(Int64 hDC, Binary lpMetrics)

#### Parameters

hDC  

<!-- -->

lpMetrics  

#### Return Value

### Method getUniscribeGlyphIndices

    public static int getUniscribeGlyphIndices(Int64 hDC, Int64 hGDIObject, str lpstr, Binary pgi)

#### Parameters

hDC  

<!-- -->

hGDIObject  

<!-- -->

lpstr  

<!-- -->

pgi  

#### Return Value

### Method selectObject

    public static Int64 selectObject(Int64 hDC, Int64 hGDIObject)

#### Parameters

hDC  

<!-- -->

hGDIObject  

#### Return Value

### Method new

Initializes a new instance of the WinAPINative class.

    private void new()

