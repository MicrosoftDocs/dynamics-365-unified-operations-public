---
title: TreeNodeType class
description: This topic describes the TreeNodeType class.
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

# Class TreeNodeType

[!include [banner](../../includes/banner.md)]

```xpp
class TreeNodeType extends Object
```

The TreeNodeType class retrieves information about types of TreeNode classes.

## Remarks

This class enable you to reflect on a TreeNode class instance. The reflection information is not specific to an instance of a TreeNode class. All TreeNode instances with the same NodeType share the same TreeNodeType. The TreeNode.TreeNodeType method return a treeNodeType object with the reflection information.

## Examples

## Methods

| Method                                     | Description                                                                                            |
|--------------------------------------------|--------------------------------------------------------------------------------------------------------|
| public int id()                            | Returns the type's ID.                                                                                 |
| public boolean isConsumingMemory()         | Indicates whether instances of this node type are consuming memory that needs to be manually released. |
| public boolean isGetNodeInLayerSupported() | Indicates whether instances of this node type support the TreeNode.GetNodeInLayer method.              |
| public boolean isLayerAware()              | Indicates whether instances of this node type are decorated with layers in the AOT.                    |
| public boolean isModelElement()            | Indicates whether instances of this node type are model-elements.                                      |
| public boolean isRootElement()             | Indicates whether instances of this node type are root-elements.                                       |
| public boolean isUtilElement()             | Indicates whether instances of this node type are util-elements.                                       |
| public boolean isVCSControllableElement()  |                                                                                                        |
| private void new()                         | Initializes a new instance of the TreeNodeType class.                                                  |

## Method id

Returns the type's ID.

```xpp
public int id()
```

### Return Value - id

The ID of the TreeNodeType.

## Method isConsumingMemory

Indicates whether instances of this node type are consuming memory that needs to be manually released.

```xpp
public boolean isConsumingMemory()
```

### Return Value - isConsumingMemory

true if tree nodes of this type consumes memory; otherwise, false.

### Remarks - isConsumingMemory

After working with TreeNode instances of this type it is important to call the TreeNode.TreeNodeRelease method to release any consumed memory. Failure to do this will result in out-of-memory exceptions. Do not call the TreeNode.TreeNodeRelease method before all instances of TreeNode classes in the composition hierarchy has been garbage collected. For example, do not call the TreeNode.TreeNodeRelease() method on MyClass, if you still have a TreeNode instance of MyClass.myMethod.

## Method isGetNodeInLayerSupported

Indicates whether instances of this node type support the TreeNode.GetNodeInLayer method.

```xpp
public boolean isGetNodeInLayerSupported()
```

### Return Value - isGetNodeInLayerSupported

true if tree nodes of this type support the TreeNode.GetNodeInLayer method; otherwise, false.

## Method isLayerAware

Indicates whether instances of this node type are decorated with layers in the AOT.

```xpp
public boolean isLayerAware()
```

### Return Value - isLayerAware

true if tree nodes of this type are decorated with layers; otherwise, false.

### Remarks - isLayerAware

Tree nodes of this type support the AOTLayer and AOTLayers methods.

## Method isModelElement

Indicates whether instances of this node type are model-elements.

```xpp
public boolean isModelElement()
```

### Return Value - isModelElement

true if tree nodes of this type are model-elements; otherwise, false.

### Remarks - isModelElement

A model-element is a tree node that is (or can be) persisted in the model store. For each model-element tree node one record can be found in the ModelElements table in the model store. Model-elements are visually decorated with the name of the Model they are contained by in the AOT.

## Method isRootElement

Indicates whether instances of this node type are root-elements.

```xpp
public boolean isRootElement()
```

### Return Value - isRootElement

true if tree nodes of this type are root-elements; otherwise, false.

### Remarks - isRootElement

A root-element is the root in a composition hierarchy of tree nodes. A root-element never has a model-element parent. Examples include MyTable, MyClass, MyForm.

## Method isUtilElement

Indicates whether instances of this node type are util-elements.

```xpp
public boolean isUtilElement()
```

### Return Value - isUtilElement

true if tree nodes of this type are util-elements; otherwise, false.

### Remarks - isUtilElement

An util-element is a tree node that can be accessed via the UtilElements and UtilIdElements views. Util-elements are a subset of model-elements.

## Method isVCSControllableElement

```xpp
public boolean isVCSControllableElement()
```

### Return Value - isVCSControllableElement

## Method new

Initializes a new instance of the TreeNodeType class.

```xpp
private void new()
```


