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

[!include [banner](../includes/banner.md)]
[!include [preview](../includes/preview-banner.md)]
[!include [preview](../includes/preview-banner.md)]

Finance and Operations, being a financial system, considers *Organization* to be a core concept and the system setup starts with configuring an organization hierarchy. This allows business financials and operations to be tracked at the organization level as well as any level within the organization hierarchy. Common Data Service (CDS) does not contain the organization hierarchy concept but it has a few loose concepts like total sales revenue. As part of CDS integration, the organization hierarchy data structure is added to CDS.

## Data flow

If a business eco-system is made up of Finance and Operations and CDS, it will continue to have organization hierarchy built on Finance and Operations but exposed in CDS for information and extensibility. The following organization hierarchy information is exposed in CDS as a one-way data flowing from Finance and Operations to CDS.

![architecture image](media/dual-write-data-flow.png)

## Templates

Organization hierarchy entity maps are available to synchronize data one-way from Finance and Operations to CDS.

[!include [banner](../includes/dual-write-symbols.md)]

## Internal Organization Hierarchy Purpose

Provides one-way synchronization of internal organization hierarchy purpose information from Finance and Operations to Customer Engagement.

<!-- ![architecture image](media/dual-write-purpose.png) -->

Source field | Map type | Destination field
---|---|---
HIERARCHYTYPE | > | msdyn_hierarchypurposetypename
HIERARCHYTYPE | > | msdyn_hierarchytype.msdyn_name
HIERARCHYPURPOSE | >> | msdyn_hierarchypurpose
IMMUTABLE | >> | msdyn_immutable
SETASDEFAULT | >> | msdyn_setasdefault


## Internal Organization Hierarchy Type

Provides one-way synchronization of internal organization hierarchy type information from Finance and Operations to Customer Engagement.

<!-- ![architecture image](media/dual-write-type.png) -->

Source field | Map type | Destination field
---|---|---
NAME | > | msdyn_name


## Internal Organization Hierarchy

Provides one-way synchronization of internal organization hierarchy information from Finance and Operations to Customer Engagement.

<!-- ![architecture image](media/dual-write-organization.png) -->

Source field | Map type | Destination field
---|---|---
VALIDTO | > | msdyn_validto
VALIDFROM | > | msdyn_validfrom
HIERARCHYTYPE | > | msdyn_hierarchytypename
PARENTORGANIZATIONPARTYNUMBER | > | msdyn_parentpartyid
CHILDORGANIZATIONPARTYNUMBER | > | msdyn_childpartyid
HIERARCHYTYPE | > | msdyn_hierarchytypeid.msdyn_name
CHILDORGANIZATIONPARTYNUMBER | > | msdyn_childid.msdyn_partynumber
PARENTORGANIZATIONPARTYNUMBER | > | msdyn_parentid.msdyn_partynumber


## Internal Organization

Internal organization information in CDS comes from 2 entities of Finance and Operations, **operating unit** and **legal entities**.

<!-- ![architecture image](media/dual-write-operating-unit.png) -->

<!-- ![architecture image](media/dual-write-legal-entities.png) -->

### Operating unit

Source field | Map type | Destination field
---|---|---
LANGUAGEID | > | msdyn_languageid
NAMEALIAS | > | msdyn_namealias
NAME | > | msdyn_name
PARTYNUMBER | > | msdyn_partynumber
OPERATINGUNITTYPE | >> | msdyn_type

### Legal entity

Source field | Map type | Destination field
---|---|---
NAMEALIAS | > | msdyn_namealias
LANGUAGEID | > | msdyn_languageid
NAME | > | msdyn_name
PARTYNUMBER | > | msdyn_partynumber
none | >> | msdyn_type
LEGALENTITYID | > | msdyn_companycode


## Company

Provies bidirectional synchronization of legal entity (company) information between Finance and Operations and Customer Engagement.

<!-- ![architecture image](media/dual-write-company.png) -->

Source field | Map type | Destination field
---|---|---
NAME | = | cdm_name
LEGALENTITYID | = | cdm_companycode



