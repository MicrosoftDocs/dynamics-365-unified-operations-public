---
# required metadata
title: Image
description: Image control interface for representing images in the mobile app. Images can be of any of the following types&amp;58 DataUri, Base64, URL, AOTResource, or Symbol.
author: shadykdc
manager: AnnBe
ms.date: 
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

# Image Type
Image control interface for representing images in the mobile app.
Images can be of any of the following types: DataUri, Base64, URL, AOTResource, or Symbol.

### Hierarchy

[Control](view-model-control-basecontrol-icontrol-icontrol.md) <br>&nbsp;&nbsp;&nbsp;└─ Image <br>

## Index

### Properties

* [imageSource](view-model-control-image-iimage-iimage.md#imagesource)
* [imageView](view-model-control-image-iimage-iimage.md#imageview)
* [placeholderClass](view-model-control-image-iimage-iimage.md#placeholderclass)
* [symbol](view-model-control-image-iimage-iimage.md#symbol)

### Methods

* [applyDesign](view-model-control-image-iimage-iimage.md#applydesign)
* [getDesign](view-model-control-image-iimage-iimage.md#getdesign)
* [isEditable](view-model-control-image-iimage-iimage.md#iseditable)
* [metadata](view-model-control-image-iimage-iimage.md#metadata)
* [parent](view-model-control-image-iimage-iimage.md#parent)
* [root](view-model-control-image-iimage-iimage.md#root)

## Properties

### imageSource

imageSource: string

Defines the imageSource.


### imageView

imageView: string

Dictates the style of the image.


### placeholderClass

placeholderClass: string




### symbol

symbol: string

Defines the symbol if the image is of type symbol.


## Methods

### applyDesign


applyDesign(design: [ImageDesign](view-model-control-image-iimage-iimagedesign.md)): void

Applies given design to the design on the control.
If a design already exists, the prototype chain of the design will be preserved.

> Overrides [Control](view-model-control-basecontrol-icontrol-icontrol.md).[applyDesign](view-model-control-basecontrol-icontrol-icontrol.md#applydesign)


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| design|[ImageDesign](view-model-control-image-iimage-iimagedesign.md)|object containing design properties as keys|

#### Returns void

### getDesign


getDesign(): [Design](view-model-ipage-idesign.md)

Returns the design object of this control.

> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[getDesign](view-model-control-basecontrol-icontrol-icontrol.md#getdesign)

#### Returns [Design](view-model-ipage-idesign.md)



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


metadata(): [ImageMetadata](view-model-control-image-iimage-iimagemetadata.md)

Returns the metadata object of this control.

> Overrides [Control](view-model-control-basecontrol-icontrol-icontrol.md).[metadata](view-model-control-basecontrol-icontrol-icontrol.md#metadata)

#### Returns [ImageMetadata](view-model-control-image-iimage-iimagemetadata.md)



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



