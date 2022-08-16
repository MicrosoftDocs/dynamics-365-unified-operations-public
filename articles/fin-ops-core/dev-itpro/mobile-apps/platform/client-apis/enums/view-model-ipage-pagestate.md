---
title: PageState enumeration
description: Represents the various high-level states the page can be in.
author: jasongre
ms.date: 05/24/2022
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: jasongre
---

# PageState enumeration

[!include [banner](../../../../includes/banner.md)]
[!include [mobile app deprecated](../../../../includes/mobile-app-deprecation-banner.md)]

Represents the various high-level states the page can be in.

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




[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]
