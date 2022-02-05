---
title: Defer module
description: Defer type
author: tonyafehr
ms.date: 08/01/2017
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: tfehr
---

# Defer module

[!include [banner](../../../../includes/banner.md)]

## Index

### Types

* [Deferred](../interfaces/defer-ideferred.md)

### Functions

* [all](defer.md#all)
* [defer](defer.md)
* [reject](defer.md#reject)
* [resolve](defer.md#resolve)

## Types


### Deferred

#### Hierarchy

Deferred <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [promise](../interfaces/defer-ideferred.md#promise) |promise: Promise &lt;T&gt; <br>|  |

#### Methods

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [reject](../interfaces/defer-ideferred.md#reject) |reject(error?: any): void|  |
| [resolve](../interfaces/defer-ideferred.md#resolve) |resolve(value?: T &#124; PromiseLike &lt;T&gt;): void|  |

## Functions


### all
all(...args: any [ ]): Promise &lt;any [ ]&gt;




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| ...args|any [ ]||

#### Returns Promise &lt;any [ ]&gt;


### defer
defer &lt;T&gt;(): [Deferred](../interfaces/defer-ideferred.md) &lt;T&gt;



#### Returns [Deferred](../interfaces/defer-ideferred.md) &lt;T&gt;


### reject
reject(error?: any): Promise &lt;any&gt;




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| error?|any||

#### Returns Promise &lt;any&gt;


### resolve
resolve &lt;T&gt;(value?: T &#124; PromiseLike &lt;T&gt;): Promise &lt;T&gt;




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| value?|T &#124; PromiseLike &lt;T&gt;||

#### Returns Promise &lt;T&gt;



[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]