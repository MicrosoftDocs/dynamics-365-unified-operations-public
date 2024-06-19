---
title: Multi-Lookup module
description: Learn about the Multi-lookup module, which includes the MultiLookup, MultiLookupDesign, and MultiLookupMetadata index types.
author: jasongre
ms.author: jasongre
ms.topic: article
ms.date: 05/26/2022
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
---

# Multi-Lookup module

[!include [banner](../../../../includes/banner.md)]
[!include [mobile app deprecated](../../../../includes/mobile-app-deprecation-banner.md)]

Multi-Lookup controls are similar to regular lookups except they allow multiple selections at once.

## Index

### Types

* [MultiLookup](../interfaces/view-model-control-lookup-imultilookup-imultilookup.md)
* [MultiLookupDesign](../interfaces/view-model-control-lookup-imultilookup-imultilookupdesign.md)
* [MultiLookupMetadata](../interfaces/view-model-control-lookup-imultilookup-imultilookupmetadata.md)

## Types


### MultiLookup

#### Hierarchy

[InputControl](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontrol.md) <br>&nbsp;&nbsp;&nbsp;└─ MultiLookup <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [container](../interfaces/view-model-control-lookup-imultilookup-imultilookup.md#container) |container: boolean (optional)  <br>|True if the control is a container.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[container](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#container) <br> |
| [generic](../interfaces/view-model-control-lookup-imultilookup-imultilookup.md#generic) |generic: boolean (optional)  <br>|  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[generic](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#generic) <br> |
| [getDataSource](../interfaces/view-model-control-lookup-imultilookup-imultilookup.md#getdatasource) |getDataSource: function(): any <br>|  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[getDataSource](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#getdatasource) <br> |
| [getEntityRefs](../interfaces/view-model-control-lookup-imultilookup-imultilookup.md#getentityrefs) |getEntityRefs: function(): string [ ] &#124; number [ ] <br>|  |
| [hidden](../interfaces/view-model-control-lookup-imultilookup-imultilookup.md#hidden) |hidden: boolean <br>|True if the control is hidden.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[hidden](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#hidden) <br> |
| [setEntityRefs](../interfaces/view-model-control-lookup-imultilookup-imultilookup.md#setentityrefs) |setEntityRefs: function(ids: string [ ] &#124; number [ ]): Promise &lt;any&gt; <br>|  |

#### Methods

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [applyDesign](../interfaces/view-model-control-lookup-imultilookup-imultilookup.md#applydesign) |applyDesign(IDesign: [MultiLookupDesign](../interfaces/view-model-control-lookup-imultilookup-imultilookupdesign.md)): void|Applies given design to the design on the control.<br>  Overrides [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[applyDesign](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#applydesign) <br> |
| [dataContext](../interfaces/view-model-control-lookup-imultilookup-imultilookup.md#datacontext) |dataContext(): any|  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[dataContext](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#datacontext) <br> |
| [getDesign](../interfaces/view-model-control-lookup-imultilookup-imultilookup.md#getdesign) |getDesign(): [Design](../interfaces/view-model-ipage-idesign.md)|Returns the design object of this control.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[getDesign](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#getdesign) <br> |
| [getLookupPage](../interfaces/view-model-control-lookup-imultilookup-imultilookup.md#getlookuppage) |getLookupPage(): [Page](../interfaces/view-model-ipage-ipage.md)|  |
| [isEditable](../interfaces/view-model-control-lookup-imultilookup-imultilookup.md#iseditable) |isEditable(): boolean|Boolean indicating if the control is editable.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[isEditable](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#iseditable) <br> |
| [metadata](../interfaces/view-model-control-lookup-imultilookup-imultilookup.md#metadata) |metadata(): [MultiLookupMetadata](../interfaces/view-model-control-lookup-imultilookup-imultilookupmetadata.md)|Returns the metadata object of this control.<br>  Overrides [InputControl](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontrol.md).[metadata](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontrol.md#metadata) <br> |
| [parent](../interfaces/view-model-control-lookup-imultilookup-imultilookup.md#parent) |parent(): [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md) &#124; [Page](../interfaces/view-model-ipage-ipage.md)|Returns the parent (control or page) of this control.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[parent](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#parent) <br> |
| [root](../interfaces/view-model-control-lookup-imultilookup-imultilookup.md#root) |root(): [Page](../interfaces/view-model-ipage-ipage.md)|Returns the root form instance (page) of this control.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[root](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#root) <br> |

#### Events

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [onDataChanged](../interfaces/view-model-control-lookup-imultilookup-imultilookup.md#ondatachanged) |onDataChanged: [EventHook](../interfaces/event-ievent-ieventhook.md) &lt;null&gt; <br>|An event that is triggered when the input control's data changes.<br>  Inherited from [InputControl](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontrol.md).[onDataChanged](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontrol.md#ondatachanged) <br> |


### MultiLookupDesign

#### Hierarchy

[InputControlDesign](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontroldesign.md) <br>&nbsp;&nbsp;&nbsp;└─ MultiLookupDesign <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [alignItems](../interfaces/view-model-control-lookup-imultilookup-imultilookupdesign.md#alignitems) |alignItems: string (optional)  <br>|This property is an alias for the CSS property "align-items".<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[alignItems](../interfaces/view-model-ipage-idesign.md#alignitems) <br> |
| [alignSelf](../interfaces/view-model-control-lookup-imultilookup-imultilookupdesign.md#alignself) |alignSelf: string (optional)  <br>|  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[alignSelf](../interfaces/view-model-ipage-idesign.md#alignself) <br> |
| [bindings](../interfaces/view-model-control-lookup-imultilookup-imultilookupdesign.md#bindings) |bindings: any (optional)  <br>|  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[bindings](../interfaces/view-model-ipage-idesign.md#bindings) <br> |
| [border](../interfaces/view-model-control-lookup-imultilookup-imultilookupdesign.md#border) |border: "none" &#124; "solid" &#124; "left" &#124; "right" &#124; "top" &#124; "bottom" (optional)  <br>|The border behavior of a control. This property will not be inherited by the children.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[border](../interfaces/view-model-ipage-idesign.md#border) <br> |
| [color](../interfaces/view-model-control-lookup-imultilookup-imultilookupdesign.md#color) |color: string (optional)  <br>|The foreground color of the container.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[color](../interfaces/view-model-ipage-idesign.md#color) <br> |
| [flexFlow](../interfaces/view-model-control-lookup-imultilookup-imultilookupdesign.md#flexflow) |flexFlow: string (optional)  <br>|Specifying this property makes the component a flex container component.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[flexFlow](../interfaces/view-model-ipage-idesign.md#flexflow) <br> |
| [flexSize](../interfaces/view-model-control-lookup-imultilookup-imultilookupdesign.md#flexsize) |flexSize: string (optional)  <br>|One number or two numbers written as a string. For example, "(size to grow) [(size-to-shrink)]" to accommodate available space in the immediate flex container.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[flexSize](../interfaces/view-model-ipage-idesign.md#flexsize) <br> |
| [fontSize](../interfaces/view-model-control-lookup-imultilookup-imultilookupdesign.md#fontsize) |fontSize: "medium" &#124; "xx-small" &#124; "x-small" &#124; "small" &#124; "large" &#124; "x-large" &#124; "xx-large" (optional)  <br>|The proportional text size<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[fontSize](../interfaces/view-model-ipage-idesign.md#fontsize) <br> |
| [fontWeight](../interfaces/view-model-control-lookup-imultilookup-imultilookupdesign.md#fontweight) |fontWeight: "normal" &#124; "bold" (optional)  <br>|Normal or bold text.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[fontWeight](../interfaces/view-model-ipage-idesign.md#fontweight) <br> |
| [justifyItems](../interfaces/view-model-control-lookup-imultilookup-imultilookupdesign.md#justifyitems) |justifyItems: "flex-start" &#124; "flex-end" &#124; "center" &#124; "space-between" (optional)  <br>|This property is an alias for the CSS property "justify-content".<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[justifyItems](../interfaces/view-model-ipage-idesign.md#justifyitems) <br> |
| [label](../interfaces/view-model-control-lookup-imultilookup-imultilookupdesign.md#label) |label: string (optional)  <br>|  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[label](../interfaces/view-model-ipage-idesign.md#label) <br> |
| [labelPosition](../interfaces/view-model-control-lookup-imultilookup-imultilookupdesign.md#labelposition) |labelPosition: "stacked" &#124; "hidden" &#124; "inline" (optional)  <br>|Determines how a label is positioned, if at all. By default, labelPosition is set to stacked.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[labelPosition](../interfaces/view-model-ipage-idesign.md#labelposition) <br> |
| [name](../interfaces/view-model-control-lookup-imultilookup-imultilookupdesign.md#name) |name: string (optional)  <br>|  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[name](../interfaces/view-model-ipage-idesign.md#name) <br> |
| [padding](../interfaces/view-model-control-lookup-imultilookup-imultilookupdesign.md#padding) |padding: "none" &#124; "small" &#124; "std" (optional)  <br>|Allows specifying the component's padding behavior.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[padding](../interfaces/view-model-ipage-idesign.md#padding) <br> |
| [type](../interfaces/view-model-control-lookup-imultilookup-imultilookupdesign.md#type) |type: [ControlType](view-model-control-basecontrol-icontrol.md#controltype) (optional)  <br>|The type of the control as a string.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[type](../interfaces/view-model-ipage-idesign.md#type) <br> |


### MultiLookupMetadata

#### Hierarchy

[InputControlMetadata](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md) <br>&nbsp;&nbsp;&nbsp;└─ MultiLookupMetadata <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [BoundEntity](../interfaces/view-model-control-lookup-imultilookup-imultilookupmetadata.md#boundentity) |BoundEntity: string (optional)  <br>|The entity to which the control is bound.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[BoundEntity](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#boundentity) <br> |
| [BoundField](../interfaces/view-model-control-lookup-imultilookup-imultilookupmetadata.md#boundfield) |BoundField: string (optional)  <br>|  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[BoundField](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#boundfield) <br> |
| [Description](../interfaces/view-model-control-lookup-imultilookup-imultilookupmetadata.md#description) |Description: string (optional)  <br>|Description of the control.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Description](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#description) <br> |
| [Design](../interfaces/view-model-control-lookup-imultilookup-imultilookupmetadata.md#design) |Design: [Design](../interfaces/view-model-ipage-idesign.md) (optional)  <br>|Design object for the lookup page that is referenced by the LookupPageId.<br>  |
| [Editable](../interfaces/view-model-control-lookup-imultilookup-imultilookupmetadata.md#editable) |Editable: boolean (optional)  <br>|Boolean indicating if the control is editable.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Editable](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#editable) <br> |
| [ExtType](../interfaces/view-model-control-lookup-imultilookup-imultilookupmetadata.md#exttype) |ExtType: [ControlType](view-model-control-basecontrol-icontrol.md#controltype) (optional)  <br>|The extended control type. For example, a control of type Input might have an extended type of Barcode.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[ExtType](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#exttype) <br> |
| [FilterContext](../interfaces/view-model-control-lookup-imultilookup-imultilookupmetadata.md#filtercontext) |FilterContext: DataFilter (optional)  <br>|  |
| [FilterLocalOnly](../interfaces/view-model-control-lookup-imultilookup-imultilookupmetadata.md#filterlocalonly) |FilterLocalOnly: boolean (optional)  <br>|  |
| [HelpText](../interfaces/view-model-control-lookup-imultilookup-imultilookupmetadata.md#helptext) |HelpText: string (optional)  <br>|The keyboard shortcut for a command. For example, "(Shift+F5)"<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[HelpText](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#helptext) <br> |
| [Hidden](../interfaces/view-model-control-lookup-imultilookup-imultilookupmetadata.md#hidden) |Hidden: boolean (optional)  <br>|Boolean indicating if the control is hidden or not.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Hidden](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#hidden) <br> |
| [Id](../interfaces/view-model-control-lookup-imultilookup-imultilookupmetadata.md#id) |Id: string (optional)  <br>|Identification string for a control.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Id](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#id) <br> |
| [Label](../interfaces/view-model-control-lookup-imultilookup-imultilookupmetadata.md#label) |Label: string (optional)  <br>|Label for a control. For example, a control representing a person's first name might have a label "First Name".<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Label](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#label) <br> |
| [LookupPageId](../interfaces/view-model-control-lookup-imultilookup-imultilookupmetadata.md#lookuppageid) |LookupPageId: string (optional)  <br>|Page that is hosted within the multi-lookup.<br>  |
| [Mandatory](../interfaces/view-model-control-lookup-imultilookup-imultilookupmetadata.md#mandatory) |Mandatory: boolean (optional)  <br>|If set to true then input for the control is required for the task to be completed. Mandatory controls will have a red outline.<br>  Inherited from [InputControlMetadata](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md).[Mandatory](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md#mandatory) <br> |
| [Name](../interfaces/view-model-control-lookup-imultilookup-imultilookupmetadata.md#name) |Name: string (optional)  <br>|Name of a control.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Name](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#name) <br> |
| [NumSequence](../interfaces/view-model-control-lookup-imultilookup-imultilookupmetadata.md#numsequence) |NumSequence: [NumberSequenceConfig](../interfaces/view-model-control-basecontrol-iinputcontrol-inumbersequenceconfig.md) (optional)  <br>|Used for auto detecting and changing visibility of the number sequence controls in the task or page, based on AX number sequence configuration, through extended business logic.<br>  Inherited from [InputControlMetadata](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md).[NumSequence](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md#numsequence) <br> |
| [Order](../interfaces/view-model-control-lookup-imultilookup-imultilookupmetadata.md#order) |Order: number (optional)  <br>|Number indicating the order in which a control will appear on a page.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Order](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#order) <br> |
| [ReferenceAppId](../interfaces/view-model-control-lookup-imultilookup-imultilookupmetadata.md#referenceappid) |ReferenceAppId: string (optional)  <br>|  |
| [ReverseLookupRelation](../interfaces/view-model-control-lookup-imultilookup-imultilookupmetadata.md#reverselookuprelation) |ReverseLookupRelation: boolean (optional)  <br>|  |
| [ShowPending](../interfaces/view-model-control-lookup-imultilookup-imultilookupmetadata.md#showpending) |ShowPending: boolean (optional)  <br>|  |
| [Type](../interfaces/view-model-control-lookup-imultilookup-imultilookupmetadata.md#type) |Type: [ControlType](view-model-control-basecontrol-icontrol.md#controltype) (optional)  <br>|String indicating the control type.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Type](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#type) <br> |

#### Events

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [OnLookupPageCreate](../interfaces/view-model-control-lookup-imultilookup-imultilookupmetadata.md#onlookuppagecreate) |OnLookupPageCreate: function(args: any, multiLookup: any): void (optional)  <br>|  |
| [OnLookupPageCreated](../interfaces/view-model-control-lookup-imultilookup-imultilookupmetadata.md#onlookuppagecreated) |OnLookupPageCreated: function(args: any, multiLookup: any): void (optional)  <br>|  |



[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]
