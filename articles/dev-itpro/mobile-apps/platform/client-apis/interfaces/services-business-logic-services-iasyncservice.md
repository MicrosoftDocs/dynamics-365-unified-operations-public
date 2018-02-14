---
# required metadata
title: AsyncService
description: Provides ability to perform async operations from business logic code.
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
ms.reviewer: robinr
ms.search.scope: 
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: Global
# ms.search.industry: 
ms.author: kashea
ms.search.validFrom:
ms.dyn365.ops.version:
---

# AsyncService Type
Provides ability to perform async operations from business logic code.

### Hierarchy

AsyncService <br>

## Index

### Methods

* [all](services-business-logic-services-iasyncservice.md#all)
* [defer](services-business-logic-services-iasyncservice.md#defer)

## Methods

### all


all(...args: any [ ]): Promise &lt;any [ ]&gt;




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| ...args|any [ ]||

#### Returns Promise &lt;any [ ]&gt;

### defer


defer &lt;T&gt;(): [Deferred](defer-ideferred.md) &lt;T&gt;

Creates a deferred object which can be used to return a promise from event handlers (where applicable) and resolve/reject them asynchronously.

#### Returns [Deferred](defer-ideferred.md) &lt;T&gt;

