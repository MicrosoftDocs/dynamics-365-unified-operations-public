---
# required metadata
title: EventHook
description: 
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

# EventHook Type&lt;T&gt;


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

