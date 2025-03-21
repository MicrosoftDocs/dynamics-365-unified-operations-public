---
title: Business logic events
description: Learn about code that executes in business logic can make runtime modifications to the metadata of Pages, Actions, and Controls.
author: jasongre
ms.author: jasongre
ms.topic: overview
ms.date: 12/31/2024
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

Mobile workspace business logic events provide places for developers to specify workspace configuration to enhance capability, and implement business-scenario-specific behaviors. All mobile business logic executes in the process of the mobile app, and business logic execution flow is controlled by the Operations mobile app framework. 

Code that executes in business logic can make runtime modifications to the metadata of Pages, Actions, and Controls. These runtime modifications overlayer the static metadata that is cached in the app, but the modifications do not directly change the cached static metadata, nor do they affect the static metadata that is stored on the server. These runtime modifications only persist until the app is closed. 

Code that executes in the business logic of the app can make runtime modifications to business data that is stored in the app. These modifications (when performed according to correct practices) participate in the normal data processing framework as other business data in the app. That means adhering to the offline-first capabilities and asynchronous save behaviors provided by the framework.



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
