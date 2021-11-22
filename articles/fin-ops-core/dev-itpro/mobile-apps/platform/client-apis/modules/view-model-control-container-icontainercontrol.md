---
title: Container module
description: A container control can contain any number of controls.
author: tonyafehr
ms.date: 08/01/2017
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: tfehr
---

# Container module (Client APIs)

[!include [banner](../../../../includes/banner.md)]

A container control can contain any number of controls.

## Index

### Types

* [ContainerControl](../interfaces/view-model-control-container-icontainercontrol-icontainercontrol.md)
* [ContainerControlDesign](../interfaces/view-model-control-container-icontainercontrol-icontainercontroldesign.md)
* [ContainerControlMetadata](../interfaces/view-model-control-container-icontainercontrol-icontainercontrolmetadata.md)

## Types


### ContainerControl

#### Hierarchy

[Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md) <br>&nbsp;&nbsp;&nbsp;└─ ContainerControl <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─ [Group](../interfaces/view-model-control-group-igroup-igroup.md) <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─ [List](../interfaces/view-model-control-list-ilist-ilist.md) <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─ [Part](../interfaces/view-model-control-part-ipart-ipart.md) <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [container](../interfaces/view-model-control-container-icontainercontrol-icontainercontrol.md#container) |container: boolean <br>|True if the control is a container.<br>  Overrides [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[container](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#container) <br> |
| [generic](../interfaces/view-model-control-container-icontainercontrol-icontainercontrol.md#generic) |generic: boolean (optional)  <br>|  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[generic](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#generic) <br> |
| [getDataSource](../interfaces/view-model-control-container-icontainercontrol-icontainercontrol.md#getdatasource) |getDataSource: function(): any <br>|  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[getDataSource](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#getdatasource) <br> |
| [hidden](../interfaces/view-model-control-container-icontainercontrol-icontainercontrol.md#hidden) |hidden: boolean <br>|True if the control is hidden.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[hidden](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#hidden) <br> |

#### Methods

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [applyDesign](../interfaces/view-model-control-container-icontainercontrol-icontainercontrol.md#applydesign) |applyDesign(design: [Design](../interfaces/view-model-ipage-idesign.md)): void|Applies given design to the design on the control.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[applyDesign](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#applydesign) <br> |
| [dataContext](../interfaces/view-model-control-container-icontainercontrol-icontainercontrol.md#datacontext) |dataContext(): any|  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[dataContext](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#datacontext) <br> |
| [getControl](../interfaces/view-model-control-container-icontainercontrol-icontainercontrol.md#getcontrol) |getControl(controlName: string): [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md)|Given the name of a control, returns the control instance.<br>  |
| [getControlById](../interfaces/view-model-control-container-icontainercontrol-icontainercontrol.md#getcontrolbyid) |getControlById(id: string): [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md)|Given the ID of a control, returns the control instance.<br>  |
| [getDesign](../interfaces/view-model-control-container-icontainercontrol-icontainercontrol.md#getdesign) |getDesign(): [Design](../interfaces/view-model-ipage-idesign.md)|Returns the design object of this control.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[getDesign](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#getdesign) <br> |
| [isEditable](../interfaces/view-model-control-container-icontainercontrol-icontainercontrol.md#iseditable) |isEditable(): boolean|Boolean indicating if the control is editable.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[isEditable](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#iseditable) <br> |
| [metadata](../interfaces/view-model-control-container-icontainercontrol-icontainercontrol.md#metadata) |metadata(): [ContainerControlMetadata](../interfaces/view-model-control-container-icontainercontrol-icontainercontrolmetadata.md)|Returns the metadata object of this control.<br>  Overrides [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[metadata](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#metadata) <br> |
| [parent](../interfaces/view-model-control-container-icontainercontrol-icontainercontrol.md#parent) |parent(): [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md) &#124; [Page](../interfaces/view-model-ipage-ipage.md)|Returns the parent (control or page) of this control.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[parent](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#parent) <br> |
| [root](../interfaces/view-model-control-container-icontainercontrol-icontainercontrol.md#root) |root(): [Page](../interfaces/view-model-ipage-ipage.md)|Returns the root form instance (page) of this control.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[root](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#root) <br> |


### ContainerControlDesign

#### Hierarchy

[Design](../interfaces/view-model-ipage-idesign.md) <br>&nbsp;&nbsp;&nbsp;└─ ContainerControlDesign <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─ [GroupDesign](../interfaces/view-model-control-group-igroup-igroupdesign.md) <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─ [ListDesign](../interfaces/view-model-control-list-ilist-ilistdesign.md) <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─ [PartDesign](../interfaces/view-model-control-part-ipart-ipartdesign.md) <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [alignItems](../interfaces/view-model-control-container-icontainercontrol-icontainercontroldesign.md#alignitems) |alignItems: string (optional)  <br>|This property is an alias for the CSS property "align-items".<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[alignItems](../interfaces/view-model-ipage-idesign.md#alignitems) <br> |
| [alignSelf](../interfaces/view-model-control-container-icontainercontrol-icontainercontroldesign.md#alignself) |alignSelf: string (optional)  <br>|  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[alignSelf](../interfaces/view-model-ipage-idesign.md#alignself) <br> |
| [allowScroll](../interfaces/view-model-control-container-icontainercontrol-icontainercontroldesign.md#allowscroll) |allowScroll: string (optional)  <br>|True if the container will allow scrolling when its items do not fit into the container's available space. If a container has an item which may scroll, then set this property to false to prevent nested scrolling areas.<br>  |
| [background](../interfaces/view-model-control-container-icontainercontrol-icontainercontroldesign.md#background) |background: string (optional)  <br>|The background color of the container.<br>  |
| [bindings](../interfaces/view-model-control-container-icontainercontrol-icontainercontroldesign.md#bindings) |bindings: any (optional)  <br>|  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[bindings](../interfaces/view-model-ipage-idesign.md#bindings) <br> |
| [border](../interfaces/view-model-control-container-icontainercontrol-icontainercontroldesign.md#border) |border: "none" &#124; "solid" &#124; "left" &#124; "right" &#124; "top" &#124; "bottom" (optional)  <br>|The border behavior of a control. This property will not be inherited by the children.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[border](../interfaces/view-model-ipage-idesign.md#border) <br> |
| [color](../interfaces/view-model-control-container-icontainercontrol-icontainercontroldesign.md#color) |color: string (optional)  <br>|The foreground color of the container.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[color](../interfaces/view-model-ipage-idesign.md#color) <br> |
| [flexFlow](../interfaces/view-model-control-container-icontainercontrol-icontainercontroldesign.md#flexflow) |flexFlow: string (optional)  <br>|Specifying this property makes the component a flex container component.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[flexFlow](../interfaces/view-model-ipage-idesign.md#flexflow) <br> |
| [flexSize](../interfaces/view-model-control-container-icontainercontrol-icontainercontroldesign.md#flexsize) |flexSize: string (optional)  <br>|One number or two numbers written as a string. For example, "(size to grow) [(size-to-shrink)]" to accommodate available space in the immediate flex container.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[flexSize](../interfaces/view-model-ipage-idesign.md#flexsize) <br> |
| [fontSize](../interfaces/view-model-control-container-icontainercontrol-icontainercontroldesign.md#fontsize) |fontSize: "medium" &#124; "xx-small" &#124; "x-small" &#124; "small" &#124; "large" &#124; "x-large" &#124; "xx-large" (optional)  <br>|The proportional text size<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[fontSize](../interfaces/view-model-ipage-idesign.md#fontsize) <br> |
| [fontWeight](../interfaces/view-model-control-container-icontainercontrol-icontainercontroldesign.md#fontweight) |fontWeight: "normal" &#124; "bold" (optional)  <br>|Normal or bold text.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[fontWeight](../interfaces/view-model-ipage-idesign.md#fontweight) <br> |
| [itemBorder](../interfaces/view-model-control-container-icontainercontrol-icontainercontroldesign.md#itemborder) |itemBorder: "solid" &#124; "none" (optional)  <br>|If true, a border will appear around each row in the list.<br>  |
| [items](../interfaces/view-model-control-container-icontainercontrol-icontainercontroldesign.md#items) |items: string &#124; [Design](../interfaces/view-model-ipage-idesign.md) \[ \] (optional)  <br>|An array containing the components to place inside of the container.<br>  |
| [justifyItems](../interfaces/view-model-control-container-icontainercontrol-icontainercontroldesign.md#justifyitems) |justifyItems: "flex-start" &#124; "flex-end" &#124; "center" &#124; "space-between" (optional)  <br>|This property is an alias for the CSS property "justify-content".<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[justifyItems](../interfaces/view-model-ipage-idesign.md#justifyitems) <br> |
| [label](../interfaces/view-model-control-container-icontainercontrol-icontainercontroldesign.md#label) |label: string (optional)  <br>|  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[label](../interfaces/view-model-ipage-idesign.md#label) <br> |
| [labelPosition](../interfaces/view-model-control-container-icontainercontrol-icontainercontroldesign.md#labelposition) |labelPosition: "stacked" &#124; "hidden" &#124; "inline" (optional)  <br>|Determines how a label is positioned, if at all. By default, labelPosition is set to stacked.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[labelPosition](../interfaces/view-model-ipage-idesign.md#labelposition) <br> |
| [name](../interfaces/view-model-control-container-icontainercontrol-icontainercontroldesign.md#name) |name: string (optional)  <br>|  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[name](../interfaces/view-model-ipage-idesign.md#name) <br> |
| [padding](../interfaces/view-model-control-container-icontainercontrol-icontainercontroldesign.md#padding) |padding: "none" &#124; "small" &#124; "std" (optional)  <br>|Allows specifying the component's padding behavior.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[padding](../interfaces/view-model-ipage-idesign.md#padding) <br> |
| [type](../interfaces/view-model-control-container-icontainercontrol-icontainercontroldesign.md#type) |type: [ControlType](view-model-control-basecontrol-icontrol.md#controltype) (optional)  <br>|The type of the control as a string.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[type](../interfaces/view-model-ipage-idesign.md#type) <br> |


### ContainerControlMetadata

#### Hierarchy

[ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md) <br>&nbsp;&nbsp;&nbsp;└─ ContainerControlMetadata <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─ [GroupMetadata](../interfaces/view-model-control-group-igroup-igroupmetadata.md) <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─ [ListMetadata](../interfaces/view-model-control-list-ilist-ilistmetadata.md) <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─ [PartMetadata](../interfaces/view-model-control-part-ipart-ipartmetadata.md) <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [BoundEntity](../interfaces/view-model-control-container-icontainercontrol-icontainercontrolmetadata.md#boundentity) |BoundEntity: string (optional)  <br>|The entity to which the control is bound.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[BoundEntity](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#boundentity) <br> |
| [BoundField](../interfaces/view-model-control-container-icontainercontrol-icontainercontrolmetadata.md#boundfield) |BoundField: string (optional)  <br>|  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[BoundField](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#boundfield) <br> |
| [Description](../interfaces/view-model-control-container-icontainercontrol-icontainercontrolmetadata.md#description) |Description: string (optional)  <br>|Description of the control.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Description](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#description) <br> |
| [Editable](../interfaces/view-model-control-container-icontainercontrol-icontainercontrolmetadata.md#editable) |Editable: boolean (optional)  <br>|Boolean indicating if the control is editable.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Editable](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#editable) <br> |
| [ExtType](../interfaces/view-model-control-container-icontainercontrol-icontainercontrolmetadata.md#exttype) |ExtType: [ControlType](view-model-control-basecontrol-icontrol.md#controltype) (optional)  <br>|The extended control type. For example, a control of type Input might have an extended type of Barcode.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[ExtType](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#exttype) <br> |
| [HelpText](../interfaces/view-model-control-container-icontainercontrol-icontainercontrolmetadata.md#helptext) |HelpText: string (optional)  <br>|The keyboard shortcut for a command. For example, "(Shift+F5)"<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[HelpText](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#helptext) <br> |
| [Hidden](../interfaces/view-model-control-container-icontainercontrol-icontainercontrolmetadata.md#hidden) |Hidden: boolean (optional)  <br>|Boolean indicating if the control is hidden or not.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Hidden](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#hidden) <br> |
| [Id](../interfaces/view-model-control-container-icontainercontrol-icontainercontrolmetadata.md#id) |Id: string (optional)  <br>|Identification string for a control.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Id](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#id) <br> |
| [Label](../interfaces/view-model-control-container-icontainercontrol-icontainercontrolmetadata.md#label) |Label: string (optional)  <br>|Label for a control. For example, a control representing a person's first name might have a label "First Name".<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Label](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#label) <br> |
| [Name](../interfaces/view-model-control-container-icontainercontrol-icontainercontrolmetadata.md#name) |Name: string (optional)  <br>|Name of a control.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Name](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#name) <br> |
| [Order](../interfaces/view-model-control-container-icontainercontrol-icontainercontrolmetadata.md#order) |Order: number (optional)  <br>|Number indicating the order in which a control will appear on a page.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Order](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#order) <br> |
| [Type](../interfaces/view-model-control-container-icontainercontrol-icontainercontrolmetadata.md#type) |Type: [ControlType](view-model-control-basecontrol-icontrol.md#controltype) (optional)  <br>|String indicating the control type.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Type](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#type) <br> |



[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]