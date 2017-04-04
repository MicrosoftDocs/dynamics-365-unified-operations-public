---
# required metadata

title: V Classes
description: System API classes that start with the letter V.
author: RobinARH
manager: AnnBe
ms.date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: RobinARH
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 55841
ms.assetid: fd3859a7-c0e5-41b3-9bd3-fc68099e727f
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# V Classes

System API classes that start with the letter V.

Class ValidateEventArgs
-----------------------

    class ValidateEventArgs extends DataEventArgs

### Remarks

### Examples

### Methods

| Method                                                | Description |
|-------------------------------------------------------|-------------|
| public boolean parmValidateResult(\[boolean result\]) |             |
| public void new(boolean result)                       |             |

### Method parmValidateResult

    public boolean parmValidateResult([boolean result])

#### Parameters

result  

#### Return Value

### Method new

    public void new(boolean result)

#### Parameters

result  

## Class ValidateFieldEventArgs
    class ValidateFieldEventArgs extends ValidateEventArgs

### Remarks

### Examples

### Methods

| Method                                       | Description |
|----------------------------------------------|-------------|
| public int parmFieldId()                     |             |
| public void new(int fieldId, boolean result) |             |

### Method parmFieldId

    public int parmFieldId()

#### Return Value

### Method new

    public void new(int fieldId, boolean result)

#### Parameters

fieldId  

<!-- -->

result  

## Class ValidateFieldValueEventArgs
    class ValidateFieldValueEventArgs extends ValidateEventArgs

### Remarks

### Examples

### Methods

| Method                                                         | Description |
|----------------------------------------------------------------|-------------|
| public str parmFieldName()                                     |             |
| public int parmArrayIndex()                                    |             |
| public void new(str fieldName, int arrayIndex, boolean result) |             |

### Method parmFieldName

    public str parmFieldName()

#### Return Value

### Method parmArrayIndex

    public int parmArrayIndex()

#### Return Value

### Method new

    public void new(str fieldName, int arrayIndex, boolean result)

#### Parameters

fieldName  

<!-- -->

arrayIndex  

<!-- -->

result  

## Class VirtualChannelManager
    class VirtualChannelManager extends Object

### Remarks

### Examples

### Methods

| Method                                         | Description                                                    |
|------------------------------------------------|----------------------------------------------------------------|
| public void finalize()                         |                                                                |
| public void new()                              | Initializes a new instance of the VirtualChannelManager class. |
| public void sendData(int listenerId, str data) |                                                                |

### Method finalize

    public void finalize()

### Method new

Initializes a new instance of the VirtualChannelManager class.

    public void new()

### Method sendData

    public void sendData(int listenerId, str data)

#### Parameters

listenerId  

<!-- -->

data  

## Class VSItemNode
    class VSItemNode extends TreeNode

The VSItemNode class is a base class for Microsoft Visual Studio project nodes in the Microsoft Dynamics 365 for Operations Application Object Tree (AOT).

### Remarks

### Examples

### Methods

| Method                                                             | Description                                          |
|--------------------------------------------------------------------|------------------------------------------------------|
| public str AOTgetSource()                                          | Returns the source code of this node.                |
| public BinData getFileData()                                       |                                                      |
| ::public static void notifyFileDeleted(TreeNode node, str aotPath) | Notifies listeners that a file has been deleted.     |
| ::public static void notifyFileUpdated(TreeNode node)              | Notifies listeners that a file has been updated.     |
| public void setFileData(BinData data)                              |                                                      |
| public void AOTsetSource(str source, \[boolean isStatic\])         | Sets the source code of this node.                   |
| public void getFile(str fileName)                                  |                                                      |
| ::public static void notifyFileCreated(TreeNode node)              | Notifies listeners that a new file has been created. |
| ::public static void notifyFileRenamed(TreeNode node, str oldName) | Notifies listeners that a file has been renamed.     |
| public void setFile(str fileName)                                  |                                                      |

