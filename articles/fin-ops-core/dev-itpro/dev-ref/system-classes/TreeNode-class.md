---
title: TreeNode class
description: This topic describes the TreeNode class.
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

# Class TreeNode

[!include [banner](../../includes/banner.md)]

```xpp
class TreeNode extends Object
```

The TreeNode class retrieves and represents any node in the Application Object Tree (AOT).

## Remarks

This class, and the classes that extend it, enable you to create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before calling this API or APIs that are derived from this class. The TreeNode class can be used to get a handle to any node in the AOT. The TreeNode class is a generic class in that it can be a reference to any type of node in the AOT. In addition to providing access to some of the functions on the shortcut menu of the AOT, this class also contains methods that are used to maneuver in the tree. The TreeNodeTraverser class is also useful in navigating in the AOT. The TreeNode::findNode and TreeNode::rootNode methods return a treeNode object from which you can maneuver to any other node.

## Examples

## Methods

| Method                                                                                                                                              | Description                                                                                                                                                          |
|-----------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public TreeNode SysObsoleteAttribute(UtilElementName name)                                                                                          |                                                                                                                                                                      |
| public TreeNode SysObsoleteAttribute(str name, Types type)                                                                                          |                                                                                                                                                                      |
| public TreeNode SysObsoleteAttribute()                                                                                                              |                                                                                                                                                                      |
| public TreeNode SysObsoleteAttribute(int nodetype)                                                                                                  |                                                                                                                                                                      |
| public boolean AOTAllowEdit()                                                                                                                       |                                                                                                                                                                      |
| public int AOTbitmapId()                                                                                                                            | Returns the resource ID of the bitmap of the tree node.                                                                                                              |
| public int AOTchildNodeCount()                                                                                                                      | Counts the number of child nodes that a given tree node has.                                                                                                         |
| public boolean SysObsoleteAttribute(\[int flag\], \[boolean forceNoXRef\], \[boolean fastMode\])                                                    |                                                                                                                                                                      |
| public boolean AOTDrop(TreeNode sourcenode, \[TreeNode after\])                                                                                     | Creates a copy of a specified tree node as a child to the TreeNode object.                                                                                           |
| public TreeNode AOTDuplicate()                                                                                                                      |                                                                                                                                                                      |
| public TreeNode AOTfindChild(str name, \[int nodeType\])                                                                                            | Finds the specified child node of this node.                                                                                                                         |
| public TreeNode AOTfirstChild()                                                                                                                     | Retrieves the first child of the tree node.                                                                                                                          |
| public TreeNode AOTfirstChildEx(\[boolean loadFullNode\])                                                                                           |                                                                                                                                                                      |
| public int AOTgetExecutableLineCount()                                                                                                              | Returns the number of executable lines of code for this node.                                                                                                        |
| public Set AOTgetExecutableLines()                                                                                                                  | Returns the executable lines of code for this node.                                                                                                                  |
| public int AOTGetModel()                                                                                                                            |                                                                                                                                                                      |
| public str AOTgetProperties(\[boolean includeInvisible\], \[boolean includeReadOnly\], \[boolean includeNonExportable\])                            | Returns a string containing the properties of the tree node.                                                                                                         |
| public Struct AOTgetPropertiesExt(\[str filter\])                                                                                                   |                                                                                                                                                                      |
| public AnyType AOTgetProperty(str name)                                                                                                             |                                                                                                                                                                      |
| public str AOTgetSource()                                                                                                                           | Returns the source code of this node.                                                                                                                                |
| public boolean AOTIncludeInCompare()                                                                                                                |                                                                                                                                                                      |
| public boolean AOTIsDirty()                                                                                                                         |                                                                                                                                                                      |
| public boolean AOTIsOld()                                                                                                                           | Indicates whether this node is from a file found in the old model store.                                                                                             |
| public boolean AOTIsPersisted()                                                                                                                     | Indicates whether this node has been persisted in the model store.                                                                                                   |
| public boolean AOTIsProxyNode()                                                                                                                     |                                                                                                                                                                      |
| public TreeNodeIterator AOTiterator()                                                                                                               | Returns an object which can be used to iterate the child nodes of the tree node.                                                                                     |
| public KernelHelpType AOTKernelHelpType()                                                                                                           |                                                                                                                                                                      |
| public UtilEntryLevel AOTLayer()                                                                                                                    | Returns the layer of the tree node.                                                                                                                                  |
| public Set AOTLayers(\[boolean old\])                                                                                                               | Returns a collection of the layers the tree node is defined in.                                                                                                      |
| public str AOTname()                                                                                                                                | Returns the value of the name property of the node.                                                                                                                  |
| public int AOTnewWindow()                                                                                                                           | Opens a new AOT tree window with the tree node as the root.                                                                                                          |
| public TreeNode AOTnextSibling()                                                                                                                    | Returns the next node on the same level as the tree node.                                                                                                            |
| public boolean AOTObjectNode()                                                                                                                      | Indicates whether the node is an application object.                                                                                                                 |
| public int AOToverlayBitmapId()                                                                                                                     | Returns the resource ID of the overlay in the AOT associated with this node.                                                                                         |
| public TreeNode AOTparent()                                                                                                                         | Returns the parent node of the tree node.                                                                                                                            |
| public TreeNode AOTprevious()                                                                                                                       | Returns the previous sibling of this tree node.                                                                                                                      |
| public boolean SysObsoleteAttribute(str name)                                                                                                       |                                                                                                                                                                      |
| public str AOTtoolTip()                                                                                                                             | Returns the tool tip associated with the tree node.                                                                                                                  |
| public str AOTToString()                                                                                                                            |                                                                                                                                                                      |
| public str AOTtypeStr()                                                                                                                             | Returns the internal string code for the element type used in XPO files.                                                                                             |
| public UtilFileType AOTUtilFileType()                                                                                                               | Retrieves the value of the UtilFileType enumeration type for the TreeNode object. The UtilFileType indicates which kind of file the application object is stored in. |
| public int applObjectId()                                                                                                                           | Returns the application object ID, if applicable.                                                                                                                    |
| public int applObjectLayerMask()                                                                                                                    | Returns a bitmask that specifies which layers contain this element.                                                                                                  |
| public int applObjectOldLayerMask()                                                                                                                 | Returns a bitmask that specifies which layers contain this element in the baseline model store.                                                                      |
| public TreeNode getNodeInLayer(UtilEntryLevel layer, \[boolean old\])                                                                               | Retrieves a version of the tree node from a specified layer.                                                                                                         |
| public Int64 hashKey()                                                                                                                              |                                                                                                                                                                      |
| public TreeNode makeCopy()                                                                                                                          |                                                                                                                                                                      |
| public str newObjectName(\[str oldName\])                                                                                                           | Returns a string that contains the name of the new element.                                                                                                          |
| public str toString()                                                                                                                               | Returns a string that represents the current object.                                                                                                                 |
| public str treeNodeName()                                                                                                                           | Returns the name of the tree node.                                                                                                                                   |
| public str treeNodePath()                                                                                                                           | Returns the unique path to the tree node within the Application Object Tree (AOT).                                                                                   |
| public TreeNodeType treeNodeType()                                                                                                                  | Retrieves an instance of a TreeNodeType class that provides reflection information for the tree node.                                                                |
| public int updateNodePermissions(boolean throwExceptions)                                                                                           |                                                                                                                                                                      |
| public UtilElements utilElement()                                                                                                                   | Returns a UtilElements record that is related to the node.                                                                                                           |
| public UtilIdElements utilIdElement()                                                                                                               | Returns a UtilIdElements record that is related to the node.                                                                                                         |
| public boolean validateNameCharacters(str name)                                                                                                     |                                                                                                                                                                      |
| ::public static TreeNode findNode(str path)                                                                                                         | Returns a specified node in the Application Object Tree (AOT).                                                                                                       |
| ::public static str generateObjectName(str template)                                                                                                |                                                                                                                                                                      |
| ::public static int getMaximumNodeNameLength(int modelElementTypeId)                                                                                |                                                                                                                                                                      |
| ::public static boolean isNodeReferenceValid(TreeNode treeNode)                                                                                     |                                                                                                                                                                      |
| ::public static boolean isValidObjectName(str name)                                                                                                 | Determines whether the string passed as an argument can be used as a name for a node in the Application Object Tree (AOT).                                           |
| ::public static TreeNode rootNode()                                                                                                                 | Returns the root node of the AOT.                                                                                                                                    |
| public void SysObsoleteAttribute()                                                                                                                  |                                                                                                                                                                      |
| public void treeNodeRelease()                                                                                                                       | Releases the tree node explicitly.                                                                                                                                   |
| public void SysObsoleteAttribute(str name, xRefKind xrefKind, int lineNumber, int columNumber, \[XRefReference xrefRef\], \[ClassId parentTypeId\]) |                                                                                                                                                                      |
| public void AOTrun()                                                                                                                                | Compiles this node and its subtree in the Application Object Tree (AOT).                                                                                             |
| public void SysObsoleteAttribute()                                                                                                                  |                                                                                                                                                                      |
| public void AOTrefresh()                                                                                                                            | Refreshes the node with the latest changes to the .aod file.                                                                                                         |
| public void SysObsoleteAttribute(Struct struct1)                                                                                                    |                                                                                                                                                                      |
| public void SysObsoleteAttribute(str properties)                                                                                                    |                                                                                                                                                                      |
| public void AOTconfigure()                                                                                                                          |                                                                                                                                                                      |
| public void AOTload()                                                                                                                               | Ensures that the object is loaded.                                                                                                                                   |
| public void treeNodeExport(str filename, \[int flag\])                                                                                              | Exports this node and its subtree from the Application Object Tree (AOT).                                                                                            |
| public void SysObsoleteAttribute(str source, \[boolean isStatic\])                                                                                  |                                                                                                                                                                      |
| public void AOTendXref()                                                                                                                            |                                                                                                                                                                      |
| public void AOTmessageLine(str text, int linenumber)                                                                                                | Writes text to the Application Object Tree (AOT) Message window.                                                                                                     |
| public void SysObsoleteAttribute(str name, AnyType value)                                                                                           |                                                                                                                                                                      |
| public void AOTrestore(\[boolean forceReload\])                                                                                                     | Reloads this node from the disk, if applicable.                                                                                                                      |
| public void AOTregenerate()                                                                                                                         |                                                                                                                                                                      |
| public void AOTmakeXref(\[int flag\], \[boolean xRefAll\])                                                                                          | Compiles this node and its subtree in the AOT, updating the cross-reference system.                                                                                  |
| public void AOTedit(\[int Line\], \[int Column\])                                                                                                   | Opens the appropriate editor for this node.                                                                                                                          |
| public void AOTshowProperties()                                                                                                                     | Opens the property sheet (if not already open) and shows the properties for this node.                                                                               |
| public void AOTinsert(TreeNode parent, \[TreeNode after\], \[boolean doNotDuplicate\])                                                              | Inserts a node among the subnodes of this node.                                                                                                                      |
| public void new()                                                                                                                                   | Initializes a new instance of the TreeNode class.                                                                                                                    |
| public void AOTMove(TreeNode parent, \[TreeNode after\])                                                                                            |                                                                                                                                                                      |
| public void SysObsoleteAttribute(int modelId)                                                                                                       |                                                                                                                                                                      |

