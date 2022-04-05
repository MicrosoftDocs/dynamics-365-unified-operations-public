---
title: PartMetadata type
description: Part metadata type.
author: tonyafehr
ms.date: 08/01/2017
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: tfehr
---

# PartMetadata type

[!include [banner](../../../../includes/banner.md)]

Part metadata type.

### Hierarchy

[ContainerControlMetadata](view-model-control-container-icontainercontrol-icontainercontrolmetadata.md) <br>&nbsp;&nbsp;&nbsp;└─ PartMetadata <br>

## Index

### Properties

* [BoundEntity](view-model-control-part-ipart-ipartmetadata.md#boundentity)
* [BoundField](view-model-control-part-ipart-ipartmetadata.md#boundfield)
* [Description](view-model-control-part-ipart-ipartmetadata.md#description)
* [Design](view-model-control-part-ipart-ipartmetadata.md#design)
* [Editable](view-model-control-part-ipart-ipartmetadata.md#editable)
* [ExtType](view-model-control-part-ipart-ipartmetadata.md#exttype)
* [HelpText](view-model-control-part-ipart-ipartmetadata.md#helptext)
* [Hidden](view-model-control-part-ipart-ipartmetadata.md#hidden)
* [Id](view-model-control-part-ipart-ipartmetadata.md#id)
* [Label](view-model-control-part-ipart-ipartmetadata.md#label)
* [Name](view-model-control-part-ipart-ipartmetadata.md#name)
* [Order](view-model-control-part-ipart-ipartmetadata.md#order)
* [Target](view-model-control-part-ipart-ipartmetadata.md#target)
* [Type](view-model-control-part-ipart-ipartmetadata.md#type)

## Properties

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


### Design

Design: [PartDesign](view-model-control-part-ipart-ipartdesign.md) (optional) 

Design for the target page.


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


### Target

Target: [PageTarget](view-model-ipage-ipagetarget.md) (optional) 

Target page of the part.


### Type

Type: [ControlType](../modules/view-model-control-basecontrol-icontrol.md#controltype) (optional) 

String indicating the control type.

> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Type](view-model-control-basecontrol-icontrol-icontrolmetadata.md#type)




[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]