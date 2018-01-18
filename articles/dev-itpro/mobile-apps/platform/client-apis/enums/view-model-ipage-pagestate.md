---
# required metadata
title: PageState
description: Represents the various high-level states the a page can be in.
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

# PageState Enumeration
Represents the various high-level states the a page can be in.

## Index

### Enumeration members

* [error](view-model-ipage-pagestate.md#error)
* [loaded](view-model-ipage-pagestate.md#loaded)
* [loading](view-model-ipage-pagestate.md#loading)
* [offline](view-model-ipage-pagestate.md#offline)
* [refreshing](view-model-ipage-pagestate.md#refreshing)

## Enumeration members

### error

error: 
10
The page is currently in the error state, but can be refreshed in an attempt to get out of this state.


### loaded

loaded: 
3
The page is fully loaded and can be refreshed and, if possible, submitted.


### loading

loading: 
2
The page is currently being loaded.


### offline

offline: 
1
The page was loaded in the offline mode, thus not refreshable.


### refreshing

refreshing: 
4
The page is currently refreshing its data.