### Method AOTgetSource

Returns the source code of this node.

    public str AOTgetSource()

#### Return Value

The string that contains the source code, if there is any; otherwise, nullNothingnullptrunita null reference (Nothing in Visual Basic).

#### Remarks

This function is overridden by nodes that have source code.

### Method getFileData

    public BinData getFileData()

#### Return Value

### Method notifyFileDeleted

Notifies listeners that a file has been deleted.

    public static void notifyFileDeleted(TreeNode node, str aotPath)

#### Parameters

node  
The AOT path of the file.

<!-- -->

aotPath  
The AOT path of the file.

### Method notifyFileUpdated

Notifies listeners that a file has been updated.

    public static void notifyFileUpdated(TreeNode node)

#### Parameters

node  
The node that has been updated.

### Method setFileData

    public void setFileData(BinData data)

#### Parameters

data  

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

### Method getFile

    public void getFile(str fileName)

#### Parameters

fileName  

### Method notifyFileCreated

Notifies listeners that a new file has been created.

    public static void notifyFileCreated(TreeNode node)

#### Parameters

node  
The node that has been created.

### Method notifyFileRenamed

Notifies listeners that a file has been renamed.

    public static void notifyFileRenamed(TreeNode node, str oldName)

#### Parameters

node  
The old name of the file.

<!-- -->

oldName  
The old name of the file.

### Method setFile

    public void setFile(str fileName)

#### Parameters

fileName  

## Class VSProjectFileNode
    class VSProjectFileNode extends VSItemNode

The VSProjectFileNode class represents files in the Microsoft Visual Studio project nodes in the Microsoft Dynamics 365 for Operations Application Object Tree (AOT).

### Remarks

### Examples

### Methods

| Method                                                             | Description                           |
|--------------------------------------------------------------------|---------------------------------------|
| public str AOTgetSource()                                          | Returns the source code of this node. |
| public BinData getFileData()                                       |                                       |
| ::public static void notifyFileCreated(TreeNode node)              |                                       |
| public void setFileData(BinData data)                              |                                       |
| public void getFile(str fileName)                                  |                                       |
| ::public static void notifyFileDeleted(TreeNode node, str aotPath) |                                       |
| ::public static void notifyFileUpdated(TreeNode node)              |                                       |
| public void setFile(str fileName)                                  |                                       |
| ::public static void notifyFileRenamed(TreeNode node, str oldName) |                                       |
| public void AOTsetSource(str source, \[boolean isStatic\])         | Sets the source code of this node.    |

### Method AOTgetSource

Returns the source code of this node.

    public str AOTgetSource()

#### Return Value

The string that contains source code, if there is any; otherwise, nullNothingnullptrunita null reference (Nothing in Visual Basic).

#### Remarks

This function is overridden by nodes that have source code.

### Method getFileData

    public BinData getFileData()

#### Return Value

### Method notifyFileCreated

    public static void notifyFileCreated(TreeNode node)

#### Parameters

node  

### Method setFileData

    public void setFileData(BinData data)

#### Parameters

data  

### Method getFile

    public void getFile(str fileName)

#### Parameters

fileName  

### Method notifyFileDeleted

    public static void notifyFileDeleted(TreeNode node, str aotPath)

#### Parameters

node  

<!-- -->

aotPath  

### Method notifyFileUpdated

    public static void notifyFileUpdated(TreeNode node)

#### Parameters

node  

### Method setFile

    public void setFile(str fileName)

#### Parameters

fileName  

### Method notifyFileRenamed

    public static void notifyFileRenamed(TreeNode node, str oldName)

#### Parameters

node  

<!-- -->

oldName  

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

## Class VSProjectFolderNode
    class VSProjectFolderNode extends TreeNode

The VSProjectFolderNode class represents folders in the Microsoft Visual Studio project nodes in the Microsoft Dynamics 365 for Operations Application Object Tree (AOT).

### Remarks

### Examples

