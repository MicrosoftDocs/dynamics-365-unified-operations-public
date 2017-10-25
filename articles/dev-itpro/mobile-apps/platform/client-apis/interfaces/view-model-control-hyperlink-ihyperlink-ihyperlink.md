---
# required metadata
title: HyperLink
description: Hyperlink control type. Hyperlink control is a control to represent hyperlinks. Pagelinks can also be used in most cases.
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

# HyperLink Type
Hyperlink control type. Hyperlink control is a control to represent hyperlinks. Pagelinks can also be used in most cases.

### Hierarchy

[Value](view-model-control-value-ivalue-ivalue.md) <br>&nbsp;&nbsp;&nbsp;└─ HyperLink <br>

## Index

### Properties

* [container](view-model-control-hyperlink-ihyperlink-ihyperlink.md#container)
* [generic](view-model-control-hyperlink-ihyperlink-ihyperlink.md#generic)
* [getDataSource](view-model-control-hyperlink-ihyperlink-ihyperlink.md#getdatasource)
* [hidden](view-model-control-hyperlink-ihyperlink-ihyperlink.md#hidden)

### Methods

* [applyDesign](view-model-control-hyperlink-ihyperlink-ihyperlink.md#applydesign)
* [dataContext](view-model-control-hyperlink-ihyperlink-ihyperlink.md#datacontext)
* [getDesign](view-model-control-hyperlink-ihyperlink-ihyperlink.md#getdesign)
* [getHyperLinkValue](view-model-control-hyperlink-ihyperlink-ihyperlink.md#gethyperlinkvalue)
* [getValue](view-model-control-hyperlink-ihyperlink-ihyperlink.md#getvalue)
* [isEditable](view-model-control-hyperlink-ihyperlink-ihyperlink.md#iseditable)
* [isHyperLinkURLPresent](view-model-control-hyperlink-ihyperlink-ihyperlink.md#ishyperlinkurlpresent)
* [metadata](view-model-control-hyperlink-ihyperlink-ihyperlink.md#metadata)
* [parent](view-model-control-hyperlink-ihyperlink-ihyperlink.md#parent)
* [root](view-model-control-hyperlink-ihyperlink-ihyperlink.md#root)
* [setBaseURL](view-model-control-hyperlink-ihyperlink-ihyperlink.md#setbaseurl)
* [setValue](view-model-control-hyperlink-ihyperlink-ihyperlink.md#setvalue)

### Events

* [onDataChanged](view-model-control-hyperlink-ihyperlink-ihyperlink.md#ondatachanged)

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


applyDesign(IDesign: [HyperLinkDesign](view-model-control-hyperlink-ihyperlink-ihyperlinkdesign.md)): void

Applies given design to the design on the control.
If a design already exists, the prototype chain of the design will be preserved.

> Overrides [Control](view-model-control-basecontrol-icontrol-icontrol.md).[applyDesign](view-model-control-basecontrol-icontrol-icontrol.md#applydesign)


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| IDesign|[HyperLinkDesign](view-model-control-hyperlink-ihyperlink-ihyperlinkdesign.md)|object containing design properties as keys|

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



### getHyperLinkValue


getHyperLinkValue(): string



#### Returns string

### getValue


getValue(): string

Returns the value of the control.

> Inherited from [Value](view-model-control-value-ivalue-ivalue.md).[getValue](view-model-control-value-ivalue-ivalue.md#getvalue)

#### Returns string



### isEditable


isEditable(): boolean

Boolean indicating if the control is editable.
Returns false when either the control or it's parent is not editable.
Returns true when both the control and it's parent are editable.
Returns true when either the control or it's parent is editable and the other is undefined.
Returns undefined if both the control's edit-ability and it's parent's edit-ability is undefined.

> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[isEditable](view-model-control-basecontrol-icontrol-icontrol.md#iseditable)

#### Returns boolean



### isHyperLinkURLPresent


isHyperLinkURLPresent(): boolean



#### Returns boolean

### metadata


metadata(): [HyperLinkMetadata](view-model-control-hyperlink-ihyperlink-ihyperlinkmetadata.md)

Returns the metadata object of this control.

> Overrides [Value](view-model-control-value-ivalue-ivalue.md).[metadata](view-model-control-value-ivalue-ivalue.md#metadata)

#### Returns [HyperLinkMetadata](view-model-control-hyperlink-ihyperlink-ihyperlinkmetadata.md)



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



### setBaseURL


setBaseURL(url: string): any




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| url|string||

#### Returns any

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