## Method SysObsoleteAttribute

```xpp
public TreeNode SysObsoleteAttribute(UtilElementName name)
```

### Parameters - SysObsoleteAttribute

name  

### Return Value - SysObsoleteAttribute

## Method SysObsoleteAttribute

```xpp
public TreeNode SysObsoleteAttribute(str name, Types type)
```

### Parameters - SysObsoleteAttribute

name  

<!-- -->

type  

### Return Value - SysObsoleteAttribute

## Method SysObsoleteAttribute

```xpp
public TreeNode SysObsoleteAttribute()
```

### Return Value - SysObsoleteAttribute

## Method SysObsoleteAttribute

```xpp
public TreeNode SysObsoleteAttribute(int nodetype)
```

### Parameters - SysObsoleteAttribute

nodetype  

### Return Value - SysObsoleteAttribute

## Method AOTAllowEdit

```xpp
public boolean AOTAllowEdit()
```

### Return Value - AOTAllowEdit

## Method AOTbitmapId

Returns the resource ID of the bitmap of the tree node.

```xpp
public int AOTbitmapId()
```

### Return Value - AOTbitmapId

The resource ID of the bitmap of the tree node.

### Examples - AOTbitmapId

The following example prints the resource ID of the Extended Data Types node in the Application Object Tree (AOT).

