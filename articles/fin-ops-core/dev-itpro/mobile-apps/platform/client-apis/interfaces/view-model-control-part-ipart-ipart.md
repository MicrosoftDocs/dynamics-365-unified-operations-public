---
title: Part type
description: Learn about the part type, a container control that contains only a page, allowing for a page to be embedded within a page.
author: jasongre
ms.author: jasongre
ms.topic: article
ms.date: 05/24/2022
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
---

# Part type

[!include [banner](../../../../includes/banner.md)]
[!include [mobile app deprecated](../../../../includes/mobile-app-deprecation-banner.md)]

Part control type. A part is a container control that contains only a page, allowing for a page to be embedded within a page.

### Hierarchy

[ContainerControl](view-model-control-container-icontainercontrol-icontainercontrol.md) <br>&nbsp;&nbsp;&nbsp;└─ Part <br>

## Index

### Properties

* [container](view-model-control-part-ipart-ipart.md#container)
* [generic](view-model-control-part-ipart-ipart.md#generic)
* [getDataSource](view-model-control-part-ipart-ipart.md#getdatasource)
* [hidden](view-model-control-part-ipart-ipart.md#hidden)

### Methods

* [applyDesign](view-model-control-part-ipart-ipart.md#applydesign)
* [dataContext](view-model-control-part-ipart-ipart.md#datacontext)
* [getControl](view-model-control-part-ipart-ipart.md#getcontrol)
* [getControlById](view-model-control-part-ipart-ipart.md#getcontrolbyid)
* [getDesign](view-model-control-part-ipart-ipart.md#getdesign)
* [getEntityRef](view-model-control-part-ipart-ipart.md#getentityref)
* [getPartPage](view-model-control-part-ipart-ipart.md#getpartpage)
* [hasTarget](view-model-control-part-ipart-ipart.md#hastarget)
* [isEditable](view-model-control-part-ipart-ipart.md#iseditable)
* [metadata](view-model-control-part-ipart-ipart.md#metadata)
* [parent](view-model-control-part-ipart-ipart.md#parent)
* [root](view-model-control-part-ipart-ipart.md#root)

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


applyDesign(IDesign: [PartDesign](view-model-control-part-ipart-ipartdesign.md)): void

Applies given design to the design on the control.
If a design already exists, the prototype chain of the design will be preserved.

> Overrides [Control](view-model-control-basecontrol-icontrol-icontrol.md).[applyDesign](view-model-control-basecontrol-icontrol-icontrol.md#applydesign)


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| IDesign|[PartDesign](view-model-control-part-ipart-ipartdesign.md)|object containing design properties as keys|

#### Returns void

### dataContext


dataContext(): any



> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[dataContext](view-model-control-basecontrol-icontrol-icontrol.md#datacontext)

#### Returns any

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



### getEntityRef


getEntityRef(): string

Gets value of entityRef binding to control.

#### Returns string



### getPartPage


getPartPage(): [Page](view-model-ipage-ipage.md)

Gets the page of the part.

#### Returns [Page](view-model-ipage-ipage.md)



### hasTarget


hasTarget(): boolean

Returns true if the part has a target page.

#### Returns boolean



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


metadata(): [PartMetadata](view-model-control-part-ipart-ipartmetadata.md)

Returns the metadata object of this control.

> Overrides [ContainerControl](view-model-control-container-icontainercontrol-icontainercontrol.md).[metadata](view-model-control-container-icontainercontrol-icontainercontrol.md#metadata)

#### Returns [PartMetadata](view-model-control-part-ipart-ipartmetadata.md)



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
