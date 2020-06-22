---
title: ProjectNode class
description: This topic describes the ProjectNode class.
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

# Class ProjectNode

[!include [banner](../../includes/banner.md)]

```xpp
class ProjectNode extends TreeNode
```

The ProjectNode class controls the behavior of an AOT project.

## Remarks

This class enables you to create, read, update, and delete X++ code and metadata. Create a new, user-defined AOT project by extending from this class. Control the behavior of the project by overriding the methods of this class. Create both Web projects and Help projects by creating classes that extend the ProjectNode class.

## Examples

## Methods

| Method                                                                                       | Description                                                                                                                                   |
|----------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public str addContextMenuItems()                                                             | Adds a list of items to the shortcut menu of the project node.                                                                                |
| public str changedBy(\[str value\])                                                          | Gets or sets the name of the user who last changed the application object.                                                                    |
| public Date changedDate(\[Date value\])                                                      | Gets or sets the date an application object was last changed.                                                                                 |
| public str changedTime(\[str value\])                                                        | Gets or sets the time an application object was last changed.                                                                                 |
| public str createdBy(\[str value\])                                                          | Gets or sets the name of the user who created the application object.                                                                         |
| public Date creationDate(\[Date value\])                                                     | Gets or sets the date an application object was created.                                                                                      |
| public str creationTime(\[str value\])                                                       |                                                                                                                                               |
| public str export(str buffer)                                                                |                                                                                                                                               |
| public TreeNode findGroupMember(str name, UtilElementType type, \[boolean searchSubgroups\]) | Searches the project or group for a specific element.                                                                                         |
| public str getProjectClassName()                                                             | Returns the name of the class corresponding to the classid of the project.                                                                    |
| public ProjectNode getRunNode()                                                              | Opens the project window and returns the root projectNode of that window, for a particular projectNode found in the project overview window.  |
| public str import(str buffer)                                                                |                                                                                                                                               |
| public boolean isRunNode()                                                                   |                                                                                                                                               |
| public ProjectNode loadForInspection()                                                       | Returns a loaded version of a projectNode found in the project overview window.                                                               |
| public str name(\[str value\])                                                               | Gets or sets the name that is used in the code to identify a form, report, table, query, or other application object. |
| public Guid origin(\[Guid value\])                                                           |                                                                                                                                               |
| public boolean removeFromProject(TreeNode node)                                              |                                                                                                                                               |
| public str tooltipText(TreeNode node)                                                        |                                                                                                                                               |
| ::public static str projectType()                                                            |                                                                                                                                               |
| public void lockUpdate()                                                                     | Prevents visual updates while a series of actions is being performed.                                                                         |
| public void addSpecialOverlayIcon(str path, int resId, \[int xOffset\], \[int yOffset\])     |                                                                                                                                               |
| public void created(str name)                                                                | Enables the ability to perform custom actions on a project when a new instance of the project is created.                                     |
| public void setSpecialIcon(int type, str name, int resId)                                    | Assigns a different icon to a specific node in the project.                                                                                   |
| public void loadProject(str buffer)                                                          | Enables storing and retrieving custom data in the project definition when a project is loaded.                                                |
| public void saveProject(str buffer)                                                          | Enables saving custom data together with the project in the application object database.                                                      |
| public void unlockUpdate()                                                                   | Enables a visual update after a series of actions started with lockUpdate.                                                                    |
| public void handleContextMenuItem(int id)                                                    | Handles a user selecting an item on the shortcut menu that has been defined by the corresponding method addContextMenuItems.                  |
| public void addNode(TreeNode node)                                                           | Adds an existing node to the project.                                                                                                         |
| public void addUtilNode(UtilElementType type, str name)                                      | Adds a node to the project.                                                                                                                   |
| public void clear()                                                                          | Removes the contents of a project.                                                                                                            |
| public void setProjectClass(int classid)                                                     | Assigns a class to the project, which gives the project the type that the class defines.                                                      |
| public void removeSpecialOverlayIcons(str path)                                              |                                                                                                                                               |
| public void new()                                                                            | Initializes a new instance of the ProjectNode class.                                                                                          |

## Method addContextMenuItems

Adds a list of items to the shortcut menu of the project node.