```xpp
AOT 
static void myJobAOTbitmapId(Args _args) 
{ 
    treeNode treeNode = TreeNode::findNode(#ExtendedDataTypesPath); 
    print treeNode.AOTbitmapId(); 
    pause; 
}
```

This job will print the integer 895. If you run the Tutorial resources form, you can see the bitmap and verify that it is the same as the one that is used for Extended Data Types in the AOT.

## Method AOTchildNodeCount

Counts the number of child nodes that a given tree node has.

```xpp
public int AOTchildNodeCount()
```

### Return Value - AOTchildNodeCount

An integer that indicates the number of child nodes for the tree node.

### Examples - AOTchildNodeCount

The following example prints the number of child nodes that appear under the Menu Items node in the Application Object Tree (AOT).

```xpp
AOT 
static void myJobAOTchildNodeCount(Args _args) 
{ 
    treeNode treeNode = TreeNode::findNode(#MenuItemsPath); 
    print "Number of nodes below Menu Items: ", treeNode.AOTchildNodeCount(); 
    pause; 
}
```

## Method SysObsoleteAttribute

```xpp
public boolean SysObsoleteAttribute([int flag], [boolean forceNoXRef], [boolean fastMode])
```

### Parameters - SysObsoleteAttribute

flag  

<!-- -->

forceNoXRef  

<!-- -->

fastMode  

### Return Value - SysObsoleteAttribute

## Method AOTDrop

Creates a copy of a specified tree node as a child to the TreeNode object.

```xpp
public boolean AOTDrop(TreeNode sourcenode, [TreeNode after])
```

### Parameters - AOTDrop

sourcenode  
The child node of the tree node that the source should be inserted after; optional.

<!-- -->

after  
The child node of the tree node that the source should be inserted after; optional.

### Return Value - AOTDrop

true if the drop operation was successful; otherwise, false.

### Examples - AOTDrop

The following example creates the tabPage:CopyOfContainers tree node as the last node underTab:Tab in the tutorial\_Form\_Controls form.

```xpp
AOT 
static void myJobAOTDrop(Args _args) 
{ 
    treeNode treeNodeTab; 
    treeNode treeNodeTabPageContainers; 
    treeNodeTab = TreeNode::findNode(#FormsPath + '\\' +  
        formStr(tutorial_form_controls)+ '\\Designs\\Design\\[Tab:Tab]'); 
    treeNodeTabPageContainers = TreeNode::findNode(#FormsPath + '\\' +  
        formStr(tutorial_form_controls)+  
        '\\Designs\\Design\\[Tab:Tab]\\[TabPage:Containers]'); 
    if (treeNodeTab && treeNodeTabPageContainers) 
    { 
        // Drop the TabPage:Containers node on the Tab:Tab node. 
        print treeNodeTab.AOTDrop(treeNodeTabPageContainers); 
    } 
    else 
    { 
        print "Could not find treeNodeTab or treeNodeTabPageContainers"; 
    } 
    pause; 
}
```

## Method AOTDuplicate

```xpp
public TreeNode AOTDuplicate()
```

