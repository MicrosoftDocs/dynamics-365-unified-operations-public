---
# required metadata
title: Event
description: Event module
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

# Event 


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