```xpp
public str addContextMenuItems()
```

### Return Value - addContextMenuItems

A comma-separated list of the menu items to be added.

### Remarks - addContextMenuItems

Override this method to add a list of items to the shortcut menu of the project node. When one of the added menu items is selected by a user, the handleContextMenuItem method is called. Override this method to perform the appropriate action.

## Method changedBy

Gets or sets the name of the user who last changed the application object.

```xpp
public str changedBy([str value])
```

### Parameters - changedBy

value  

### Return Value - changedBy

The name of the user.

## Method changedDate

Gets or sets the date an application object was last changed.

```xpp
public Date changedDate([Date value])
```

### Parameters - changedDate

value  

### Return Value - changedDate

The date an application object was last changed.

## Method changedTime

Gets or sets the time an application object was last changed.

```xpp
public str changedTime([str value])
```

### Parameters - changedTime

value  

### Return Value - changedTime

The time an application object was last changed.

## Method createdBy

Gets or sets the name of the user who created the application object.

```xpp
public str createdBy([str value])
```

### Parameters - createdBy

value  

### Return Value - createdBy

The name of the user.

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

## Method export

```xpp
public str export(str buffer)
```

### Parameters - export

buffer  

### Return Value - export

## Method findGroupMember

Searches the project or group for a specific element.

```xpp
public TreeNode findGroupMember(str name, UtilElementType type, [boolean searchSubgroups])
```

### Parameters - findGroupMember

name  
A Boolean flag to determine whether the search should be recursive; optional.

<!-- -->

type  
A Boolean flag to determine whether the search should be recursive; optional.

<!-- -->

searchSubgroups  
A Boolean flag to determine whether the search should be recursive; optional.

### Return Value - findGroupMember

The first object that fits the criteria, or nullNothingnullptrunita null reference (Nothing in Visual Basic) if no object is found.

### Remarks - findGroupMember

This method is also found on ProjectGroupNode.

## Method getProjectClassName

Returns the name of the class corresponding to the classid of the project.

```xpp
public str getProjectClassName()
```

### Return Value - getProjectClassName

The name of the class corresponding to the classid of the project.

### Remarks - getProjectClassName

The setClassId method assigns a classid to the project.

## Method getRunNode

Opens the project window and returns the root projectNode of that window, for a particular projectNode found in the project overview window.

```xpp
public ProjectNode getRunNode()
```

### Return Value - getRunNode

The running projectNode.

### Remarks - getRunNode

To obtain a running projectNode without opening the project window, use the ProjectNode.loadForInspection Method.

## Method import

```xpp
public str import(str buffer)
```

### Parameters - import

buffer  

### Return Value - import

## Method isRunNode

```xpp
public boolean isRunNode()
```

### Return Value - isRunNode

## Method loadForInspection

Returns a loaded version of a projectNode found in the project overview window.

```xpp
public ProjectNode loadForInspection()
```

### Return Value - loadForInspection

The loaded projectNode.

### Remarks - loadForInspection

To get a loaded projectNode while also opening the project window, use the method getRunNode.

## Method name

Gets or sets the name that is used in the code to identify a form, report, table, query, or other application object.

```xpp
public str name([str value])
```

### Parameters - name

value  

### Return Value - name

The name that is used in the code to identify an application object.

### Remarks - name

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

## Method origin

```xpp
public Guid origin([Guid value])
```

### Parameters - origin

value  

### Return Value - origin

## Method removeFromProject

```xpp
public boolean removeFromProject(TreeNode node)
```

### Parameters - removeFromProject

node  

### Return Value - removeFromProject

## Method tooltipText

```xpp
public str tooltipText(TreeNode node)
```

### Parameters - tooltipText

node  

### Return Value - tooltipText

## Method projectType

```xpp
public static str projectType()
```

### Return Value - projectType

## Method lockUpdate

Prevents visual updates while a series of actions is being performed.

```xpp
public void lockUpdate()
```

### Remarks - lockUpdate

To perform visual updates after the series of actions, call unlockUpdate.

## Method addSpecialOverlayIcon

```xpp
public void addSpecialOverlayIcon(str path, int resId, [int xOffset], [int yOffset])
```

### Parameters - addSpecialOverlayIcon