### Methods

| Method                                                                                       | Description                                                                                              |
|----------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------|
| public str AOTgetSource()                                                                    | Returns the source code of this node.                                                                    |
| public VSProjectFileNode createFileNode(str name)                                            | Creates a new instance of the VSProjectFileNode class as a child of this VSProjectFolderNode instance.   |
| public VSProjectFolderNode createFolderNode(str name)                                        | Creates a new instance of the VSProjectFolderNode class as a child of this VSProjectFolderNode instance. |
| public VSProjectLinkNode createLinkNode(str name, str aotPath, \[boolean createLinkedNode\]) | Creates a new instance of the VSProjectLinkNode class as a child of this VSProjectFolderNode instance.   |
| public BinData getFileData()                                                                 |                                                                                                          |
| ::public static void notifyFileUpdated(TreeNode node)                                        |                                                                                                          |
| ::public static void notifyFileDeleted(TreeNode node, str aotPath)                           |                                                                                                          |
| public void setFileData(BinData data)                                                        |                                                                                                          |
| public void AOTsetSource(str source, \[boolean isStatic\])                                   | Sets the source code of this node.                                                                       |
| public void getFile(str fileName)                                                            |                                                                                                          |
| ::public static void notifyFileCreated(TreeNode node)                                        |                                                                                                          |
| ::public static void notifyFileRenamed(TreeNode node, str oldName)                           |                                                                                                          |
| public void setFile(str fileName)                                                            |                                                                                                          |

### Method AOTgetSource

Returns the source code of this node.

    public str AOTgetSource()

#### Return Value

The string that contains source code, if there is any; otherwise, nullNothingnullptrunita null reference (Nothing in Visual Basic).

#### Remarks

This function is overridden by nodes that have source code.

### Method createFileNode

Creates a new instance of the VSProjectFileNode class as a child of this VSProjectFolderNode instance.

    public VSProjectFileNode createFileNode(str name)

#### Parameters

name  
The name of the file node.

#### Return Value

The new instance of the VSProjectFileNode class.

### Method createFolderNode

Creates a new instance of the VSProjectFolderNode class as a child of this VSProjectFolderNode instance.

    public VSProjectFolderNode createFolderNode(str name)

#### Parameters

name  
The name of the folder node.

#### Return Value

The new instance of the VSProjectFolderNode class.

### Method createLinkNode

Creates a new instance of the VSProjectLinkNode class as a child of this VSProjectFolderNode instance.

    public VSProjectLinkNode createLinkNode(str name, str aotPath, [boolean createLinkedNode])

#### Parameters

name  

<!-- -->

aotPath  

<!-- -->

createLinkedNode  

#### Return Value

The new instance of the VSProjectLinkNode class.

### Method getFileData

    public BinData getFileData()

#### Return Value

### Method notifyFileUpdated

    public static void notifyFileUpdated(TreeNode node)

#### Parameters

node  

### Method notifyFileDeleted

    public static void notifyFileDeleted(TreeNode node, str aotPath)

#### Parameters

node  

<!-- -->

aotPath  

### Method setFileData

    public void setFileData(BinData data)

#### Parameters

data  

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

### Method getFile

    public void getFile(str fileName)

#### Parameters

fileName  

### Method notifyFileCreated

    public static void notifyFileCreated(TreeNode node)

#### Parameters

node  

### Method notifyFileRenamed

    public static void notifyFileRenamed(TreeNode node, str oldName)

#### Parameters

node  

<!-- -->

oldName  

### Method setFile

    public void setFile(str fileName)

#### Parameters

fileName  

## Class VSProjectLinkNode
    class VSProjectLinkNode extends VSItemNode

The VSProjectLinkNode class represents links to other Microsoft Dynamics 365 for Operations Application Object Tree (AOT) nodes in the Microsoft Visual Studio project nodes in the AOT.

### Remarks

### Examples

### Methods

