---
# required metadata
title: ContainerControl
description: Container control interface with methods and attributes for all container controls. A container control can contain any number of controls.
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

# ContainerControl Type
Container control interface with methods and attributes for all container controls.
A container control can contain any number of controls.

### Hierarchy

[Control](view-model-control-basecontrol-icontrol-icontrol.md) <br>&nbsp;&nbsp;&nbsp;└─ ContainerControl <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─ [Group](view-model-control-group-igroup-igroup.md) <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─ [List](view-model-control-list-ilist-ilist.md) <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─ [Part](view-model-control-part-ipart-ipart.md) <br>

## Index

### Properties

* [container](view-model-control-container-icontainercontrol-icontainercontrol.md#container)
* [generic](view-model-control-container-icontainercontrol-icontainercontrol.md#generic)
* [getDataSource](view-model-control-container-icontainercontrol-icontainercontrol.md#getdatasource)
* [hidden](view-model-control-container-icontainercontrol-icontainercontrol.md#hidden)

### Methods

* [applyDesign](view-model-control-container-icontainercontrol-icontainercontrol.md#applydesign)
* [dataContext](view-model-control-container-icontainercontrol-icontainercontrol.md#datacontext)
* [getControl](view-model-control-container-icontainercontrol-icontainercontrol.md#getcontrol)
* [getControlById](view-model-control-container-icontainercontrol-icontainercontrol.md#getcontrolbyid)
* [getDesign](view-model-control-container-icontainercontrol-icontainercontrol.md#getdesign)
* [isEditable](view-model-control-container-icontainercontrol-icontainercontrol.md#iseditable)
* [metadata](view-model-control-container-icontainercontrol-icontainercontrol.md#metadata)
* [parent](view-model-control-container-icontainercontrol-icontainercontrol.md#parent)
* [root](view-model-control-container-icontainercontrol-icontainercontrol.md#root)

## Properties

### container

container: boolean

True if the control is a container.

> Overrides [Control](view-model-control-basecontrol-icontrol-icontrol.md).[container](view-model-control-basecontrol-icontrol-icontrol.md#container)


### generic

generic: boolean (optional) 



> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[generic](view-model-control-basecontrol-icontrol-icontrol.md#generic)


### getDataSource

getDataSource: function(): any



> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[getDataSource](view-model-control-basecontrol-icontrol-icontrol.md#getdatasource)


### hidden

hidden: boolean

True if the control is hidden.

> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[hidden](view-model-control-basecontrol-icontrol-icontrol.md#hidden)


## Methods

### applyDesign


applyDesign(design: [Design](view-model-ipage-idesign.md)): void

Applies given design to the design on the control.
If a design already exists, the prototype chain of the design will be preserved.

> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[applyDesign](view-model-control-basecontrol-icontrol-icontrol.md#applydesign)


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| design|[Design](view-model-ipage-idesign.md)|object containing design properties as keys|

#### Returns void

### dataContext


dataContext(): any



> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[dataContext](view-model-control-basecontrol-icontrol-icontrol.md#datacontext)

#### Returns any

### getControl


getControl(controlName: string): [Control](view-model-control-basecontrol-icontrol-icontrol.md)

Given the name of a control, returns the control instance.


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| controlName|string|control name|

#### Returns [Control](view-model-control-basecontrol-icontrol-icontrol.md)



### getControlById


getControlById(id: string): [Control](view-model-control-basecontrol-icontrol-icontrol.md)

Given the ID of a control, returns the control instance.


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| id|string|control ID|

#### Returns [Control](view-model-control-basecontrol-icontrol-icontrol.md)



### getDesign


getDesign(): [Design](view-model-ipage-idesign.md)

Returns the design object of this control.

> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[getDesign](view-model-control-basecontrol-icontrol-icontrol.md#getdesign)

#### Returns [Design](view-model-ipage-idesign.md)



### isEditable


isEditable(): boolean

Boolean indicating if the control is editable.
Returns false when either the control or it's parent is not editable.
Returns true when both the control and it's parent are editable.
Returns true when either the control or it's parent is editable and the other is undefined.
Returns undefined if both the control's edit-ability and it's parent's edit-ability is undefined.

> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[isEditable](view-model-control-basecontrol-icontrol-icontrol.md#iseditable)

#### Returns boolean



### metadata


metadata(): [ContainerControlMetadata](view-model-control-container-icontainercontrol-icontainercontrolmetadata.md)

Returns the metadata object of this control.

> Overrides [Control](view-model-control-basecontrol-icontrol-icontrol.md).[metadata](view-model-control-basecontrol-icontrol-icontrol.md#metadata)

#### Returns [ContainerControlMetadata](view-model-control-container-icontainercontrol-icontainercontrolmetadata.md)



### parent


parent(): [Control](view-model-control-basecontrol-icontrol-icontrol.md) &#124; [Page](view-model-ipage-ipage.md)

Returns the parent (control or page) of this control.

> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[parent](view-model-control-basecontrol-icontrol-icontrol.md#parent)

#### Returns [Control](view-model-control-basecontrol-icontrol-icontrol.md) &#124; [Page](view-model-ipage-ipage.md)



### root


root(): [Page](view-model-ipage-ipage.md)

Returns the root form instance (page) of this control.

> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[root](view-model-control-basecontrol-icontrol-icontrol.md#root)

#### Returns [Page](view-model-ipage-ipage.md)



