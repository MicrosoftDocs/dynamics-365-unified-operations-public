---
title: Pagelink module
description: Learn about the Pagelink module, which includes the PageLink, PageLinkDesign, and PageLinkMetadata index types.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 12/31/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.custom: 
  - bap-template
---

# Pagelink module

[!include [banner](../../../../includes/banner.md)]
[!include [mobile app deprecated](../../../../includes/mobile-app-deprecation-banner.md)]

A pagelink is a control that navigates to another page.

## Index

### Types

* [PageLink](../interfaces/view-model-control-pagelink-ipagelink-ipagelink.md)
* [PageLinkDesign](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkdesign.md)
* [PageLinkMetadata](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkmetadata.md)

## Types


### PageLink

#### Hierarchy

[Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md) <br>&nbsp;&nbsp;&nbsp;└─ PageLink <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [container](../interfaces/view-model-control-pagelink-ipagelink-ipagelink.md#container) |container: boolean (optional)  <br>|True if the control is a container.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[container](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#container) <br> |
| [generic](../interfaces/view-model-control-pagelink-ipagelink-ipagelink.md#generic) |generic: boolean (optional)  <br>|  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[generic](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#generic) <br> |
| [getDataSource](../interfaces/view-model-control-pagelink-ipagelink-ipagelink.md#getdatasource) |getDataSource: function(): any <br>|  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[getDataSource](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#getdatasource) <br> |
| [hidden](../interfaces/view-model-control-pagelink-ipagelink-ipagelink.md#hidden) |hidden: boolean <br>|True if the control is hidden.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[hidden](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#hidden) <br> |

#### Methods

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [allowsNavigation](../interfaces/view-model-control-pagelink-ipagelink-ipagelink.md#allowsnavigation) |allowsNavigation(): boolean|  |
| [applyDesign](../interfaces/view-model-control-pagelink-ipagelink-ipagelink.md#applydesign) |applyDesign(design: [PageLinkDesign](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkdesign.md)): void|Applies given design to the design on the control.<br>  Overrides [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[applyDesign](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#applydesign) <br> |
| [dataContext](../interfaces/view-model-control-pagelink-ipagelink-ipagelink.md#datacontext) |dataContext(): any|  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[dataContext](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#datacontext) <br> |
| [getCount](../interfaces/view-model-control-pagelink-ipagelink-ipagelink.md#getcount) |getCount(): number &#124; string|  |
| [getDesign](../interfaces/view-model-control-pagelink-ipagelink-ipagelink.md#getdesign) |getDesign(): [Design](../interfaces/view-model-ipage-idesign.md)|Returns the design object of this control.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[getDesign](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#getdesign) <br> |
| [getNavigationHandler](../interfaces/view-model-control-pagelink-ipagelink-ipagelink.md#getnavigationhandler) |getNavigationHandler(): [NavigationArgs](../interfaces/view-model-ipage-inavigationargs.md)|  |
| [isEditable](../interfaces/view-model-control-pagelink-ipagelink-ipagelink.md#iseditable) |isEditable(): boolean|Boolean indicating if the control is editable.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[isEditable](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#iseditable) <br> |
| [metadata](../interfaces/view-model-control-pagelink-ipagelink-ipagelink.md#metadata) |metadata(): [PageLinkMetadata](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkmetadata.md)|Returns the metadata object of this control.<br>  Overrides [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[metadata](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#metadata) <br> |
| [parent](../interfaces/view-model-control-pagelink-ipagelink-ipagelink.md#parent) |parent(): [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md) &#124; [Page](../interfaces/view-model-ipage-ipage.md)|Returns the parent (control or page) of this control.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[parent](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#parent) <br> |
| [root](../interfaces/view-model-control-pagelink-ipagelink-ipagelink.md#root) |root(): [Page](../interfaces/view-model-ipage-ipage.md)|Returns the root form instance (page) of this control.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[root](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#root) <br> |
| [showCount](../interfaces/view-model-control-pagelink-ipagelink-ipagelink.md#showcount) |showCount(): boolean|  |


### PageLinkDesign

#### Hierarchy

[Design](../interfaces/view-model-ipage-idesign.md) <br>&nbsp;&nbsp;&nbsp;└─ PageLinkDesign <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [alignItems](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkdesign.md#alignitems) |alignItems: string (optional)  <br>|This property is an alias for the CSS property "align-items".<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[alignItems](../interfaces/view-model-ipage-idesign.md#alignitems) <br> |
| [alignSelf](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkdesign.md#alignself) |alignSelf: string (optional)  <br>|  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[alignSelf](../interfaces/view-model-ipage-idesign.md#alignself) <br> |
| [background](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkdesign.md#background) |background: string (optional)  <br>|Sets the background color.<br>  |
| [bindings](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkdesign.md#bindings) |bindings: any (optional)  <br>|  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[bindings](../interfaces/view-model-ipage-idesign.md#bindings) <br> |
| [border](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkdesign.md#border) |border: "none" &#124; "solid" &#124; "left" &#124; "right" &#124; "top" &#124; "bottom" (optional)  <br>|The border behavior of a control. This property will not be inherited by the children.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[border](../interfaces/view-model-ipage-idesign.md#border) <br> |
| [color](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkdesign.md#color) |color: string (optional)  <br>|The foreground color of the container.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[color](../interfaces/view-model-ipage-idesign.md#color) <br> |
| [excludeContext](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkdesign.md#excludecontext) |excludeContext: boolean (optional)  <br>|  |
| [flexFlow](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkdesign.md#flexflow) |flexFlow: string (optional)  <br>|Specifying this property makes the component a flex container component.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[flexFlow](../interfaces/view-model-ipage-idesign.md#flexflow) <br> |
| [flexSize](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkdesign.md#flexsize) |flexSize: string (optional)  <br>|One number or two numbers written as a string. For example, "(size to grow) [(size-to-shrink)]" to accommodate available space in the immediate flex container.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[flexSize](../interfaces/view-model-ipage-idesign.md#flexsize) <br> |
| [fontSize](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkdesign.md#fontsize) |fontSize: "medium" &#124; "xx-small" &#124; "x-small" &#124; "small" &#124; "large" &#124; "x-large" &#124; "xx-large" (optional)  <br>|The proportional text size<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[fontSize](../interfaces/view-model-ipage-idesign.md#fontsize) <br> |
| [fontWeight](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkdesign.md#fontweight) |fontWeight: "normal" &#124; "bold" (optional)  <br>|Normal or bold text.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[fontWeight](../interfaces/view-model-ipage-idesign.md#fontweight) <br> |
| [hideArrow](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkdesign.md#hidearrow) |hideArrow: boolean (optional)  <br>|Allows an arrow ( > ) on a default styled navigation control to be hidden.<br>  |
| [icon](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkdesign.md#icon) |icon: string (optional)  <br>|Name of the icon that is displayed in the pagelink control.<br>  |
| [justifyItems](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkdesign.md#justifyitems) |justifyItems: "flex-start" &#124; "flex-end" &#124; "center" &#124; "space-between" (optional)  <br>|This property is an alias for the CSS property "justify-content".<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[justifyItems](../interfaces/view-model-ipage-idesign.md#justifyitems) <br> |
| [label](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkdesign.md#label) |label: string (optional)  <br>|  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[label](../interfaces/view-model-ipage-idesign.md#label) <br> |
| [labelPosition](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkdesign.md#labelposition) |labelPosition: "stacked" &#124; "hidden" &#124; "inline" (optional)  <br>|Determines how a label is positioned, if at all. By default, labelPosition is set to stacked.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[labelPosition](../interfaces/view-model-ipage-idesign.md#labelposition) <br> |
| [name](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkdesign.md#name) |name: string (optional)  <br>|  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[name](../interfaces/view-model-ipage-idesign.md#name) <br> |
| [navigation](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkdesign.md#navigation) |navigation: [NavigationArgs](../interfaces/view-model-ipage-inavigationargs.md) (optional)  <br>|Navigation object of the pagelink.<br>  |
| [padding](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkdesign.md#padding) |padding: "none" &#124; "small" &#124; "std" (optional)  <br>|Allows specifying the component's padding behavior.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[padding](../interfaces/view-model-ipage-idesign.md#padding) <br> |
| [showCount](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkdesign.md#showcount) |showCount: boolean (optional)  <br>|If true, shows a count of the records present in the list on the target page.<br>  |
| [style](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkdesign.md#style) |style: string (optional)  <br>|Determines the visual style of the pagelink control. Options: * "inline": takes up the full width its container, with the label in-line with the icon * "button": takes up only as much width as needed by the label, with the label below the icon<br>  |
| [type](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkdesign.md#type) |type: [ControlType](view-model-control-basecontrol-icontrol.md#controltype) (optional)  <br>|The type of the control as a string.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[type](../interfaces/view-model-ipage-idesign.md#type) <br> |


### PageLinkMetadata

#### Hierarchy

[ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md) <br>&nbsp;&nbsp;&nbsp;└─ PageLinkMetadata <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [BoundEntity](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#boundentity) |BoundEntity: string (optional)  <br>|The entity to which the control is bound.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[BoundEntity](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#boundentity) <br> |
| [BoundField](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#boundfield) |BoundField: string (optional)  <br>|  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[BoundField](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#boundfield) <br> |
| [Description](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#description) |Description: string (optional)  <br>|Description of the control.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Description](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#description) <br> |
| [Editable](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#editable) |Editable: boolean (optional)  <br>|Boolean indicating if the control is editable.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Editable](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#editable) <br> |
| [ExcludeContext](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#excludecontext) |ExcludeContext: boolean (optional)  <br>|  |
| [ExtType](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#exttype) |ExtType: [ControlType](view-model-control-basecontrol-icontrol.md#controltype) (optional)  <br>|The extended control type. For example, a control of type Input might have an extended type of Barcode.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[ExtType](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#exttype) <br> |
| [HelpText](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#helptext) |HelpText: string (optional)  <br>|The keyboard shortcut for a command. For example, "(Shift+F5)"<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[HelpText](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#helptext) <br> |
| [Hidden](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#hidden) |Hidden: boolean (optional)  <br>|Boolean indicating if the control is hidden or not.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Hidden](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#hidden) <br> |
| [Icon](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#icon) |Icon: string (optional)  <br>|Name of the icon that is displayed in the pagelink control.<br>  |
| [IconSize](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#iconsize) |IconSize: number (optional)  <br>|Determines the size of the icon that is displayed in the pagelink control.<br>  |
| [Id](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#id) |Id: string (optional)  <br>|Identification string for a control.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Id](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#id) <br> |
| [Label](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#label) |Label: string (optional)  <br>|Label for a control. For example, a control representing a person's first name might have a label "First Name".<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Label](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#label) <br> |
| [Name](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#name) |Name: string (optional)  <br>|Name of a control.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Name](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#name) <br> |
| [Navigation](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#navigation) |Navigation: [NavigationArgs](../interfaces/view-model-ipage-inavigationargs.md) (optional)  <br>|Navigation object of the pagelink.<br>  |
| [Order](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#order) |Order: number (optional)  <br>|Number indicating the order in which a control will appear on a page.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Order](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#order) <br> |
| [ShowCount](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#showcount) |ShowCount: boolean (optional)  <br>|If true, shows a count of the records present in the list on the target page.<br>  |
| [Style](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#style) |Style: string (optional)  <br>|Determines the visual style of the pagelink control.<br>  |
| [Target](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#target) |Target: string (optional)  <br>|Name of the target action or page to navigate to when the pagelink is selected.<br>  |
| [Type](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#type) |Type: [ControlType](view-model-control-basecontrol-icontrol.md#controltype) (optional)  <br>|String indicating the control type.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Type](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#type) <br> |
| [UseDataContext](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#usedatacontext) |UseDataContext: boolean (optional)  <br>|  |

#### Events

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [OnNavigate](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkmetadata.md#onnavigate) |OnNavigate: function(navigation: [NavigationArgs](../interfaces/view-model-ipage-inavigationargs.md) &#124; string): any (optional)  <br>|An event that is triggered when the navigation is triggered.<br>  |



[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]
