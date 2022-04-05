---
title: MultiLookup type
description: Multi-Lookup control type. Multi-Lookup controls are similar to regular lookups except they allow multiple selections at once.
author: tonyafehr
ms.date: 08/01/2017
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: tfehr
---

# MultiLookup type

[!include [banner](../../../../includes/banner.md)]

Multi-Lookup control type. Multi-Lookup controls are similar to regular lookups except they allow multiple selections at once.

### Hierarchy

[InputControl](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md) <br>&nbsp;&nbsp;&nbsp;└─ MultiLookup <br>

## Index

### Properties

* [container](view-model-control-lookup-imultilookup-imultilookup.md#container)
* [generic](view-model-control-lookup-imultilookup-imultilookup.md#generic)
* [getDataSource](view-model-control-lookup-imultilookup-imultilookup.md#getdatasource)
* [getEntityRefs](view-model-control-lookup-imultilookup-imultilookup.md#getentityrefs)
* [hidden](view-model-control-lookup-imultilookup-imultilookup.md#hidden)
* [setEntityRefs](view-model-control-lookup-imultilookup-imultilookup.md#setentityrefs)

### Methods

* [applyDesign](view-model-control-lookup-imultilookup-imultilookup.md#applydesign)
* [dataContext](view-model-control-lookup-imultilookup-imultilookup.md#datacontext)
* [getDesign](view-model-control-lookup-imultilookup-imultilookup.md#getdesign)
* [getLookupPage](view-model-control-lookup-imultilookup-imultilookup.md#getlookuppage)
* [isEditable](view-model-control-lookup-imultilookup-imultilookup.md#iseditable)
* [metadata](view-model-control-lookup-imultilookup-imultilookup.md#metadata)
* [parent](view-model-control-lookup-imultilookup-imultilookup.md#parent)
* [root](view-model-control-lookup-imultilookup-imultilookup.md#root)

### Events

* [onDataChanged](view-model-control-lookup-imultilookup-imultilookup.md#ondatachanged)

## Properties

### container

container: boolean (optional) 

True if the control is a container.

> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[container](view-model-control-basecontrol-icontrol-icontrol.md#container)


### generic

generic: boolean (optional) 



> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[generic](view-model-control-basecontrol-icontrol-icontrol.md#generic)


### getDataSource

getDataSource: function(): any



> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[getDataSource](view-model-control-basecontrol-icontrol-icontrol.md#getdatasource)


### getEntityRefs

getEntityRefs: function(): string [ ] &#124; number [ ]




### hidden

hidden: boolean

True if the control is hidden.

> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[hidden](view-model-control-basecontrol-icontrol-icontrol.md#hidden)


### setEntityRefs

setEntityRefs: function(ids: string [ ] &#124; number [ ]): Promise &lt;any&gt;




## Methods

### applyDesign


applyDesign(IDesign: [MultiLookupDesign](view-model-control-lookup-imultilookup-imultilookupdesign.md)): void

Applies given design to the design on the control.
If a design already exists, the prototype chain of the design will be preserved.

> Overrides [Control](view-model-control-basecontrol-icontrol-icontrol.md).[applyDesign](view-model-control-basecontrol-icontrol-icontrol.md#applydesign)


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| IDesign|[MultiLookupDesign](view-model-control-lookup-imultilookup-imultilookupdesign.md)|object containing design properties as keys|

#### Returns void

### dataContext


dataContext(): any



> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[dataContext](view-model-control-basecontrol-icontrol-icontrol.md#datacontext)

#### Returns any

### getDesign


getDesign(): [Design](view-model-ipage-idesign.md)

Returns the design object of this control.

> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[getDesign](view-model-control-basecontrol-icontrol-icontrol.md#getdesign)

#### Returns [Design](view-model-ipage-idesign.md)



### getLookupPage


getLookupPage(): [Page](view-model-ipage-ipage.md)



#### Returns [Page](view-model-ipage-ipage.md)

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


metadata(): [MultiLookupMetadata](view-model-control-lookup-imultilookup-imultilookupmetadata.md)

Returns the metadata object of this control.

> Overrides [InputControl](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md).[metadata](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md#metadata)

#### Returns [MultiLookupMetadata](view-model-control-lookup-imultilookup-imultilookupmetadata.md)



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



## Events

### onDataChanged

onDataChanged: [EventHook](event-ievent-ieventhook.md) &lt;null&gt;

An event that is triggered when the input control's data changes.

> Inherited from [InputControl](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md).[onDataChanged](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md#ondatachanged)




[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]