path  

<!-- -->

resId  

<!-- -->

xOffset  

<!-- -->

yOffset  

## Method created

Enables the ability to perform custom actions on a project when a new instance of the project is created.

```xpp
public void created(str name)
```

### Parameters - created

name  
The name of the project instance.

### Remarks - created

This method is called when a new instance of the project is created. Override this method to perform custom actions on your project.

## Method setSpecialIcon

Assigns a different icon to a specific node in the project.

```xpp
public void setSpecialIcon(int type, str name, int resId)
```

### Parameters - setSpecialIcon

type  
The ID of the icon that must be used for the specified node.

<!-- -->

name  
The ID of the icon that must be used for the specified node.

<!-- -->

resId  
The ID of the icon that must be used for the specified node.

## Method loadProject

Enables storing and retrieving custom data in the project definition when a project is loaded.

```xpp
public void loadProject(str buffer)
```

### Parameters - loadProject

buffer  
A string that contains the custom data that was saved in the project by saveProject.

### Remarks - loadProject

This method is called when a project is loaded. By overriding saveProject and loadProject, a user can store and retrieve custom data in the project definition. You must call super() for the project to continue loading.

## Method saveProject

Enables saving custom data together with the project in the application object database.

```xpp
public void saveProject(str buffer)
```

### Parameters - saveProject

buffer  
A string buffer that must be used for packing the data. The buffer must then be passed on to super().

### Remarks - saveProject

By overriding this method, you can save custom data together with the project in the application object database. It is recommended that the data be formed as an XML string in the following form: "&lt;APPDATA&gt; ... &lt;/APPDATA&gt;" The data can be retrieved by overriding the loadProject method.

## Method unlockUpdate

Enables a visual update after a series of actions started with lockUpdate.

```xpp
public void unlockUpdate()
```

## Method handleContextMenuItem

Handles a user selecting an item on the shortcut menu that has been defined by the corresponding method addContextMenuItems.

```xpp
public void handleContextMenuItem(int id)
```

### Parameters - handleContextMenuItem

id  
The ID of the menu items. This is the zero-based number in the list set by the addContextMenuItems method. If accContextMenuItems returns the string "item1,item2" and the user selects the item "item2" in the shortcut menu, this method uses the value 1.

### Remarks - handleContextMenuItem

This method is called when a user selects an item on the shortcut menu that has been defined by the corresponding method addContextMenuItems.

## Method addNode

Adds an existing node to the project.

```xpp
public void addNode(TreeNode node)
```

### Parameters - addNode

node  
The node to add.

## Method addUtilNode

Adds a node to the project.

```xpp
public void addUtilNode(UtilElementType type, str name)
```

### Parameters - addUtilNode

type  
The name of the node.

<!-- -->

name  
The name of the node.

### Remarks - addUtilNode

This function is also found on ProjectGroupNode.

## Method clear

Removes the contents of a project.

```xpp
public void clear()
```

### Remarks - clear

This method does not remove the project contents from the Application Object Tree (AOT)�only from the project itself. This method removes the project contents but does not remove the project folder. To delete a project and its contents in one method call, use the AOTdelete method. To delete objects from the AOT, use the AOTdelete method.

### Examples - clear

The following example removes any objects in the Project1 project in the Private folder.

```xpp
static void clearProjectObjects(Args _args) 
    { 
        ProjectNode privatePn; 
        ProjectNode pn; 
        // Navigate to the Private projects folder. 
        privatePn = infolog.projectRootNode().AOTfindChild("Private"); 
        // Get a reference to the project. 
        pn = privatePn.AOTfindChild("Project1"); 
        // Clear the project. 
        pn.clear(); 
    }
```

## Method setProjectClass

Assigns a class to the project, which gives the project the type that the class defines.

```xpp
public void setProjectClass(int classid)
```

### Parameters - setProjectClass

classid  
The ID of the class to assign to the project.

### Remarks - setProjectClass

The specified class must extend the projectNode class.

## Method removeSpecialOverlayIcons

```xpp
public void removeSpecialOverlayIcons(str path)
```

### Parameters - removeSpecialOverlayIcons

path  

## Method new

Initializes a new instance of the ProjectNode class.

```xpp
public void new()
```

