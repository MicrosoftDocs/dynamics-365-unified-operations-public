---
title: DataService type
description: Learn about the DataService type, which provides ability access data under the application workspace, including the findEntityData and get PageData methods.
author: jasongre
ms.author: jasongre
ms.topic: article
ms.date: 05/24/2022
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
---

# DataService type

[!include [banner](../../../../includes/banner.md)]
[!include [mobile app deprecated](../../../../includes/mobile-app-deprecation-banner.md)]

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
