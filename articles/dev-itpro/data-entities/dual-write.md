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

In this digital world,  business eco-systems use Dynamics 365 suite as a whole. Data from people, customers, operations and IoT devices flows in to one source creating the opportunity for digital feedback loops. To achieve this experience, native integration between Dynamics 365 for Finance and Operations and Dynamics 365 for Customer Engagement applications is essential. Dynamics 365 for Customer Engagement Applications is built on top of Common Data Services platform. Finance and Operations data integrating with Common Data Services enables the Customer Engagement applications to talk to Finance and Operations coherently and fluently.

The Finance and Operations and Common Data Service provides near real-time data synchronization between Dynamics 365 for Finance and Operations and Dynamics 365 for Customer Engagement applications via dual-write framework. The coverage is pretty broad and spans across 28 surface areas of Dynamics 365 for Finance and Operations. The idea is to give users "One Dynamics 365" user experience through seamless data flows that connect the business processes across applications say from customers, products through financials.

The following value propositions are available for the customers.

-   Organization hierarchy in Common Data Service
-   Company concept in Common Data Service
-   Integrated customer master
-   Integrated vendor master
-   Unified product master

## System requirements for Finance and Operations:

Synchronous, bi-directional near-real time data flows requires the following versions.

-   Microsoft Dynamics 365 for Finance and Operations, Enterprise
    edition 10.0.4 Platform Update 28 or higher
-   Dynamics 365 Customer Engagement, Platform version 9.1 (4.2) or
    higher

For system setup instructions, refer to [Announcing Dual Write Preview](https://powerapps.microsoft.com/en-us/blog/announcing-dual-write-preview). It has step-by-step guide as a PDF at the bottom.

## Organization hierarchy on Common Data Service

F&O being a financial system, considers organization to be a core
concept and the system setup starts with configuring an organization
hierarchy. This allows business financials and operations can be tracked
at the organization level as well as any level within the organization
hierarchy. CDS does not contain organization hierarchy concept but has
few loose concepts like total sales revenue. As part of CDS integration,
we are introducing organization hierarchy data structure in CDS.

### Data flow

If a business eco-system is made up of F&O and CDS, it will continue to
have organization hierarchy built on F&O but exposed in CDS for
information and extensibility. So, the following organization hierarchy
information is exposed in CDS as a one-way data flowing from F&O to CDS.

![architecture image](media/dual-write-data-flow.png)

### Templates

Following organization hierarchy entity maps are available to synchronize data one-way from F&O to CDS.

#### Internal Organization Hierarchy Purpose

One-way synchronization of internal organization hierarchy purpose information from F&O to CE.

![architecture image](media/dual-write-purpose.png)

#### Internal Organization Hierarchy Type

One-way synchronization of internal organization hierarchy type information from F&O to CE.

![architecture image](media/dual-write-type.png)

#### Internal Organization Hierarchy

One-way synchronization of internal organization hierarchy information from F&O to CE.

![architecture image](media/dual-write-organization.png)

#### Internal Organization

Internal organization information in CDS comes from 2 entities of F&O namely "operating unit" and "legal entities".

![architecture image](media/dual-write-operating-unit.png)

![architecture image](media/dual-write-legal-entities.png)

#### Company

Bi-directional synchronization of legal entity (aka company) information between F&O and CE.

![architecture image](media/dual-write-company.png)

## Related Topics

-   Organization Hierarchy in Common Data Service
-   Company concept in Common Data Service
-   Integrated customer master
-   Integrated vendor master
-   Unified product master