### Return Value - AOTDuplicate

## Method AOTfindChild

Finds the specified child node of this node.

```xpp
public TreeNode AOTfindChild(str name, [int nodeType])
```

### Parameters - AOTfindChild

name  

<!-- -->

nodeType  

### Return Value - AOTfindChild

The specified TreeNode.

## Method AOTfirstChild

Retrieves the first child of the tree node.

```xpp
public TreeNode AOTfirstChild()
```

### Return Value - AOTfirstChild

The first child node of the tree node.

## Method AOTfirstChildEx

```xpp
public TreeNode AOTfirstChildEx([boolean loadFullNode])
```

### Parameters - AOTfirstChildEx

loadFullNode  

### Return Value - AOTfirstChildEx

## Method AOTgetExecutableLineCount

Returns the number of executable lines of code for this node.

```xpp
public int AOTgetExecutableLineCount()
```

### Return Value - AOTgetExecutableLineCount

The number of executable lines of code for this node if any; otherwise, zero.

### Remarks - AOTgetExecutableLineCount

This function calls a method which is overridden by nodes which have source code.

## Method AOTgetExecutableLines

Returns the executable lines of code for this node.

```xpp
public Set AOTgetExecutableLines()
```

### Return Value - AOTgetExecutableLines

A Set object containing the executable lines of code for this node if any; otherwise, nullNothingnullptrunita null reference (Nothing in Visual Basic).

### Remarks - AOTgetExecutableLines

This function calls a method which is overridden by nodes which have source code.

## Method AOTGetModel

```xpp
public int AOTGetModel()
```

### Return Value - AOTGetModel

## Method AOTgetProperties

Returns a string containing the properties of the tree node.

```xpp
public str AOTgetProperties([boolean includeInvisible], [boolean includeReadOnly], [boolean includeNonExportable])
```

### Parameters - AOTgetProperties

includeInvisible  

<!-- -->

includeReadOnly  

<!-- -->

includeNonExportable  

### Return Value - AOTgetProperties

A string containing the properties of the tree node.

### Examples - AOTgetProperties

The following example provides a list of temporary tables.

```xpp
{ 
    #aot 
    #properties 
    TreeNode        tn = TreeNode::findNode(#TablesPath); 
    str             tableName; 
    str             temporaryProperty; 
    tn = tn.AOTfirstChild(); 
    while (tn) 
    { 
        tableName = findProperty(tn.AOTgetProperties(), #PropertyName); 
        temporaryProperty = findProperty( 
            tn.AOTgetProperties(), 
            #PropertyTemporary); 
        info (strfmt( 
            'Table %1 has the temporary property specified as %2', 
            tableName, temporaryProperty)); 
        tn = tn.AOTnextSibling(); 
    } 
}
```

## Method AOTgetPropertiesExt

```xpp
public Struct AOTgetPropertiesExt([str filter])
```

### Parameters - AOTgetPropertiesExt

filter  

### Return Value - AOTgetPropertiesExt

## Method AOTgetProperty

```xpp
public AnyType AOTgetProperty(str name)
```

### Parameters - AOTgetProperty

name  

### Return Value - AOTgetProperty

## Method AOTgetSource

Returns the source code of this node.

```xpp
public str AOTgetSource()
```

### Return Value - AOTgetSource

The string that contains source code if any; otherwise, nullNothingnullptrunita null reference (Nothing in Visual Basic).

### Remarks - AOTgetSource

This function is overridden by nodes which have source code.

## Method AOTIncludeInCompare

```xpp
public boolean AOTIncludeInCompare()
```

### Return Value - AOTIncludeInCompare

## Method AOTIsDirty

```xpp
public boolean AOTIsDirty()
```

### Return Value - AOTIsDirty

## Method AOTIsOld

Indicates whether this node is from a file found in the old model store.

```xpp
public boolean AOTIsOld()
```

### Return Value - AOTIsOld

true if this node is from the old model store; otherwise false.

## Method AOTIsPersisted

Indicates whether this node has been persisted in the model store.

```xpp
public boolean AOTIsPersisted()
```

### Return Value - AOTIsPersisted

true if this node has been persisted; otherwise false.

### Remarks - AOTIsPersisted

This method throws an exception if the method is not supported for the tree node. Use the TreeNode.TreeNodeType().isModelElement() method to determine if the method is supported.

## Method AOTIsProxyNode

```xpp
public boolean AOTIsProxyNode()
```

### Return Value - AOTIsProxyNode

## Method AOTiterator

Returns an object which can be used to iterate the child nodes of the tree node.

```xpp
public TreeNodeIterator AOTiterator()
```

### Return Value - AOTiterator

The TreeNodeIterator object used to iterate the children of the tree node.

## Method AOTKernelHelpType

```xpp
public KernelHelpType AOTKernelHelpType()
```

### Return Value - AOTKernelHelpType

## Method AOTLayer

Returns the layer of the tree node.

```xpp
public UtilEntryLevel AOTLayer()
```

### Return Value - AOTLayer

The layer that this node resides in.

### Remarks - AOTLayer

This method throws an exception if the method is not supported for the tree node. Use the TreeNode.TreeNodeType().isLayerAware() method to determine if the method is supported.

## Method AOTLayers

Returns a collection of the layers the tree node is defined in.

