---
title: PageData type
description: Learna bout the PageData type, which represents the data that is loaded into a page and includes the getControlValue and setControlValue methods.
author: jasongre
ms.author: jasongre
ms.topic: article
ms.date: 05/24/2022
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
---

# PageData type

[!include [banner](../../../../includes/banner.md)]
[!include [mobile app deprecated](../../../../includes/mobile-app-deprecation-banner.md)]

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



[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]
