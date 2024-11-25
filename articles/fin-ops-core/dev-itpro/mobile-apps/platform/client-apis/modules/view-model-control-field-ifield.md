---
title: Field module
description: Learn about the field module, which represents the run-time instance of a field and include the Field, FieldDesign, and FieldMetadata types.
author: jasongre
ms.author: jasongre
ms.topic: article
ms.date: 05/26/2022
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
---

# Field module

[!include [banner](../../../../includes/banner.md)]
[!include [mobile app deprecated](../../../../includes/mobile-app-deprecation-banner.md)]

Represents the run-time instance of a field.

## Index

### Types

* [Field](../interfaces/view-model-control-field-ifield-ifield.md)
* [FieldDesign](../interfaces/view-model-control-field-ifield-ifielddesign.md)
* [FieldMetadata](../interfaces/view-model-control-field-ifield-ifieldmetadata.md)

## Types


### Field

#### Hierarchy

[InputControl](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontrol.md) <br>&nbsp;&nbsp;&nbsp;└─ Field <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [container](../interfaces/view-model-control-field-ifield-ifield.md#container) |container: boolean (optional)  <br>|True if the control is a container.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[container](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#container) <br> |
| [generic](../interfaces/view-model-control-field-ifield-ifield.md#generic) |generic: boolean (optional)  <br>|  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[generic](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#generic) <br> |
| [getDataSource](../interfaces/view-model-control-field-ifield-ifield.md#getdatasource) |getDataSource: function(): any <br>|  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[getDataSource](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#getdatasource) <br> |
| [hidden](../interfaces/view-model-control-field-ifield-ifield.md#hidden) |hidden: boolean <br>|True if the control is hidden.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[hidden](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#hidden) <br> |

#### Methods

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [applyDesign](../interfaces/view-model-control-field-ifield-ifield.md#applydesign) |applyDesign(IDesign: [FieldDesign](../interfaces/view-model-control-field-ifield-ifielddesign.md)): void|Applies given design to the design on the control.<br>  Overrides [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[applyDesign](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#applydesign) <br> |
| [dataContext](../interfaces/view-model-control-field-ifield-ifield.md#datacontext) |dataContext(): any|  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[dataContext](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#datacontext) <br> |
| [getDesign](../interfaces/view-model-control-field-ifield-ifield.md#getdesign) |getDesign(): [Design](../interfaces/view-model-ipage-idesign.md)|Returns the design object of this control.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[getDesign](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#getdesign) <br> |
| [getEditableFormattedValue](../interfaces/view-model-control-field-ifield-ifield.md#geteditableformattedvalue) |getEditableFormattedValue(): string &#124; number &#124; Date|Gets a formatted decimal string value of an editable field control.<br>  |
| [getEditableValue](../interfaces/view-model-control-field-ifield-ifield.md#geteditablevalue) |getEditableValue(): string &#124; number &#124; Date|Gets the value for an editable field control.<br>  |
| [getEntityRef](../interfaces/view-model-control-field-ifield-ifield.md#getentityref) |getEntityRef(): any|Gets value of entityRef binding to control.<br>  |
| [getFormattedValue](../interfaces/view-model-control-field-ifield-ifield.md#getformattedvalue) |getFormattedValue(): string|Gets a formatted decimal string value.<br>  |
| [getRefLink](../interfaces/view-model-control-field-ifield-ifield.md#getreflink) |getRefLink(): [NavigationArgs](../interfaces/view-model-ipage-inavigationargs.md)|Gets the navigation object for a reference link.<br>  |
| [getValue](../interfaces/view-model-control-field-ifield-ifield.md#getvalue) |getValue(): any|Gets the value for a field control.<br>  |
| [hasRefLink](../interfaces/view-model-control-field-ifield-ifield.md#hasreflink) |hasRefLink(): boolean|Returns true if the field has a refLink, otherwise false.<br>  |
| [hasUnWrapText](../interfaces/view-model-control-field-ifield-ifield.md#hasunwraptext) |hasUnWrapText(): boolean|Gets wrap text property of control.<br>  |
| [isEditable](../interfaces/view-model-control-field-ifield-ifield.md#iseditable) |isEditable(): boolean|Boolean indicating if the control is editable.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[isEditable](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#iseditable) <br> |
| [metadata](../interfaces/view-model-control-field-ifield-ifield.md#metadata) |metadata(): [FieldMetadata](../interfaces/view-model-control-field-ifield-ifieldmetadata.md)|Returns the metadata object of this control.<br>  Overrides [InputControl](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontrol.md).[metadata](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontrol.md#metadata) <br> |
| [parent](../interfaces/view-model-control-field-ifield-ifield.md#parent) |parent(): [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md) &#124; [Page](../interfaces/view-model-ipage-ipage.md)|Returns the parent (control or page) of this control.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[parent](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#parent) <br> |
| [root](../interfaces/view-model-control-field-ifield-ifield.md#root) |root(): [Page](../interfaces/view-model-ipage-ipage.md)|Returns the root form instance (page) of this control.<br>  Inherited from [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md).[root](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md#root) <br> |
| [setEditableValue](../interfaces/view-model-control-field-ifield-ifield.md#seteditablevalue) |setEditableValue(value: string &#124; number &#124; Date): void|Sets the value for an editable field control.<br>  |

#### Events

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [onDataChanged](../interfaces/view-model-control-field-ifield-ifield.md#ondatachanged) |onDataChanged: [EventHook](../interfaces/event-ievent-ieventhook.md) &lt;null&gt; <br>|An event that is triggered when the input control's data changes.<br>  Inherited from [InputControl](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontrol.md).[onDataChanged](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontrol.md#ondatachanged) <br> |


### FieldDesign

#### Hierarchy

[InputControlDesign](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontroldesign.md) <br>&nbsp;&nbsp;&nbsp;└─ FieldDesign <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [alignItems](../interfaces/view-model-control-field-ifield-ifielddesign.md#alignitems) |alignItems: string (optional)  <br>|This property is an alias for the CSS property "align-items".<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[alignItems](../interfaces/view-model-ipage-idesign.md#alignitems) <br> |
| [alignSelf](../interfaces/view-model-control-field-ifield-ifielddesign.md#alignself) |alignSelf: string (optional)  <br>|  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[alignSelf](../interfaces/view-model-ipage-idesign.md#alignself) <br> |
| [bindings](../interfaces/view-model-control-field-ifield-ifielddesign.md#bindings) |bindings: any (optional)  <br>|  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[bindings](../interfaces/view-model-ipage-idesign.md#bindings) <br> |
| [border](../interfaces/view-model-control-field-ifield-ifielddesign.md#border) |border: "none" &#124; "solid" &#124; "left" &#124; "right" &#124; "top" &#124; "bottom" (optional)  <br>|The border behavior of a control. This property will not be inherited by the children.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[border](../interfaces/view-model-ipage-idesign.md#border) <br> |
| [color](../interfaces/view-model-control-field-ifield-ifielddesign.md#color) |color: string (optional)  <br>|The foreground color of the container.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[color](../interfaces/view-model-ipage-idesign.md#color) <br> |
| [flexFlow](../interfaces/view-model-control-field-ifield-ifielddesign.md#flexflow) |flexFlow: string (optional)  <br>|Specifying this property makes the component a flex container component.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[flexFlow](../interfaces/view-model-ipage-idesign.md#flexflow) <br> |
| [flexSize](../interfaces/view-model-control-field-ifield-ifielddesign.md#flexsize) |flexSize: string (optional)  <br>|One number or two numbers written as a string. For example, "(size to grow) [(size-to-shrink)]" to accommodate available space in the immediate flex container.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[flexSize](../interfaces/view-model-ipage-idesign.md#flexsize) <br> |
| [fontSize](../interfaces/view-model-control-field-ifield-ifielddesign.md#fontsize) |fontSize: "medium" &#124; "xx-small" &#124; "x-small" &#124; "small" &#124; "large" &#124; "x-large" &#124; "xx-large" (optional)  <br>|The proportional text size<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[fontSize](../interfaces/view-model-ipage-idesign.md#fontsize) <br> |
| [fontWeight](../interfaces/view-model-control-field-ifield-ifielddesign.md#fontweight) |fontWeight: "normal" &#124; "bold" (optional)  <br>|Normal or bold text.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[fontWeight](../interfaces/view-model-ipage-idesign.md#fontweight) <br> |
| [justifyItems](../interfaces/view-model-control-field-ifield-ifielddesign.md#justifyitems) |justifyItems: "flex-start" &#124; "flex-end" &#124; "center" &#124; "space-between" (optional)  <br>|This property is an alias for the CSS property "justify-content".<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[justifyItems](../interfaces/view-model-ipage-idesign.md#justifyitems) <br> |
| [label](../interfaces/view-model-control-field-ifield-ifielddesign.md#label) |label: string (optional)  <br>|  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[label](../interfaces/view-model-ipage-idesign.md#label) <br> |
| [labelPosition](../interfaces/view-model-control-field-ifield-ifielddesign.md#labelposition) |labelPosition: "stacked" &#124; "hidden" &#124; "inline" (optional)  <br>|Determines how a label is positioned, if at all. By default, labelPosition is set to stacked.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[labelPosition](../interfaces/view-model-ipage-idesign.md#labelposition) <br> |
| [name](../interfaces/view-model-control-field-ifield-ifielddesign.md#name) |name: string (optional)  <br>|  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[name](../interfaces/view-model-ipage-idesign.md#name) <br> |
| [padding](../interfaces/view-model-control-field-ifield-ifielddesign.md#padding) |padding: "none" &#124; "small" &#124; "std" (optional)  <br>|Allows specifying the component's padding behavior.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[padding](../interfaces/view-model-ipage-idesign.md#padding) <br> |
| [type](../interfaces/view-model-control-field-ifield-ifielddesign.md#type) |type: [ControlType](view-model-control-basecontrol-icontrol.md#controltype) (optional)  <br>|The type of the control as a string.<br>  Inherited from [Design](../interfaces/view-model-ipage-idesign.md).[type](../interfaces/view-model-ipage-idesign.md#type) <br> |


### FieldMetadata

#### Hierarchy

[InputControlMetadata](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md) <br>&nbsp;&nbsp;&nbsp;└─ FieldMetadata <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [BoundEntity](../interfaces/view-model-control-field-ifield-ifieldmetadata.md#boundentity) |BoundEntity: string (optional)  <br>|The entity to which the control is bound.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[BoundEntity](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#boundentity) <br> |
| [BoundField](../interfaces/view-model-control-field-ifield-ifieldmetadata.md#boundfield) |BoundField: string (optional)  <br>|  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[BoundField](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#boundfield) <br> |
| [DecimalPlaces](../interfaces/view-model-control-field-ifield-ifieldmetadata.md#decimalplaces) |DecimalPlaces: number (optional)  <br>|The number of decimals that appear on a field of type "Real".<br>  |
| [Description](../interfaces/view-model-control-field-ifield-ifieldmetadata.md#description) |Description: string (optional)  <br>|Description of the control.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Description](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#description) <br> |
| [Editable](../interfaces/view-model-control-field-ifield-ifieldmetadata.md#editable) |Editable: boolean (optional)  <br>|Boolean indicating if the control is editable.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Editable](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#editable) <br> |
| [ExtType](../interfaces/view-model-control-field-ifield-ifieldmetadata.md#exttype) |ExtType: [ControlType](view-model-control-basecontrol-icontrol.md#controltype) (optional)  <br>|The extended control type. For example, a control of type Input might have an extended type of Barcode.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[ExtType](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#exttype) <br> |
| [Formatting](../interfaces/view-model-control-field-ifield-ifieldmetadata.md#formatting) |Formatting: any (optional)  <br>|Formats a field of type "DateTime" or "Date".<br>  |
| [HelpText](../interfaces/view-model-control-field-ifield-ifieldmetadata.md#helptext) |HelpText: string (optional)  <br>|The keyboard shortcut for a command. For example, "(Shift+F5)"<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[HelpText](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#helptext) <br> |
| [Hidden](../interfaces/view-model-control-field-ifield-ifieldmetadata.md#hidden) |Hidden: boolean (optional)  <br>|Boolean indicating if the control is hidden or not.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Hidden](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#hidden) <br> |
| [Id](../interfaces/view-model-control-field-ifield-ifieldmetadata.md#id) |Id: string (optional)  <br>|Identification string for a control.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Id](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#id) <br> |
| [Label](../interfaces/view-model-control-field-ifield-ifieldmetadata.md#label) |Label: string (optional)  <br>|Label for a control. For example, a control representing a person's first name might have a label "First Name".<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Label](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#label) <br> |
| [LinkType](../interfaces/view-model-control-field-ifield-ifieldmetadata.md#linktype) |LinkType: "Telephone" &#124; "Email" &#124; "Url" (optional)  <br>|Assigning the link type of a field allows for the appropriate mobile application to be opened when the link is selected.<br>  |
| [Mandatory](../interfaces/view-model-control-field-ifield-ifieldmetadata.md#mandatory) |Mandatory: boolean (optional)  <br>|If set to true then input for the control is required for the task to be completed. Mandatory controls will have a red outline.<br>  Inherited from [InputControlMetadata](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md).[Mandatory](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md#mandatory) <br> |
| [Name](../interfaces/view-model-control-field-ifield-ifieldmetadata.md#name) |Name: string (optional)  <br>|Name of a control.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Name](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#name) <br> |
| [NumSequence](../interfaces/view-model-control-field-ifield-ifieldmetadata.md#numsequence) |NumSequence: [NumberSequenceConfig](../interfaces/view-model-control-basecontrol-iinputcontrol-inumbersequenceconfig.md) (optional)  <br>|Used for auto detecting and changing visibility of the number sequence controls in the task or page, based on AX number sequence configuration, through extended business logic.<br>  Inherited from [InputControlMetadata](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md).[NumSequence](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md#numsequence) <br> |
| [Order](../interfaces/view-model-control-field-ifield-ifieldmetadata.md#order) |Order: number (optional)  <br>|Number indicating the order in which a control will appear on a page.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Order](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#order) <br> |
| [ReferenceAppId](../interfaces/view-model-control-field-ifield-ifieldmetadata.md#referenceappid) |ReferenceAppId: string (optional)  <br>|The ID of the app that the field control lives in.<br>  |
| [ReferencePageId](../interfaces/view-model-control-field-ifield-ifieldmetadata.md#referencepageid) |ReferencePageId: string (optional)  <br>|The ID of the page that the field control lives in.<br>  |
| [Style](../interfaces/view-model-control-field-ifield-ifieldmetadata.md#style) |Style: string (optional)  <br>|Styles a field of type "DateTime" or "Date".<br>  |
| [Type](../interfaces/view-model-control-field-ifield-ifieldmetadata.md#type) |Type: [ControlType](view-model-control-basecontrol-icontrol.md#controltype) (optional)  <br>|String indicating the control type.<br>  Inherited from [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Type](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md#type) <br> |
| [UnWrapText](../interfaces/view-model-control-field-ifield-ifieldmetadata.md#unwraptext) |UnWrapText: boolean (optional)  <br>|False by default -- text of the page will be wrapped.<br>  |
| [WrapText](../interfaces/view-model-control-field-ifield-ifieldmetadata.md#wraptext) |WrapText: boolean (optional)  <br>|If true then the text of the field control will wrap to the next line.<br>  |



[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]