```xpp
public Set AOTLayers([boolean old])
```

### Parameters - AOTLayers

old  
A Boolean value that indicates whether to return the layers of the tree node definitions from the old model store; optional.

### Return Value - AOTLayers

A Set object with the layers.

### Remarks - AOTLayers

This method throws an exception if the method is not supported for the tree node. Use the TreeNode.TreeNodeType().isLayerAware() method to determine if the method is supported.

## Method AOTname

Returns the value of the name property of the node.

```xpp
public str AOTname()
```

### Return Value - AOTname

The string that contains the value of the name property

### Remarks - AOTname

In most cases, this yields the same result as the method TreeNodeName.

### Examples - AOTname

The following example prints out the name of the first child of the tree node.

```xpp
static void Job(Args _args) 
{ 
    treeNode t = infolog.findNode('\\Reports\\AssetAcquisition\\Designs\\ReportDesign1\\AutoDesignSpecs'); 
    t = t.AOTfirstChild(); 
    print "treeNodeName: " + t.treeNodeName(); 
    print "AOTName:" + t.AOTName(); 
    pause; 
}
```

## Method AOTnewWindow

Opens a new AOT tree window with the tree node as the root.

```xpp
public int AOTnewWindow()
```

### Return Value - AOTnewWindow

## Method AOTnextSibling

Returns the next node on the same level as the tree node.

```xpp
public TreeNode AOTnextSibling()
```

### Return Value - AOTnextSibling

The next node on the same level as the current tree node.

## Method AOTObjectNode

Indicates whether the node is an application object.

```xpp
public boolean AOTObjectNode()
```

### Return Value - AOTObjectNode

true if the node is an application object; otherwise false.

### Remarks - AOTObjectNode

A form or report is an application object. A control on a form, or any other subpart, is not.

## Method AOToverlayBitmapId

Returns the resource ID of the overlay in the AOT associated with this node.

```xpp
public int AOToverlayBitmapId()
```

### Return Value - AOToverlayBitmapId

The resource ID of the overlay in the AOT associated with this node.

## Method AOTparent

Returns the parent node of the tree node.

```xpp
public TreeNode AOTparent()
```

### Return Value - AOTparent

The parent node of the tree node.

## Method AOTprevious

Returns the previous sibling of this tree node.

```xpp
public TreeNode AOTprevious()
```

### Return Value - AOTprevious

The previous tree node relative to this one on the same level.

## Method SysObsoleteAttribute

```xpp
public boolean SysObsoleteAttribute(str name)
```

### Parameters - SysObsoleteAttribute

name  

### Return Value - SysObsoleteAttribute

## Method AOTtoolTip

Returns the tool tip associated with the tree node.

```xpp
public str AOTtoolTip()
```

### Return Value - AOTtoolTip

The string that contains the tool tip.

## Method AOTToString

```xpp
public str AOTToString()
```

### Return Value - AOTToString

## Method AOTtypeStr

Returns the internal string code for the element type used in XPO files.

```xpp
public str AOTtypeStr()
```

### Return Value - AOTtypeStr

The string that contains the tree node type.

## Method AOTUtilFileType

Retrieves the value of the UtilFileType enumeration type for the TreeNode object. The UtilFileType indicates which kind of file the application object is stored in.

```xpp
public UtilFileType AOTUtilFileType()
```

### Return Value - AOTUtilFileType

The value of the UtilFileType enumeration for the tree node. The possible values are in the following list. UtilFileType::Application means that the element is stored in the .aod file (form, report, query, table, and so on). UtilFileType::ApplicationCodeDocumentation means that the element is stored in the .add file. UtilFileType::ApplicationHelp means that the element is stored in the .ahd file. UtilFileType::KernelHelp means that the element is stored in the .akh file.

### Examples - AOTUtilFileType

The following example finds a TreeNode object of each UtilFileType, and then prints the path of the UtilFileType to the Infolog.

```xpp
static void myJob(Args _args) 
{ 
    treeNode tn; 
    tn = treeNode::findNode("\\Forms"); 
    tn = tn.AOTfirstChild(); 
    info(strfmt( 
         "Path: %1 \nUtilFileType: %2", 
         tn.treeNodePath(), 
         tn.AOTUtilFileType())); 
    tn = treeNode::findNode("\\System Documentation"); 
    tn = tn.AOTfirstChild(); 
    tn = tn.AOTfirstChild(); 
    info(strfmt( 
         "Path: %1 \nUtilFileType: %2", 
         tn.treeNodePath(), 
         tn.AOTUtilFileType())); 
    tn = treeNode::findNode("\\Application Developer Documentation"); 
    tn = tn.AOTfirstChild(); 
    tn = tn.AOTfirstChild(); 
    info(strfmt( 
        "Path: %1 \nUtilFileType: %2", 
        tn.treeNodePath(), 
        tn.AOTUtilFileType())); 
    tn = treeNode::findNode("\\Application Documentation"); 
    tn = tn.AOTfirstChild(); 
    tn = tn.AOTfirstChild(); 
    info(strfmt( 
        "Path: %1 \nUtilFileType: %2", 
        tn.treeNodePath(), 
        tn.AOTUtilFileType())); 
}
```

## Method applObjectId

Returns the application object ID, if applicable.

```xpp
public int applObjectId()
```

### Return Value - applObjectId

