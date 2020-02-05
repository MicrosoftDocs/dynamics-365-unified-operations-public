---
# required metadata

title: What does dual-write mean for CRM users and CRM architects?
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
ms.author: 
ms.dyn365.ops.version: 
ms.search.validFrom: 2020-01-06

---

# What does dual-write mean for CRM users and CRM architects? 

[!include [banner](../../includes/banner.md)]

[!include [banner](../../includes/preview-banner.md)]

Dual-write automates the data flow between Finance and Operations apps and Common Data Service. Concepts in model-driven apps like the customer, contact, quotation, and order will scale to mid and upper-mid market customers. 

At the start, most of these changes are coming from dual-write solutions. The plan is to merge these solutions to the Common Data Service platform soon. We recommend the users to understand dual-write and embrace it from start to avoid future surprises. Some of the crucial revisions are: 
+ Common Data Service has new concepts like company and party. These concepts will impact all applications built on Common Data Service, including Sales, Marketing, Customer Service, and Field Service. 
+ 'Activities' and 'Notes' are unified and expanded to support both C1s (users of the system) and C2s (customers of the system). 
+ Common Data Service platform is getting revised, which includes the following:
    - **Decimal** data type will replace **Money**.
    - New **Date Effectivity** framework will accommodate past, present, and future data at the same place.
    - More support for **Currency** and **Exchange Rates**, and this includes the revision of Exchange Rate API.
    - Unit conversions will be possible.

For more information about dual-write, see the [Dual-write overview](dual-write-purpose.md). 
