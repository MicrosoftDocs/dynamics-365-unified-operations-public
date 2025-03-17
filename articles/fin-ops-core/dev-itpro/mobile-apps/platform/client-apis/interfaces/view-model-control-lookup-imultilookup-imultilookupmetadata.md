---
title: MultiLookupMetadata type
description: Learn about the multi-Lookup metadata type, which includes the BoundEntity, BoundField, Description, Design, Editable, and other properties.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 12/31/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.custom: 
  - bap-template
---

# MultiLookupMetadata type

[!include [banner](../../../../includes/banner.md)]
[!include [mobile app deprecated](../../../../includes/mobile-app-deprecation-banner.md)]

Multi-Lookup metadata type.

### Hierarchy

[InputControlMetadata](view-model-control-basecontrol-iinputcontrol-iinputcontrolmetadata.md) <br>&nbsp;&nbsp;&nbsp;└─ MultiLookupMetadata <br>

## Index

### Properties

* [BoundEntity](view-model-control-lookup-imultilookup-imultilookupmetadata.md#boundentity)
* [BoundField](view-model-control-lookup-imultilookup-imultilookupmetadata.md#boundfield)
* [Description](view-model-control-lookup-imultilookup-imultilookupmetadata.md#description)
* [Design](view-model-control-lookup-imultilookup-imultilookupmetadata.md#design)
* [Editable](view-model-control-lookup-imultilookup-imultilookupmetadata.md#editable)
* [ExtType](view-model-control-lookup-imultilookup-imultilookupmetadata.md#exttype)
* [FilterContext](view-model-control-lookup-imultilookup-imultilookupmetadata.md#filtercontext)
* [FilterLocalOnly](view-model-control-lookup-imultilookup-imultilookupmetadata.md#filterlocalonly)
* [HelpText](view-model-control-lookup-imultilookup-imultilookupmetadata.md#helptext)
* [Hidden](view-model-control-lookup-imultilookup-imultilookupmetadata.md#hidden)
* [Id](view-model-control-lookup-imultilookup-imultilookupmetadata.md#id)
* [Label](view-model-control-lookup-imultilookup-imultilookupmetadata.md#label)
* [LookupPageId](view-model-control-lookup-imultilookup-imultilookupmetadata.md#lookuppageid)
* [Mandatory](view-model-control-lookup-imultilookup-imultilookupmetadata.md#mandatory)
* [Name](view-model-control-lookup-imultilookup-imultilookupmetadata.md#name)
* [NumSequence](view-model-control-lookup-imultilookup-imultilookupmetadata.md#numsequence)
* [Order](view-model-control-lookup-imultilookup-imultilookupmetadata.md#order)
* [ReferenceAppId](view-model-control-lookup-imultilookup-imultilookupmetadata.md#referenceappid)
* [ReverseLookupRelation](view-model-control-lookup-imultilookup-imultilookupmetadata.md#reverselookuprelation)
* [ShowPending](view-model-control-lookup-imultilookup-imultilookupmetadata.md#showpending)
* [Type](view-model-control-lookup-imultilookup-imultilookupmetadata.md#type)

### Events

* [OnLookupPageCreate](view-model-control-lookup-imultilookup-imultilookupmetadata.md#onlookuppagecreate)
* [OnLookupPageCreated](view-model-control-lookup-imultilookup-imultilookupmetadata.md#onlookuppagecreated)

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


### Design

Design: [Design](view-model-ipage-idesign.md) (optional) 

Design object for the lookup page that is referenced by the LookupPageId.


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




### FilterLocalOnly

FilterLocalOnly: boolean (optional) 




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


### LookupPageId

LookupPageId: string (optional) 

Page that is hosted within the multi-lookup.


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




### ReverseLookupRelation

ReverseLookupRelation: boolean (optional) 




### ShowPending

ShowPending: boolean (optional) 




### Type

Type: [ControlType](../modules/view-model-control-basecontrol-icontrol.md#controltype) (optional) 

String indicating the control type.

> Inherited from [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md).[Type](view-model-control-basecontrol-icontrol-icontrolmetadata.md#type)


## Events

### OnLookupPageCreate

OnLookupPageCreate: function(args: any, multiLookup: any): void (optional) 




### OnLookupPageCreated

OnLookupPageCreated: function(args: any, multiLookup: any): void (optional) 






[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]
