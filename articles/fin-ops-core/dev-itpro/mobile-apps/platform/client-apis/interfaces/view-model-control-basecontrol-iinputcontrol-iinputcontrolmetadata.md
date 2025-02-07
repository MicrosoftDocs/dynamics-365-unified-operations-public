---
title: InputControlMetadata type
description: Learn about the InputControlMetadata type, which includes the BoundEntity, BoundField, Description, Editable, ExtType, and other properties.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 12/31/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.custom: 
  - bap-template
---

# InputControlMetadata type

[!include [banner](../../../../includes/banner.md)]
[!include [mobile app deprecated](../../../../includes/mobile-app-deprecation-banner.md)]

Metadata for input controls.

### Hierarchy

[ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md) <br>&nbsp;&nbsp;&nbsp;└─ InputControlMetadata <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─ [FieldMetadata](view-model-control-field-ifield-ifieldmetadata.md) <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─ [LookupMetadata](view-model-control-lookup-ilookup-ilookupmetadata.md) <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─ [MultiLookupMetadata](view-model-control-lookup-imultilookup-imultilookupmetadata.md) <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─ [ValueMetadata](view-model-control-value-ivalue-ivaluemetadata.md) <br>

## Index

### Properties

* [BoundEntity](view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md#boundentity)
* [BoundField](view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md#boundfield)
* [Description](view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md#description)
* [Editable](view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md#editable)
* [ExtType](view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md#exttype)
* [HelpText](view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md#helptext)
* [Hidden](view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md#hidden)
* [Id](view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md#id)
* [Label](view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md#label)
* [Mandatory](view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md#mandatory)
* [Name](view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md#name)
* [NumSequence](view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md#numsequence)
* [Order](view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md#order)
* [Type](view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md#type)

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


### Mandatory

Mandatory: boolean (optional) 

If set to true then input for the control is required for the task to be completed.
Mandatory controls will have a red outline.


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


### Order

Order: number (optional) 

Number indicating the order in which a control will appear on a page.

> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Order](view-model-control-basecontrol-icontrol-icontrolmetadata.md#order)


### Type

Type: [ControlType](../modules/view-model-control-basecontrol-icontrol.md#controltype) (optional) 

String indicating the control type.

> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Type](view-model-control-basecontrol-icontrol-icontrolmetadata.md#type)




[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]
