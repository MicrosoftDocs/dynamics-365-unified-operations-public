---
title: ControlMetadata type
description: Interface for the metadata of a control. Overriding control metadata can modify a controls&#x27; look and behavior.
author: tonyafehr
ms.date: 08/01/2017
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: tfehr
---

# ControlMetadata type

[!include [banner](../../../../includes/banner.md)]

Interface for the metadata of a control. Overriding control metadata can modify a controls' look and behavior.
Properties that can be modified vary by control but every control will have the base properties listed here.

### Hierarchy

ControlMetadata <br>&nbsp;&nbsp;&nbsp;└─ [PageLinkMetadata](view-model-control-pagelink-ipagelink-ipagelinkmetadata.md) <br>&nbsp;&nbsp;&nbsp;└─ [ContainerControlMetadata](view-model-control-container-icontainercontrol-icontainercontrolmetadata.md) <br>&nbsp;&nbsp;&nbsp;└─ [InputControlMetadata](view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md) <br>&nbsp;&nbsp;&nbsp;└─ [ImageMetadata](view-model-control-image-iimage-iimagemetadata.md) <br>

## Index

### Properties

* [BoundEntity](view-model-control-basecontrol-icontrol-icontrolmetadata.md#boundentity)
* [BoundField](view-model-control-basecontrol-icontrol-icontrolmetadata.md#boundfield)
* [Description](view-model-control-basecontrol-icontrol-icontrolmetadata.md#description)
* [Editable](view-model-control-basecontrol-icontrol-icontrolmetadata.md#editable)
* [ExtType](view-model-control-basecontrol-icontrol-icontrolmetadata.md#exttype)
* [HelpText](view-model-control-basecontrol-icontrol-icontrolmetadata.md#helptext)
* [Hidden](view-model-control-basecontrol-icontrol-icontrolmetadata.md#hidden)
* [Id](view-model-control-basecontrol-icontrol-icontrolmetadata.md#id)
* [Label](view-model-control-basecontrol-icontrol-icontrolmetadata.md#label)
* [Name](view-model-control-basecontrol-icontrol-icontrolmetadata.md#name)
* [Order](view-model-control-basecontrol-icontrol-icontrolmetadata.md#order)
* [Type](view-model-control-basecontrol-icontrol-icontrolmetadata.md#type)

## Properties

### BoundEntity

BoundEntity: string (optional) 

The entity to which the control is bound.


### BoundField

BoundField: string (optional) 




### Description

Description: string (optional) 

Description of the control.


### Editable

Editable: boolean (optional) 

Boolean indicating if the control is editable.
False when either the control or its parent is not editable.
True when both the control and its parent are editable.
True when either the control or its parent is editable and the other is undefined.
Undefined if both the control's edit-ability and its parent's edit-ability is undefined.


### ExtType

ExtType: [ControlType](../modules/view-model-control-basecontrol-icontrol.md#controltype) (optional) 

The extended control type. For example, a control of type Input might have an extended type of Barcode.


### HelpText

HelpText: string (optional) 

The keyboard shortcut for a command. For example, "(Shift+F5)"


### Hidden

Hidden: boolean (optional) 

Boolean indicating if the control is hidden or not.


### Id

Id: string (optional) 

Identification string for a control.


### Label

Label: string (optional) 

Label for a control. For example, a control representing a person's first name might have a label "First Name".


### Name

Name: string (optional) 

Name of a control.


### Order

Order: number (optional) 

Number indicating the order in which a control will appear on a page.


### Type

Type: [ControlType](../modules/view-model-control-basecontrol-icontrol.md#controltype) (optional) 

String indicating the control type.




[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]