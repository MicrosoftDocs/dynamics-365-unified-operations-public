---
# required metadata
title: PageLink
description: Pagelink control type. A pagelink is a control that navigates to another page.
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

# PageLink Type
Pagelink control type. A pagelink is a control that navigates to another page.

### Hierarchy

[Control](view-model-control-basecontrol-icontrol-icontrol.md) <br>&nbsp;&nbsp;&nbsp;└─ PageLink <br>

## Index

### Properties

* [container](view-model-control-pagelink-ipagelink-ipagelink.md#container)
* [generic](view-model-control-pagelink-ipagelink-ipagelink.md#generic)
* [getDataSource](view-model-control-pagelink-ipagelink-ipagelink.md#getdatasource)
* [hidden](view-model-control-pagelink-ipagelink-ipagelink.md#hidden)

### Methods

* [allowsNavigation](view-model-control-pagelink-ipagelink-ipagelink.md#allowsnavigation)
* [applyDesign](view-model-control-pagelink-ipagelink-ipagelink.md#applydesign)
* [dataContext](view-model-control-pagelink-ipagelink-ipagelink.md#datacontext)
* [getCount](view-model-control-pagelink-ipagelink-ipagelink.md#getcount)
* [getDesign](view-model-control-pagelink-ipagelink-ipagelink.md#getdesign)
* [getNavigationHandler](view-model-control-pagelink-ipagelink-ipagelink.md#getnavigationhandler)
* [isEditable](view-model-control-pagelink-ipagelink-ipagelink.md#iseditable)
* [metadata](view-model-control-pagelink-ipagelink-ipagelink.md#metadata)
* [parent](view-model-control-pagelink-ipagelink-ipagelink.md#parent)
* [root](view-model-control-pagelink-ipagelink-ipagelink.md#root)
* [showCount](view-model-control-pagelink-ipagelink-ipagelink.md#showcount)

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

### allowsNavigation


allowsNavigation(): boolean



#### Returns boolean

### applyDesign


applyDesign(design: [PageLinkDesign](view-model-control-pagelink-ipagelink-ipagelinkdesign.md)): void

Applies given design to the design on the control.
If a design already exists, the prototype chain of the design will be preserved.

> Overrides [Control](view-model-control-basecontrol-icontrol-icontrol.md).[applyDesign](view-model-control-basecontrol-icontrol-icontrol.md#applydesign)


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| design|[PageLinkDesign](view-model-control-pagelink-ipagelink-ipagelinkdesign.md)|object containing design properties as keys|

#### Returns void

### dataContext


dataContext(): any



> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[dataContext](view-model-control-basecontrol-icontrol-icontrol.md#datacontext)

#### Returns any

### getCount


getCount(): number &#124; string



#### Returns number &#124; string

### getDesign


getDesign(): [Design](view-model-ipage-idesign.md)

Returns the design object of this control.

> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[getDesign](view-model-control-basecontrol-icontrol-icontrol.md#getdesign)

#### Returns [Design](view-model-ipage-idesign.md)



### getNavigationHandler


getNavigationHandler(): [NavigationArgs](view-model-ipage-inavigationargs.md)



#### Returns [NavigationArgs](view-model-ipage-inavigationargs.md)

### isEditable


isEditable(): boolean

Boolean indicating if the control is editable.
Returns false when either the control or it's parent is not editable.
Returns true when both the control and it's parent are editable.
Returns true when either the control or it's parent is editable and the other is undefined.
Returns undefined if both the control's edit-ability and it's parent's edit-ability is undefined.

> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[isEditable](view-model-control-basecontrol-icontrol-icontrol.md#iseditable)

#### Returns boolean



### metadata


metadata(): [PageLinkMetadata](view-model-control-pagelink-ipagelink-ipagelinkmetadata.md)

Returns the metadata object of this control.

> Overrides [Control](view-model-control-basecontrol-icontrol-icontrol.md).[metadata](view-model-control-basecontrol-icontrol-icontrol.md#metadata)

#### Returns [PageLinkMetadata](view-model-control-pagelink-ipagelink-ipagelinkmetadata.md)



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



### showCount


showCount(): boolean



#### Returns boolean

