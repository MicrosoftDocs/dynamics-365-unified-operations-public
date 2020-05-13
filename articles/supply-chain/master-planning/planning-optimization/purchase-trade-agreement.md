---
# required metadata

title: Purchase trade agreement
description: This topic describes how Planning Optimization can select vendor and lead time from purchase trade agreements.
author: ChristianRytt
manager: tfehr
ms.date: 12/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ReqCreatePlanWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: crytt
ms.search.validFrom: 2020-5-12
ms.dyn365.ops.version: AX 10.0.12

---
# Purchase trade agreement

[!include [banner](../../includes/banner.md)]

This topic describes how Planning Optimization can select vendor and lead time from purchase trade agreements, based on best price or lead time.

The feature is available from version 10.0.12 and must be enabled via feature management.

## Setup needed for master planning to consider purchase trade agreements

### Master planning parameters

Vendor:

- **Find trade agreement** ( **Yes** / **No** )
- **Search criterion** ( **Minimum lead time** / **Lowest unit price** )

**Find trade agreement** control if master planning is looking for purchase trade agreements at all. When activated the selection of purchase trade agreement can be based on **Minimum lead time** or **Lowest unit price**.

### Checklist

Here follows a checklist of required setups for vendor and/or lead time to originate from purchase trade agreement during master planning:

- Master planning parameters: **Find trade agreement** = **Yes**
- Procurement and sourcing, Activate price/discount: **Vendor** = **Yes**
- Storage dimension group with **Storage dimension** setup to include **For purchase prices**
- No vendor added on the related **Released product**
- **Item coverage** do not overwrite vendor
- Supply is not coming from a **Supply forecast** with vendor specified
- Purchase trade agreement exist and **Ignore lead time** = **No** if **Lead time** should originate from purchase trade agreement

### Determining vendor and lead time

There are many parameters that controls the vendor and lead time for a planned purchase order created by master planning. The following table provides an overview, with examples of the setup options and the related result on the planned purchase order.

| **Released product** | **Default order settings** | **Item coverage** | **Item coverage** | **Trade agreement** | **Trade agreement** | **Trade agreement** | **Planned order** | **Planned order** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| **Vendor** | **Lead time** | **Vendor is overwritten** | **Lead time is overwritten** | **Vendor** | **Lead time** | **Ignore lead time** | **Vendor** | **Lead time** |
| **US001** | **1** | No | No | US003 | 3 | NO | **US001** | **1** |
| US001 | 1 | **Yes, US002** | **Yes, 2** | US003 | 3 | NO | **US002** | **2** |
| &#39;blank&#39;  | 1 | No | No | **US003** | **3** | NO | **US003** | **3** |
|  &#39;blank&#39; | **1** | No | No | **US003** | 3 | YES | **US003** | **1** |
|  &#39;blank&#39; | **1** | **Yes, US002** | No | US003 | 3 | NO | **US002** | **1** |
|  &#39;blank&#39; | **1** | **Yes, US002** | No | US002 | 3 | NO | **US002** | **1** |
|  &#39;blank&#39; | 1 | No | Yes, 2 | **US003** | **3** | NO | **US003** | **3** |
|  &#39;blank&#39; | 1 | No | **Yes, 2** | **US003** | 3 | YES | **US003** | **2** |


## Additional resources

[Purchase agreements](https://docs.microsoft.com/en-us/dynamics365/supply-chain/procurement/purchase-agreements)
