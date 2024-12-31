---
title: ListMetadata type
description: Learn about the ListMetadata type, which includes the BoundEntity, BoundField, Children, Description, DetailsPageAppId, and other properties.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 12/31/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.custom: 
  - bap-template
---

# ListMetadata type

[!include [banner](../../../../includes/banner.md)]
[!include [mobile app deprecated](../../../../includes/mobile-app-deprecation-banner.md)]

Metadata for list control.

### Hierarchy

[ContainerControlMetadata](view-model-control-container-icontainercontrol-icontainercontrolmetadata.md) <br>&nbsp;&nbsp;&nbsp;└─ ListMetadata <br>

## Index

### Properties

* [BoundEntity](view-model-control-list-ilist-ilistmetadata.md#boundentity)
* [BoundField](view-model-control-list-ilist-ilistmetadata.md#boundfield)
* [Children](view-model-control-list-ilist-ilistmetadata.md#children)
* [Description](view-model-control-list-ilist-ilistmetadata.md#description)
* [DetailsPageAppId](view-model-control-list-ilist-ilistmetadata.md#detailspageappid)
* [DetailsPageId](view-model-control-list-ilist-ilistmetadata.md#detailspageid)
* [Editable](view-model-control-list-ilist-ilistmetadata.md#editable)
* [EmptyListMessage](view-model-control-list-ilist-ilistmetadata.md#emptylistmessage)
* [ExtType](view-model-control-list-ilist-ilistmetadata.md#exttype)
* [HelpText](view-model-control-list-ilist-ilistmetadata.md#helptext)
* [Hidden](view-model-control-list-ilist-ilistmetadata.md#hidden)
* [HideEmptyListMessage](view-model-control-list-ilist-ilistmetadata.md#hideemptylistmessage)
* [HideSearchBar](view-model-control-list-ilist-ilistmetadata.md#hidesearchbar)
* [Id](view-model-control-list-ilist-ilistmetadata.md#id)
* [InfiniteScroll](view-model-control-list-ilist-ilistmetadata.md#infinitescroll)
* [InfiniteScrollPageSize](view-model-control-list-ilist-ilistmetadata.md#infinitescrollpagesize)
* [Label](view-model-control-list-ilist-ilistmetadata.md#label)
* [ListStyle](view-model-control-list-ilist-ilistmetadata.md#liststyle)
* [MultiSelect](view-model-control-list-ilist-ilistmetadata.md#multiselect)
* [Name](view-model-control-list-ilist-ilistmetadata.md#name)
* [NonEntityProjection](view-model-control-list-ilist-ilistmetadata.md#nonentityprojection)
* [Order](view-model-control-list-ilist-ilistmetadata.md#order)
* [Type](view-model-control-list-ilist-ilistmetadata.md#type)

### Methods

* [navigationHandler](view-model-control-list-ilist-ilistmetadata.md#navigationhandler)

### Events

* [OnNavigate](view-model-control-list-ilist-ilistmetadata.md#onnavigate)
* [OnRowSelect](view-model-control-list-ilist-ilistmetadata.md#onrowselect)

## Properties

### BoundEntity

BoundEntity: string (optional) 

The entity to which the control is bound.

> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[BoundEntity](view-model-control-basecontrol-icontrol-icontrolmetadata.md#boundentity)


### BoundField

BoundField: string (optional) 



> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[BoundField](view-model-control-basecontrol-icontrol-icontrolmetadata.md#boundfield)


### Children

Children: [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md) \[ \] (optional) 

List of metadata for controls that will appear in each row of the list.


### Description

Description: string (optional) 

Description of the control.

> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Description](view-model-control-basecontrol-icontrol-icontrolmetadata.md#description)


### DetailsPageAppId

DetailsPageAppId: string (optional) 

App ID of the page that each row in the list will navigate to.


### DetailsPageId

DetailsPageId: string (optional) 

The ID of the page to which each row will navigate.


### Editable

Editable: boolean (optional) 

Boolean indicating if the control is editable.
False when either the control or its parent is not editable.
True when both the control and its parent are editable.
True when either the control or its parent is editable and the other is undefined.
Undefined if both the control's edit-ability and its parent's edit-ability is undefined.

> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Editable](view-model-control-basecontrol-icontrol-icontrolmetadata.md#editable)


### EmptyListMessage

EmptyListMessage: string (optional) 

If set, overrides the default message for empty lists.


### ExtType

ExtType: [ControlType](../modules/view-model-control-basecontrol-icontrol.md#controltype) (optional) 

The extended control type. For example, a control of type Input might have an extended type of Barcode.

> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[ExtType](view-model-control-basecontrol-icontrol-icontrolmetadata.md#exttype)


### HelpText

HelpText: string (optional) 

The keyboard shortcut for a command. For example, "(Shift+F5)"

> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[HelpText](view-model-control-basecontrol-icontrol-icontrolmetadata.md#helptext)


### Hidden

Hidden: boolean (optional) 

Boolean indicating if the control is hidden or not.

> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Hidden](view-model-control-basecontrol-icontrol-icontrolmetadata.md#hidden)


### HideEmptyListMessage

HideEmptyListMessage: boolean (optional) 

If true, the empty list message will be hidden.


### HideSearchBar

HideSearchBar: boolean (optional) 

If true, the search bar will be hidden.


### Id

Id: string (optional) 

Identification string for a control.

> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Id](view-model-control-basecontrol-icontrol-icontrolmetadata.md#id)


### InfiniteScroll

InfiniteScroll: boolean (optional) 

If set to true then the list will allow infinite scroll.


### InfiniteScrollPageSize

InfiniteScrollPageSize: number (optional) 

Number of rows to load initially and the number of rows to load after the user reaches the end of the currently displayed rows.


### Label

Label: string (optional) 

Label for a control. For example, a control representing a person's first name might have a label "First Name".

> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Label](view-model-control-basecontrol-icontrol-icontrolmetadata.md#label)


### ListStyle

ListStyle: string (optional) 

Dictates the list template type.
Options:
* "Simple": simple style<br>
* "Card": card style


### MultiSelect

MultiSelect: boolean (optional) 

If true, then the list will be a multi-select list.


### Name

Name: string (optional) 

Name of a control.

> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Name](view-model-control-basecontrol-icontrol-icontrolmetadata.md#name)


### NonEntityProjection

NonEntityProjection: boolean (optional) 




### Order

Order: number (optional) 

Number indicating the order in which a control will appear on a page.

> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Order](view-model-control-basecontrol-icontrol-icontrolmetadata.md#order)


### Type

Type: [ControlType](../modules/view-model-control-basecontrol-icontrol.md#controltype) (optional) 

String indicating the control type.

> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Type](view-model-control-basecontrol-icontrol-icontrolmetadata.md#type)


## Methods

### navigationHandler
Optional 

navigationHandler(row: [Row](view-model-control-list-ilist-irow.md)): Promise &lt;any&gt; &#124; [NavigationArgs](view-model-ipage-inavigationargs.md)

A function that determines the navigation for a given row.


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| row|[Row](view-model-control-list-ilist-irow.md)|row to get navigation handler for.|

#### Returns Promise &lt;any&gt; &#124; [NavigationArgs](view-model-ipage-inavigationargs.md)



## Events

### OnNavigate

OnNavigate: function(navigation: [NavigationArgs](view-model-ipage-inavigationargs.md)): any (optional) 

An event that is triggered when a pagelink control is selected.


### OnRowSelect

OnRowSelect: function(row: [Row](view-model-control-list-ilist-irow.md)): void (optional) 

An event that is triggered when a row is selected.




[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]
