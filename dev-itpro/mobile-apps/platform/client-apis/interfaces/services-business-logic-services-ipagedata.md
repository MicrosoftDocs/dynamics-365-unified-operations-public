---
# required metadata
title: PageData
description: Represents the data that is loaded into a page.
author: shadykdc
manager: AnnBe
ms.date: 08/01/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 
# optional metadata
# ms.search.form:
audience: Developer
# ms.devlang: 
# ms.reviewer: robinr
ms.search.scope: 
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: Global
# ms.search.industry: 
ms.author: kashea
ms.search.validFrom:
ms.dyn365.ops.version:
---

# PageData Type
Represents the data that is loaded into a page.

### Hierarchy

PageData <br>

## Index

### Methods

* [getControlValue](services-business-logic-services-ipagedata.md#getcontrolvalue)
* [setControlValue](services-business-logic-services-ipagedata.md#setcontrolvalue)

## Methods

### getControlValue


getControlValue(controlName: string): any

Gets the value of a control directly from the data set loaded in the page.
The "value" is loosely defined across all different types of controls
and generally indicates the primary single field value displayed or interacted with the control. Some complex controls (e.g a lookup or a list)
may not have a simple value and thus cannot be accessed via this API.


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| controlName|string|name of the control whose value is to be retrieved|

#### Returns any

### setControlValue


setControlValue(controlName: string, value: any): any

Sets the value of a control directly into the data set loaded in the page.
The "value" is loosely defined across all different types of controls
and generally indicates the primary single field value displayed or interacted with the control. Some complex controls (e.g a lookup or a list)
may not have a simple value and thus cannot be accessed via this API.


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| controlName|string|Name of the control whose value is to be set|
| value|any|The value to be set|

#### Returns any

