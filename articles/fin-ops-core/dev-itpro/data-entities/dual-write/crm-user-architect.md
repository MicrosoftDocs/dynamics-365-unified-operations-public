---
# required metadata

title: Dual-write and customer relationship management products
description: 
author: shsrav
manager: AnnBe
ms.date: 01/06/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: ramasri
ms.dyn365.ops.version: 
ms.search.validFrom: 2020-01-06

---

# What does dual-write mean for users and architects of customer relationship management products? 

[!include [banner](../../includes/banner.md)]

[!include [banner](../../includes/preview-banner.md)]

Dual-write automates the data flow between Finance and Operations apps and Common Data Service. In future releases, concepts in model-driven apps in Dynamics 365 like customer, contact, quotation, and order will scale to mid- and upper-mid market customers. 

In the first release, most of the automation is handled by dual-write solutions. In future releases, these solutions will become part of the Common Data Service. Understanding the upcoming changes to the Common Data Service will save you effort in the long run. Some of the crucial revisions are: 
+ Common Data Service will have new concepts like company and party. These concepts will impact all applications built on Common Data Service, including Sales, Marketing, Customer Service, and Field Service. 
+ Activities and notes are unified and expanded to support both C1s (users of the system) and C2s (customers of the system). 
+ Upcoming changes in the Common Data Service include:
    - The decimal data type will replace the money data type.
    - Date effectivity will support past, present, and future data in the same place.
    - There will be more support for currency and exchange rates, including a revision of the **Exchange Rate** API.
    - Unit conversions will be supported.

For more information on upcoming changes, see [Data in Common Data Service – phase 1 & 2](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/extensibility/extensibility-roadmap).
