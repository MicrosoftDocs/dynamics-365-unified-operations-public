---
title: Lookup type
description: Learn about the Lookup control type, an input control that is used to select an input from a list of options, which includes various properties and methods.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 12/31/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.custom: 
  - bap-template
---

# Lookup type

[!include [banner](../../../../includes/banner.md)]
[!include [mobile app deprecated](../../../../includes/mobile-app-deprecation-banner.md)]

Lookup control type. A lookup is an input control that is used to select an input from a list of options.
For example, a lookup could be used to lookup a customer when linking a customer to a new sales order.

### Hierarchy

[InputControl](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md) <br>&nbsp;&nbsp;&nbsp;└─ Lookup <br>

## Index

### Properties

* [container](view-model-control-lookup-ilookup-ilookup.md#container)
* [generic](view-model-control-lookup-ilookup-ilookup.md#generic)
* [getDataSource](view-model-control-lookup-ilookup-ilookup.md#getdatasource)
* [hidden](view-model-control-lookup-ilookup-ilookup.md#hidden)

### Methods

* [applyDesign](view-model-control-lookup-ilookup-ilookup.md#applydesign)
* [dataContext](view-model-control-lookup-ilookup-ilookup.md#datacontext)
* [getDesign](view-model-control-lookup-ilookup-ilookup.md#getdesign)
* [getDisplayValue](view-model-control-lookup-ilookup-ilookup.md#getdisplayvalue)
* [getLookupPage](view-model-control-lookup-ilookup-ilookup.md#getlookuppage)
* [getValue](view-model-control-lookup-ilookup-ilookup.md#getvalue)
* [isEditable](view-model-control-lookup-ilookup-ilookup.md#iseditable)
* [metadata](view-model-control-lookup-ilookup-ilookup.md#metadata)
* [parent](view-model-control-lookup-ilookup-ilookup.md#parent)
* [root](view-model-control-lookup-ilookup-ilookup.md#root)
* [setEntityRef](view-model-control-lookup-ilookup-ilookup.md#setentityref)

### Events

* [onDataChanged](view-model-control-lookup-ilookup-ilookup.md#ondatachanged)

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


applyDesign(IDesign: [LookupDesign](view-model-control-lookup-ilookup-ilookupdesign.md)): void

Applies given design to the design on the control.
If a design already exists, the prototype chain of the design will be preserved.

> Overrides [Control](view-model-control-basecontrol-icontrol-icontrol.md).[applyDesign](view-model-control-basecontrol-icontrol-icontrol.md#applydesign)


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| IDesign|[LookupDesign](view-model-control-lookup-ilookup-ilookupdesign.md)|object containing design properties as keys|

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



### getDisplayValue


getDisplayValue(): string



#### Returns string

### getLookupPage


getLookupPage(): [Page](view-model-ipage-ipage.md)



#### Returns [Page](view-model-ipage-ipage.md)

### getValue


getValue(): string &#124; number



#### Returns string &#124; number

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


metadata(): [LookupMetadata](view-model-control-lookup-ilookup-ilookupmetadata.md)

Returns the metadata object of this control.

> Overrides [InputControl](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md).[metadata](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md#metadata)

#### Returns [LookupMetadata](view-model-control-lookup-ilookup-ilookupmetadata.md)



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



### setEntityRef


setEntityRef(newValue: string &#124; number): Promise &lt;any&gt;




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| newValue|string &#124; number||

#### Returns Promise &lt;any&gt;

## Events

### onDataChanged

onDataChanged: [EventHook](event-ievent-ieventhook.md) &lt;null&gt;

An event that is triggered when the input control's data changes.

> Inherited from [InputControl](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md).[onDataChanged](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md#ondatachanged)




[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]
