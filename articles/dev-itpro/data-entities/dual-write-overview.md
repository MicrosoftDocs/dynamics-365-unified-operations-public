---
# required metadata

title: Near-real time data integration between Finance and Operations and Common Data Service
description: 
author: RamaKrishnamoorthy 
manager: AnnBe
ms.date: 07/15/2019
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
ms.search.validFrom: 2019-07-15

---

# Near-real time data integration between Finance and Operations and Common Data Service

In this digital world,  business eco-systems use the Dynamics 365 suite as a whole. Data from people, customers, operations, and IoT devices flows in to one source creating the opportunity for digital feedback loops. To achieve this experience, native integration between Dynamics 365 for Finance and Operations and Dynamics 365 for Customer Engagement applications is essential. Dynamics 365 for Customer Engagement Applications is built on top of Common Data Services (CDS). Finance and Operations data integrating with Common Data Services enables the Customer Engagement applications to communicate with Finance and Operations coherently and fluently.

The Finance and Operations and Common Data Service provide near real-time data synchronization between Dynamics 365 for Finance and Operations and Dynamics 365 for Customer Engagement applications via a dual-write framework. The coverage is broad and spans across 28 surface areas of Dynamics 365 for Finance and Operations. The goal is to provide a "One Dynamics 365" user experience through seamless data flows that connect the business processes across applications.

The following value propositions are available for the customers.

+ [Organization hierarchy in Common Data Service](dual-write-organization.md)
+ [Company concept in Common Data Service](dual-write-company.md)
+ [Integrated customer master](dual-write-customer.md)
+ [Integrated vendor master](dual-write-vendor.md)
+ Unified product master

## System requirements

Synchronous, bidirectional near-real time data flows requires the following versions.

+ Microsoft Dynamics 365 for Finance and Operations, Enterprise edition 10.0.4 Platform Update 28 or higher
+ Dynamics 365 Customer Engagement, Platform version 9.1 (4.2) or higher

For system setup instructions, see [Announcing Dual Write Preview](https://powerapps.microsoft.com/en-us/blog/announcing-dual-write-preview). It includes a [step-by-step guide](https://aka.ms/dualwrite-docs).
