---
# required metadata

title: Organization hierarchy on Common Data Service
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

## Organization hierarchy on Common Data Service

Finance and Operations, being a financial system, considers *Organization* to be a core concept and the system setup starts with configuring an organization hierarchy. This allows business financials and operations to be tracked at the organization level as well as any level within the organization hierarchy. Common Data Service (CDS) does not contain the organization hierarchy concept but it has a few loose concepts like total sales revenue. As part of CDS integration, the organization hierarchy data structure is added to CDS.

## Data flow

If a business eco-system is made up of Finance and Operations and CDS, it will continue to have organization hierarchy built on Finance and Operations but exposed in CDS for information and extensibility. The following organization hierarchy information is exposed in CDS as a one-way data flowing from Finance and Operations to CDS.

![architecture image](media/dual-write-data-flow.png)

## Templates

Organization hierarchy entity maps are available to synchronize data one-way from Finance and Operations to CDS.

## Internal Organization Hierarchy Purpose

Provides one-way synchronization of internal organization hierarchy purpose information from Finance and Operations to Customer Engagement.

![architecture image](media/dual-write-purpose.png)

## Internal Organization Hierarchy Type

Provides one-way synchronization of internal organization hierarchy type information from Finance and Operations to Customer Engagement.

![architecture image](media/dual-write-type.png)

## Internal Organization Hierarchy

Provides one-way synchronization of internal organization hierarchy information from Finance and Operations to Customer Engagement.

![architecture image](media/dual-write-organization.png)

## Internal Organization

Internal organization information in CDS comes from 2 entities of Finance and Operations, **operating unit** and **legal entities**.

![architecture image](media/dual-write-operating-unit.png)

![architecture image](media/dual-write-legal-entities.png)

## Company

Provies bidirectional synchronization of legal entity (company) information between Finance and Operations and Customer Engagement.

![architecture image](media/dual-write-company.png)


