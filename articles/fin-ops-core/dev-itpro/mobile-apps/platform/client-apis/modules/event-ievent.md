---
title: Event module
description: Learn about the Event module, which includes the EventHook type, the IEventListener type alias, and various methods.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 12/31/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.custom: 
  - bap-template
---

# Event module

[!include [banner](../../../../includes/banner.md)]
[!include [mobile app deprecated](../../../../includes/mobile-app-deprecation-banner.md)]

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
