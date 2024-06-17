---
title: LookupMetadata type
description: Learn about the lookup metadata type, which includes the BoundEntity, BoundField, Description, DisplayField, DisplayKey, and other properties.
author: jasongre
ms.author: jasongre
ms.topic: article
ms.date: 05/24/2022
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
---

# LookupMetadata type

[!include [banner](../../../../includes/banner.md)]
[!include [mobile app deprecated](../../../../includes/mobile-app-deprecation-banner.md)]

Lookup metadata type.

### Hierarchy

[InputControlMetadata](view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md) <br>&nbsp;&nbsp;&nbsp;└─ LookupMetadata <br>

## Index

### Properties

* [BoundEntity](view-model-control-lookup-ilookup-ilookupmetadata.md#boundentity)
* [BoundField](view-model-control-lookup-ilookup-ilookupmetadata.md#boundfield)
* [Description](view-model-control-lookup-ilookup-ilookupmetadata.md#description)
* [DisplayField](view-model-control-lookup-ilookup-ilookupmetadata.md#displayfield)
* [DisplayKey](view-model-control-lookup-ilookup-ilookupmetadata.md#displaykey)
* [Editable](view-model-control-lookup-ilookup-ilookupmetadata.md#editable)
* [ExtType](view-model-control-lookup-ilookup-ilookupmetadata.md#exttype)
* [FilterContext](view-model-control-lookup-ilookup-ilookupmetadata.md#filtercontext)
* [HelpText](view-model-control-lookup-ilookup-ilookupmetadata.md#helptext)
* [Hidden](view-model-control-lookup-ilookup-ilookupmetadata.md#hidden)
* [Id](view-model-control-lookup-ilookup-ilookupmetadata.md#id)
* [Label](view-model-control-lookup-ilookup-ilookupmetadata.md#label)
* [LookupEntity](view-model-control-lookup-ilookup-ilookupmetadata.md#lookupentity)
* [LookupPage](view-model-control-lookup-ilookup-ilookupmetadata.md#lookuppage)
* [LookupPageId](view-model-control-lookup-ilookup-ilookupmetadata.md#lookuppageid)
* [Mandatory](view-model-control-lookup-ilookup-ilookupmetadata.md#mandatory)
* [MultiSelect](view-model-control-lookup-ilookup-ilookupmetadata.md#multiselect)
* [Name](view-model-control-lookup-ilookup-ilookupmetadata.md#name)
* [NumSequence](view-model-control-lookup-ilookup-ilookupmetadata.md#numsequence)
* [Order](view-model-control-lookup-ilookup-ilookupmetadata.md#order)
* [ReferenceAppId](view-model-control-lookup-ilookup-ilookupmetadata.md#referenceappid)
* [ShowLookupPage](view-model-control-lookup-ilookup-ilookupmetadata.md#showlookuppage)
* [Type](view-model-control-lookup-ilookup-ilookupmetadata.md#type)
* [ValueField](view-model-control-lookup-ilookup-ilookupmetadata.md#valuefield)
* [ValueKey](view-model-control-lookup-ilookup-ilookupmetadata.md#valuekey)

### Events

* [OnOptionSelected](view-model-control-lookup-ilookup-ilookupmetadata.md#onoptionselected)
* [OnValueChanged](view-model-control-lookup-ilookup-ilookupmetadata.md#onvaluechanged)

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


### DisplayField

DisplayField: string (optional) 

The name of a control on the page, whose value should be displayed to the user. Usually, this value is user-friendly/user-readable text.


### DisplayKey

DisplayKey: string (optional) 




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


### FilterContext

FilterContext: DataFilter (optional) 




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


### LookupEntity

LookupEntity: any (optional) 

The entity that is being looked up in the lookup.


### LookupPage

LookupPage: string (optional) 




### LookupPageId

LookupPageId: string (optional) 




### Mandatory

Mandatory: boolean (optional) 

If set to true then input for the control is required for the task to be completed.
Mandatory controls will have a red outline.

> Inherited from [InputControlMetadata](view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md).[Mandatory](view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md#mandatory)


### MultiSelect

MultiSelect: boolean (optional) 

If true, lookup will be configured as a multi-select.


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




### ShowLookupPage

ShowLookupPage: boolean (optional) 




### Type

Type: [ControlType](../modules/view-model-control-basecontrol-icontrol.md#controltype) (optional) 

String indicating the control type.

> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Type](view-model-control-basecontrol-icontrol-icontrolmetadata.md#type)


### ValueField

ValueField: string (optional) 

The name of a control on the page, whose value should be used when committing the data. Usually, this value is a unique key.


### ValueKey

ValueKey: string (optional) 




## Events

### OnOptionSelected

OnOptionSelected: function(lookup: any, lookupEntityData: any): void (optional) 

An event that is triggered by an option being selected.


### OnValueChanged

OnValueChanged: function(value: any): void (optional) 

An event that is triggered by a value being changed.




[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]
