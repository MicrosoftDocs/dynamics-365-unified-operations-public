---
title: ImageMetadata type
description: Learn about the ImageMetadata type, which includes the BaseUrl, BoundEntity, BoundField, Description, Editable, ExtType, Height, HelpText and other properties.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 12/31/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.custom: 
  - bap-template
---

# ImageMetadata type

[!include [banner](../../../../includes/banner.md)]
[!include [mobile app deprecated](../../../../includes/mobile-app-deprecation-banner.md)]

Image metadata type.

### Hierarchy

[ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md) <br>&nbsp;&nbsp;&nbsp;└─ ImageMetadata <br>

## Index

### Properties

* [BaseUrl](view-model-control-image-iimage-iimagemetadata.md#baseurl)
* [BoundEntity](view-model-control-image-iimage-iimagemetadata.md#boundentity)
* [BoundField](view-model-control-image-iimage-iimagemetadata.md#boundfield)
* [Description](view-model-control-image-iimage-iimagemetadata.md#description)
* [Editable](view-model-control-image-iimage-iimagemetadata.md#editable)
* [ExtType](view-model-control-image-iimage-iimagemetadata.md#exttype)
* [Height](view-model-control-image-iimage-iimagemetadata.md#height)
* [HelpText](view-model-control-image-iimage-iimagemetadata.md#helptext)
* [Hidden](view-model-control-image-iimage-iimagemetadata.md#hidden)
* [Id](view-model-control-image-iimage-iimagemetadata.md#id)
* [ImageStyle](view-model-control-image-iimage-iimagemetadata.md#imagestyle)
* [Label](view-model-control-image-iimage-iimagemetadata.md#label)
* [Name](view-model-control-image-iimage-iimagemetadata.md#name)
* [Order](view-model-control-image-iimage-iimagemetadata.md#order)
* [Type](view-model-control-image-iimage-iimagemetadata.md#type)
* [Width](view-model-control-image-iimage-iimagemetadata.md#width)

## Properties

### BaseUrl

BaseUrl: string (optional) 

Base URL for AOTResource type image.


### BoundEntity

BoundEntity: string (optional) 

The entity to which the control is bound.

> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[BoundEntity](view-model-control-basecontrol-icontrol-icontrolmetadata.md#boundentity)


### BoundField

BoundField: string (optional) 



> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[BoundField](view-model-control-basecontrol-icontrol-icontrolmetadata.md#boundfield)


### Description

Description: string (optional) 

Description of the control.

> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Description](view-model-control-basecontrol-icontrol-icontrolmetadata.md#description)


### Editable

Editable: boolean (optional) 

Boolean indicating if the control is editable.
False when either the control or its parent is not editable.
True when both the control and its parent are editable.
True when either the control or its parent is editable and the other is undefined.
Undefined if both the control's edit-ability and its parent's edit-ability is undefined.

> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Editable](view-model-control-basecontrol-icontrol-icontrolmetadata.md#editable)


### ExtType

ExtType: [ControlType](../modules/view-model-control-basecontrol-icontrol.md#controltype) (optional) 

The extended control type. For example, a control of type Input might have an extended type of Barcode.

> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[ExtType](view-model-control-basecontrol-icontrol-icontrolmetadata.md#exttype)


### Height

Height: number (optional) 

The relative vertical size of the image.
Sizes are about equivalent to CSS em sizes.


### HelpText

HelpText: string (optional) 

The keyboard shortcut for a command. For example, "(Shift+F5)"

> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[HelpText](view-model-control-basecontrol-icontrol-icontrolmetadata.md#helptext)


### Hidden

Hidden: boolean (optional) 

Boolean indicating if the control is hidden or not.

> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Hidden](view-model-control-basecontrol-icontrol-icontrolmetadata.md#hidden)


### Id

Id: string (optional) 

Identification string for a control.

> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Id](view-model-control-basecontrol-icontrol-icontrolmetadata.md#id)


### ImageStyle

ImageStyle: [ImageStyleType](../modules/view-model-control-image-iimage.md#imagestyletype) (optional) 

The style of the image.


### Label

Label: string (optional) 

Label for a control. For example, a control representing a person's first name might have a label "First Name".

> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Label](view-model-control-basecontrol-icontrol-icontrolmetadata.md#label)


### Name

Name: string (optional) 

Name of a control.

> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Name](view-model-control-basecontrol-icontrol-icontrolmetadata.md#name)


### Order

Order: number (optional) 

Number indicating the order in which a control will appear on a page.

> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Order](view-model-control-basecontrol-icontrol-icontrolmetadata.md#order)


### Type

Type: [ControlType](../modules/view-model-control-basecontrol-icontrol.md#controltype) (optional) 

String indicating the control type.

> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Type](view-model-control-basecontrol-icontrol-icontrolmetadata.md#type)


### Width

Width: number (optional) 

The relative horizontal size of the image.
Sizes are about equivalent to CSS em sizes.




[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]
