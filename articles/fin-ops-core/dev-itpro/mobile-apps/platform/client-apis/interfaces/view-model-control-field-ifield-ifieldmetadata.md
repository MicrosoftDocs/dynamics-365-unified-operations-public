---
title: FieldMetadata type
description: Learn about the FieldMetadata type, an interface for field metadata that includes the BoundEntity, BoundField, DecimalPlaces, Description, and other properties.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 12/31/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.custom: 
  - bap-template
---

# FieldMetadata type

[!include [banner](../../../../includes/banner.md)]
[!include [mobile app deprecated](../../../../includes/mobile-app-deprecation-banner.md)]

Interface for field metadata.

### Hierarchy

[InputControlMetadata](view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md) <br>&nbsp;&nbsp;&nbsp;└─ FieldMetadata <br>

## Index

### Properties

* [BoundEntity](view-model-control-field-ifield-ifieldmetadata.md#boundentity)
* [BoundField](view-model-control-field-ifield-ifieldmetadata.md#boundfield)
* [DecimalPlaces](view-model-control-field-ifield-ifieldmetadata.md#decimalplaces)
* [Description](view-model-control-field-ifield-ifieldmetadata.md#description)
* [Editable](view-model-control-field-ifield-ifieldmetadata.md#editable)
* [ExtType](view-model-control-field-ifield-ifieldmetadata.md#exttype)
* [Formatting](view-model-control-field-ifield-ifieldmetadata.md#formatting)
* [HelpText](view-model-control-field-ifield-ifieldmetadata.md#helptext)
* [Hidden](view-model-control-field-ifield-ifieldmetadata.md#hidden)
* [Id](view-model-control-field-ifield-ifieldmetadata.md#id)
* [Label](view-model-control-field-ifield-ifieldmetadata.md#label)
* [LinkType](view-model-control-field-ifield-ifieldmetadata.md#linktype)
* [Mandatory](view-model-control-field-ifield-ifieldmetadata.md#mandatory)
* [Name](view-model-control-field-ifield-ifieldmetadata.md#name)
* [NumSequence](view-model-control-field-ifield-ifieldmetadata.md#numsequence)
* [Order](view-model-control-field-ifield-ifieldmetadata.md#order)
* [ReferenceAppId](view-model-control-field-ifield-ifieldmetadata.md#referenceappid)
* [ReferencePageId](view-model-control-field-ifield-ifieldmetadata.md#referencepageid)
* [Style](view-model-control-field-ifield-ifieldmetadata.md#style)
* [Type](view-model-control-field-ifield-ifieldmetadata.md#type)
* [UnWrapText](view-model-control-field-ifield-ifieldmetadata.md#unwraptext)
* [WrapText](view-model-control-field-ifield-ifieldmetadata.md#wraptext)

## Properties

### BoundEntity

BoundEntity: string (optional) 

The entity to which the control is bound.

> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[BoundEntity](view-model-control-basecontrol-icontrol-icontrolmetadata.md#boundentity)


### BoundField

BoundField: string (optional) 



> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[BoundField](view-model-control-basecontrol-icontrol-icontrolmetadata.md#boundfield)


### DecimalPlaces

DecimalPlaces: number (optional) 

The number of decimals that appear on a field of type "Real".
Default = 2; number must be in the range [0:20].


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


### Formatting

Formatting: any (optional) 

Formats a field of type "DateTime" or "Date".
**Note:** if browser does not support `toLocaleString` with options then it will show the entire value.
<br>The options for Formatting depends on the Style that has been chosen:
 [Style: "DateOnly" options](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/toLocaleDateString),
 [Style: "TimeOnly" options](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/toLocaleTimeString), and
 [options for no style](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/toLocaleString).

<br>Example 1: `{ Style: "TimeOnly", Formatting: { timeZone: "UTC", timeZoneName: "short" } }`

<br>Example 2: `{ Style: "DateOnly", Formatting: { month: "long", day: "numeric" } }` result: March 2


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


### LinkType

LinkType: "Telephone" &#124; "Email" &#124; "Url" (optional) 

Assigning the link type of a field allows for the appropriate mobile application to be opened when the link is selected.


### Mandatory

Mandatory: boolean (optional) 

If set to true then input for the control is required for the task to be completed.
Mandatory controls will have a red outline.

> Inherited from [InputControlMetadata](view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md).[Mandatory](view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md#mandatory)


### Name

Name: string (optional) 

Name of a control.

> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Name](view-model-control-basecontrol-icontrol-icontrolmetadata.md#name)


### NumSequence

NumSequence: [NumberSequenceConfig](view-model-control-basecontrol-iinputcontrol-inumbersequenceconfig.md) (optional) 

Used for auto detecting and changing visibility of the number sequence controls in the task or page,
based on AX number sequence configuration, through extended business logic.
Example:
```javascript
// hide number sequence reference page from users
metadataService.hideNavigation('numSeqReferencePage');

// parameters to be passed to 'numSequence' flag in configureControl
var configParam = {
     referencePageName: 'numSeqReferencePage',
     dataType: 'HcmPersonnelNumberId'
};

// setup 'PersonnelNumber' control as number sequence in the task 'add-worker'
metadataService.configureControl('add-worker', 'PersonnelNumber', { numSequence: configParam });
```

> Inherited from [InputControlMetadata](view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md).[NumSequence](view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md#numsequence)


### Order

Order: number (optional) 

Number indicating the order in which a control will appear on a page.

> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Order](view-model-control-basecontrol-icontrol-icontrolmetadata.md#order)


### ReferenceAppId

ReferenceAppId: string (optional) 

The ID of the app that the field control lives in.


### ReferencePageId

ReferencePageId: string (optional) 

The ID of the page that the field control lives in.


### Style

Style: string (optional) 

Styles a field of type "DateTime" or "Date".
Example: `{ Style: TimeOnly }` result: 12:00:00 AM


### Type

Type: [ControlType](../modules/view-model-control-basecontrol-icontrol.md#controltype) (optional) 

String indicating the control type.

> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Type](view-model-control-basecontrol-icontrol-icontrolmetadata.md#type)


### UnWrapText

UnWrapText: boolean (optional) 

False by default -- text of the page will be wrapped.


### WrapText

WrapText: boolean (optional) 

If true then the text of the field control will wrap to the next line.




[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]
