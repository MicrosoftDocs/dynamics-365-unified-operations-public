---
title: DocNode class
description: This topic describes the DocNode class.
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

# Class DocNode

[!include [banner](../../includes/banner.md)]

```xpp
class DocNode extends TreeNode
```

The DocNode class provides the information and functions for a documentation node.

## Remarks

This class lets you create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

## Examples

## Methods

| Method                                                                                                                                                                                            | Description                                                                                                                             |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| public str AOTgetSource()                                                                                                                                                                         | Returns the source code for the node.                                                                                                   |
| public str changedBy(\[str value\])                                                                                                                                                               | Gets or sets the name of the user who last changed the application object.                                                              |
| public Date changedDate(\[Date value\])                                                                                                                                                           | Gets or sets the date that an application object was last changed.                                                                      |
| public str changedTime(\[str value\])                                                                                                                                                             | Gets or sets the time that an application object was last changed.                                                                      |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                                                                                                          | Gets or sets the configuration key that is assigned to the control.                                                                     |
| public str createdBy(\[str value\])                                                                                                                                                               | Gets or sets the name of the user who created the application object.                                                                   |
| public Date creationDate(\[Date value\])                                                                                                                                                          | Gets or sets the date that an application object was created.                                                                           |
| public str creationTime(\[str value\])                                                                                                                                                            |                                                                                                                                         |
| public str description(\[str value\])                                                                                                                                                             | Sets or returns the description of the documentation node.                                                                              |
| public str name(\[str value\])                                                                                                                                                                    | Gets or sets the name that is used in code to identify a form, report, table, query, or other application object. |
| public int neededAccessLevel(\[int value\])                                                                                                                                                       | Gets or sets the neededAccessLevel property for the MenuFunction class.                                                                 |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                                                                                                         | Sets or returns the security key for the documentation node.                                                                            |
| public str title(\[str value\])                                                                                                                                                                   | Sets or returns the title of the documentation node.                                                                                    |
| ::public static DocNode findAOTElementDocNode(ApplCodeDocType HelpType, str Name, \[str ParentName\], \[int Mode\])                                                                               | Performs a search for an element documentation node in the Application Object Tree (AOT).                         |
| ::public static DocNode findApplicationDocNode(ApplHelpType HelpType, str Name, \[str ParentName\], \[int Mode\])                                                                                 | Performs a search for an application element documentation node.                                                                        |
| ::public static DocNode findKernelDocNode(KernelHelpType HelpType, str Name, \[str ParentName\], \[int Mode\])                                                                                    | Performs a search for a kernel element documentation node.                                                                              |
| ::public static DocNode getNodeDetached(UtilFileType helpType, int UtilType, str Name, \[int ParentId\], \[int Type\], \[UtilEntryLevel Utillevel\], \[boolean Forcelevel\], \[boolean OldUtil\]) | Returns the specified documentation node.                                                                                               |
| public void AOTsetSource(str source, \[boolean isStatic\])                                                                                                                                        | Sets the source code for the node.                                                                                                      |
| public void AOTedit(\[int Line\], \[int Column\])                                                                                                                                                 | Opens the appropriate editor for this node.                                                                                             |

## Method AOTgetSource

Returns the source code for the node.

```xpp
public str AOTgetSource()
```

### Return Value - AOTgetSource

The source code for the node as a string; null, Nothing, nullptr, unit, a null reference (Nothing in Visual Basic) if there is no source code for the node.

## Method changedBy

Gets or sets the name of the user who last changed the application object.

```xpp
public str changedBy([str value])
```

### Parameters - changedBy

value  
The value that is being assigned as the user who changed the documentation node.

### Return Value - changedBy

The name of the user.

## Method changedDate

Gets or sets the date that an application object was last changed.

```xpp
public Date changedDate([Date value])
```

### Parameters - changedDate

value  
The value that is being assigned as the change date for the documentation node.

### Return Value - changedDate

The date that an application object was last changed.

## Method changedTime

Gets or sets the time that an application object was last changed.

```xpp
public str changedTime([str value])
```

### Parameters - changedTime

value  
The value that is being assigned as the change time for the documentation node.

### Return Value - changedTime

The time that an application object was last changed.

## Method configurationKey

Gets or sets the configuration key that is assigned to the control.

```xpp
public ConfigurationKeyId configurationKey([ConfigurationKeyId value])
```

### Parameters - configurationKey

value  
The value that is being assigned for the configuration key ID.

### Return Value - configurationKey

The identifier of the configuration key that is assigned to the control.

### Remarks - configurationKey

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

## Method createdBy

Gets or sets the name of the user who created the application object.

```xpp
public str createdBy([str value])
```

### Parameters - createdBy

value  
The value that is being assigned as the user who created the documentation node.

### Return Value - createdBy

The name of the user.

## Method creationDate

Gets or sets the date that an application object was created.

```xpp
public Date creationDate([Date value])
```

### Parameters - creationDate

value  
The value that is being assigned as the creation date for the documentation node.

### Return Value - creationDate

The date that an application object was created.

## Method creationTime

```xpp
public str creationTime([str value])
```

### Parameters - creationTime

