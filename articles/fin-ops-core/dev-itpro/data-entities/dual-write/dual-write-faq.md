---
# required metadata

title: Dual-write frequently asked questions
description: This topic answers frequently asked questions.
author: robinarh
manager: AnnBe
ms.date: 07/21/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 21311
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: rhaertle
ms.search.validFrom: 2020-07-21
ms.dyn365.ops.version: AX 7.0.0

---

# Dual-write frequently asked questions

[!include [banner](../../includes/banner.md)]

## Setup
### Is dual write available for Government Community Cloud (GCC)?
Not yet. 
Dual write requires Finance and Operations apps environment and CDS environment to be in the same tenant. Since Finance and Operations apps is not available in GCC yet, dual write doesn’t support linking Finance and Operations apps/CDS across two different tenants.
### If a customer doesn't have sales or field service, but they just want to have the sales order data in CDS, can they do it without buying sales/CE license?
When customers possess a valid Finance and Operations applications license, they are entitled to enable dual write between the Common Data Service and Finance and Operations applications. This entitlement does not include capacity consumed by the replicated data; if necessary, this is purchased separately. This entitlement does not include use rights for the Dynamics 365 for Customer Engagement applications, including Sales, Service, Marketing, etc; if necessary, this is purchased separately.
### Any plans to let DW use CDS as a hub between multiple F&O instances, allowing for data to synchronize between two or  more F&O instances?
The current plan of record is to restrict this to 1-1 mapping between F&O and CDS.
