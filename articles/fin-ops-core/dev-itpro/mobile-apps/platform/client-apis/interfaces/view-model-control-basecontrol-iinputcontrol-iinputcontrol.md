---
title: InputControl type
description: Input control interface with methods and attributes for all input controls.
author: tonyafehr
ms.date: 08/01/2017
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: tfehr
---

# InputControl type

[!include [banner](../../../../includes/banner.md)]

Input control interface with methods and attributes for all input controls.
Input controls are typically used on task pages for collecting user input, for example, for a new control.

### Hierarchy

[Control](view-model-control-basecontrol-icontrol-icontrol.md) <br>&nbsp;&nbsp;&nbsp;└─ InputControl <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─ [Field](view-model-control-field-ifield-ifield.md) <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─ [Lookup](view-model-control-lookup-ilookup-ilookup.md) <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─ [MultiLookup](view-model-control-lookup-imultilookup-imultilookup.md) <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─ [Value](view-model-control-value-ivalue-ivalue.md) <br>

## Index

### Properties

* [container](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md#container)
* [generic](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md#generic)
* [getDataSource](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md#getdatasource)
* [hidden](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md#hidden)

### Methods

* [applyDesign](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md#applydesign)
* [dataContext](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md#datacontext)
* [getDesign](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md#getdesign)
* [isEditable](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md#iseditable)
* [metadata](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md#metadata)
* [parent](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md#parent)
* [root](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md#root)

### Events

* [onDataChanged](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md#ondatachanged)

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


metadata(): [InputControlMetadata](view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md)

Returns the metadata object of this control.

> Overrides [Control](view-model-control-basecontrol-icontrol-icontrol.md).[metadata](view-model-control-basecontrol-icontrol-icontrol.md#metadata)

#### Returns [InputControlMetadata](view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md)



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




[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]