| Method                                                             | Description                           |
|--------------------------------------------------------------------|---------------------------------------|
| public str AOTgetSource()                                          | Returns the source code of this node. |
| public str getAOTPath()                                            |                                       |
| public BinData getFileData()                                       |                                       |
| ::public static void notifyFileCreated(TreeNode node)              |                                       |
| public void setFile(str fileName)                                  |                                       |
| public void setFileData(BinData data)                              |                                       |
| public void getFile(str fileName)                                  |                                       |
| ::public static void notifyFileUpdated(TreeNode node)              |                                       |
| public void AOTsetSource(str source, \[boolean isStatic\])         | Sets the source code of this node.    |
| ::public static void notifyFileRenamed(TreeNode node, str oldName) |                                       |
| ::public static void notifyFileDeleted(TreeNode node, str aotPath) |                                       |

### Method AOTgetSource

Returns the source code of this node.

    public str AOTgetSource()

#### Return Value

The string that contains source code, if there is any; otherwise, nullNothingnullptrunita null reference (Nothing in Visual Basic).

#### Remarks

This function is overridden by nodes that have source code.

### Method getAOTPath

    public str getAOTPath()

#### Return Value

### Method getFileData

    public BinData getFileData()

#### Return Value

### Method notifyFileCreated

    public static void notifyFileCreated(TreeNode node)

#### Parameters

node  

### Method setFile

    public void setFile(str fileName)

#### Parameters

fileName  

### Method setFileData

    public void setFileData(BinData data)

#### Parameters

data  

### Method getFile

    public void getFile(str fileName)

#### Parameters

fileName  

### Method notifyFileUpdated

    public static void notifyFileUpdated(TreeNode node)

#### Parameters

node  

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

### Method notifyFileRenamed

    public static void notifyFileRenamed(TreeNode node, str oldName)

#### Parameters

node  

<!-- -->

oldName  

### Method notifyFileDeleted

    public static void notifyFileDeleted(TreeNode node, str aotPath)

#### Parameters

node  

<!-- -->

aotPath  

## Class VSProjectNode
    class VSProjectNode extends xResourceNode

The VSProjectNode class represents projects in the Microsoft Visual Studio project nodes in the Microsoft Dynamics 365 for Operations Application Object Tree (AOT).

### Remarks

### Examples

### Methods

| Method                                                                | Description                                                                                       |
|-----------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| public container extract(\[str path\], \[boolean extractReferenced\]) | Extracts the whole project to disk.                                                               |
| public VSProjectFolderNode getContentNode()                           | Gets the content VSProjectFolderNode object that contains the Visual Studio project files.        |
| public DeployTo getDeployTo()                                         | Gets value of the deployTo property.                                                              |
| public VSProjectFolderNode getOutputNode()                            | Gets the output VSProjectFolderNode object that contains the Visual Studio project output files.  |
| public VSProjectFileNode getPrimaryOutputNode()                       | Gets the VSProjectFileNode object that represent the primary output of the Visual Studio project. |
| public str getPrimaryTargetFileName()                                 | Gets the primary target file name of the Visual Studio project.                                   |
| public Map getProxies()                                               | Gets the proxies in this project.                                                                 |
| public container getProxiesContainer()                                | Gets the proxies in this project.                                                                 |
| public str getReferencedProjectsInAOT()                               | Gets the AOT paths of the projects that are referenced by this Visual Studio project.             |
| public str referencedProjects(\[str value\])                          |                                                                                                   |
| public void setPrimaryTargetFileName(str targetFileName)              | Sets the primary target file name of the Visual Studio project.                                   |
| public void extractToSpecificDir(str directory)                       |                                                                                                   |
| public void setDeployTo(DeployTo deployTo)                            | Sets the value of the deployTo property.                                                          |

### Method extract

Extracts the whole project to disk.

    public container extract([str path], [boolean extractReferenced])

#### Parameters

path  
A Boolean value that determines whether to extract the referenced projects.

<!-- -->

