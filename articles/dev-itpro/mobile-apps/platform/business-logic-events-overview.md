---
# required metadata

title: Business logic events overview
description: Code that executes in business logic can make runtime modifications to the metadata of Pages, Actions and Controls.
author: makhabaz
manager: AnnBe
ms.date: 08/14/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: Operations, Platform
# ms.tgt_pltfrm: 
ms.custom: 255544
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: makhabaz
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Platform update 3

---

# Business logic events overview
Mobile workspace business logic events provide places for developers to specify workspace configuration to enhace capability, and implement business-scenario-specific behaviors. All mobile business logic executes in the process of the mobile app, and busines logic execution flow is controlled by the Operations mobile app framework. 

Code that executes in business logic can make runtime modifications to the metadata of Pages, Actions and Controls. These runtime modifications will overlayer the static metadata that is cached in the app, but the modifications do not directly change the cached static metadata, nor do they affect the static metadata that is stored on the server. These runtime modifications only persist until the app is closed. 

Code that executes in the business logic of the app can make runtime modifications to business data that is stored in the app. These modifications (when performed according to correct practices) participate in the normal data processing framework as other business data in the app. That means adhering to the offline-first capabilities and asycnrhonous save behaviors provided by the framework.

