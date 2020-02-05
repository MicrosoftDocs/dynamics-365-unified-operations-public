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

Dual-write automates the data flow between Microsoft Dynamics 365 Finance and Operations and Common Data Service. Basic CRM concepts like the 'Customer,' 'Contact,' 'Quotation,' 'Order,' etc. are going through a revision to scale to mid and upper-mid market customers. 

At the start, most of these changes are coming from dual-write solutions. The plan is to merge these solutions to the Common Data Service platform soon. It is in the best interest of CRM folks and CRM architects to understand dual-write and embrace it from start to avoid future surprises. Some of the crucial revisions are: 
+ Common Data Service has new concepts like 'Company' and 'Party'. These concepts will impact all applications built on Common Data Service, including Sales, Marketing, Customer Service, and Field Service. 
+ 'Activities' and 'Notes' are unified and expanded to support both C1s (users of the system) and C2s (customers of the system). 
+ Common Data Service platform is getting revised, which includes the following:
    - 'Decimal' data type replaces 'Money'.
    - New 'Date Effectivity' framework accommodates past, present, and future data at the same place.
    - More support for 'Currency' and 'Exchange Rates,' including revision of Exchange Rate API.
    - Unit conversions are now possible.

For more information about dual-write, see [Dual-write overview](dual-write-purpose.md). 
