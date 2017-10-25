---
# required metadata
title: Row
description: Row controls are what make up a list. A list contains any number of row controls.
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

# Row Type
Row controls are what make up a list. A list contains any number of row controls.

### Hierarchy

Row <br>

## Index

### Properties

* [fieldList](view-model-control-list-ilist-irow.md#fieldlist)
* [headerField](view-model-control-list-ilist-irow.md#headerfield)
* [hidden](view-model-control-list-ilist-irow.md#hidden)
* [imageFields](view-model-control-list-ilist-irow.md#imagefields)
* [isSelected](view-model-control-list-ilist-irow.md#isselected)
* [item](view-model-control-list-ilist-irow.md#item)
* [template](view-model-control-list-ilist-irow.md#template)

### Methods

* [getControl](view-model-control-list-ilist-irow.md#getcontrol)
* [getControlById](view-model-control-list-ilist-irow.md#getcontrolbyid)
* [getControlValueById](view-model-control-list-ilist-irow.md#getcontrolvaluebyid)
* [getRowHeader](view-model-control-list-ilist-irow.md#getrowheader)
* [getRowId](view-model-control-list-ilist-irow.md#getrowid)
* [hasImageField](view-model-control-list-ilist-irow.md#hasimagefield)
* [isEntityCreatedNew](view-model-control-list-ilist-irow.md#isentitycreatednew)
* [isEntityDeleted](view-model-control-list-ilist-irow.md#isentitydeleted)
* [isEntityModified](view-model-control-list-ilist-irow.md#isentitymodified)
* [isEntitySyncPending](view-model-control-list-ilist-irow.md#isentitysyncpending)
* [select](view-model-control-list-ilist-irow.md#select)

## Properties

### fieldList

fieldList: [Control](view-model-control-basecontrol-icontrol-icontrol.md) [ ]




### headerField

headerField: [Control](view-model-control-basecontrol-icontrol-icontrol.md)




### hidden

hidden: boolean

If true then the row will be hidden.


### imageFields

imageFields: [Control](view-model-control-basecontrol-icontrol-icontrol.md) [ ]




### isSelected

isSelected: boolean




### item

item: any

A container of rendered data.


### template

template: [Group](view-model-control-group-igroup-igroup.md)

Group control that represents the template for a row.


## Methods

### getControl


getControl(controlName: string): [Control](view-model-control-basecontrol-icontrol-icontrol.md)




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| controlName|string||

#### Returns [Control](view-model-control-basecontrol-icontrol-icontrol.md)

### getControlById


getControlById(id: string): [Control](view-model-control-basecontrol-icontrol-icontrol.md)




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| id|string|id can be valueKey or the displayKey of the list control metadata|

#### Returns [Control](view-model-control-basecontrol-icontrol-icontrol.md)

### getControlValueById


getControlValueById(id: string): string




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| id|string|id can be valueKey or the displayKey of the list control metadata|

#### Returns string

### getRowHeader


getRowHeader(): [Control](view-model-control-basecontrol-icontrol-icontrol.md)



#### Returns [Control](view-model-control-basecontrol-icontrol-icontrol.md)

### getRowId


getRowId(): string



#### Returns string

### hasImageField


hasImageField(): boolean

Returns true if the row has an image field.

#### Returns boolean



### isEntityCreatedNew


isEntityCreatedNew(): boolean



#### Returns boolean

### isEntityDeleted


isEntityDeleted(): boolean



#### Returns boolean

### isEntityModified


isEntityModified(): boolean



#### Returns boolean

### isEntitySyncPending


isEntitySyncPending(): boolean



#### Returns boolean

### select


select(): any



#### Returns any

