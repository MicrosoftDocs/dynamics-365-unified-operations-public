---
title: Deferred type<T>
description: Learn about the Deferred type <T> including the properties, which includes promise, and methods, which include reject and resolve.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 12/31/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.custom: 
  - bap-template
---

# Deferred type&lt;T&gt;

[!include [banner](../../../../includes/banner.md)]
[!include [mobile app deprecated](../../../../includes/mobile-app-deprecation-banner.md)]

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



[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]
