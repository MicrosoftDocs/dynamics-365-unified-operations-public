---
# required metadata
title: Deferred
description: Deferred type
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

# Deferred Type&lt;T&gt;


### Hierarchy

Deferred <br>

## Index

### Properties

* [promise](defer-ideferred.md#promise)

### Methods

* [reject](defer-ideferred.md#reject)
* [resolve](defer-ideferred.md#resolve)

## Properties

### promise

promise: Promise &lt;T&gt;




## Methods

### reject


reject(error?: any): void




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| error?|any||

#### Returns void

### resolve


resolve(value?: T &#124; PromiseLike &lt;T&gt;): void




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| value?|T &#124; PromiseLike &lt;T&gt;||

#### Returns void