The ID of the application object.

## Method applObjectLayerMask

Returns a bitmask that specifies which layers contain this element.

```xpp
public int applObjectLayerMask()
```

### Return Value - applObjectLayerMask

A bitmask that specifies which layers contain this element.

## Method applObjectOldLayerMask

Returns a bitmask that specifies which layers contain this element in the baseline model store.

```xpp
public int applObjectOldLayerMask()
```

### Return Value - applObjectOldLayerMask

A bitmask that specifies which layers contain this element.

## Method getNodeInLayer

Retrieves a version of the tree node from a specified layer.

```xpp
public TreeNode getNodeInLayer(UtilEntryLevel layer, [boolean old])
```

### Parameters - getNodeInLayer

layer  
The value specifying whether or not the node should be retrieved from the layer file in the old model store; optional.

<!-- -->

old  
The value specifying whether or not the node should be retrieved from the layer file in the old model store; optional.

### Return Value - getNodeInLayer

The new TreeNode.

### Remarks - getNodeInLayer

This method throws an exception if the method is not supported for the tree node. Use the TreeNode.TreeNodeType().isGetNodeInLayerSupported method to determine if the method is supported.

## Method hashKey

```xpp
public Int64 hashKey()
```

### Return Value - hashKey

## Method makeCopy

```xpp
public TreeNode makeCopy()
```

### Return Value - makeCopy

## Method newObjectName

Returns a string that contains the name of the new element.

```xpp
public str newObjectName([str oldName])
```

### Parameters - newObjectName

oldName  
The new name of the node; optional. If no argument is passed, the new node name is determined by the child node type.

### Return Value - newObjectName

The string that contains the name of the new element.

### Remarks - newObjectName

If no argument is passed, the new node name is determined by the child node type. For example, if the TreeNode has forms as children, calling this method without an argument will return "Form1". If the tree node has several child node types, the method returns the string "object".

### Examples - newObjectName

The following call to Treenode.newObjectName returns "object" because the data dictionary node has children that represent several object types.

```xpp
{ 
    TreeNode t; 
    str s; 
    t = TreeNode::findNode("\Data dictionary"); 
    s = t.newObjectName(); 
    print s; 
    pause; 
}
```

## Method toString

Returns a string that represents the current object.

```xpp
public str toString()
```

### Return Value - toString

A string that represents the current object.

### Remarks - toString

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the class returns the method name and type of the method, such as instance or static.

## Method treeNodeName

Returns the name of the tree node.

```xpp
public str treeNodeName()
```

### Return Value - treeNodeName

The string that contains the name of the tree node.

## Method treeNodePath

Returns the unique path to the tree node within the Application Object Tree (AOT).

```xpp
public str treeNodePath()
```

### Return Value - treeNodePath

Returns the unique path of the tree node in the AOT.

### Examples - treeNodePath

The following example finds a TreeNode object of each UtilFileType and prints the path of the UtilFileType to the Infolog.

```xpp
static void myJob(Args _args) 
{ 
    treeNode tn; 
    tn = treeNode::findNode("\\Forms"); 
    tn = tn.AOTfirstChild(); 
    info(strfmt( 
         "Path: %1 \nUtilFileType: %2", 
         tn.treeNodePath(), 
         tn.AOTUtilFileType())); 
    tn = treeNode::findNode("\\System Documentation"); 
    tn = tn.AOTfirstChild(); 
    tn = tn.AOTfirstChild(); 
    info(strfmt( 
         "Path: %1 \nUtilFileType: %2", 
         tn.treeNodePath(), 
         tn.AOTUtilFileType())); 
    tn = treeNode::findNode("\\Application Developer Documentation"); 
    tn = tn.AOTfirstChild(); 
    tn = tn.AOTfirstChild(); 
    info(strfmt( 
        "Path: %1 \nUtilFileType: %2", 
        tn.treeNodePath(), 
        tn.AOTUtilFileType())); 
    tn = treeNode::findNode("\\Application Documentation"); 
    tn = tn.AOTfirstChild(); 
    tn = tn.AOTfirstChild(); 
    info(strfmt( 
        "Path: %1 \nUtilFileType: %2", 
        tn.treeNodePath(), 
        tn.AOTUtilFileType())); 
}
```

## Method treeNodeType

Retrieves an instance of a TreeNodeType class that provides reflection information for the tree node.

```xpp
public TreeNodeType treeNodeType()
```

### Return Value - treeNodeType

An instance of a TreeNodeType class.

## Method updateNodePermissions

```xpp
public int updateNodePermissions(boolean throwExceptions)
```

### Parameters - updateNodePermissions

throwExceptions  

### Return Value - updateNodePermissions

## Method utilElement

Returns a UtilElements record that is related to the node.

```xpp
public UtilElements utilElement()
```

### Return Value - utilElement

The UtilElements record that is related to the node.

### Remarks - utilElement

This method throws an exception if the method is not supported for the tree node.

## Method utilIdElement

Returns a UtilIdElements record that is related to the node.

```xpp
public UtilIdElements utilIdElement()
```

### Return Value - utilIdElement

The UtilIdElements record that is related to the node.

### Remarks - utilIdElement

This method throws an exception if the method is not supported for the tree node.

## Method validateNameCharacters

```xpp
public boolean validateNameCharacters(str name)
```

