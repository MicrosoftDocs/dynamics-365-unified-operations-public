---
title: EventHook type<T>
description: EventHook type
author: tonyafehr
ms.date: 08/01/2017
  
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: tfehr
---

# EventHook type&lt;T&gt;

[!include [banner](../../../../includes/banner.md)]

### Hierarchy

EventHook <br>

## Index

### Methods

* [subscribe](event-ievent-ieventhook.md#subscribe)
* [unsubscribe](event-ievent-ieventhook.md#unsubscribe)
* [unsubscribeAll](event-ievent-ieventhook.md#unsubscribeall)

## Methods

### subscribe


subscribe(listener: [IEventListener](../modules/event-ievent.md#ieventlistener) &lt;T&gt;): void

Subscribe a listener to this event.


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| listener|[IEventListener](../modules/event-ievent.md#ieventlistener) &lt;T&gt;||

#### Returns void

### unsubscribe


unsubscribe(listener: [IEventListener](../modules/event-ievent.md#ieventlistener) &lt;T&gt;): void

Unsubscribe a listener from this event.


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| listener|[IEventListener](../modules/event-ievent.md#ieventlistener) &lt;T&gt;||

#### Returns void

### unsubscribeAll


unsubscribeAll(): void

Remove all listeners from this event.

#### Returns void



[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]