extractReferenced  
A Boolean value that determines whether to extract the referenced projects.

#### Return Value

A list of paths where the project was extracted.

### Method getContentNode

Gets the content VSProjectFolderNode object that contains the Visual Studio project files.

    public VSProjectFolderNode getContentNode()

#### Return Value

The content VSProjectFolderNode object that contains the Visual Studio project files.

### Method getDeployTo

Gets value of the deployTo property.

    public DeployTo getDeployTo()

#### Return Value

The deployTo property value.

### Method getOutputNode

Gets the output VSProjectFolderNode object that contains the Visual Studio project output files.

    public VSProjectFolderNode getOutputNode()

#### Return Value

The output VSProjectFolderNode object that contains the Visual Studio project output files.

### Method getPrimaryOutputNode

Gets the VSProjectFileNode object that represent the primary output of the Visual Studio project.

    public VSProjectFileNode getPrimaryOutputNode()

#### Return Value

A VSProjectFileNode object that represent the primary output of the Visual Studio project.

### Method getPrimaryTargetFileName

Gets the primary target file name of the Visual Studio project.

    public str getPrimaryTargetFileName()

#### Return Value

The primary target file name of the Visual Studio project.

### Method getProxies

Gets the proxies in this project.

    public Map getProxies()

#### Return Value

A map that contains the Class, Enum, and Table keys. Each key contains a list of proxies.

### Method getProxiesContainer

Gets the proxies in this project.

    public container getProxiesContainer()

#### Return Value

A container that holds the packed representation of a map that contains the Class, Enum, and Table keys. Each key contains a list of proxies.

### Method getReferencedProjectsInAOT

Gets the AOT paths of the projects that are referenced by this Visual Studio project.

    public str getReferencedProjectsInAOT()

#### Return Value

A list of AOT paths of the projects that are referenced by this Visual Studio project.

### Method referencedProjects

    public str referencedProjects([str value])

#### Parameters

value  

#### Return Value

### Method setPrimaryTargetFileName

Sets the primary target file name of the Visual Studio project.

    public void setPrimaryTargetFileName(str targetFileName)

#### Parameters

targetFileName  
The primary target file name of the Visual Studio project.

### Method extractToSpecificDir

    public void extractToSpecificDir(str directory)

#### Parameters

directory  

### Method setDeployTo

Sets the value of the deployTo property.

    public void setDeployTo(DeployTo deployTo)

#### Parameters

deployTo  
The deployTo property value.

## Class VSProjectsNode
    class VSProjectsNode extends xResourceNode

The VSProjectNode class is the root of the Microsoft Visual Studio project nodes in the Microsoft Dynamics 365 for Operations Application Object Tree (AOT).

### Remarks

### Examples

### Methods

| Method                                                                                            | Description                                                                                |
|---------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
| public TreeNode AOTfindChild(str name, \[int nodeType\])                                          | Finds the specified child node of this node.                                               |
| public VSProjectNode createProjectNode(str name, str projectTypesString, \[boolean virtualNode\]) | Creates a new instance of the VSProjectNode class.                                         |
| public container getProjectsDeployingTo(DeployTo deployTo)                                        | Gets a list of VSProjectNode objects that have the specified deployTo property.            |
| public container getProjectsModifiedAfter(DateTime timestamp)                                     | Gets a list of VSProjectNode objects that were modified after the specified date and time. |
| public VSProjectTypeNode getTypeNodeFromGuid(str projectTypesString)                              |                                                                                            |
| public Object getVSProjectNodeObservable()                                                        | Gets the VSProjectNodeObservable object.                                                   |
| public void AOTrefresh()                                                                          | Updates the node with the latest changes to the .aod file.                                 |

### Method AOTfindChild

Finds the specified child node of this node.

    public TreeNode AOTfindChild(str name, [int nodeType])

#### Parameters

name  

<!-- -->

nodeType  

#### Return Value

The specified tree node.

### Method createProjectNode

