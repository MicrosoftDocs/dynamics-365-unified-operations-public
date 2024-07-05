---
title: Control module
description: Learn about the Control module, which includes the Control and ControlMetadata types, and the ControlType type alias.
author: jasongre
ms.author: jasongre
ms.topic: article
ms.date: 05/26/2022
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
---

# Control module

[!include [banner](../../../../includes/banner.md)]
[!include [mobile app deprecated](../../../../includes/mobile-app-deprecation-banner.md)]

Controls are what make up the content of a page.

## Index

### Types

* [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md)
* [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md)

### Type aliases

* [ControlType](view-model-control-basecontrol-icontrol.md#controltype)

## Types


### Control

#### Hierarchy

Control <br>&nbsp;&nbsp;&nbsp;└─ [PageLink](../interfaces/view-model-control-pagelink-ipagelink-ipagelink.md) <br>&nbsp;&nbsp;&nbsp;└─ [ContainerControl](../interfaces/view-model-control-container-icontainercontrol-icontainercontrol.md) <br>&nbsp;&nbsp;&nbsp;└─ [InputControl](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontrol.md) <br>&nbsp;&nbsp;&nbsp;└─ [Image](../interfaces/view-model-control-image-iimage-iimage.md) <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [container](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#container) |container: boolean (optional)  <br>|True if the control is a container.<br>  |
| [generic](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#generic) |generic: boolean (optional)  <br>|  |
| [getDataSource](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#getdatasource) |getDataSource: function(): any <br>|  |
| [hidden](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#hidden) |hidden: boolean <br>|True if the control is hidden.<br>  |

#### Methods

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [applyDesign](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#applydesign) |applyDesign(design: [Design](../interfaces/view-model-ipage-idesign.md)): void|Applies given design to the design on the control.<br>  |
| [dataContext](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#datacontext) |dataContext(): any|  |
| [getDesign](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#getdesign) |getDesign(): [Design](../interfaces/view-model-ipage-idesign.md)|Returns the design object of this control.<br>  |
| [isEditable](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#iseditable) |isEditable(): boolean|Boolean indicating if the control is editable.<br>  |
| [metadata](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#metadata) |metadata(): [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md)|Returns the metadata object of this control.<br>  |
| [parent](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#parent) |parent(): [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md) &#124; [Page](../interfaces/view-model-ipage-ipage.md)|Returns the parent (control or page) of this control.<br>  |
| [root](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#root) |root(): [Page](../interfaces/view-model-ipage-ipage.md)|Returns the root form instance (page) of this control.<br>  |


### ControlMetadata

#### Hierarchy

ControlMetadata <br>&nbsp;&nbsp;&nbsp;└─ [PageLinkMetadata](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkmetadata.md) <br>&nbsp;&nbsp;&nbsp;└─ [ContainerControlMetadata](../interfaces/view-model-control-container-icontainercontrol-icontainercontrolmetadata.md) <br>&nbsp;&nbsp;&nbsp;└─ [InputControlMetadata](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md) <br>&nbsp;&nbsp;&nbsp;└─ [ImageMetadata](../interfaces/view-model-control-image-iimage-iimagemetadata.md) <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [BoundEntity](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#boundentity) |BoundEntity: string (optional)  <br>|The entity to which the control is bound.<br>  |
| [BoundField](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#boundfield) |BoundField: string (optional)  <br>|  |
| [Description](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#description) |Description: string (optional)  <br>|Description of the control.<br>  |
| [Editable](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#editable) |Editable: boolean (optional)  <br>|Boolean indicating if the control is editable.<br>  |
| [ExtType](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#exttype) |ExtType: [ControlType](view-model-control-basecontrol-icontrol.md#controltype) (optional)  <br>|The extended control type. For example, a control of type Input might have an extended type of Barcode.<br>  |
| [HelpText](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#helptext) |HelpText: string (optional)  <br>|The keyboard shortcut for a command. For example, "(Shift+F5)"<br>  |
| [Hidden](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#hidden) |Hidden: boolean (optional)  <br>|Boolean indicating if the control is hidden or not.<br>  |
| [Id](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#id) |Id: string (optional)  <br>|Identification string for a control.<br>  |
| [Label](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#label) |Label: string (optional)  <br>|Label for a control. For example, a control representing a person's first name might have a label "First Name".<br>  |
| [Name](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#name) |Name: string (optional)  <br>|Name of a control.<br>  |
| [Order](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#order) |Order: number (optional)  <br>|Number indicating the order in which a control will appear on a page.<br>  |
| [Type](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#type) |Type: [ControlType](view-model-control-basecontrol-icontrol.md#controltype) (optional)  <br>|String indicating the control type.<br>  |

## Type aliases


### ControlType
ControlType: "FileUpload" &#124; "Barcode" &#124; "Input" &#124; "MultilineInput" &#124; "Navigation" &#124; "Integer" &#124; "Int64" &#124; "Date" &#124; "DateTime" &#124; "ComboBox" &#124; "Real" &#124; "List" &#124; "Lookup" &#124; "MultiLookup" &#124; "Navigation" &#124; "Image" &#124; "Group" &#124; "Part" &#124; "Calendar" &#124; "HyperLink" &#124; "Timer"


Controls must be assigned any of the types listed in ControlType.



[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]
