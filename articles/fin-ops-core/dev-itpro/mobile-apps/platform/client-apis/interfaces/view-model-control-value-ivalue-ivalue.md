---
title: Value type
description: Learn about the value control type, which includes the container, generic, getDataSource, and hidden properties and various methods.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 12/31/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.custom: 
  - bap-template
---

# Value type

[!include [banner](../../../../includes/banner.md)]
[!include [mobile app deprecated](../../../../includes/mobile-app-deprecation-banner.md)]

Value control type. This is the base class for single value controls.

### Hierarchy

[InputControl](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md) <br>&nbsp;&nbsp;&nbsp;└─ Value <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─ [FileUploader](view-model-control-fileuploader-ifileuploader-ifileuploader.md) <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─ [HyperLink](view-model-control-hyperlink-ihyperlink-ihyperlink.md) <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─ [GenericValue](view-model-control-value-ivalue-igenericvalue.md) <br>

## Index

### Properties

* [container](view-model-control-value-ivalue-ivalue.md#container)
* [generic](view-model-control-value-ivalue-ivalue.md#generic)
* [getDataSource](view-model-control-value-ivalue-ivalue.md#getdatasource)
* [hidden](view-model-control-value-ivalue-ivalue.md#hidden)

### Methods

* [applyDesign](view-model-control-value-ivalue-ivalue.md#applydesign)
* [dataContext](view-model-control-value-ivalue-ivalue.md#datacontext)
* [getDesign](view-model-control-value-ivalue-ivalue.md#getdesign)
* [getValue](view-model-control-value-ivalue-ivalue.md#getvalue)
* [isEditable](view-model-control-value-ivalue-ivalue.md#iseditable)
* [metadata](view-model-control-value-ivalue-ivalue.md#metadata)
* [parent](view-model-control-value-ivalue-ivalue.md#parent)
* [root](view-model-control-value-ivalue-ivalue.md#root)
* [setValue](view-model-control-value-ivalue-ivalue.md#setvalue)

### Events

* [onDataChanged](view-model-control-value-ivalue-ivalue.md#ondatachanged)

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



### getValue


getValue(): string

Returns the value of the control.

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
