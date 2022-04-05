---
title: Event module
description: Event module
author: tonyafehr
ms.date: 08/01/2017
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: tfehr
---

# Event module

[!include [banner](../../../../includes/banner.md)]

## Index

### Types

* [EventHook](../interfaces/event-ievent-ieventhook.md)

### Type aliases

* [IEventListener](event-ievent.md#ieventlistener)

## Types


### EventHook

#### Hierarchy

EventHook <br>

#### Methods

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [subscribe](../interfaces/event-ievent-ieventhook.md#subscribe) |subscribe(listener: [IEventListener](event-ievent.md#ieventlistener) &lt;T&gt;): void|Subscribe a listener to this event.<br>  |
| [unsubscribe](../interfaces/event-ievent-ieventhook.md#unsubscribe) |unsubscribe(listener: [IEventListener](event-ievent.md#ieventlistener) &lt;T&gt;): void|Unsubscribe a listener from this event.<br>  |
| [unsubscribeAll](../interfaces/event-ievent-ieventhook.md#unsubscribeall) |unsubscribeAll(): void|Remove all listeners from this event.<br>  |

## Type aliases


### IEventListener
IEventListener: function






[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]