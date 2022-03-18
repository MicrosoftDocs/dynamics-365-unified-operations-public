---
title: Field type
description: Field control type.
author: tonyafehr
ms.date: 08/01/2017
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: tfehr
---

# Field type

[!include [banner](../../../../includes/banner.md)]

Field control type.

### Hierarchy

[InputControl](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md) <br>&nbsp;&nbsp;&nbsp;└─ Field <br>

## Index

### Properties

* [container](view-model-control-field-ifield-ifield.md#container)
* [generic](view-model-control-field-ifield-ifield.md#generic)
* [getDataSource](view-model-control-field-ifield-ifield.md#getdatasource)
* [hidden](view-model-control-field-ifield-ifield.md#hidden)

### Methods

* [applyDesign](view-model-control-field-ifield-ifield.md#applydesign)
* [dataContext](view-model-control-field-ifield-ifield.md#datacontext)
* [getDesign](view-model-control-field-ifield-ifield.md#getdesign)
* [getEditableFormattedValue](view-model-control-field-ifield-ifield.md#geteditableformattedvalue)
* [getEditableValue](view-model-control-field-ifield-ifield.md#geteditablevalue)
* [getEntityRef](view-model-control-field-ifield-ifield.md#getentityref)
* [getFormattedValue](view-model-control-field-ifield-ifield.md#getformattedvalue)
* [getRefLink](view-model-control-field-ifield-ifield.md#getreflink)
* [getValue](view-model-control-field-ifield-ifield.md#getvalue)
* [hasRefLink](view-model-control-field-ifield-ifield.md#hasreflink)
* [hasUnWrapText](view-model-control-field-ifield-ifield.md#hasunwraptext)
* [isEditable](view-model-control-field-ifield-ifield.md#iseditable)
* [metadata](view-model-control-field-ifield-ifield.md#metadata)
* [parent](view-model-control-field-ifield-ifield.md#parent)
* [root](view-model-control-field-ifield-ifield.md#root)
* [setEditableValue](view-model-control-field-ifield-ifield.md#seteditablevalue)

### Events

* [onDataChanged](view-model-control-field-ifield-ifield.md#ondatachanged)

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


applyDesign(IDesign: [FieldDesign](view-model-control-field-ifield-ifielddesign.md)): void

Applies given design to the design on the control.
If a design already exists, the prototype chain of the design will be preserved.

> Overrides [Control](view-model-control-basecontrol-icontrol-icontrol.md).[applyDesign](view-model-control-basecontrol-icontrol-icontrol.md#applydesign)


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| IDesign|[FieldDesign](view-model-control-field-ifield-ifielddesign.md)|object containing design properties as keys|

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



### getEditableFormattedValue


getEditableFormattedValue(): string &#124; number &#124; Date

Gets a formatted decimal string value of an editable field control.

#### Returns string &#124; number &#124; Date



### getEditableValue


getEditableValue(): string &#124; number &#124; Date

Gets the value for an editable field control.

#### Returns string &#124; number &#124; Date



### getEntityRef


getEntityRef(): any

Gets value of entityRef binding to control.

#### Returns any
value of entityRef binding to control


### getFormattedValue


getFormattedValue(): string

Gets a formatted decimal string value.

#### Returns string



### getRefLink


getRefLink(): [NavigationArgs](view-model-ipage-inavigationargs.md)

Gets the navigation object for a reference link.

#### Returns [NavigationArgs](view-model-ipage-inavigationargs.md)



### getValue


getValue(): any

Gets the value for a field control.

#### Returns any



### hasRefLink


hasRefLink(): boolean

Returns true if the field has a refLink, otherwise false.

#### Returns boolean



### hasUnWrapText


hasUnWrapText(): boolean

Gets wrap text property of control.

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


metadata(): [FieldMetadata](view-model-control-field-ifield-ifieldmetadata.md)

Returns the metadata object of this control.

> Overrides [InputControl](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md).[metadata](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md#metadata)

#### Returns [FieldMetadata](view-model-control-field-ifield-ifieldmetadata.md)



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



### setEditableValue


setEditableValue(value: string &#124; number &#124; Date): void

Sets the value for an editable field control.


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| value|string &#124; number &#124; Date|value|

#### Returns void

## Events

### onDataChanged

onDataChanged: [EventHook](event-ievent-ieventhook.md) &lt;null&gt;

An event that is triggered when the input control's data changes.

> Inherited from [InputControl](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md).[onDataChanged](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md#ondatachanged)




[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]