---
# required metadata
title: Control
description: Control interface with base methods and attributes for all controls. This represents the runtime instance of a control. Modifying the properties are immediately reflected in the UI.
author: shadykdc
manager: AnnBe
ms.date: 08/01/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 
# optional metadata
# ms.search.form:
audience: Developer
# ms.devlang: 
# ms.reviewer: robinr
ms.search.scope: 
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: Global
# ms.search.industry: 
ms.author: kashea
ms.search.validFrom:
ms.dyn365.ops.version:
---

# Control Type
Control interface with base methods and attributes for all controls.
This represents the runtime instance of a control. Modifying the properties are immediately reflected in the UI.

### Hierarchy

Control <br>&nbsp;&nbsp;&nbsp;└─ [PageLink](view-model-control-pagelink-ipagelink-ipagelink.md) <br>&nbsp;&nbsp;&nbsp;└─ [ContainerControl](view-model-control-container-icontainercontrol-icontainercontrol.md) <br>&nbsp;&nbsp;&nbsp;└─ [InputControl](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md) <br>&nbsp;&nbsp;&nbsp;└─ [Image](view-model-control-image-iimage-iimage.md) <br>

## Index

### Properties

* [container](view-model-control-basecontrol-icontrol-icontrol.md#container)
* [generic](view-model-control-basecontrol-icontrol-icontrol.md#generic)
* [getDataSource](view-model-control-basecontrol-icontrol-icontrol.md#getdatasource)
* [hidden](view-model-control-basecontrol-icontrol-icontrol.md#hidden)

### Methods

* [applyDesign](view-model-control-basecontrol-icontrol-icontrol.md#applydesign)
* [dataContext](view-model-control-basecontrol-icontrol-icontrol.md#datacontext)
* [getDesign](view-model-control-basecontrol-icontrol-icontrol.md#getdesign)
* [isEditable](view-model-control-basecontrol-icontrol-icontrol.md#iseditable)
* [metadata](view-model-control-basecontrol-icontrol-icontrol.md#metadata)
* [parent](view-model-control-basecontrol-icontrol-icontrol.md#parent)
* [root](view-model-control-basecontrol-icontrol-icontrol.md#root)

## Properties

### container

container: boolean (optional) 

True if the control is a container.


### generic

generic: boolean (optional) 




### getDataSource

getDataSource: function(): any




### hidden

hidden: boolean

True if the control is hidden.


## Methods

### applyDesign


applyDesign(design: [Design](view-model-ipage-idesign.md)): void

Applies given design to the design on the control.
If a design already exists, the prototype chain of the design will be preserved.


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| design|[Design](view-model-ipage-idesign.md)|object containing design properties as keys|

#### Returns void

### dataContext


dataContext(): any



#### Returns any

### getDesign


getDesign(): [Design](view-model-ipage-idesign.md)

Returns the design object of this control.

#### Returns [Design](view-model-ipage-idesign.md)



### isEditable


isEditable(): boolean

Boolean indicating if the control is editable.
Returns false when either the control or it's parent is not editable.
Returns true when both the control and it's parent are editable.
Returns true when either the control or it's parent is editable and the other is undefined.
Returns undefined if both the control's edit-ability and it's parent's edit-ability is undefined.

#### Returns boolean



### metadata


metadata(): [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md)

Returns the metadata object of this control.

#### Returns [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md)



### parent


parent(): [Control](view-model-control-basecontrol-icontrol-icontrol.md) &#124; [Page](view-model-ipage-ipage.md)

Returns the parent (control or page) of this control.

#### Returns [Control](view-model-control-basecontrol-icontrol-icontrol.md) &#124; [Page](view-model-ipage-ipage.md)



### root


root(): [Page](view-model-ipage-ipage.md)

Returns the root form instance (page) of this control.

#### Returns [Page](view-model-ipage-ipage.md)



