---
title: PageLinkMetadata type
description: Learn about the page link metadata type, which includes the BoundEntity, BoundField, Description, Editable, and other properties.
author: jasongre
ms.author: jasongre
ms.topic: article
ms.date: 05/24/2022
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
---

# PageLinkMetadata type

[!include [banner](../../../../includes/banner.md)]
[!include [mobile app deprecated](../../../../includes/mobile-app-deprecation-banner.md)]

Pagelink metadata type.

### Hierarchy

[ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md) <br>&nbsp;&nbsp;&nbsp;└─ PageLinkMetadata <br>

## Index

### Properties

* [BoundEntity](view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#boundentity)
* [BoundField](view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#boundfield)
* [Description](view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#description)
* [Editable](view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#editable)
* [ExcludeContext](view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#excludecontext)
* [ExtType](view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#exttype)
* [HelpText](view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#helptext)
* [Hidden](view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#hidden)
* [Icon](view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#icon)
* [IconSize](view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#iconsize)
* [Id](view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#id)
* [Label](view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#label)
* [Name](view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#name)
* [Navigation](view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#navigation)
* [Order](view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#order)
* [ShowCount](view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#showcount)
* [Style](view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#style)
* [Target](view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#target)
* [Type](view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#type)
* [UseDataContext](view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#usedatacontext)

### Events

* [OnNavigate](view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#onnavigate)

## Properties

### BoundEntity

BoundEntity: string (optional)

The entity to which the control is bound.

Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[BoundEntity](view-model-control-basecontrol-icontrol-icontrolmetadata.md#boundentity)

### BoundField

BoundField: string (optional)

Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[BoundField](view-model-control-basecontrol-icontrol-icontrolmetadata.md#boundfield)

### Description

Description: string (optional)

Description of the control.

Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Description](view-model-control-basecontrol-icontrol-icontrolmetadata.md#description)

### Editable

Editable: boolean (optional)

Boolean indicating if the control is editable.
False when either the control or its parent is not editable.
True when both the control and its parent are editable.
True when either the control or its parent is editable and the other is undefined.
Undefined if both the control's edit-ability and its parent's edit-ability is undefined.

Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Editable](view-model-control-basecontrol-icontrol-icontrolmetadata.md#editable)

### ExcludeContext

ExcludeContext: boolean (optional)

### ExtType

ExtType: [ControlType](../modules/view-model-control-basecontrol-icontrol.md#controltype) (optional)

The extended control type. For example, a control of type Input might have an extended type of Barcode.

Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[ExtType](view-model-control-basecontrol-icontrol-icontrolmetadata.md#exttype)

### HelpText

HelpText: string (optional)

The keyboard shortcut for a command. For example, "(Shift+F5)"

Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[HelpText](view-model-control-basecontrol-icontrol-icontrolmetadata.md#helptext)

### Hidden

Hidden: boolean (optional)

Boolean indicating if the control is hidden or not.

Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Hidden](view-model-control-basecontrol-icontrol-icontrolmetadata.md#hidden)

### Icon

Icon: string (optional)

Name of the icon that is displayed in the page link control.
Here is a [list of available icons](/dynamics/s-e/).

### IconSize

IconSize: number (optional)

Determines the size of the icon that is displayed in the page link control.

### Id

Id: string (optional)

Identification string for a control.

Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Id](view-model-control-basecontrol-icontrol-icontrolmetadata.md#id)

### Label

Label: string (optional)

Label for a control. For example, a control representing a person's first name might have a label "First Name".

Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Label](view-model-control-basecontrol-icontrol-icontrolmetadata.md#label)

### Name

Name: string (optional)

Name of a control.

Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Name](view-model-control-basecontrol-icontrol-icontrolmetadata.md#name)

### Navigation

Navigation: [NavigationArgs](view-model-ipage-inavigationargs.md) (optional)

Navigation object of the page link.

### Order

Order: number (optional)

Number indicating the order in which a control will appear on a page.

Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Order](view-model-control-basecontrol-icontrol-icontrolmetadata.md#order)

### ShowCount

ShowCount: boolean (optional)

If true, shows a count of the records present in the list on the target page.
This property is only suitable when the navigation target is a Page which contains on a List control.

### Style

Style: string (optional)

Determines the visual style of the page link control.
Options:
* "inline": takes up the full width its container, with the label in-line with the icon
* "button": takes up only as much width as needed by the label, with the label below the icon

### Target

Target: string (optional)

Name of the target action or page to navigate to when the page link is selected.

### Type

Type: [ControlType](../modules/view-model-control-basecontrol-icontrol.md#controltype) (optional)

String indicating the control type.

Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Type](view-model-control-basecontrol-icontrol-icontrolmetadata.md#type)

### UseDataContext

UseDataContext: boolean (optional)

## Events

### OnNavigate

OnNavigate: function(navigation: [NavigationArgs](view-model-ipage-inavigationargs.md) &#124; string): any (optional)

An event that is triggered when the navigation is triggered.



[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]