value  

### Return Value - creationTime

## Method description

Sets or returns the description of the documentation node.

```xpp
public str description([str value])
```

### Parameters - description

value  
The value that is being assigned as the description of the documentation node.

### Return Value - description

The description of the documentation node.

## Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other application object.

```xpp
public str name([str value])
```

### Parameters - name

value  
The name that is being assigned to the documentation node.

### Return Value - name

The name that is used in code to identify an application object.

### Remarks - name

The name property value of an object must meet the following criteria to avoid code conflicts:

-   It must begin with a letter.
-   It cannot exceed 250 characters.
-   It can include numbers and underscore (\_) characters.
-   It cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, and classes.

## Method neededAccessLevel

Gets or sets the neededAccessLevel property for the MenuFunction class.

```xpp
public int neededAccessLevel([int value])
```

### Parameters - neededAccessLevel

value  

### Return Value - neededAccessLevel

The current value of the neededAccessLevel property.

### Remarks - neededAccessLevel

The possible values for the AccessType system enumuration value are as follows:

-   AccessType::NoAccess.
-   AccessType::View.
-   AccessType::Edit.
-   AccessType::Add.
-   AccessType::Delete.

## Method securityKey

Sets or returns the security key for the documentation node.

```xpp
public SecurityKeyId securityKey([SecurityKeyId value])
```

### Parameters - securityKey

value  
The value that is being assigned for the security key ID.

### Return Value - securityKey

The security key ID for the documentation node; 0 (zero) if no security key is associated with the documentation node.

## Method title

Sets or returns the title of the documentation node.

```xpp
public str title([str value])
```

### Parameters - title

value  
The title that is being assigned to the documentation node.

### Return Value - title

The title of the documentation node.

## Method findAOTElementDocNode

Performs a search for an element documentation node in the Application Object Tree (AOT).

```xpp
public static DocNode findAOTElementDocNode(ApplCodeDocType HelpType, str Name, [str ParentName], [int Mode])
```

### Parameters - findAOTElementDocNode

HelpType  
The mode to use for the search; optional.

<!-- -->

Name  
The mode to use for the search; optional.

<!-- -->

ParentName  
The mode to use for the search; optional.

<!-- -->

Mode  
The mode to use for the search; optional.

### Return Value - findAOTElementDocNode

The node that is found; otherwise, null, Nothing, nullptr, unit, a null reference (Nothing in Visual Basic).

## Method findApplicationDocNode

Performs a search for an application element documentation node.

```xpp
public static DocNode findApplicationDocNode(ApplHelpType HelpType, str Name, [str ParentName], [int Mode])
```

### Parameters - findApplicationDocNode

HelpType  
The mode to use for the search; optional.

<!-- -->

Name  
The mode to use for the search; optional.

<!-- -->

ParentName  
The mode to use for the search; optional.

<!-- -->

Mode  
The mode to use for the search; optional.

### Return Value - findApplicationDocNode

The node that is found; null, Nothing, nullptr, unit, a null reference (Nothing in Visual Basic) if the node was not found.

## Method findKernelDocNode

Performs a search for a kernel element documentation node.

```xpp
public static DocNode findKernelDocNode(KernelHelpType HelpType, str Name, [str ParentName], [int Mode])
```

### Parameters - findKernelDocNode

HelpType  
The mode to use for the search; optional.

<!-- -->

Name  
The mode to use for the search; optional.

<!-- -->

ParentName  
The mode to use for the search; optional.

<!-- -->

Mode  
The mode to use for the search; optional.

### Return Value - findKernelDocNode

The node that is found; otherwise, null, Nothing, nullptr, unit, a null reference (Nothing in Visual Basic).

## Method getNodeDetached

Returns the specified documentation node.

```xpp
public static DocNode getNodeDetached(UtilFileType helpType, int UtilType, str Name, [int ParentId], [int Type], [UtilEntryLevel Utillevel], [boolean Forcelevel], [boolean OldUtil])
```

### Parameters - getNodeDetached

helpType  
Reserved; optional.

<!-- -->

UtilType  
Reserved; optional.

<!-- -->

Name  
Reserved; optional.

<!-- -->

ParentId  
Reserved; optional.

<!-- -->

Type  
Reserved; optional.

<!-- -->

Utillevel  
Reserved; optional.

<!-- -->

Forcelevel  
Reserved; optional.

<!-- -->

OldUtil  
Reserved; optional.

### Return Value - getNodeDetached

The specified documentation node.

## Method AOTsetSource

Sets the source code for the node.

```xpp
public void AOTsetSource(str source, [boolean isStatic])
```

### Parameters - AOTsetSource

source  
A Boolean value that indicates whether the method is static.

<!-- -->

isStatic  
A Boolean value that indicates whether the method is static.

## Method AOTedit

Opens the appropriate editor for this node.

```xpp
public void AOTedit([int Line], [int Column])
```

### Parameters - AOTedit

Line  
The column of the cursor position; optional.

<!-- -->

Column  
The column of the cursor position; optional.

### Remarks - AOTedit

If the node is a method, the code editor opens. If the node is a documentation object, the Help editor opens.

