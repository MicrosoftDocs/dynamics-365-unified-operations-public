---
title: Lookup module
description: Learn about the Lookup module, a lookup is an input control that is used to select an input from a list of options.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 12/31/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.custom: 
  - bap-template
---

# Lookup module

[!include [banner](../../../../includes/banner.md)]
[!include [mobile app deprecated](../../../../includes/mobile-app-deprecation-banner.md)]

A lookup is an input control that is used to select an input from a list of options.
For example, a lookup could be used to lookup a customer when linking a customer to a new sales order.

## Index

### Types

* [Lookup](../interfaces/view-model-control-lookup-ilookup-ilookup.md)
* [LookupDesign](../interfaces/view-model-control-lookup-ilookup-ilookupdesign.md)
* [LookupMetadata](../interfaces/view-model-control-lookup-ilookup-ilookupmetadata.md)

## Types


### Lookup

#### Hierarchy

[InputControl](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontrol.md) <br>&nbsp;&nbsp;&nbsp;└─ Lookup <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [container](../interfaces/view-model-control-lookup-ilookup-ilookup.md#container) |container: boolean (optional)  <br>|True if the control is a container.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[container](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#container) <br> |
| [generic](../interfaces/view-model-control-lookup-ilookup-ilookup.md#generic) |generic: boolean (optional)  <br>|  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[generic](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#generic) <br> |
| [getDataSource](../interfaces/view-model-control-lookup-ilookup-ilookup.md#getdatasource) |getDataSource: function(): any <br>|  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[getDataSource](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#getdatasource) <br> |
| [hidden](../interfaces/view-model-control-lookup-ilookup-ilookup.md#hidden) |hidden: boolean <br>|True if the control is hidden.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[hidden](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#hidden) <br> |

#### Methods

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [applyDesign](../interfaces/view-model-control-lookup-ilookup-ilookup.md#applydesign) |applyDesign(IDesign: [LookupDesign](../interfaces/view-model-control-lookup-ilookup-ilookupdesign.md)): void|Applies given design to the design on the control.<br>  Overrides [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[applyDesign](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#applydesign) <br> |
| [dataContext](../interfaces/view-model-control-lookup-ilookup-ilookup.md#datacontext) |dataContext(): any|  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[dataContext](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#datacontext) <br> |
| [getDesign](../interfaces/view-model-control-lookup-ilookup-ilookup.md#getdesign) |getDesign(): [Design](../interfaces/view-model-ipage-idesign.md)|Returns the design object of this control.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[getDesign](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#getdesign) <br> |
| [getDisplayValue](../interfaces/view-model-control-lookup-ilookup-ilookup.md#getdisplayvalue) |getDisplayValue(): string|  |
| [getLookupPage](../interfaces/view-model-control-lookup-ilookup-ilookup.md#getlookuppage) |getLookupPage(): [Page](../interfaces/view-model-ipage-ipage.md)|  |
| [getValue](../interfaces/view-model-control-lookup-ilookup-ilookup.md#getvalue) |getValue(): string &#124; number|  |
| [isEditable](../interfaces/view-model-control-lookup-ilookup-ilookup.md#iseditable) |isEditable(): boolean|Boolean indicating if the control is editable.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[isEditable](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#iseditable) <br> |
| [metadata](../interfaces/view-model-control-lookup-ilookup-ilookup.md#metadata) |metadata(): [LookupMetadata](../interfaces/view-model-control-lookup-ilookup-ilookupmetadata.md)|Returns the metadata object of this control.<br>  Overrides [InputControl](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontrol.md).[metadata](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontrol.md#metadata) <br> |
| [parent](../interfaces/view-model-control-lookup-ilookup-ilookup.md#parent) |parent(): [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md) &#124; [Page](../interfaces/view-model-ipage-ipage.md)|Returns the parent (control or page) of this control.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[parent](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#parent) <br> |
| [root](../interfaces/view-model-control-lookup-ilookup-ilookup.md#root) |root(): [Page](../interfaces/view-model-ipage-ipage.md)|Returns the root form instance (page) of this control.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[root](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#root) <br> |
| [setEntityRef](../interfaces/view-model-control-lookup-ilookup-ilookup.md#setentityref) |setEntityRef(newValue: string &#124; number): Promise &lt;any&gt;|  |

#### Events

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [onDataChanged](../interfaces/view-model-control-lookup-ilookup-ilookup.md#ondatachanged) |onDataChanged: [EventHook](../interfaces/event-ievent-ieventhook.md) &lt;null&gt; <br>|An event that is triggered when the input control's data changes.<br>  Inherited from [InputControl](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontrol.md).[onDataChanged](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontrol.md#ondatachanged) <br> |


### LookupDesign

#### Hierarchy

[InputControlDesign](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontroldesign.md) <br>&nbsp;&nbsp;&nbsp;└─ LookupDesign <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [alignItems](../interfaces/view-model-control-lookup-ilookup-ilookupdesign.md#alignitems) |alignItems: string (optional)  <br>|This property is an alias for the CSS property "align-items".<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[alignItems](../interfaces/view-model-ipage-idesign.md#alignitems) <br> |
| [alignSelf](../interfaces/view-model-control-lookup-ilookup-ilookupdesign.md#alignself) |alignSelf: string (optional)  <br>|  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[alignSelf](../interfaces/view-model-ipage-idesign.md#alignself) <br> |
| [bindings](../interfaces/view-model-control-lookup-ilookup-ilookupdesign.md#bindings) |bindings: any (optional)  <br>|  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[bindings](../interfaces/view-model-ipage-idesign.md#bindings) <br> |
| [border](../interfaces/view-model-control-lookup-ilookup-ilookupdesign.md#border) |border: "none" &#124; "solid" &#124; "left" &#124; "right" &#124; "top" &#124; "bottom" (optional)  <br>|The border behavior of a control. This property will not be inherited by the children.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[border](../interfaces/view-model-ipage-idesign.md#border) <br> |
| [color](../interfaces/view-model-control-lookup-ilookup-ilookupdesign.md#color) |color: string (optional)  <br>|The foreground color of the container.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[color](../interfaces/view-model-ipage-idesign.md#color) <br> |
| [flexFlow](../interfaces/view-model-control-lookup-ilookup-ilookupdesign.md#flexflow) |flexFlow: string (optional)  <br>|Specifying this property makes the component a flex container component.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[flexFlow](../interfaces/view-model-ipage-idesign.md#flexflow) <br> |
| [flexSize](../interfaces/view-model-control-lookup-ilookup-ilookupdesign.md#flexsize) |flexSize: string (optional)  <br>|One number or two numbers written as a string. For example, "(size to grow) [(size-to-shrink)]" to accommodate available space in the immediate flex container.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[flexSize](../interfaces/view-model-ipage-idesign.md#flexsize) <br> |
| [fontSize](../interfaces/view-model-control-lookup-ilookup-ilookupdesign.md#fontsize) |fontSize: "medium" &#124; "xx-small" &#124; "x-small" &#124; "small" &#124; "large" &#124; "x-large" &#124; "xx-large" (optional)  <br>|The proportional text size<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[fontSize](../interfaces/view-model-ipage-idesign.md#fontsize) <br> |
| [fontWeight](../interfaces/view-model-control-lookup-ilookup-ilookupdesign.md#fontweight) |fontWeight: "normal" &#124; "bold" (optional)  <br>|Normal or bold text.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[fontWeight](../interfaces/view-model-ipage-idesign.md#fontweight) <br> |
| [justifyItems](../interfaces/view-model-control-lookup-ilookup-ilookupdesign.md#justifyitems) |justifyItems: "flex-start" &#124; "flex-end" &#124; "center" &#124; "space-between" (optional)  <br>|This property is an alias for the CSS property "justify-content".<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[justifyItems](../interfaces/view-model-ipage-idesign.md#justifyitems) <br> |
| [label](../interfaces/view-model-control-lookup-ilookup-ilookupdesign.md#label) |label: string (optional)  <br>|  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[label](../interfaces/view-model-ipage-idesign.md#label) <br> |
| [labelPosition](../interfaces/view-model-control-lookup-ilookup-ilookupdesign.md#labelposition) |labelPosition: "stacked" &#124; "hidden" &#124; "inline" (optional)  <br>|Determines how a label is positioned, if at all. By default, labelPosition is set to stacked.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[labelPosition](../interfaces/view-model-ipage-idesign.md#labelposition) <br> |
| [name](../interfaces/view-model-control-lookup-ilookup-ilookupdesign.md#name) |name: string (optional)  <br>|  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[name](../interfaces/view-model-ipage-idesign.md#name) <br> |
| [padding](../interfaces/view-model-control-lookup-ilookup-ilookupdesign.md#padding) |padding: "none" &#124; "small" &#124; "std" (optional)  <br>|Allows specifying the component's padding behavior.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[padding](../interfaces/view-model-ipage-idesign.md#padding) <br> |
| [type](../interfaces/view-model-control-lookup-ilookup-ilookupdesign.md#type) |type: [ControlType](view-model-control-basecontrol-icontrol.md#controltype) (optional)  <br>|The type of the control as a string.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[type](../interfaces/view-model-ipage-idesign.md#type) <br> |


### LookupMetadata

#### Hierarchy

[InputControlMetadata](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md) <br>&nbsp;&nbsp;&nbsp;└─ LookupMetadata <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [BoundEntity](../interfaces/view-model-control-lookup-ilookup-ilookupmetadata.md#boundentity) |BoundEntity: string (optional)  <br>|The entity to which the control is bound.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[BoundEntity](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#boundentity) <br> |
| [BoundField](../interfaces/view-model-control-lookup-ilookup-ilookupmetadata.md#boundfield) |BoundField: string (optional)  <br>|  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[BoundField](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#boundfield) <br> |
| [Description](../interfaces/view-model-control-lookup-ilookup-ilookupmetadata.md#description) |Description: string (optional)  <br>|Description of the control.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Description](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#description) <br> |
| [DisplayField](../interfaces/view-model-control-lookup-ilookup-ilookupmetadata.md#displayfield) |DisplayField: string (optional)  <br>|The name of a control on the page, whose value should be displayed to the user. Usually, this value is user-friendly user-readable text.<br>  |
| [DisplayKey](../interfaces/view-model-control-lookup-ilookup-ilookupmetadata.md#displaykey) |DisplayKey: string (optional)  <br>|  |
| [Editable](../interfaces/view-model-control-lookup-ilookup-ilookupmetadata.md#editable) |Editable: boolean (optional)  <br>|Boolean indicating if the control is editable.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Editable](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#editable) <br> |
| [ExtType](../interfaces/view-model-control-lookup-ilookup-ilookupmetadata.md#exttype) |ExtType: [ControlType](view-model-control-basecontrol-icontrol.md#controltype) (optional)  <br>|The extended control type. For example, a control of type Input might have an extended type of Barcode.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[ExtType](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#exttype) <br> |
| [FilterContext](../interfaces/view-model-control-lookup-ilookup-ilookupmetadata.md#filtercontext) |FilterContext: DataFilter (optional)  <br>|  |
| [HelpText](../interfaces/view-model-control-lookup-ilookup-ilookupmetadata.md#helptext) |HelpText: string (optional)  <br>|The keyboard shortcut for a command. For example, "(Shift+F5)"<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[HelpText](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#helptext) <br> |
| [Hidden](../interfaces/view-model-control-lookup-ilookup-ilookupmetadata.md#hidden) |Hidden: boolean (optional)  <br>|Boolean indicating if the control is hidden or not.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Hidden](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#hidden) <br> |
| [Id](../interfaces/view-model-control-lookup-ilookup-ilookupmetadata.md#id) |Id: string (optional)  <br>|Identification string for a control.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Id](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#id) <br> |
| [Label](../interfaces/view-model-control-lookup-ilookup-ilookupmetadata.md#label) |Label: string (optional)  <br>|Label for a control. For example, a control representing a person's first name might have a label "First Name".<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Label](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#label) <br> |
| [LookupEntity](../interfaces/view-model-control-lookup-ilookup-ilookupmetadata.md#lookupentity) |LookupEntity: any (optional)  <br>|The entity that is being looked up in the lookup.<br>  |
| [LookupPage](../interfaces/view-model-control-lookup-ilookup-ilookupmetadata.md#lookuppage) |LookupPage: string (optional)  <br>|  |
| [LookupPageId](../interfaces/view-model-control-lookup-ilookup-ilookupmetadata.md#lookuppageid) |LookupPageId: string (optional)  <br>|  |
| [Mandatory](../interfaces/view-model-control-lookup-ilookup-ilookupmetadata.md#mandatory) |Mandatory: boolean (optional)  <br>|If set to true then input for the control is required for the task to be completed. Mandatory controls will have a red outline.<br>  Inherited from [InputControlMetadata](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md).[Mandatory](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md#mandatory) <br> |
| [MultiSelect](../interfaces/view-model-control-lookup-ilookup-ilookupmetadata.md#multiselect) |MultiSelect: boolean (optional)  <br>|If true, lookup will be configured as a multi-select.<br>  |
| [Name](../interfaces/view-model-control-lookup-ilookup-ilookupmetadata.md#name) |Name: string (optional)  <br>|Name of a control.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Name](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#name) <br> |
| [NumSequence](../interfaces/view-model-control-lookup-ilookup-ilookupmetadata.md#numsequence) |NumSequence: [NumberSequenceConfig](../interfaces/view-model-control-basecontrol-iinputcontrol-inumbersequenceconfig.md) (optional)  <br>|Used for auto detecting and changing visibility of the number sequence controls in the task or page, based on AX number sequence configuration, through extended business logic.<br>  Inherited from [InputControlMetadata](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md).[NumSequence](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md#numsequence) <br> |
| [Order](../interfaces/view-model-control-lookup-ilookup-ilookupmetadata.md#order) |Order: number (optional)  <br>|Number indicating the order in which a control will appear on a page.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Order](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#order) <br> |
| [ReferenceAppId](../interfaces/view-model-control-lookup-ilookup-ilookupmetadata.md#referenceappid) |ReferenceAppId: string (optional)  <br>|  |
| [ShowLookupPage](../interfaces/view-model-control-lookup-ilookup-ilookupmetadata.md#showlookuppage) |ShowLookupPage: boolean (optional)  <br>|  |
| [Type](../interfaces/view-model-control-lookup-ilookup-ilookupmetadata.md#type) |Type: [ControlType](view-model-control-basecontrol-icontrol.md#controltype) (optional)  <br>|String indicating the control type.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Type](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#type) <br> |
| [ValueField](../interfaces/view-model-control-lookup-ilookup-ilookupmetadata.md#valuefield) |ValueField: string (optional)  <br>|The name of a control on the page, whose value should be used when committing the data. Usually, this value is a unique key.<br>  |
| [ValueKey](../interfaces/view-model-control-lookup-ilookup-ilookupmetadata.md#valuekey) |ValueKey: string (optional)  <br>|  |

#### Events

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [OnOptionSelected](../interfaces/view-model-control-lookup-ilookup-ilookupmetadata.md#onoptionselected) |OnOptionSelected: function(lookup: any, lookupEntityData: any): void (optional)  <br>|An event that is triggered by an option being selected.<br>  |
| [OnValueChanged](../interfaces/view-model-control-lookup-ilookup-ilookupmetadata.md#onvaluechanged) |OnValueChanged: function(value: any): void (optional)  <br>|An event that is triggered by a value being changed.<br>  |



[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]
