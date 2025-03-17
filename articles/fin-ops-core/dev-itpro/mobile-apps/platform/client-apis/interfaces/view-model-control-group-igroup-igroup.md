---
title: Group type
description: Learn about the Group type, a group container control type that contains the container, generic, getDataSource, and hidden properties and various methods.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 12/31/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.custom: 
  - bap-template
---

# Group type

[!include [banner](../../../../includes/banner.md)]
[!include [mobile app deprecated](../../../../includes/mobile-app-deprecation-banner.md)]

Group container control type.
A group control is a container control that has any number of controls as children.

### Hierarchy

[ContainerControl](view-model-control-container-icontainercontrol-icontainercontrol.md) <br>&nbsp;&nbsp;&nbsp;└─ Group <br>

## Index

### Properties

* [container](view-model-control-group-igroup-igroup.md#container)
* [generic](view-model-control-group-igroup-igroup.md#generic)
* [getDataSource](view-model-control-group-igroup-igroup.md#getdatasource)
* [hidden](view-model-control-group-igroup-igroup.md#hidden)

### Methods

* [applyDesign](view-model-control-group-igroup-igroup.md#applydesign)
* [dataContext](view-model-control-group-igroup-igroup.md#datacontext)
* [getChildren](view-model-control-group-igroup-igroup.md#getchildren)
* [getControl](view-model-control-group-igroup-igroup.md#getcontrol)
* [getControlById](view-model-control-group-igroup-igroup.md#getcontrolbyid)
* [getDesign](view-model-control-group-igroup-igroup.md#getdesign)
* [isEditable](view-model-control-group-igroup-igroup.md#iseditable)
* [metadata](view-model-control-group-igroup-igroup.md#metadata)
* [parent](view-model-control-group-igroup-igroup.md#parent)
* [root](view-model-control-group-igroup-igroup.md#root)

## Properties

### container

container: boolean

True if the control is a container.

> Inherited from [ContainerControl](view-model-control-container-icontainercontrol-icontainercontrol.md).[container](view-model-control-container-icontainercontrol-icontainercontrol.md#container)
> 
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


applyDesign(IDesign: [GroupDesign](view-model-control-group-igroup-igroupdesign.md)): void

Applies given design to the design on the control.
If a design already exists, the prototype chain of the design will be preserved.

> Overrides [Control](view-model-control-basecontrol-icontrol-icontrol.md).[applyDesign](view-model-control-basecontrol-icontrol-icontrol.md#applydesign)


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| IDesign|[GroupDesign](view-model-control-group-igroup-igroupdesign.md)|object containing design properties as keys|

#### Returns void

### dataContext


dataContext(): any



> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[dataContext](view-model-control-basecontrol-icontrol-icontrol.md#datacontext)

#### Returns any

### getChildren


getChildren(): [Control](view-model-control-basecontrol-icontrol-icontrol.md) [ ]

Returns the list of children associated with this group control.

#### Returns [Control](view-model-control-basecontrol-icontrol-icontrol.md) [ ]



### getControl


getControl(controlName: string): [Control](view-model-control-basecontrol-icontrol-icontrol.md)

Given the name of a control, returns the control instance.

> Inherited from [ContainerControl](view-model-control-container-icontainercontrol-icontainercontrol.md).[getControl](view-model-control-container-icontainercontrol-icontainercontrol.md#getcontrol)


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| controlName|string|control name|

#### Returns [Control](view-model-control-basecontrol-icontrol-icontrol.md)



### getControlById


getControlById(id: string): [Control](view-model-control-basecontrol-icontrol-icontrol.md)

Given the ID of a control, returns the control instance.

> Inherited from [ContainerControl](view-model-control-container-icontainercontrol-icontainercontrol.md).[getControlById](view-model-control-container-icontainercontrol-icontainercontrol.md#getcontrolbyid)


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
Returns false when either the control or its parent is not editable.
Returns true when both the control and its parent are editable.
Returns true when either the control or its parent is editable and the other is undefined.
Returns undefined if both the control's edit-ability and its parent's edit-ability is undefined.

> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[isEditable](view-model-control-basecontrol-icontrol-icontrol.md#iseditable)

#### Returns boolean



### metadata


metadata(): [GroupMetadata](view-model-control-group-igroup-igroupmetadata.md)

Returns the metadata object of this control.

> Overrides [ContainerControl](view-model-control-container-icontainercontrol-icontainercontrol.md).[metadata](view-model-control-container-icontainercontrol-icontainercontrol.md#metadata)

#### Returns [GroupMetadata](view-model-control-group-igroup-igroupmetadata.md)



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





[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]
