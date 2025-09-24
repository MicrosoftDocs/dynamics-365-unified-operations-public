---
title: GenericValue type
description: Learn about the generic value control type, which includes the container, generic, getDatSource, and hidden properties and various methods.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 12/31/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.custom: 
  - bap-template
---

# GenericValue type

[!include [banner](../../../../includes/banner.md)]
[!include [mobile app deprecated](../../../../includes/mobile-app-deprecation-banner.md)]

Generic value control type.

### Hierarchy

[Value](view-model-control-value-ivalue-ivalue.md) <br>&nbsp;&nbsp;&nbsp;└─ GenericValue <br>

## Index

### Properties

* [container](view-model-control-value-ivalue-igenericvalue.md#container)
* [generic](view-model-control-value-ivalue-igenericvalue.md#generic)
* [getDataSource](view-model-control-value-ivalue-igenericvalue.md#getdatasource)
* [hidden](view-model-control-value-ivalue-igenericvalue.md#hidden)

### Methods

* [applyDesign](view-model-control-value-ivalue-igenericvalue.md#applydesign)
* [dataContext](view-model-control-value-ivalue-igenericvalue.md#datacontext)
* [getDesign](view-model-control-value-ivalue-igenericvalue.md#getdesign)
* [getValue](view-model-control-value-ivalue-igenericvalue.md#getvalue)
* [isEditable](view-model-control-value-ivalue-igenericvalue.md#iseditable)
* [metadata](view-model-control-value-ivalue-igenericvalue.md#metadata)
* [parent](view-model-control-value-ivalue-igenericvalue.md#parent)
* [root](view-model-control-value-ivalue-igenericvalue.md#root)
* [setValue](view-model-control-value-ivalue-igenericvalue.md#setvalue)

### Events

* [onDataChanged](view-model-control-value-ivalue-igenericvalue.md#ondatachanged)

## Properties

### container

container: boolean (optional) 

True if the control is a container.

> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[container](view-model-control-basecontrol-icontrol-icontrol.md#container)


### generic

generic: boolean

True if the control is a generic.

> Overrides [Control](view-model-control-basecontrol-icontrol-icontrol.md).[generic](view-model-control-basecontrol-icontrol-icontrol.md#generic)


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



### getValue


getValue(): string

Returns the value of the control.

> Inherited from [Value](view-model-control-value-ivalue-ivalue.md).[getValue](view-model-control-value-ivalue-ivalue.md#getvalue)

#### Returns string



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


metadata(): [ValueMetadata](view-model-control-value-ivalue-ivaluemetadata.md)

Returns the metadata object of this control.

> Inherited from [Value](view-model-control-value-ivalue-ivalue.md).[metadata](view-model-control-value-ivalue-ivalue.md#metadata)
> 
> Overrides [InputControl](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md).[metadata](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md#metadata)

#### Returns [ValueMetadata](view-model-control-value-ivalue-ivaluemetadata.md)



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



### setValue


setValue(value: string): void

Sets the value of the control.

> Inherited from [Value](view-model-control-value-ivalue-ivalue.md).[setValue](view-model-control-value-ivalue-ivalue.md#setvalue)


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| value|string||

#### Returns void

## Events

### onDataChanged

onDataChanged: [EventHook](event-ievent-ieventhook.md) &lt;null&gt;

An event that is triggered when the input control's data changes.

> Inherited from [InputControl](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md).[onDataChanged](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md#ondatachanged)




[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]
