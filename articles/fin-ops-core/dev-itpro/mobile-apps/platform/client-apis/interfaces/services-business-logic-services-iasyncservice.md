---
title: AsyncService type
description: Provides ability to perform async operations from business logic code.
author: jasongre
ms.date: 05/24/2022
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: jasongre
---

# AsyncService type

[!include [banner](../../../../includes/banner.md)]
[!include [mobile app deprecated](../../../../includes/mobile-app-deprecation-banner.md)]

Provides ability to perform async operations from business logic code.

### Hierarchy

AsyncService

## Index

### Method list

* [all](services-business-logic-services-iasyncservice.md#all)
* [defer](services-business-logic-services-iasyncservice.md#defer)

## Methods

### all

`all(...args: any [ ]): Promise <any [ ]>`

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| ...args|any [ ]||

#### Returns Promise &lt;any [ ]&gt;

### defer

`defer <>(): [Deferred](defer-ideferred.md) <>`

Creates a deferred object that can be used to return a promise from event handlers (where applicable) and resolve/reject them asynchronously.

#### Returns [Deferred](defer-ideferred.md) &lt;T&gt;


[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]
