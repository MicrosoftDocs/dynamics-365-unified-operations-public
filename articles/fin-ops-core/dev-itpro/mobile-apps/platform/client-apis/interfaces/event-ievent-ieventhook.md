---
title: EventHook type<T>
description: Learn about the EventHook type, including learning about the subscribe, unsubscribe, and unsubscribeAll methods and parameters.
author: jasongre
ms.author: jasongre
ms.topic: article
ms.date: 05/24/2022
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
---

# EventHook type&lt;T&gt;

[!include [banner](../../../../includes/banner.md)]
[!include [mobile app deprecated](../../../../includes/mobile-app-deprecation-banner.md)]

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