### Parameters - validateNameCharacters

name  

### Return Value - validateNameCharacters

## Method findNode

Returns a specified node in the Application Object Tree (AOT).

```xpp
public static TreeNode findNode(str path)
```

### Parameters - findNode

path  
A string that indicates the path that is used in the search.

### Return Value - findNode

The requested TreeNode object or nullNothingnullptrunita null reference (Nothing in Visual Basic) if no node with the specified path exists.

### Remarks - findNode

Another way of getting a TreeNode object is by using the Info.getNode method. An important difference between the two methods is that the Info.getNode method will give you a node that is detached from the AOT, whereas the findNode method will return the node in the AOT. This means that the node that is returned by the Info.getNode method will not have a parent node, whereas the one returned by the findNode method will have a parent node.

### Examples - findNode

The following example retrieves the name of the tree node that is found the TreeNode::findNode method is called. This example checks whether the user has the required security key before it calls the TreeNode.findNode method.

```xpp
server static public void Main(Args _args) 
{ 
    TreeNode tn; 
    str name; 
    tn = TreeNode::findNode(@"\Classes"); 
    if (tn) 
    { 
        name = tn.treeNodeName(); 
    } 
}
```

## Method generateObjectName

```xpp
public static str generateObjectName(str template)
```

### Parameters - generateObjectName

template  

### Return Value - generateObjectName

## Method getMaximumNodeNameLength

```xpp
public static int getMaximumNodeNameLength(int modelElementTypeId)
```

### Parameters - getMaximumNodeNameLength

modelElementTypeId  

### Return Value - getMaximumNodeNameLength

## Method isNodeReferenceValid

```xpp
public static boolean isNodeReferenceValid(TreeNode treeNode)
```

### Parameters - isNodeReferenceValid

treeNode  

### Return Value - isNodeReferenceValid

## Method isValidObjectName

Determines whether the string passed as an argument can be used as a name for a node in the Application Object Tree (AOT).

```xpp
public static boolean isValidObjectName(str name)
```

### Parameters - isValidObjectName

name  
The string that contains the tree node name to validate.

### Return Value - isValidObjectName

true if each condition is met; otherwise false.

### Remarks - isValidObjectName

A candidate name must meet the following conditions:

-   The first character must be a letter.
-   It can only contain letters, numbers or an underscore.
-   It must not evaluate to a token.

This method does not check if an element of the same name already exists. It only validates that the argument is a valid name for an AOT object. Duplicate names may not exist within classes, tables, extended data types, or enums.

### Examples - isValidObjectName

The following example gives examples of valid and invalid arguments.

```xpp
boolean validName; 
validName = TreeNode::isValidObjectName('ValidName'); //true 
validName = TreeNode::isValidObjectName('Name with spaces'); //false 
validName = TreeNode::isValidObjectName('4StartsWithDigit'); //false 
validName = TreeNode::isValidObjectName('Illegal;Character'); //false 
validName = TreeNode::isValidObjectName('if'); // false (token name)
```

## Method rootNode

Returns the root node of the AOT.

```xpp
public static TreeNode rootNode()
```

### Return Value - rootNode

The root node of the AOT.

### Remarks - rootNode

The method provides similar functionality to the rootNode method.

## Method SysObsoleteAttribute

```xpp
public void SysObsoleteAttribute()
```

## Method treeNodeRelease

Releases the tree node explicitly.

```xpp
public void treeNodeRelease()
```

### Remarks - treeNodeRelease

Usually you do not have to explicitly unload objects, because the garbage collector will do it automatically. However, because tree nodes are ordinarily linked to the AOT, they are not garbage-collected. If you run this method on many tree nodes in the same execution, it can be demanding on resources. You should unload the tree nodes as you go along to give the garbage collector a chance to remove them. Make sure to remove all references to the tree node and its subnodes before you call this method. Use the TreeNode.TreeNodeType().isConsumingMemory method to determine if you need to call this method.

## Method SysObsoleteAttribute

```xpp
public void SysObsoleteAttribute(str name, xRefKind xrefKind, int lineNumber, int columNumber, [XRefReference xrefRef], [ClassId parentTypeId])
```

### Parameters - SysObsoleteAttribute

name  

<!-- -->

xrefKind  

<!-- -->

lineNumber  

<!-- -->

columNumber  

<!-- -->

xrefRef  

<!-- -->

parentTypeId  

## Method AOTrun

Compiles this node and its subtree in the Application Object Tree (AOT).

```xpp
public void AOTrun()
```

## Method SysObsoleteAttribute

```xpp
public void SysObsoleteAttribute()
```

## Method AOTrefresh

Refreshes the node with the latest changes to the .aod file.

```xpp
public void AOTrefresh()
```

## Method SysObsoleteAttribute

```xpp
public void SysObsoleteAttribute(Struct struct1)
```

### Parameters - SysObsoleteAttribute

struct1  

## Method SysObsoleteAttribute

```xpp
public void SysObsoleteAttribute(str properties)
```

### Parameters - SysObsoleteAttribute

properties  

## Method AOTconfigure

```xpp
public void AOTconfigure()
```

## Method AOTload

Ensures that the object is loaded.

```xpp
public void AOTload()
```

## Method treeNodeExport

Exports this node and its subtree from the Application Object Tree (AOT).

