---
title: Business logic events
description: Learn about code that executes in business logic can make runtime modifications to the metadata of Pages, Actions, and Controls.
author: jasongre
ms.author: jasongre
ms.topic: overview
ms.date: 03/17/2026
ms.reviewer: johnmichalak
ms.collection: get-started
ms.search.region: Global
ms.search.validFrom: 2016-11-30
ms.custom: 
  - bap-template
---

# Business logic events

[!include [banner](../../includes/banner.md)]
[!include [mobile app deprecated](../../includes/mobile-app-deprecation-banner.md)]

By using mobile workspace business logic events, developers can specify workspace configuration to enhance capability and implement business-scenario-specific behaviors. All mobile business logic runs in the process of the mobile app. The Operations mobile app framework controls the business logic execution flow. 

Code that runs in business logic can make runtime modifications to the metadata of pages, actions, and controls. These runtime modifications overlayer the static metadata that the app caches, but they don't directly change the cached static metadata or affect the static metadata that the server stores. These runtime modifications persist only until the app closes.

Code that runs in the business logic of the app can make runtime modifications to business data that the app stores. When you follow correct practices, these modifications participate in the normal data processing framework like other business data in the app. This framework means adhering to the offline-first capabilities and asynchronous save behaviors that the framework provides.

[!INCLUDE [footer-include](../../../../includes/footer-banner.md)]
