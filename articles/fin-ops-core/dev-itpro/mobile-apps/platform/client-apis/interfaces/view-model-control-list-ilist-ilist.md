---
title: List type
description: Learn about the list control type, which contains any number of rows and contains the DefaultSearchColumn, container, emptyListMessage, and other properties.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 12/31/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.custom: 
  - bap-template
---

# List type

[!include [banner](../../../../includes/banner.md)]
[!include [mobile app deprecated](../../../../includes/mobile-app-deprecation-banner.md)]

List control type.
A list is a control that contains any numbers of rows.
Each row follows a template for the layout of any number of controls.
Lists come in two styles: simple and card.

### Hierarchy

[ContainerControl](view-model-control-container-icontainercontrol-icontainercontrol.md) <br>&nbsp;&nbsp;&nbsp;└─ List <br>

## Index

### Properties

* [$accessibility](view-model-control-list-ilist-ilist.md#accessibility)
* [DefaultSearchColumn](view-model-control-list-ilist-ilist.md#defaultsearchcolumn)
* [container](view-model-control-list-ilist-ilist.md#container)
* [emptyListMessage](view-model-control-list-ilist-ilist.md#emptylistmessage)
* [enableMultiSelect](view-model-control-list-ilist-ilist.md#enablemultiselect)
* [generic](view-model-control-list-ilist-ilist.md#generic)
* [getDataSource](view-model-control-list-ilist-ilist.md#getdatasource)
* [hidden](view-model-control-list-ilist-ilist.md#hidden)
* [hideEmptyListMessage](view-model-control-list-ilist-ilist.md#hideemptylistmessage)
* [imageFields](view-model-control-list-ilist-ilist.md#imagefields)
* [performingRemoteSearch](view-model-control-list-ilist-ilist.md#performingremotesearch)
* [searchQuery](view-model-control-list-ilist-ilist.md#searchquery)

### Methods

* [allowsNavigation](view-model-control-list-ilist-ilist.md#allowsnavigation)
* [applyDesign](view-model-control-list-ilist-ilist.md#applydesign)
* [applySearch](view-model-control-list-ilist-ilist.md#applysearch)
* [canPerformRemoteSearch](view-model-control-list-ilist-ilist.md#canperformremotesearch)
* [clearSearch](view-model-control-list-ilist-ilist.md#clearsearch)
* [dataContext](view-model-control-list-ilist-ilist.md#datacontext)
* [getColumnLabel](view-model-control-list-ilist-ilist.md#getcolumnlabel)
* [getControl](view-model-control-list-ilist-ilist.md#getcontrol)
* [getControlById](view-model-control-list-ilist-ilist.md#getcontrolbyid)
* [getControlMetadata](view-model-control-list-ilist-ilist.md#getcontrolmetadata)
* [getControlMetadataById](view-model-control-list-ilist-ilist.md#getcontrolmetadatabyid)
* [getData](view-model-control-list-ilist-ilist.md#getdata)
* [getDesign](view-model-control-list-ilist-ilist.md#getdesign)
* [getListData](view-model-control-list-ilist-ilist.md#getlistdata)
* [getRenderedRows](view-model-control-list-ilist-ilist.md#getrenderedrows)
* [getRowNavigation](view-model-control-list-ilist-ilist.md#getrownavigation)
* [getRowSelectionCount](view-model-control-list-ilist-ilist.md#getrowselectioncount)
* [getRowSelections](view-model-control-list-ilist-ilist.md#getrowselections)
* [getRowTracking](view-model-control-list-ilist-ilist.md#getrowtracking)
* [getSearchColumn](view-model-control-list-ilist-ilist.md#getsearchcolumn)
* [getSearchColumnLabel](view-model-control-list-ilist-ilist.md#getsearchcolumnlabel)
* [getSearchableColumns](view-model-control-list-ilist-ilist.md#getsearchablecolumns)
* [hideSearchBar](view-model-control-list-ilist-ilist.md#hidesearchbar)
* [isEditable](view-model-control-list-ilist-ilist.md#iseditable)
* [loadMetaData](view-model-control-list-ilist-ilist.md#loadmetadata)
* [loadMore](view-model-control-list-ilist-ilist.md#loadmore)
* [metadata](view-model-control-list-ilist-ilist.md#metadata)
* [parent](view-model-control-list-ilist-ilist.md#parent)
* [performRemoteSearch](view-model-control-list-ilist-ilist.md#performremotesearch)
* [root](view-model-control-list-ilist-ilist.md#root)
* [selectSearchColumn](view-model-control-list-ilist-ilist.md#selectsearchcolumn)
* [setRowSections](view-model-control-list-ilist-ilist.md#setrowsections)

### Events

* [onRowCreate](view-model-control-list-ilist-ilist.md#onrowcreate)
* [onRowSelect](view-model-control-list-ilist-ilist.md#onrowselect)

## Properties

### $accessibility

$accessibility: any




### DefaultSearchColumn

DefaultSearchColumn: string




### container

container: boolean

True if the control is a container.

> Inherited from [ContainerControl](view-model-control-container-icontainercontrol-icontainercontrol.md).[container](view-model-control-container-icontainercontrol-icontainercontrol.md#container)
> 
> Overrides [Control](view-model-control-basecontrol-icontrol-icontrol.md).[container](view-model-control-basecontrol-icontrol-icontrol.md#container)


### emptyListMessage

emptyListMessage: string

Settable property to override default empty list message.


### enableMultiSelect

enableMultiSelect: boolean




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


### hideEmptyListMessage

hideEmptyListMessage: boolean

If true, no message is shown if the list is empty.
To set this property, update the corresponding metadata property via configureControl.


### imageFields

imageFields: any [ ]




### performingRemoteSearch

performingRemoteSearch: boolean




### searchQuery

searchQuery: [value: string]: any




## Methods

### allowsNavigation


allowsNavigation(): boolean



#### Returns boolean

### applyDesign


applyDesign(IDesign: [ListDesign](view-model-control-list-ilist-ilistdesign.md)): void

Applies given design to the design on the control.
If a design already exists, the prototype chain of the design will be preserved.

> Overrides [Control](view-model-control-basecontrol-icontrol-icontrol.md).[applyDesign](view-model-control-basecontrol-icontrol-icontrol.md#applydesign)


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| IDesign|[ListDesign](view-model-control-list-ilist-ilistdesign.md)|object containing design properties as keys|

#### Returns void

### applySearch


applySearch(): void



#### Returns void

### canPerformRemoteSearch


canPerformRemoteSearch(): boolean



#### Returns boolean

### clearSearch


clearSearch(): void



#### Returns void

### dataContext


dataContext(): any



> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[dataContext](view-model-control-basecontrol-icontrol-icontrol.md#datacontext)

#### Returns any

### getColumnLabel


getColumnLabel(id: string): string




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| id|string||

#### Returns string

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



### getControlMetadata


getControlMetadata(controlName: string): [Control](view-model-control-basecontrol-icontrol-icontrol.md)




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| controlName|string||

#### Returns [Control](view-model-control-basecontrol-icontrol-icontrol.md)

### getControlMetadataById


getControlMetadataById(id: string): [Control](view-model-control-basecontrol-icontrol-icontrol.md)




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| id|string||

#### Returns [Control](view-model-control-basecontrol-icontrol-icontrol.md)

### getData


getData(): any [ ]



#### Returns any [ ]

### getDesign


getDesign(): [Design](view-model-ipage-idesign.md)

Returns the design object of this control.

> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[getDesign](view-model-control-basecontrol-icontrol-icontrol.md#getdesign)

#### Returns [Design](view-model-ipage-idesign.md)



### getListData


getListData(): any



#### Returns any

### getRenderedRows


getRenderedRows(): [Row](view-model-control-list-ilist-irow.md) [ ]



#### Returns [Row](view-model-control-list-ilist-irow.md) [ ]

### getRowNavigation


getRowNavigation(row: [Row](view-model-control-list-ilist-irow.md)): Promise &lt;any&gt; &#124; any




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| row|[Row](view-model-control-list-ilist-irow.md)||

#### Returns Promise &lt;any&gt; &#124; any

### getRowSelectionCount


getRowSelectionCount(): number



#### Returns number

### getRowSelections


getRowSelections(): string [ ]



#### Returns string [ ]

### getRowTracking


getRowTracking(row: any, index: string): string




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| row|any||
| index|string||

#### Returns string

### getSearchColumn


getSearchColumn(): string



#### Returns string

### getSearchColumnLabel


getSearchColumnLabel(): string



#### Returns string

### getSearchableColumns


getSearchableColumns(): any [ ]



#### Returns any [ ]

### hideSearchBar


hideSearchBar(): boolean



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



### loadMetaData


loadMetaData(): void



#### Returns void

### loadMore


loadMore(): void



#### Returns void

### metadata


metadata(): [ListMetadata](view-model-control-list-ilist-ilistmetadata.md)

Returns the metadata object of this control.

> Overrides [ContainerControl](view-model-control-container-icontainercontrol-icontainercontrol.md).[metadata](view-model-control-container-icontainercontrol-icontainercontrol.md#metadata)

#### Returns [ListMetadata](view-model-control-list-ilist-ilistmetadata.md)



### parent


parent(): [Control](view-model-control-basecontrol-icontrol-icontrol.md) &#124; [Page](view-model-ipage-ipage.md)

Returns the parent (control or page) of this control.

> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[parent](view-model-control-basecontrol-icontrol-icontrol.md#parent)

#### Returns [Control](view-model-control-basecontrol-icontrol-icontrol.md) &#124; [Page](view-model-ipage-ipage.md)



### performRemoteSearch


performRemoteSearch(): void



#### Returns void

### root


root(): [Page](view-model-ipage-ipage.md)

Returns the root form instance (page) of this control.

> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[root](view-model-control-basecontrol-icontrol-icontrol.md#root)

#### Returns [Page](view-model-ipage-ipage.md)



### selectSearchColumn


selectSearchColumn(column: string): void




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| column|string||

#### Returns void

### setRowSections


setRowSections(selections: string [ ]): void




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| selections|string [ ]||

#### Returns void

## Events

### onRowCreate

onRowCreate: [EventHook](event-ievent-ieventhook.md) &lt;[Row](view-model-control-list-ilist-irow.md)&gt;




### onRowSelect

onRowSelect: [EventHook](event-ievent-ieventhook.md) &lt;[Row](view-model-control-list-ilist-irow.md)&gt;






[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]