```xpp
public void treeNodeExport(str filename, [int flag])
```

### Parameters - treeNodeExport

filename  

<!-- -->

flag  

### Remarks - treeNodeExport

If an attacker can control input to this method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission from the . Ensure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

### Examples - treeNodeExport

This example uses the treeNodeExport method to export the ExampleClass class to an .xpo file.

```xpp
void TreeNodeExample() 
{ 
    TreeNode treeNode; 
    TreeNode childNode; 
    FileIoPermission perm; 
    #define.ExportFile(@"c:\TreeNodeExportExampleClass.xpo") 
    #define.ExportMode("w") 
    perm = new FileIoPermission(#ExportFile, #ExportMode); 
    if (perm == null) 
    { 
        return; 
    } 
    perm.assert(); 
    treeNode = TreeNode::findNode(@"\Classes"); 
    if (treeNode != null) 
    { 
        childNode = treeNode.AOTfindChild(@"ExampleClass"); 
        // BP deviation documented. 
        childNode.treeNodeExport(#ExportFile); 
    } 
    CodeAccessPermission::revertAssert(); 
}
```

## Method SysObsoleteAttribute

```xpp
public void SysObsoleteAttribute(str source, [boolean isStatic])
```

### Parameters - SysObsoleteAttribute

source  

<!-- -->

isStatic  

## Method AOTendXref

```xpp
public void AOTendXref()
```

## Method AOTmessageLine

Writes text to the Application Object Tree (AOT) Message window.

```xpp
public void AOTmessageLine(str text, int linenumber)
```

### Parameters - AOTmessageLine

text  
An integer that is ignored. It does not currently direct the written text to a specific line number in the output Message window.

<!-- -->

linenumber  
An integer that is ignored. It does not currently direct the written text to a specific line number in the output Message window.

### Remarks - AOTmessageLine

This method is intended to be used to output text so that when the user later double-clicks that line of text in the message window, some action will happen regarding this node.

### Examples - AOTmessageLine

The following example executes the AOTmessageLine method on a Form object, because Form inherits this method from TreeNode.

```xpp
static void JobAOTmessageLineDemo(Args _args) 
{ 
    Form f = new Form('testAOTMessageLine'); 
    // 
    f.AOTmessageLine('test message 1a',1); 
    f.AOTmessageLine('test message 2a',2); 
    f.AOTmessageLine('test message 3a',3); 
    f.AOTmessageLine('test message 1b',1); 
    f.AOTmessageLine('test message 2b',2); 
    f.AOTmessageLine('test message 3b',3); 
    f.AOTmessageLine('test message 2c',2); 
    // 
    /******* 
    Actual Output in the Message window 
    (the 7 identical lines): 
    test message 2c 
    test message 2c 
    test message 2c 
    test message 2c 
    test message 2c 
    test message 2c 
    test message 2c 
    *******/ 
}
```

## Method SysObsoleteAttribute

```xpp
public void SysObsoleteAttribute(str name, AnyType value)
```

### Parameters - SysObsoleteAttribute

name  

<!-- -->

value  

## Method AOTrestore

Reloads this node from the disk, if applicable.

```xpp
public void AOTrestore([boolean forceReload])
```

### Parameters - AOTrestore

forceReload  

## Method AOTregenerate

```xpp
public void AOTregenerate()
```

## Method AOTmakeXref

Compiles this node and its subtree in the AOT, updating the cross-reference system.

```xpp
public void AOTmakeXref([int flag], [boolean xRefAll])
```

### Parameters - AOTmakeXref

flag  

<!-- -->

xRefAll  

### Remarks - AOTmakeXref

This method can be called at any:

-   list node (such as AOT, Tables, Forms, Project roots, and groups)
-   Application Object (such as a Table or Form)
-   methods branch
-   method

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

If the node is a method, the code editor will open. If the node is a documentation object, the Help editor will open.

### Examples - AOTedit

The following code example opens the X++ editor, shows the class declaration of the class Tax, and positions the pointer at line 6, column 8.

```xpp
AOT 
static void myJobAOTEdit(Args _args) 
{ 
    treeNode treeNode; 
    treeNode = TreeNode::findNode(#ClassesPath + '\\' + classStr(Tax)+ '\\ClassDeclaration'); 
    if (treeNode) 
    { 
        treeNode.AOTedit(6,8); 
    } 
    else 
    { 
        print "Could not find treeNode"; 
    } 
    pause; 
}
```

## Method AOTshowProperties

Opens the property sheet (if not already open) and shows the properties for this node.

```xpp
public void AOTshowProperties()
```

## Method AOTinsert

Inserts a node among the subnodes of this node.

```xpp
public void AOTinsert(TreeNode parent, [TreeNode after], [boolean doNotDuplicate])
```

### Parameters - AOTinsert

parent  

<!-- -->

after  

<!-- -->

doNotDuplicate  

## Method new

Initializes a new instance of the TreeNode class.

```xpp
public void new()
```

## Method AOTMove

```xpp
public void AOTMove(TreeNode parent, [TreeNode after])
```

### Parameters - AOTMove

parent  

<!-- -->

after  

## Method SysObsoleteAttribute

```xpp
public void SysObsoleteAttribute(int modelId)
```

### Parameters - SysObsoleteAttribute

modelId  