Creates a new instance of the VSProjectNode class.

    public VSProjectNode createProjectNode(str name, str projectTypesString, [boolean virtualNode])

#### Parameters

name  
A Boolean value that indicates whether the node is created only in memory. In this case, the node will not be persisted in the Microsoft Dynamics 365 for Operations Store.

<!-- -->

projectTypesString  
A Boolean value that indicates whether the node is created only in memory. In this case, the node will not be persisted in the Microsoft Dynamics 365 for Operations Store.

<!-- -->

virtualNode  
A Boolean value that indicates whether the node is created only in memory. In this case, the node will not be persisted in the Microsoft Dynamics 365 for Operations Store.

#### Return Value

The VSProjectNode object that is created.

### Method getProjectsDeployingTo

Gets a list of VSProjectNode objects that have the specified deployTo property.

    public container getProjectsDeployingTo(DeployTo deployTo)

#### Parameters

deployTo  
The value of the deployTo property.

#### Return Value

A list of VSProjectNode objects.

### Method getProjectsModifiedAfter

Gets a list of VSProjectNode objects that were modified after the specified date and time.

    public container getProjectsModifiedAfter(DateTime timestamp)

#### Parameters

timestamp  
The date and time as a DB\_DATETIME\_TYPE value.

#### Return Value

A list of VSProjectNode objects.

### Method getTypeNodeFromGuid

    public VSProjectTypeNode getTypeNodeFromGuid(str projectTypesString)

#### Parameters

projectTypesString  

#### Return Value

### Method getVSProjectNodeObservable

Gets the VSProjectNodeObservable object.

    public Object getVSProjectNodeObservable()

#### Return Value

The VSProjectNodeObservable object.

#### Remarks

Observers can register with this and get notified of CRUD operations on Visual Studio projects.

### Method AOTrefresh

Updates the node with the latest changes to the .aod file.

    public void AOTrefresh()

## Class VSProjectTypeNode
    class VSProjectTypeNode extends TreeNode

The VSProjectTypeNode class represents project types in the Visual Studio Project nodes in the AOT.

### Remarks

### Examples

### Methods

| Method | Description |
|--------|-------------|

## Class VSS
    class VSS extends Object

### Remarks

### Examples

### Methods

| Method                                                                                                        | Description                               |
|---------------------------------------------------------------------------------------------------------------|-------------------------------------------|
| public boolean connect()                                                                                      |                                           |
| public boolean connected()                                                                                    |                                           |
| public boolean disconnect()                                                                                   |                                           |
| public container getCheckedoutFiles()                                                                         |                                           |
| public container getConnectionInfo()                                                                          |                                           |
| public VSSItem getVSSItem(str vssItemPath, str localFilePath, \[boolean completePath\], \[int version\])      |                                           |
| public boolean init(str vssIni, str vssPrjRoot, str vssWorkingFolder, str vssUser, str vssPwd)                |                                           |
| public VSSItem newSubProject(str name, str localPath)                                                         |                                           |
| public Map synchronizeProjects(\[Set projects\], \[boolean force\], \[boolean delLocalFiles\], \[str label\]) |                                           |
| public void new()                                                                                             | Initializes an instance of the VSS class. |

### Method connect

    public boolean connect()

#### Return Value

### Method connected

    public boolean connected()

#### Return Value

### Method disconnect

    public boolean disconnect()

#### Return Value

### Method getCheckedoutFiles

    public container getCheckedoutFiles()

#### Return Value

### Method getConnectionInfo

    public container getConnectionInfo()

#### Return Value

### Method getVSSItem

    public VSSItem getVSSItem(str vssItemPath, str localFilePath, [boolean completePath], [int version])

#### Parameters

vssItemPath  

<!-- -->

localFilePath  

<!-- -->

completePath  

<!-- -->

version  

#### Return Value

### Method init

    public boolean init(str vssIni, str vssPrjRoot, str vssWorkingFolder, str vssUser, str vssPwd)

