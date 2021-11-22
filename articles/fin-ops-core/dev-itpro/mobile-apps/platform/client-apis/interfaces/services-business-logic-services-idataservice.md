---
title: DataService type
description: Provides ability access data under the application workspace.
author: tonyafehr
ms.date: 08/01/2017
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: tfehr
---

# DataService type

[!include [banner](../../../../includes/banner.md)]

Provides ability access data under the application workspace.

### Hierarchy

DataService <br>

## Index

### Methods

* [findEntityData](services-business-logic-services-idataservice.md#findentitydata)
* [getEntityData](services-business-logic-services-idataservice.md#getentitydata)
* [getPageData](services-business-logic-services-idataservice.md#getpagedata)

## Methods

### findEntityData


findEntityData(entityType: any, propertyName: string, propertyValue: any, includeChanges?: boolean): any




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| entityType|any||
| propertyName|string||
| propertyValue|any||
| includeChanges?|boolean||

#### Returns any

### getEntityData


getEntityData(entityType: any, entityId: string): any




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| entityType|any||
| entityId|string||

#### Returns any

### getPageData


getPageData(pageId: string, context: any, filter: any, allowedStaleness: number): Promise &lt;[PageData](services-business-logic-services-ipagedata.md)&gt;




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| pageId|string||
| context|any||
| filter|any||
| allowedStaleness|number||

#### Returns Promise &lt;[PageData](services-business-logic-services-ipagedata.md)&gt;



[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]