#### Parameters

vssIni  

<!-- -->

vssPrjRoot  

<!-- -->

vssWorkingFolder  

<!-- -->

vssUser  

<!-- -->

vssPwd  

#### Return Value

### Method newSubProject

    public VSSItem newSubProject(str name, str localPath)

#### Parameters

name  

<!-- -->

localPath  

#### Return Value

### Method synchronizeProjects

    public Map synchronizeProjects([Set projects], [boolean force], [boolean delLocalFiles], [str label])

#### Parameters

projects  

<!-- -->

force  

<!-- -->

delLocalFiles  

<!-- -->

label  

#### Return Value

### Method new

Initializes an instance of the VSS class.

    public void new()

## Class VSSItem
    class VSSItem extends Object

### Remarks

### Examples

### Methods

| Method                                                                               | Description                                      |
|--------------------------------------------------------------------------------------|--------------------------------------------------|
| public boolean add(\[boolean keepCheckedout\], \[str comment\])                      |                                                  |
| public boolean checkin(\[str comment\])                                              |                                                  |
| public boolean checkout(\[boolean allowMultipleCheckout\], \[boolean replaceLocal\]) |                                                  |
| public boolean delete()                                                              |                                                  |
| public boolean destroy()                                                             |                                                  |
| public Map get(\[boolean force\], \[int version\], \[str label\], \[str localFile\]) |                                                  |
| public str getActionText()                                                           |                                                  |
| public container getCheckedOutTo()                                                   |                                                  |
| public int getCheckoutVersion()                                                      |                                                  |
| public container getHistory()                                                        |                                                  |
| public ComInterface getIUnknown()                                                    |                                                  |
| public int getVersionNo()                                                            |                                                  |
| public str getVSSPath()                                                              |                                                  |
| public boolean isCheckedOut()                                                        |                                                  |
| public boolean isRenamed()                                                           |                                                  |
| public str name(str newName)                                                         |                                                  |
| public boolean rename(str newName)                                                   |                                                  |
| public boolean undoCheckout()                                                        |                                                  |
| private void new()                                                                   | Initializes a new instance of the VSSItem class. |

### Method add

    public boolean add([boolean keepCheckedout], [str comment])

#### Parameters

keepCheckedout  

<!-- -->

comment  

#### Return Value

### Method checkin

    public boolean checkin([str comment])

#### Parameters

comment  

#### Return Value

### Method checkout

    public boolean checkout([boolean allowMultipleCheckout], [boolean replaceLocal])

#### Parameters

allowMultipleCheckout  

<!-- -->

replaceLocal  

#### Return Value

### Method delete

    public boolean delete()

#### Return Value

### Method destroy

    public boolean destroy()

#### Return Value

### Method get

    public Map get([boolean force], [int version], [str label], [str localFile])

#### Parameters

force  

<!-- -->

version  

<!-- -->

label  

<!-- -->

localFile  

#### Return Value

### Method getActionText

    public str getActionText()

#### Return Value

### Method getCheckedOutTo

    public container getCheckedOutTo()

#### Return Value

### Method getCheckoutVersion

    public int getCheckoutVersion()

#### Return Value

### Method getHistory

    public container getHistory()

#### Return Value

### Method getIUnknown

    public ComInterface getIUnknown()

#### Return Value

### Method getVersionNo

    public int getVersionNo()

#### Return Value

### Method getVSSPath

    public str getVSSPath()

#### Return Value

### Method isCheckedOut

    public boolean isCheckedOut()

#### Return Value

### Method isRenamed

    public boolean isRenamed()

#### Return Value

### Method name

    public str name(str newName)

#### Parameters

newName  

#### Return Value

### Method rename

    public boolean rename(str newName)

#### Parameters

newName  

#### Return Value

### Method undoCheckout

    public boolean undoCheckout()

#### Return Value

### Method new

Initializes a new instance of the VSSItem class.

    private void new()

